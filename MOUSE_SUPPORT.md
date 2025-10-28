# Mouse Support for Kinesis Advantage 360 Pro

## Current Status: ❌ Not Available

Your current ZMK firmware version (`adv360-z3.5` from refil/zmk fork) **does not support mouse movements**.

The mouse layer (Layer 4) exists in your keymap but is currently disabled (all keys are transparent).

---

## How to Enable Mouse Support in the Future

### Option 1: Wait for Official Support
Wait for the refil/zmk fork to add mouse support to the adv360 branch.

### Option 2: Upgrade to Newer ZMK (Advanced)

**Warning**: This requires changing your ZMK source and may break other features.

1. **Update `config/west.yml`** to use a ZMK version with mouse support:
   ```yaml
   manifest:
     remotes:
       - name: zmkfirmware
         url-base: https://github.com/zmkfirmware
     projects:
       - name: zmk
         remote: zmkfirmware
         revision: main
         import: app/west.yml
     self:
       path: config
   ```

2. **Enable mouse in config files**:
   
   Add to `config/boards/arm/adv360/adv360_left_defconfig`:
   ```conf
   # Mouse/Pointer support
   CONFIG_ZMK_MOUSE=y
   ```
   
   Add to `config/boards/arm/adv360/adv360_right_defconfig`:
   ```conf
   # Mouse/Pointer support
   CONFIG_ZMK_MOUSE=y
   ```

3. **Update keymap includes** in `config/adv360.keymap`:
   ```c
   #include <dt-bindings/zmk/mouse.h>
   ```

4. **Add mouse bindings** to the Mouse_movements layer:
   ```c
   Mouse_movements {
       bindings = <
   &trans  &trans  &trans  &trans  &trans          &trans  &trans                                      &trans     &trans  &trans             &trans             &trans              &trans  &trans
   &trans  &trans  &trans  &trans  &msc SCROLL_UP  &trans  &trans                                      &trans     &trans  &mkp MB1           &mmv MOVE_UP       &mkp MB2            &trans  &trans
   &trans  &trans  &trans  &trans  &msc SCROLL_DN  &trans  &trans  &trans  &trans      &trans  &trans  &trans     &trans  &mmv MOVE_LEFT     &mmv MOVE_DOWN     &mmv MOVE_RIGHT     &trans  &trans
   &trans  &trans  &trans  &trans  &trans          &trans                  &trans      &trans                     &trans  &trans             &trans             &trans              &trans  &trans
   &trans  &trans  &trans  &trans  &trans                  &trans  &trans  &trans      &trans  &trans  &mkp MB2           &trans             &trans             &trans              &trans  &trans
       >;
   };
   ```

---

## Planned Mouse Controls (When Enabled)

**Right side (mouse buttons & movement):**
- **U key**: Left Click (MB1)
- **I key**: Move mouse up  
- **K key**: Move mouse down
- **J key**: Move mouse left
- **L key**: Move mouse right
- **O key**: Right Click (MB2)
- **Space key**: Right Click (MB2)

**Left side (scrolling):**
- **R key**: Scroll up
- **F key**: Scroll down

**Access**: Hold the `&mo 4` key (check your keymap for location, usually in left thumb cluster)

---

## Why Doesn't It Work Now?

The ZMK firmware you're using is a specialized fork for the Adv360 keyboard. It's based on Zephyr 3.5 but doesn't include the newer mouse movement features that were added to mainstream ZMK.

The hardware **is capable** of mouse emulation, but the firmware needs to be updated first.


