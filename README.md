# OSCam-Emu for Vu+ Solo 4K

This repository builds a current OSCam-Emu binary for Vu+ Solo 4K using GitHub Actions.

Target:
- ARMv7 hard-float (arm-linux-gnueabihf)
- libusb
- config directory: /etc/tuxbox/config/oscam-emu/
- WebIF, DVBAPI, Extended CW API
- Anti-cascading, Debug, Monitor, Load Balancer
- CacheEX + CacheEX AIO
- CW Cycle Check
- EMU + SoftCam
- CCcam, camd35, camd35 TCP, newcamd, gbox, constant CW
- Nagra, Nagra Merlin, Irdeto, Conax, Cryptoworks, Seca, Viaccess, Videoguard, DRE, Tongfang, Bulcrypt, Griffin, DGCrypt
- Phoenix, internal reader, SC8in1, MP35 and Smargo

The workflow also applies the CacheEX V1 WebIF change so per-service CacheEX statistic rows are visible by default.

## Output

Each successful GitHub Actions run uploads one artifact containing:

- `oscam-emu-vusolo4k-cacheex-v1` — standalone ARM binary
- `oscam-emu-vusolo4k-cacheex-v1.ipk` — generic IPK package

The IPK installs the custom binary as:

`/usr/bin/oscam-emu-vusolo4k`

It intentionally does **not** overwrite the receiver's current OSCam binary or existing configuration.

For the per-service CacheEX rows to contain data, enable:

```ini
[cache]
cacheexenablestats = 1
```

## Build

Open **Actions → Build OSCam-Emu Vu+ Solo 4K → Run workflow**.

The source is cloned at build time from `oscam-mirror/oscam-emu`, so a manual run builds the then-current source.
