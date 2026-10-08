# OnePlus 15 phone modules

Experimental Android root modules developed for Iliya Akulchev's OnePlus 15, with AI assistance. Published as an initial collection on 8 October 2026. No external adoption, download totals, or contributor counts are claimed.

## Included modules

| Module | Purpose |
| --- | --- |
| MCON Fast Connect v0.9 | Foreground-aware Bluetooth HID reconnect assistance for OhSnap MCON |
| MCON Input Device Guard v1.1 | Restores the configured MCON controller's Android Input device policy |
| MCON Xbox Bridge v1.2 | Exposes MCON as a virtual Xbox controller while Call of Duty: Mobile is foreground |
| Game Thermal Guard v1.0 | Battery-temperature-driven GPU and charging current ceilings |
| Auto INCY VPN v1.0.0 | Foreground app-triggered INCY VPN connection requests |

These are device-specific experiments, not broadly validated releases. Review the scripts before installing; root privileges are required. Preserve a recovery method for disabling modules. Existing module READMEs describe development iterations and may contain older version details.

## Input Device Guard configuration

Before starting the guard, create `/data/adb/mcon_input_device_guard/controller-address` containing your paired MCON's stable Bluetooth address. The public copy exits without modifying devices when this file is absent. The original developer's Bluetooth address has been removed.

## Thermal Guard details

The implementation enters its hot profile at 38.0 C battery temperature and restores its configured profile at 37.0 C. It writes GPU and USB input current limits; the CPU values declared in the script are unused. Sysfs paths and restoration values are specific to the original device and must be reviewed for other hardware. This module does not disable stock thermal services.

## Source and build status

Shell sources and the available Java Bluetooth helper sources are included in the archive. Existing DEX and native bridge binaries are also included. The native Xbox bridge source was not located in this workspace; that component is therefore not fully reproducible from this collection. No license grant is made for unidentified binary components. No new device testing was performed for this publication.

For a source archive, unpack `phone-modules.zip`. To package an individual module, zip its contents with `module.prop` at the archive root. Java helpers require an Android SDK and DEX compilation. Do not install the collection archive directly as a root module.

## Project direction

Make controller configuration portable, document supported Android versions, recover missing build sources, improve teardown and restoration behavior, and collect reproducible issue reports from real users.
