# How to Flash Your Keyboard with New Firmware

## Step 1: Build the Firmware
```bash
make all
```
Wait for build to complete (5-10 minutes first time).

## Step 2: Locate the Firmware Files
```bash
ls firmware/
```
You'll see two files:
- `TIMESTAMP-COMMIT-left.uf2`
- `TIMESTAMP-COMMIT-right.uf2`

## Step 3: Put LEFT Keyboard into Bootloader Mode
**Choose one method:**
- **Method A**: Press the **reset button** on the left keyboard (small button, usually under the keyboard)
- **Method B**: Press the **bootloader key combo** (if you have one configured)

## Step 4: Flash the LEFT Side
1. Left keyboard appears as USB drive named "**ADV360PRO**" or "**NRF52BOOT**"
2. Drag `*-left.uf2` file to this drive
3. Drive will auto-eject and keyboard will restart

## Step 5: Put RIGHT Keyboard into Bootloader Mode
Same as Step 3, but for the **right** keyboard half.

## Step 6: Flash the RIGHT Side
1. Right keyboard appears as USB drive
2. Drag `*-right.uf2` file to this drive
3. Drive will auto-eject and keyboard will restart

## Step 7: Test Mouse Layer (New Feature!)
1. Press your **layer 4 trigger** (`&mo 4` in left thumb cluster)
2. Use the mouse controls on the right side
3. Test scrolling on the left side

## Step 8: Re-pair Bluetooth (Important!)
**If using Bluetooth**, you MUST re-pair your keyboard after flashing:
1. Delete/forget the keyboard from your device's Bluetooth settings
2. Re-pair the keyboard from scratch

This is required because mouse support changes the HID descriptor.

---

## Mouse Controls (Layer 4)

**Right side (mouse buttons & movement):**
- **U key**: Left Click (LCLK)
- **I key**: Move mouse up  
- **K key**: Move mouse down
- **J key**: Move mouse left
- **L key**: Move mouse right
- **O key**: Right Click (RCLK)
- **Space key** (thumb): Right Click (RCLK)

**Left side (scrolling):**
- **R key**: Scroll up
- **F key**: Scroll down

**Access Layer 4**: Hold the `&mo 4` key (in left thumb cluster at home row middle)

---

## Important Notes

✅ Flash **both halves** even if you only changed one side to keep them synchronized.

⚠️ **Bluetooth users**: You MUST re-pair after enabling mouse support.

📝 This firmware uses **official ZMK main branch** with mouse support enabled.

