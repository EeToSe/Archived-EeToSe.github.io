---
layout: default
title: preparation
nav_order: 1
parent: Linux
---
# Environment Setup
{: .no_toc}
Tweak everything for efficiency
{: .no_toc .text-delta }
1. TOC
{:toc}

## Distros
OS based on Linux Kernel: Debian, Fedora, Arch, etc.

My current OS in use
* [Ubuntu 20.04 LTS](https://releases.ubuntu.com/20.04/) - maybe the most popular Debian based distribution
* [Manjaro i3](https://manjaro.org/downloads/community/i3/) - my favorite with a well riced i3wm by default

## Installation
* [Rufus](https://rufus.ie/) only available on windows used to create a bootable USB driver
* Partition: reference for [general schemes](https://help.ubuntu.com/community/PartitioningSchemes) and [well-written guide](https://help.ubuntu.com/lts/installation-guide/amd64/install.en.pdf)

My partition table
| Partition | Size(GB) |
| :---:|  :---: |
| /   |   40 |
| /home |  100 |
| swap  |  16  |

P.S. To resize your partition after installation, you could boot from USB drive and use **gparted**.

## Sync icloud-calendar with thunderbird
Detailed info found [here](https://webhostinghero.org/ubuntu-icloud-sync/), steps are summarised as below.
1. Create an Apple App-Specific Password
2. Setup icloud on Thunderbird
  * install adds-on : Lightning, LightningButton, Lightning Calendar Tabs, TbSync and Provider for CalDAV & CardDAV
  * TbSync -> Account actions -> Add new account menu and select  CalDAV & CardDAV
  * Enter the previously generated application password
  * Restart Thunderbird and ctrl + shift + c to open the calendar

## Data Transfer between linux and ios
Device: iphone 6s plus - ios 13.7 + Razer Ubuntu 20.04 LTS
### Access iphone on PC with USB
[Youtube step by step intro](https://www.youtube.com/watch?v=LWkIQK-HBDI)
```sh
sudo apt install ifuse
mkdir ~/iphone
ifuse ~/iphone
```
### Drop PC file to iphone
* Download vlc and open "sharing via WIFI"
* Open PC browser with the url providerd and drop your files  
* Open FIles in ios and check files in the vlc folder

A more technical method to try [here](https://www.addictivetips.com/ubuntu-linux-tips/transfer-files-from-linux-to-ios-wirelessly/).

### Use icloud drive

  
## Chinese input
A detailed How-to could be found [here](https://leimao.github.io/blog/Ubuntu-Gaming-Chinese-Input/)

## Overleaf
[A weird offset](https://support.mozilla.org/bg/questions/1263396?&mobile=0) found which is caused by [monospace](https://en.wikipedia.org/wiki/Monospaced_font) issue. In the prefrence page of firefox, change the option of Monospace from proportional one to monospace should fix the problem. 

## Resize disk partition
As partitions must be **unmounted** in order to be modified, a bootable USB with Gparted is suggested to boot into the computer. A online [tutorial](https://www.howtoforge.com/partitioning_with_gparted)could be found here.

## Connect with Airpods Pro
[Answer](https://reckoning.dev/blog/airpods-pro-ubuntu/) here.


