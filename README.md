# LumanoideOS releases

Update files of LumanoideOS, firmware for a 16 × 16 LED matrix panel on an ESP32-S3, and the release feed the Operator Shell reads.

## Hardware requirements

LumanoideOS does not run on every ESP32. These files are for this hardware only:

| Part | Required |
| --- | --- |
| Board | ESP32-S3 **N16R8**: 16 MB flash and 8 MB PSRAM. Other ESP32 chips (ESP32, S2, C3, C6), and S3 boards with less flash or PSRAM, are not supported |
| Panel | 16 × 16 pixels, RGBW NeoPixel LEDs (`NEO_GRBW`), data on GPIO 17 |

The panel itself checks every file before it writes anything: a file for another board or chip, or a file that does not match its checksums, is refused and nothing changes.

## Software requirements

- **LumanoideOS 0.3.48 or later** for the notice with **Install** in the Shell. From 0.3.45 a file can be installed through the Management API.
- **The partition layout of 0.3.43 or later**, with two firmware slots and two Shell volumes. It is written once over USB; an update over Wi-Fi cannot change it.

These files update an existing installation. They cannot install LumanoideOS on an empty board, and an `.update` file is not an image for `esptool`.

## Files

- `latest.json`: the newest release (version, date, file, size, SHA-256, target, notes), feed format 1.
- `lumanoideos-<version>.update`: one firmware and Shell update, installed from the Shell (**System → Update**). The target in its header is `esp32s3-n16r8`.

The Shell reads `https://mazzo26.github.io/LumanoideOS-releases/latest.json` at most once a day while it is open, and offers **Install** when a newer version is out. The browser checks the file's size and SHA-256 against the feed before it sends the file to the panel, and the panel checks it again before it writes anything. If the new firmware does not come up within 60 seconds, the panel returns to the previous one by itself.

This repository holds only published files; it holds no source.
