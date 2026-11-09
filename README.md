# LumanoideOS releases

Update files of LumanoideOS for the ESP32-S3 N16R8 LED panel, and the release feed the Operator Shell reads.

- `latest.json`: the newest release (version, date, file, size, SHA-256, target, notes), feed format 1.
- `lumanoideos-<version>.update`: one firmware and Shell update, installed from the Shell (**System → Update**).

The Shell reads `https://mazzo26.github.io/LumanoideOS-releases/latest.json` at most once a day while it is open, and offers **Install** when a newer version is out. The browser checks the file's size and SHA-256 against the feed before it sends the file to the panel, and the panel checks it again before it writes anything.

This repository holds only published files; it holds no source.
