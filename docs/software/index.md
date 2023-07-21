# Software issues/fixes

The Creality K1 is running a klipper fork from December 2022 (according to git history, it was updated one or two times
after that). This has some modifications to support the hardware of this printer. For example, the main MCU is not
supported by Klipper by default. Furthermore, loadcells are used in the heating bed for homing/leveling. These are
currently not supported by Klipper either. Furthermore, Creality uses its own web interface (which has a very low
functionality) with its own API.

## What will we do?

First, we need to set up root access. We can do this through a hack from the YouTuber
[K3D // Dimitry Sorkin](https://www.youtube.com/@SorkinDmitry){:target="_blank"}. After that, we reset Moonraker and
update it. Then we enable the Moonraker service. Moonraker is disabled by default. After the activation of the API, we
can install the web interface. In my case, the choice is Mainsail. Here I have provided a customized version to support
then Creality K1 best possible. Once the system is set up, we can start with the Klipper config. Here I have prepared a
clean config. But we still have to turn off a function of the Creality OS. Otherwise, the Klipper config will be
overwritten after each reboot.
