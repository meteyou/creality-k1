# Welcome to my Creality K1 guide

This guide will describe how to make the Creality K1 printer into a usable Klipper printer. The Creality K1 already uses
a heavily modified Klipper version by default, which Creality has customized. Some of these changes are very strange and
not very useful.

## What problems has the printer?

This printer has 1-2 massive hardware issues and furthermore the software is very messed up in my eyes. My personal main
negative point is the restriction of user rights to access the printer settings.

## Why am I doing this tutorial?

When the first K1 were delivered and by the printer's behavior, it was immediately clear to me that Klipper is running
in the background, which a Creality employee denied in an internal chat. Initially, I only wanted to demonstrate that
Creality was using Klipper with disregard for the license. I could do this through a friend who owns the printer, and I
made this public [here](https://twitter.com/meteyou/status/1666189027953766405). After that, I got the opportunity to
test a K1 through [nobufil](https://www.nobufil.com/) and to test it deeply. Since I already did all the work to make
the printer usable, I wanted to share this experience with the open-source community. I hope other users will continue
to expand this guide via PRs.

## Who am I?

My name is Stefan Dej, aka meteyou, and I am the maintainer of Mainsail. Mainsail is a well-known web interface for the
3D printer firmware/software Klipper. I have worked with Klipper for several years and know the software well.
