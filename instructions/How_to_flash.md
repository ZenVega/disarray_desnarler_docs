### Great! your macropad is built!

### so let's go ahead and flash some firmware onto it!

This guide applies to both the DisArray Desnarler and the macro_GOAT - they share the same QMK firmware repository and flashing process.

If you are in a workshop with us, we will help you and flash the first round with you, or you even got an already flashed microcontroller.

If you feel comfortable with the terminal and an IDE of your choice: This guide is for you.

# Prepare: Install QMK

This is just a quick recap. If you get stuck, check the official qmk documentation [here](https://docs.qmk.fm/newbs_getting_started)

In order to get QMK CLI installed on your system follow the first two steps from the [installation instructions] (https://docs.qmk.fm/newbs_getting_started)

Test if installation was successfull:

```bash
qmk --version
```

# Flash your macropad

Clone this [repo](https://github.com/ZenVega/qmk_disarray_desnarler) containing the firmware and the keymaps for both macropads.

To install all missing dependencies run:

```bash
git submodule update --init --recursive

git submodule sync --recursive
git submodule update --init --recursive --force
```

## Chose Keymap

We provide a few different keymaps, that we think will be useful to you.
When you look around in the repo you just cloned, there is a directory "keyboards". Within this choose the directory corresponding to the keyboard you have - `desnarler_v1` for the DisArray Desnarler, or `macro_goat_v0` for the macro_GOAT. Within this directory there are different keymaps to configure what your macropad does.

For a description of the keymaps we provide for the Desnarler and an easy introduction into QMK, see the Desnarler's [How_to_configure](../disarray_desnarler/instructions/How_to_configure.md) guide.

## Compile

After you have chosen your preferred keymap, you are ready to compile.

Compilation will create a \*.bin that holds the firmware including your compilation ready to be flashed on the MCU

```bash
qmk compile -kb <keyboard> -km <keymap>
```

so a likely use will be

```bash
qmk compile -kb desnarler_v1 -km default
```

or, for the macro_GOAT

```bash
qmk compile -kb macro_goat_v0 -km default
```

If no keyboard is defined, your keymap is 'default'. (which might not be defined in all cases)

### Flash

After compilation you are ready to flash qmk to your microcontroller (rp2040 in this case): plug it in and set it into bootloader mode.
This requires pressing the boot button while plugging it in. The device should show up as a flashable media in your files-explorer.
run:

```bash
qmk flash -kb <keyboard> -km <keymap>
```

so likely you will use

```bash
qmk flash -kb desnarler_v1 -km default
```

#### Troubleshooting Flashing

If your have done minor changes to your firmware, flashed and everything seemed fine, but the old firmware is still booting, download this [nuke file](https://datasheets.raspberrypi.com/soft/flash_nuke.uf2). Once downloaded, copy it onto your RP2040 while in bootloader mode. This will erase all traces of the former firmware. Then just flash again.

If the changes you made to your config don't act as intended, nuke the MCU: put it into bootloader mode, then drag and drop this [nuke file](./files/universal_flash_nuke.uf2) onto the newly mounted storage device. Then just flash again.
