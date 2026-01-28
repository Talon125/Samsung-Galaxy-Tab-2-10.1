# Samsung Galaxy Tab 2 (10.1 inch)

GT-P5100

This is me documenting playing around with the _Samsung Galaxy Tab 2 10.1_.

![A screenshot of the _About device_ section in the Settings app of the GT-P5100](
  Screenshots/Screenshot_2026-01-27-20-14-38.png
)

<https://geizhals.at/samsung-galaxy-tab-2-10-1-p5100-16gb-weiss-gt-p5100zwa-a798475.html>

<https://connector.pinoutguide.com/30_pin_samsung_galaxy_tab_proprietary/>

> [!IMPORTANT]
> Your tablet should have sufficient battery life before beginning.

## Table of Contents

- [Samsung Galaxy Tab 2 (10.1 inch)](#samsung-galaxy-tab-2-101-inch)
  - [Table of Contents](#table-of-contents)
  - [Flashing TWRP v2.8.5.0](#flashing-twrp-v2850)

## Flashing TWRP v2.8.5.0

Obtain the file from here:  
<https://eu.dl.twrp.me/p5100/twrp-2.8.5.0-p5100.img.html>

Other versions of TWRP:  
<https://eu.dl.twrp.me/p5100/>

Now boot into Download Mode. Shut down the tablet, then hold volume down and the
power button. In landscape (SAMSUNG logo right side up, buttons on top), this is
the righter volume button.

Now you should see this screen:

> ---
>
> **Warning!!**
>
> ---
>
> A custom OS can cause critical problems in phone and installed applications.
>
> If you want to download a custom OS, press the volume down key. Otherwise
> press the volume up key to cancel.
>
> ---
>
> **Volume up :** Cancel (restart phone)  
> **Volume down :** Continue
>
> ---
>
> ⚠️
>
> ---

Press volume down (righter button) to continue.

> [!IMPORTANT]
> I'm using Linux. Specifically, as of writing this:
>
> ```bash
> OS: Debian GNU/Linux forky/sid (forky) x86_64
> Kernel: Linux 6.18.5+deb14-amd64
> ```

Usually you'd use Odin. In this case, I'm going to use Heimdall from the
terminal.

<https://github.com/Benjamin-Dobell/Heimdall>

```bash
sudo apt install heimdall-flash
```

Connect the tablet to your computer.

Now run the following to confirm Heimdall sees your tablet:

```bash
heimdall detect
```

You should get `Device detected` as the output.

`cd` to the directory where you have your `twrp-2.8.5.0-p5100.img`.

> [!WARNING]
> Flashing incorrectly or using the wrong files may result in bricking.
> Proceed with caution and at your own risk.

Now run the following to flash TWRP to the recovery partition:

```bash
heimdall flash --RECOVERY twrp-2.8.5.0-p5100.img --no-reboot
```

This is the output I got:

```bash
talon@talon-framework-debian:~/AndroidStuff/Samsung Galaxy Tab 2 10.1 (GT-P5100)$ heimdall flash --RECOVERY twrp-2.8.5.0-p5100.img --no-reboot
Heimdall v2.1.0

Copyright (c) 2010-2017 Benjamin Dobell, Glass Echidna https://glassechidna.com.au
Copyright (c) 2021-2024 Henrik Grimler
This software is provided free of charge. Copying and redistribution is encouraged.

Initialising connection...
Detecting device...
Claiming interface...
Initialising protocol...
Resetting device...
Protocol initialisation successful.

Beginning session...

Some devices may take up to 2 minutes to respond.
Please be patient!

Session begun.

Downloading device's PIT file...
PIT file download successful.

Uploading RECOVERY
100%
RECOVERY upload successful

Ending session...
Releasing device interface...

talon@talon-framework-debian:~/AndroidStuff/Samsung Galaxy Tab 2 10.1 (GT-P5100)$ 
```

You may now unplug the tablet from your computer. This is so that the battery
status screen won't interfere with trying to boot.

Now boot into the recovery by holding volume up (lefter button) and the power
button.

You should now see Team Win Recovery Project v2.8.5.0

![A screenshot of TWRP v2.8.5.0 running on the GT-P5100](
  Screenshots/Screenshot_2026-01-28-14-23-11.png
)
