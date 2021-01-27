---
layout: default
title: i3wm
nav_order: 2
parent: Linux
---
# i3 window manager
{: .no_toc}
Titling window
{: .no_toc .text-delta }
1. TOC
{:toc}

<p align = "center">
<img src="/assets/image/i3wm.png" alt="hi" class="inline"/>
<em>Customized i3</em>
</p>

## Installation
* Old version from Ubuntu official repository
```shell
sudo apt install i3
```
This brings you i3-wm, i3status and i3lock.

* Latest version from third-party repository, see [here](https://i3wm.org/docs/repositories.html)

## Ricing
Default configuration file is located in /etc/i3 - something you could learn as beginner. User config file is in ~/.config/i3 - tweak as you want.

### Workspaces
* Move to workspace: **mod key** + workspace number
* Move focused container to workspace
* Assign applications on specific workspace

### Keyboard bindings
Bind keys to make i3 execute a command.

For example, this command simply kills the focused window.
```sh
bindsym $mod+q kill
```
### i3bar
Workspace bar is configured by a `bar` block with the following choices:  
* i3status
  ```console
  bar {
      status_command i3status
  }
  ```
* i3blocks
* polybar

i3status is handy because it comes with i3 - simple and satisfy all my needs.

The i3status config file is associated with the command.
```console
bar {
    status_command i3status --config ~/.i3status.conf
}
```
Comment out undesired widgets
```c
# order += "ipv6"
order += "cpu_usage"
order += "disk /"
order += "disk /home"
order += "wireless _first_"
order += "ethernet _first_"
order += "battery all"
order += "volume master"
# order += "load"
# order += "memory"
order += "tztime local"
```
Awesome fonts used to customized workspace name.
```sh
sudo apt-get install -y fonts-font-awesome
```
[Font Awesome](https://fontawesome.com/) - icon set

### Rofi
A window switcher, Application launcher and dmenu replacement

<p align = "center">
<img src="/assets/image/rofi.png" alt="hi" class="inline"/>
<em>Drop in menu</em>
</p>

## Reference
* Offical documents: [i3 User’s Guide](https://i3wm.org/docs/userguide.html)
* Series vedio: [i3 Youtbue](https://www.youtube.com/playlist?list=PL5ze0DjYv5DbCv9vNEzFmP6sU7ZmkGzcf)
* My i3dotfiles: [i3dotfiles Github](https://github.com/addy-dclxvi/i3-starterpack)
* Manjaro i3: [My Manjaro i3 setup](https://confluence.jaytaala.com/display/TKB/My+Manjaro+i3+setup)
