[English](README.md) | [Русский](README_ru.md)

# Ender 3 V3 SE Klipper with Display (Merged Repository)

> **NOTE:** This is a merged repository specifically created to make the original Ender 3 V3 SE display work with the latest version of Klipper (from 0xD34D).
> 
> * **Base (Klipper):** Fork of [0xD34D/klipper_ender3_v3_se](https://github.com/0xD34D/klipper_ender3_v3_se) updated with upstream [Klipper3d/klipper](https://github.com/Klipper3d/klipper) (Latest commit: `b7c0329f1`, May 2026)
> * **Display Mod:** Ported from [jpcurti/ender3-v3-se-klipper-with-display](https://github.com/jpcurti/ender3-v3-se-klipper-with-display) (Latest commit: `72e925e55`, January 2026)

---

## Configuration

A section called `[e3v3se_display]` need to be added to your `printer.cfg` to enable the display. Besides that, you can set a custom language and logging (defaulted as english and false, respectively), like:

```yaml
[e3v3se_display]
language: english # English and Russian verified, other languages untested.
logging: False
```

### Custom macros

The new 'Misc' menu list a set of custom macros that can be defined on your `printer.cfg`.
You can use this to call macros defined on Klipper using your screen directly, e.g.: Load/Unload filament, calibrate Z offset, calibrate bed mesh, clean nozzle, etc.

On your `printer.cfg` you can define the macros using a new config section `[e3v3se_display MACRO%I]` where `%i` is the macro number (This should be unique per macro). The following properties are available:

| Property | Data type | Required | Description                                                      |
|----------|-----------|----------|------------------------------------------------------------------|
| label    | Text      | Yes      | Text to be displayed on the screen                               |
| icon     | Integer   | No       | Internal firmware icon. Defaults to 14 (file icon)               |
| gcode    | Text      | Yes      | GCODE to be run when the item is selected.  i.e `G28` for homing |

Some examples for your inspiration:

```yaml
[e3v3se_display MACRO1]
gcode: LOAD_FILAMENT
label: Load filament
icon: 14

[e3v3se_display MACRO2]
gcode: UNLOAD_FILAMENT
label: Unload filament
icon: 14

[e3v3se_display MACRO3]
gcode: CALIBRATE_Z_OFFSET
label: Calibrate Z offset
icon: 12
```

To browse icon library, call the macro `ENDER_SE_DISPLAY_ICON_FINDER` on your Klipper console and use the screen to navigate through the icons.

## Supported features

The currently supported features are:

| Feature                | Status  |
| ---------------------- | ------- |
| Print file             | &check; |
| Tune print             | &check; |
| Pause/continue print   | &check; |
| Stop print             | &check; |
| Move Axis              | &check; |
| Home Axis              | &check; |
| Set Z offset           | &check; |
| Disable step motors    | &check; |
| Preheat bed            | &check; |
| Cooldown               | &check; |
| Set nozzle temperature | &check; |
| Set bed temperature    | &check; |
| Set max speed          | &cross; |
| Set max acceleration   | &cross; |
| Set steps per-mm       | &cross; |
| Manual probe popup     | &check; |
| Custom macros menu     | &check; |

## Important

- This project is based on the **E3V3SE display firmware 1.0.6**. Any changes in the firmware version, such as a new version from Creality, can change the assets locations within the display memory and a new mapping would be necessary. A list of available firmware can be found [on Creality website](https://www.creality.com/pages/download-ender-3-v3-se) and a detailed instruction on how to update your display is available on [youtube](https://www.youtube.com/watch?v=8oRuCusCyUM&ab_channel=CrealityAfter-sale).

---

Welcome to the Klipper project!
[![Klipper](docs/img/klipper-logo-small.png)](https://www.klipper3d.org/)

https://www.klipper3d.org/

The Klipper firmware controls 3d-Printers. It combines the power of a
general purpose computer with one or more micro-controllers. See the
[features document](https://www.klipper3d.org/Features.html) for more
information on why you should use the Klipper software.

Start by [installing Klipper software](https://www.klipper3d.org/Installation.html).

Klipper software is Free Software. See the [license](COPYING) or read
the [documentation](https://www.klipper3d.org/Overview.html). We
depend on the generous support from our
[sponsors](https://www.klipper3d.org/Sponsors.html).
