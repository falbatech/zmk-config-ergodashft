# zmk-config-ergodashft

## PL

Konfiguracja ZMK dla **ErgoDash FT** - klawiatury ergonomicznej FalbaTech.

## Hardware

- Shield: `ergodash` (custom physical layout w repozytorium FalbaTech)
- Kontrolery: 2x nice!nano v2
- Wyświetlacz: nice!view, Sharp Memory LCD
- Backlight: pojedyncza LED 3mm na PWM
- Pin backlight: D10 / P0.09 przez MOSFET, kanał PWM0
- 70 klawiszy, 5 rzędów x 7 kolumn + 5 thumb na stronę, column-staggered

## Warstwy

| # | Nazwa | Funkcja |
|---|---|---|
| 0 | `default_layer` | QWERTY base |
| 1 | `lower_layer` | Cyfry, F-keys, nawigacja |
| 2 | `raise_layer` | Symbole, brackets |
| 3 | `adj_layer` | System, backlight controls, BT controls |

## ZMK Studio

ZMK Studio jest aktywne.

Procedura odblokowania jest taka sama we wszystkich klawiaturach FalbaTech FT:

> Trzymaj oba thumby aktywujące warstwy systemowe i wciśnij skrajny lewy górny klawisz.

Po odblokowaniu klawiatura jest edytowalna z poziomu przeglądarki:

https://zmk.studio

## Bluetooth - obsługa 5 urządzeń

Klawiatura obsługuje 5 niezależnych profili Bluetooth. Sterowanie odbywa się w warstwie systemowej `adj_layer`.

| Klawisz | Funkcja |
|---|---|
| `Z` | Profil BT 0 |
| `X` | Profil BT 1 |
| `C` | Profil BT 2 |
| `V` | Profil BT 3 |
| `B` | Profil BT 4 |
| `N` | Wyczyść aktywny profil |
| `M` | Wyczyść wszystkie profile |
| `,` | Tryb USB |
| `.` | Tryb Bluetooth |

## Backlight controls

Sterowanie podświetleniem znajduje się w warstwie `adj_layer`.

| Klawisz | Funkcja |
|---|---|
| `S` | Backlight on/off |
| `D` | Brightness + |
| `F` | Brightness - |

Backlight wykorzystuje pojedynczą diodę LED 3mm zasilaną przez PWM przez MOSFET. Jest bardziej energooszczędny niż per-key RGB i świetnie sprawdza się podczas pracy nocą.

## Build

GitHub Actions buduje 3 pliki firmware:

- `ergodash_left-nice_nano-zmk.uf2`
- `ergodash_right-nice_nano-zmk.uf2`
- `settings_reset-nice_nano-zmk.uf2`

## Flashowanie

1. Podłącz lewą połówkę przez USB.
2. Naciśnij RESET dwa razy szybko.
3. Przeciągnij `ergodash_left-...uf2` na dysk `NICENANO`.
4. Podłącz prawą połówkę przez USB.
5. Naciśnij RESET dwa razy szybko.
6. Przeciągnij `ergodash_right-...uf2`.
7. Połącz obie połówki przewodem TRRS.
8. Sparuj klawiaturę jako "ErgoDash FT" przez Bluetooth.

## Wsparcie

FalbaTech  
https://falbatech.click

---

## EN

ZMK configuration for **ErgoDash FT** - ergonomic FalbaTech keyboard.

## Hardware

- Shield: `ergodash` (custom physical layout in the FalbaTech repository)
- Controllers: 2x nice!nano v2
- Display: nice!view, Sharp Memory LCD
- Backlight: single 3mm LED on PWM
- Backlight pin: D10 / P0.09 through MOSFET, PWM0 channel
- 70 keys, 5 rows x 7 columns + 5 thumb keys per side, column-staggered

## Layers

| # | Name | Function |
|---|---|---|
| 0 | `default_layer` | QWERTY base |
| 1 | `lower_layer` | Numbers, F-keys, navigation |
| 2 | `raise_layer` | Symbols, brackets |
| 3 | `adj_layer` | System, backlight controls, BT controls |

## ZMK Studio

ZMK Studio is enabled.

The unlock procedure is the same across all FalbaTech FT keyboards:

> Hold both thumb keys activating system layers and press the top left key.

After unlocking, the keyboard can be configured from your browser:

https://zmk.studio

## Bluetooth - 5 device support

The keyboard supports 5 independent Bluetooth profiles. Control is handled in the system layer `adj_layer`.

| Key | Function |
|---|---|
| `Z` | BT Profile 0 |
| `X` | BT Profile 1 |
| `C` | BT Profile 2 |
| `V` | BT Profile 3 |
| `B` | BT Profile 4 |
| `N` | Clear active profile |
| `M` | Clear all profiles |
| `,` | USB mode |
| `.` | Bluetooth mode |

## Backlight controls

Backlight controls are located in the `adj_layer`.

| Key | Function |
|---|---|
| `S` | Backlight on/off |
| `D` | Brightness + |
| `F` | Brightness - |

The backlight uses a single 3mm LED powered by PWM through a MOSFET. It is more power efficient than per-key RGB and excellent for night work.

## Build

GitHub Actions builds 3 firmware files:

- `ergodash_left-nice_nano-zmk.uf2`
- `ergodash_right-nice_nano-zmk.uf2`
- `settings_reset-nice_nano-zmk.uf2`

## Flashing

1. Connect the left half via USB.
2. Press RESET twice quickly.
3. Drag `ergodash_left-...uf2` onto the `NICENANO` drive.
4. Connect the right half via USB.
5. Press RESET twice quickly.
6. Drag `ergodash_right-...uf2`.
7. Connect both halves using a TRRS cable.
8. Pair the keyboard as "ErgoDash FT" over Bluetooth.

## Support

FalbaTech  
https://falbatech.click
