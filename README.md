# zmk-config-ergodashft

Konfiguracja ZMK dla ErgoDash FT - klasyczny układ ErgoDash z backlight LED i ZMK Studio.

## Hardware

- Shield: `ergodash` (oficjalny shield z upstream ZMK)
- Kontrolery: 2× nice!nano v2
- Wyświetlacze: 2× nice!view (po jednym na każdej połówce)
- Podświetlenie: 70 LED 3mm jednokolorowych (35 per strona) sterowanych MOSFET-em na pinie **D10 / P0.09** (PWM, regulacja jasności)

## Warstwy

| # | Nazwa | Aktywacja | Funkcja |
|---|-------|-----------|---------|
| 0 | DEFAULT (QWERTY) | bazowa | Klasyczny ErgoDash |
| 1 | LOWER | lewy thumb | F1-F12, BT, bootloader |
| 2 | RAISE | prawy thumb | Symbole, strzałki, HOME/END/PGUP/PGDN |
| 3 | ADJ | LOWER + RAISE jednocześnie | studio_unlock, backlight, output toggle |

## Backlight

Sterowanie backlight w warstwie **ADJ** (LOWER + RAISE):
- `BL_TOG` (Q) - włącz/wyłącz
- `BL_INC` (W) - jaśniej
- `BL_DEC` (E) - ciemniej

Domyślnie wyłączony po starcie - musisz włączyć `BL_TOG` ręcznie. Ustawienie zostaje zapisane w pamięci.

## ZMK Studio

Aktywne. Lewa połówka ma snippet `studio-rpc-usb-uart` w `build.yaml`.

**Aby odblokować:** trzymaj LOWER + RAISE (oba kciuki) → wejdziesz w ADJ → naciśnij `A` (studio_unlock). W ZMK Studio na stronie https://zmk.studio kliknij Connect → wybierz port USB → keymap się odblokuje.

## Build

GitHub Actions buduje 3 firmware automatycznie po każdym pushu:
- `ergodash_left-nice_nano-zmk.uf2`
- `ergodash_right-nice_nano-zmk.uf2`
- `settings_reset-nice_nano-zmk.uf2`

Pobierasz z Actions → ostatni run → Artifacts → firmware.

## Flashowanie

1. Lewa połówka USB → 2× reset → `NICENANO` pendrive → przeciągnij `ergodash_left-...uf2`
2. Prawa połówka USB → 2× reset → `NICENANO` → `ergodash_right-...uf2`
3. Połącz TRRS → podłącz lewą do USB → klawiatura "ErgoDash FT" pojawi się w BT

Jeśli połówki się nie łączą: `settings_reset` na obie, potem znów lewa+prawa.

## Zmiana pinu backlight

Backlight jest na pinie D10 (P0.09). Jeśli przeniesiesz tranzystor na inny pin, edytuj `config/ergodash.keymap`:

```dts
&pinctrl {
    pwm0_default: pwm0_default {
        group1 {
            psels = <NRF_PSEL(PWM_OUT0, X, Y)>;  // X=port, Y=numer pinu
        };
    };
    ...
};
```

Mapowanie nice!nano: D5=P0.24, D9=P1.06, D10=P0.09, D0=P0.08.
