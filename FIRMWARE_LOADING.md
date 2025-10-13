# The Real Cow Flasher – Firmware Loading Guide

## Overview
The Real Cow Flasher web tool allows you to flash firmware to supported devices using WebUSB. You can load firmware in two ways:

1. **Select from Predefined Firmware**: Use the dropdown to pick a firmware version included with the project.
2. **Load from Computer**: Upload a `.bin`, `.hex`, or `.dfu` file from your local machine.

---

## How to Use

### Getting Your Device into DFU Mode

To enter DFU mode on most STM32-based devices:

1. **Press and hold the BOOT button, then plug the USB**
2. **Release the BOOT button.**

Your device should now be in DFU mode and will appear in the device list when you click **Connect**.

If it does not appear, check your USB cable and try the steps again.

### 1. Connect Your Device
- Click the **Connect** button and select your device from the browser prompt.
- Wait for the status to show "Connected".

### 2. Choose Firmware
- **Option A: Dropdown**
  - Use the **Select firmware** dropdown to pick a version from the list.
- **Option B: Local File**
  - Click **Or load from computer** and select a firmware file (`.bin`, `.hex`, `.dfu`).
- Only one method can be active at a time. Selecting a file clears the dropdown, and vice versa.

### 3. Flash Firmware
- Click **Download** to start flashing.
- Progress and status messages will appear below the buttons.

### 4. Erase Only (Optional)
- Click **Erase Only** to erase the device without flashing new firmware.

---

## Technical Details

- **File Handling**: The tool uses the File API to read local files as `ArrayBuffer` for flashing.
- **Validation**: You must select either a dropdown firmware or a local file before downloading.
- **WebUSB**: Only works in Chrome or Edge browsers with WebUSB support.
- **Error Handling**: The UI will show errors if flashing fails or if no firmware is selected.

---

## Supported File Types
- `.bin` (Binary)
- `.hex` (Intel HEX)
- `.dfu` (DFU format)

---

## Troubleshooting
- **No Device Found**: Make sure your device is in DFU mode and connected via USB.
- **Browser Not Supported**: Use Chrome or Edge for WebUSB support.
- **Firmware Not Flashing**: Check that the file is valid and compatible with your device.

---

## Project Structure (Relevant Files)
- `index.html` – Main UI and dropdown logic
- `dfu-util.js` – Handles device connection, file loading, and flashing logic
- `firmware.json` – List of available firmware files for the dropdown
- `Firmware/` – Folder containing predefined firmware binaries

---

## Example: Adding New Firmware to Dropdown
1. Place your `.bin` file in the `Firmware/` folder.
2. Add the filename to `firmware.json` (as a string in the array).
3. Reload the page to see it in the dropdown.

---

## Credits
- Built with WebUSB and JavaScript
- Maintained by EmbeddedEra

---

For more details, see the code comments in `dfu-util.js` and `index.html`.
