# OpetusSMPS Inversion

Locally runnable inversion and scan viewer for OpetusSMPS measurement files.

**[Download the latest release](https://github.com/yl1Ara/opetus-smps-inversion/releases/latest)**
· [All releases](https://github.com/yl1Ara/opetus-smps-inversion/releases)

This repository contains compiled application downloads and user instructions.
The application runs on your own computer; Python installation, GitHub login,
and a hosted inversion server are not required.

## Choose a package

| Computer | Download |
|---|---|
| Windows x64 | `OpetusInversion-VERSION-windows-AMD64.zip` |
| Linux x86-64, Ubuntu 22.04 or newer | `OpetusInversion-VERSION-linux-x86_64.tar.gz` |

These laptop/desktop packages do not run on ARM or macOS.

## Getting started

1. Download and extract the **whole archive**, keeping the executable and
   `_internal` folder together.
2. Windows: double-click `OpetusInversion.exe`.
   Linux: run `./OpetusInversion` in the extracted folder.
3. The GUI opens in your browser. Keep the terminal window open; if the browser
   does not open, copy the printed `http://127.0.0.1:.../` address.
4. Select **Custom folder**, enter your scan CSV folder, and refresh the list.
   Dated subfolders are supported. Select scans and check DMA geometry, CPC,
   flow and timing settings before running the inversion.
5. Choose an output folder and use **Save plots/data** to export results.

Measurement files and reference datasets are supplied separately. Processing
runs locally. An optional update notification checks this repository's public
release metadata at startup and hourly; it requires no credentials. Processing
continues when offline.

## Download instrument scans

The **Data Download** tab can fetch new scans over a Tailscale connection.
Install/sign in to Tailscale, accept the owner's instrument invitation, enter
your name, and **Export access request**. Email that public-key JSON to the
owner. Import the connection JSON they return, then click **Download new scans**.
Automatic downloads at a chosen interval are also available.

Your private key remains on this computer; instrument access is individually
authorized and read-only. No machine password or SSH commands are needed.
Completed downloads remain usable offline. The package includes
`SCAN-ACCESS.md` with the full setup instructions.

## Updates

The GUI displays a notification when a newer stable public version is available,
with a download link for your computer. You can also click **Check updates**.

Finish calculations, close the application, extract the new release into a new
folder, and launch it. Your settings are retained separately:

- Windows: `%LOCALAPPDATA%\OpetusSMPS\Inversion`
- Linux: `${XDG_DATA_HOME:-~/.local/share}/opetusSMPS/inversion`

## Troubleshooting

Close the terminal or press **Ctrl+C** to stop. Closing just the browser tab
leaves the local application running.

```text
OpetusInversion --help
OpetusInversion --self-test
OpetusInversion --no-browser --port 5010
OpetusInversion --state-dir "path/to/my/workspace"
```
