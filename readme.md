# Vial-QMK Setup and Firmware Guide (Windows)

This guide explains how to set up your environment, compile firmware, and flash it to my keyboard using QMK and Vial on Windows.

## ✅ Enabled Features Overview

The firmware is built with the following features enabled:

* **VIA / VIAL Support**: Easily remap keys using VIA or Vial.
* **Tap Dance & Combo**: Configure keys with multiple functions.
* **QMK Settings & Extra Keys**: Includes advanced system and media keys.
* **Mouse Keys**: Control your mouse pointer from the keyboard.
* **Performance**: Link Time Optimization (LTO) enabled for smaller, faster firmware.
* **OLED & RGB**: Disabled to save space.
* **Keymap Layer**: 6 Layer

```makefile
VIA_ENABLE          = yes
VIAL_ENABLE         = yes
LTO_ENABLE          = yes

TAP_DANCE_ENABLE    = yes
COMBO_ENABLE        = yes
QMK_SETTINGS        = yes
MOUSEKEY_ENABLE     = yes
EXTRAKEY_ENABLE     = yes
VIAL_INSECURE       = yes

OLED_ENABLE         = no
OLED_DRIVER         = ssd1306
RGBLIGHT_ENABLE     = no
RGB_MATRIX_ENABLE   = no  # Can't have RGBLIGHT and RGB_MATRIX at the same time.
KEY_OVERRIDE_ENABLE = no
```

---

## 🧰 Environment Setup

### 1. Install QMK MSYS

Download the latest QMK MSYS installer from the [official release page](https://github.com/qmk/qmk_distro_msys/releases/latest) and install it.

### 2. Run QMK Setup

Launch **QMK MSYS** and run:

```bash
qmk setup
```

Respond with `y` (yes) to all prompts.

### 3. Verify Installation

Check your setup:

```bash
qmk doctor
```

Test the compilation with:

```bash
qmk compile -kb clueboard/66/rev3 -km default
```

### 4. Clone the Vial-QMK Repository

Use my customized fork of Vial-QMK:

```bash
git clone https://github.com/ayuAtama/vial-qmk.git
cd vial-qmk
```

### 5. Initialize Submodules and Recheck

```bash
make git-submodule
qmk doctor
```

---

## ⚙️ Compile and Flash Firmware

### 1. Compile the Firmware

```bash
make crkbd/rev1:ekadeva
```

### 2. Flash the Firmware

```bash
qmk flash -kb crkbd/rev1 -km ekadeva
```

### 3. Enter Flashing Mode

* Tap the **reset button twice** next to the MCU to enter DFU mode.
* Repeat this step for the **right half** of the keyboard.

### 4. Done!

Your firmware has now been successfully flashed.

---

## 📝 Notes

* This guide is specifically tailored for the **Corne (crkbd)** keyboard and the **ekadeva** keymap.
* Ensure you have the correct drivers installed if flashing fails (e.g., **QMK Toolbox** or **Zadig** for DFU support).

---

## 📌 Resources

* [Vial-QMK (fork)](https://github.com/ayuAtama/vial-qmk)
* [QMK MSYS Releases](https://github.com/qmk/qmk_distro_msys/releases/latest)
* [QMK Documentation](https://docs.qmk.fm/)
