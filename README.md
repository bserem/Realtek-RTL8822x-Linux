# RTL8822x Firmware for GNU/Linux

The files in this repository are taken from Linux Mint 19.3 and will allow a
Realtek RTL8822 b or c card to work on other distributions.

The files have been tested with Debian Live Testing ISO with non-free firmware
included (https://cdimage.debian.org/images/unofficial/non-free/images-including-firmware/weekly-live-builds/amd64/iso-hybrid/).

If you have trust issues, you can always boot with Mint 19.3 and take the files
from there to use.

# Usage

Log in with your favorite distribution, preferably with a new Kernel, as this
has only been tested with 5.4+
Unload non-working modules from the Kernel, with:
```
modprobe -r rtwpci
modprobe -r rtw88
```

You can run `lsmod` to see if they are named somehow differently in your OS,
in case you do not run Debian.

Copy the files from this repo to your system, **change the kernel path as needed**!
Load the modules with `modprobe rtw88` and the WiFi should work.

It is unclear to me whether the `/usr` files are needed or if everything will
work with just the files under `/lib`. Feel free to open an issue about this.

## Troubleshooting

Did you rename the paths to work with with your current Kernel?

# Usage on Debian Installer

Either on the graphical, text or live installer, open a terminal and do the
above procedure **before** the installer checks for WiFi cards. The resulting
installation will work out of the box and you do not need to copy the files
again.

# Systems tested

- Huawei Matebook D14 (2020) with AMD 3500U. (Probaly same as D15)

# Other Notes

The following issues are not related to the network card, but to the AMD CPU/GPU.
Since these two are commonly found together, I document the fixes here.

- If you have issues with the installer not starting use a newer Kernel.
  The ISO files listed above are fine as are the STABLE ones from Debian.

  If you have glitches with your screen (artifacts) disable compositing.
