# linux-key-remap

## 1. create a new script

Create a new script `/etc/init.d/keyremap`:

```bash
#! /bin/sh -e
set -e

PATH=/bin:/usr/bin:/sbin:/usr/sbin

# set scancode = keycode - 8
#

setkeycodes e011 148 # keycode 156 = XF86Launch1 NoSymbol XF86Launch1
setkeycodes e012 149 # keycode 157 = XF86Launch2 NoSymbol XF86Launch2
setkeycodes e013 184 # keycode 192 = XF86Launch5 NoSymbol XF86Launch5
setkeycodes e014 185 # keycode 193 = XF86Launch6 NoSymbol XF86Launch6
setkeycodes e015 186 # keycode 194 = XF86Launch7 NoSymbol XF86Launch7
setkeycodes e016 187 # keycode 195 = XF86Launch8 NoSymbol XF86Launch8
setkeycodes e017 188 # keycode 196 = XF86Launch9 NoSymbol XF86Launch9

exit 0
```

and make it exceutable:

```console
foo@bar:~$ cd /etc/init.d/
foo@bar:/etc/init.d$ sudo chmod +x keyremap
```

## 2. set the new script to be run when boots

```console
foo@bar:/etc/init.d$ cd /etc/rc5.d/
foo@bar:/etc/rc5.d/$ sudo ln -s ../init.d/keyremap S01keyremap
```

## 3. reboot and test the keys

Now the keys can be captured by program like `xev`.

## 4. set these keys as shortcuts in settings

This can be done in the `Settings` GUI.

