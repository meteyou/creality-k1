# Klipper

First, we need to replace the service file because it overwrites the config at every klipper start. This is intended for
an update process but is annoying if you want to make adjustments yourself. Furthermore, I have reworked the Klipper
config to be more straightforward and to use all fans as Klipper intended. Creality has set up all fans in the standard
config slightly strange (in my opinion). Furthermore, I found a typo in a Klipper file modified by Creality. We are also
changing this.

## Update Klipper service

I only turned off the "copy_config" function in the start function of the service.

```bash
cd /etc/init.d
rm S55klipper_service
wget -q -O S55klipper_service https://github.com/meteyou/creality-k1/raw/main/klipper/S55klipper_service
```

## Fix bug in Klipper error report

Creality forgot a `"` in the JSON error output. So this output is not a valid JSON string. It would only be a wrong
output message but have no issues with printing.

```bash
cd /usr/share/klipper/klippy
rm gcode.py
wget -q -O gcode.py https://github.com/meteyou/creality-k1/raw/main/klipper/klippy/gcode.py
```

## Change printer.cfg

I have adjusted the following settings in the Klipper config:
- split config in multiple files
- change all fans from output_pin to there real usage (heater_fan, fan, temperature_fan, ...)
- change all macros to the new fans
- optimize stepper driver settings

To remove the old config and download the new config, execute following lines:
```bash
cd /usr/data/printer_data/config
rm *.cfg
wget -q -O printer.cfg https://github.com/meteyou/creality-k1/raw/main/klipper/config/printer.cfg
mkdir addons
cd addons
wget -q -O adxl.cfg https://github.com/meteyou/creality-k1/raw/main/klipper/config/addons/adxl.cfg
wget -q -O bed_leveling.cfg https://github.com/meteyou/creality-k1/raw/main/klipper/config/addons/bed_leveling.cfg
wget -q -O chamber.cfg https://github.com/meteyou/creality-k1/raw/main/klipper/config/addons/chamber.cfg
wget -q -O extruder.cfg https://github.com/meteyou/creality-k1/raw/main/klipper/config/addons/extruder.cfg
wget -q -O fans.cfg https://github.com/meteyou/creality-k1/raw/main/klipper/config/addons/fans.cfg
wget -q -O gcode_macro.cfg https://github.com/meteyou/creality-k1/raw/main/klipper/config/addons/gcode_macro.cfg
wget -q -O heater_bed.cfg https://github.com/meteyou/creality-k1/raw/main/klipper/config/addons/heater_bed.cfg
wget -q -O led.cfg https://github.com/meteyou/creality-k1/raw/main/klipper/config/addons/led.cfg
wget -q -O mcu.cfg https://github.com/meteyou/creality-k1/raw/main/klipper/config/addons/mcu.cfg
wget -q -O printer_params.cfg https://github.com/meteyou/creality-k1/raw/main/klipper/config/addons/printer_params.cfg
wget -q -O sensorless.cfg https://github.com/meteyou/creality-k1/raw/main/klipper/config/addons/sensorless.cfg
wget -q -O stepper.cfg https://github.com/meteyou/creality-k1/raw/main/klipper/config/addons/stepper.cfg
```