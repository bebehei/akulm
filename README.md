# akulm

After KernelUpgrade Loadable Modules

# Why?

Have you ever wondered, why your USB stick isn't recognized on your shiny laptop?! Well, it may be the case that you ran `pacman -Syu` and it included a linux kernel update.

# Installation

```
git clone https://github.com/bebehei/akulm.git
cd akulm
makepkg -i
```

It'll probably be available in AUR shortly.

# How does akulm work?

akulm provides some [pacman hooks](https://www.archlinux.org/pacman/alpm-hooks.5.html). These hooks instruct pacman to copy the modules of the currently used kernel into `/run/modules` and provide a link in `/usr/lib/modules`. So upon reboot, the only debris left is a symlink.

# Background

In comparison to other distros, ArchLinux only has got one kernel available at all times. While for example on debian, many `linux-image-*` packages are installed simultaneously. So `pacman` has to remove the module files, which are actually still required by the current running kernel. Any call to `insmod`/`modprobe` fails.

# Current Limitations

You can't downgrade to your current kernel version after you previous upgrade. You have to remove the symlink manually before invoking a downgrade. An `akulm clean` should suffice.
