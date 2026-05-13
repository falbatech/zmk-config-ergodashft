:::writing{variant=“standard” id=“52731”}

zmk-config-ergodashft

PL

Konfiguracja ZMK dla ErgoDash FT - klawiatura ergonomiczna FalbaTech.

Hardware
	•	Shield: ergodash (custom physical layout w naszym repo)
	•	Kontrolery: 2× nice!nano v2
	•	Wyświetlacz: nice!view (Sharp Memory LCD)
	•	Backlight: pojedyncza LED 3mm na PWM (D10/P0.09 przez MOSFET, kanał PWM0)
	•	70 klawiszy (5 rzędów × 7 kolumn + 5 thumb na stronę, column-staggered)

Warstwy

#	Nazwa	Funkcja
0	default_layer	QWERTY base
1	lower_layer	Cyfry, F-keys, nawigacja
2	raise_layer	Symbole, brackets
3	adj_layer	System, backlight controls, BT controls

ZMK Studio

Aktywne. Procedura odblokowania (jednakowa we wszystkich klawiaturach FalbaTech FT):

Trzymaj oba thumby aktywujące warstwy systemowe → wciśnij skrajny lewy górny klawisz.

Po odblokowaniu klawiatura jest edytowalna z:
zmk.studio￼

Bluetooth - obsługa 5 urządzeń

Klawiatura obsługuje 5 niezależnych profili Bluetooth. W warstwie systemowej (adj_layer):

Klawisz	Funkcja
Z	Profil BT 0
X	Profil BT 1
C	Profil BT 2
V	Profil BT 3
B	Profil BT 4
N	Wyczyść aktywny profil
M	Wyczyść wszystkie profile
,	Tryb USB
.	Tryb Bluetooth

Backlight controls (warstwa adj_layer)

Klawisz	Funkcja
S	Backlight on/off
D	Brightness +
F	Brightness -

Backlight wykorzystuje pojedynczą LED 3mm zasilaną przez PWM przez MOSFET. Bardziej energooszczędne niż per-key RGB, świetne na nocną pracę.

Build

GitHub Actions buduje 3 firmware:
	•	ergodash_left-nice_nano-zmk.uf2
	•	ergodash_right-nice_nano-zmk.uf2
	•	settings_reset-nice_nano-zmk.uf2

Flashowanie
	1.	Lewa USB - 2× reset - ergodash_left-...uf2
	2.	Prawa USB - 2× reset - ergodash_right-...uf2
	3.	Połącz TRRS - klawiatura “ErgoDash FT” w BT

Wsparcie

FalbaTech - https://falbatech.click

⸻

EN

ZMK configuration for ErgoDash FT - ergonomic FalbaTech keyboard.

Hardware
	•	Shield: ergodash (custom physical layout in our repository)
	•	Controllers: 2× nice!nano v2
	•	Display: nice!view (Sharp Memory LCD)
	•	Backlight: single 3mm LED on PWM (D10/P0.09 through MOSFET, PWM0 channel)
	•	70 keys (5 rows × 7 columns + 5 thumb keys per side, column-staggered)

Layers

#	Name	Function
0	default_layer	QWERTY base
1	lower_layer	Numbers, F-keys, navigation
2	raise_layer	Symbols, brackets
3	adj_layer	System, backlight controls, BT controls

ZMK Studio

Enabled. Unlock procedure (same across all FalbaTech FT keyboards):

Hold both thumb keys activating system layers → press the top left key.

After unlocking, the keyboard can be configured from:
zmk.studio￼

Bluetooth - 5 device support

The keyboard supports 5 independent Bluetooth profiles. In the system layer (adj_layer):

Key	Function
Z	BT Profile 0
X	BT Profile 1
C	BT Profile 2
V	BT Profile 3
B	BT Profile 4
N	Clear active profile
M	Clear all profiles
,	USB mode
.	Bluetooth mode

Backlight controls (adj_layer)

Key	Function
S	Backlight on/off
D	Brightness +
F	Brightness -

The backlight uses a single 3mm LED powered by PWM through a MOSFET. More power efficient than per-key RGB and excellent for night work.

Build

GitHub Actions builds 3 firmware files:
	•	ergodash_left-nice_nano-zmk.uf2
	•	ergodash_right-nice_nano-zmk.uf2
	•	settings_reset-nice_nano-zmk.uf2

Flashing
	1.	Left USB - press reset 2× - ergodash_left-...uf2
	2.	Right USB - press reset 2× - ergodash_right-...uf2
	3.	Connect TRRS - keyboard appears as “ErgoDash FT” over Bluetooth

Support

FalbaTech - https://falbatech.click
:::
