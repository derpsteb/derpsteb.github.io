---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: post
title: How to run ffmpeg-4.4 on Ubuntu 18.04 LTS
author: Otto Bittner
date:   2021-11-13
tags: nix ubuntu ffmpeg ffplay
---

# [nix](https://github.com/NixOS/nix) installation

Taken from [here](https://ariya.io/2020/05/nix-package-manager-on-ubuntu-or-debian):
```sh
# execute as root

$ adduser nix_user
$ mkdir /nix
$ chown nix_user:nix_user /nix
$ su nix_user
```

```sh
# execute as nix_user

$ cd /nix
$ sh <(curl -L https://nixos.org/nix/install) --no-daemon
$ source /home/nix_user/.nix-profile/etc/profile.d/nix.sh

# optional
$ nix-env -i hello
$ which hello
$ hello
```

# FFmpeg installation

```sh
# execute as nix_user

$ nix-env -i ffmpeg-full-4.4
# grab the path to the ffplay binary
$ which ffplay
$ exit
```

Using the binary path you just got you can invoke `ffplay` like any other binary as root now. 
Beware: You can't install packages as root.
