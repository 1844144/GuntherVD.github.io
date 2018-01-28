---
layout: default
---

## Connect ESP32 with linux

Unlike windows, linux don't have com1, com2 and so on. In Linux devices are found in the /dev/ directory. In order to find the port of our ESP32 we unplug the ESP32 and type in a prompt:

```
# ls /dev/tty*
```

Now Connect your ESP32 and repeat the previous command

```
# ls /dev/tty*
```

The new device is your ESP32. in my case it is /dev/ttyUSB0. Now we need to add our user to the usergroup that may connect to the serial devices. Replace ttyUSB0 with the devicename you found.

```
# stat /dev/ttyUSB0
```

In the reply you find something like `Gid:( 14/ uucp)` so for Archlinux the group will be uucp. In other distributions you may need to use something else like `dialout` for example.

Next you need root access. Let's add our user in the group. Make sure you replace the group and if the user is not your current account the user aswell.

```
sudo usermod -a -G uucp $USER
```

Before you can use the serial connections you need to logout and login.

For the connection i use [Putty](https://www.putty.org/). You can use any terminal software of your liking. If you need to install putty do it now. Remember! This command works for Archlinux. Change it if you use a different distribution.

```
# sudo pacman -S putty
```

Now start putty.




[back](./)
