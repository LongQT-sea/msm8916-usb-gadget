# Linux-USB Gadget Setup for ARM Boards

A lightweight shell script to configure USB Gadget functionality on ARM-based boards using configfs. Supports multiple USB protocols.

## Features

- **RNDIS** (Windows-compatible Ethernet)
- **CDC ECM/NCM** (Ethernet for Linux/macOS/Windows)
- **USB Mass Storage (UMS)**
- **CDC ACM** (Serial Console)

## Compatibility

Although originally named for MSM8916, this setup works with **any ARM board** that supports USB Device (UDC) mode and `configfs`.

## Installation

```bash
sudo bash install.sh
````

## Configuration

Edit `/etc/msm8916-usb-gadget.conf` to enable or disable features:

```sh
ENABLE_RNDIS=1
ENABLE_ECM=0
ENABLE_NCM=0
ENABLE_UMS=1
ENABLE_ACM=1
```

## Usage

Control the gadget using:

```bash
sudo systemctl start msm8916-usb-gadget         # Set up gadget
sudo systemctl stop msm8916-usb-gadget          # Tear down gadget
sudo systemctl reload msm8916-usb-gadget        # Apply config changes
```

## Systemd Service

Enabled automatically on install:

* `msm8916-usb-gadget.service`
* `getty@ttyGS0.service` (provides root shell over USB serial)
