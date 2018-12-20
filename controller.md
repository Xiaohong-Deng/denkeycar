# PS4 Controller Pairing

This helps you pair the PS4 controller with Pi. If you start driving the RC car in joystick mode you will see feedback on the screen by pushing the analog sticks. The car doesn't take orders as expected. You need to hack `parts/controller.py` a bit to make it actually be able to control the RC car. Or you can check out [the new repo](https://github.com/autorope/donkeypart_ps3_controller) added to Donkey recently.

The following instructions are based on [RetroPie][0] and [ds4drv][1].

### Install `ds4drv`.

After you ssh into your Donkey, you can directly `sudo /home/pi/env/bin/pip install ds4drv`

### Grant permission to `ds4drv`.

```bash
sudo wget https://raw.githubusercontent.com/chrippa/ds4drv/master/udev/50-ds4drv.rules -O /etc/udev/rules.d/50-ds4drv.rules
sudo udevadm control --reload-rules
sudo udevadm trigger
```
### Run `ds4drv`.

`ds4drv --hidraw --led 00ff00`. If you see `Failed to create input device: "/dev/uinput" cannot be opened for writing`, reboot and retry. Probably granting permission step doesn't take effect until rebooting. Some controllers don't work with `--hidraw`. If that's the case try the command without it. `--led 00ff00` changes the light bar color, it's optional.

### Start controller in pairing mode.

Press and hold **Share** button, then press and hold **PS** button until the light bar starts blinking. If it goes **green** after a few seconds, pairing is successful.

### Run `ds4drv` in background on startup once booted.

`sudo nano /etc/rc.local`. paste `/home/pi/env/bin/ds4drv --led 00ff00` into the file. Save and exit. Again, with or without `--hidraw`, depending on the particular controller you are using.


To disconnect, kill the process `ds4drv` and hold **PS** for 10 seconds to power off the controller.

---
[0]: https://github.com/RetroPie/RetroPie-Setup/wiki/PS4-Controller#installation
[1]: https://github.com/chrippa/ds4drv
