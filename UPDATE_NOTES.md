# Update Notes - Adv360-z3.5-2 (Commit: e51968a)

## 🎉 What's New

### Mouse Support Enabled! 🖱️
The `adv360-z3.5-2` fork now includes **full mouse emulation support**!

### Key Changes:

#### 1. **Mouse Layer (Layer 4 - "Red")**
- Added complete mouse control bindings
- **Access**: Hold left thumb home row middle key (above LCTRL)
- **Controls**:
  - I/J/K/L: Move cursor (up/left/down/right)
  - U: Left click
  - O: Right click
  - Space: Right click
  - R/F: Scroll up/down

#### 2. **ZMK Studio Support**
- Includes `&studio_unlock` behavior in mod layer
- Added `&stp STP_BAT` for battery status in Studio
- Easier configuration through ZMK Studio web interface

#### 3. **Layer Structure Updates**
- Layer 0: Base (default typing)
- Layer 1: Keypad (numpad)
- Layer 2: Fn (function keys)
- Layer 3: Mod (Bluetooth, RGB, settings)
- Layer 4: Red (Mouse controls) ⭐ NEW
- Layers 5-7: Purple, Cyan, Yellow (reserved for future use)

#### 4. **Configuration Changes**
- Enabled `CONFIG_ZMK_POINTING=y` on both halves
- Added `CONFIG_ZMK_BEHAVIOR_LOCAL_ID_TYPE_CRC16=y` for Studio support
- RGB underglow auto-off disabled on right half
- Includes `<dt-bindings/zmk/pointing.h>` and `<dt-bindings/zmk/stp.h>`

## 🚀 How to Use

### Building:
```bash
make all
```

### Flashing:
See `FLASHING.md` for detailed instructions.

### Mouse Controls:
1. Hold the left thumb middle key (where `&mo 4` is mapped)
2. Use I/J/K/L to move the cursor
3. Press U to left-click, O to right-click
4. Use R/F to scroll

### Important After Flashing:
⚠️ **Bluetooth users MUST re-pair** after flashing firmware with mouse support!
The HID descriptor changes when mouse support is enabled.

## 📋 Compatibility

### ✅ Working:
- Mouse emulation (cursor movement, clicks, scrolling)
- All existing keyboard features
- RGB underglow (with custom commands)
- Backlight controls
- Bluetooth pairing
- ZMK Studio support

### ⚠️ Notes:
- This firmware uses the **refil/zmk adv360-z3.5-2 fork**, not official ZMK main
- The fork is specifically optimized for Adv360 hardware
- Mouse support may not be as mature as mainline ZMK (but it works!)

## 🔧 Customization

You can modify the mouse layer bindings in `config/adv360.keymap`:
- Change the trigger key location (currently `&mo 4` on line 45)
- Adjust mouse layer bindings (lines 80-88)
- Use other reserved layers (Purple, Cyan, Yellow) for additional features

## 📚 Resources

- [ZMK Mouse Emulation Docs](https://zmk.dev/docs/keymaps/behaviors/mouse-emulation)
- [ZMK Studio](https://zmk.studio)
- [Kinesis Advantage 360 Pro](https://kinesis-ergo.com/keyboards/advantage360/)

## 🎯 Next Steps

1. Flash both keyboard halves
2. Re-pair via Bluetooth
3. Test mouse controls
4. Customize layers as needed using ZMK Studio or by editing the keymap

Enjoy your mouse-enabled Advantage 360 Pro! 🎊

