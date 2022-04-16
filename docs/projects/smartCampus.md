---
layout: default
title: UNSW Smart Campus
nav_order: 1
parent: Projects
---

# UNSW Smart Campus
EE building Sensor Network
{: .fs-6 .fw-300 }

## Introduction
### Smart Campus Project 
Gain insights into the behavior of real estate usage on UNSW  through the instrumentation of IoT devices. Mainly covered areas: 

1. Bus queue
2. Classroom attendance
3. Car park
4. Wifi

### EE building project:
  Build a **sensor network** system to collect and cleanse sensor data from the HPD camera and beam counters installed in the Electrical Engineering building.  **Data visualization** is then performed to answer the question of the elevator and shared study space usage.

## Sensors 
<p align = "center">
<img src="/assets/image/smartcampus/sensors.png" alt="sensors" class="inline"/>
<em>Beam counter and Human counting camera</em>
</p>

<p align = "center">
<img src="/assets/image/smartcampus/device_statistics.PNG" alt="sensors" class="inline"/>
<br>
<em>Device installation covering labs, meeting rooms and corridors </em>
</p>

## Network 
Yellow routers are white listed by IT department provided with Mac address. They could therefore connected with uni_wide device(campus network) through tunnelling of VPN.

### VPN 
Tinc run on routers and the sensor_server with key pairs generated.

Server: Open certain port to listen to the connections from routers.

Routers: Store the hard-coded server list.

<table><tr>
<td> 
  <p align="center">
    <img alt="vpn_table" src="/assets/image/smartcampus/vpn_hosts.PNG" width="350">
    <br>
    <em style="color: grey">VPN hosts</em>
  </p> 
</td>
<td> 
  <p align="center">
    <img alt="vpn_table" src="/assets/image/smartcampus/vpn_table.PNG" width="300">
    <br>
    <em style="color: grey">VPN description table</em>
  </p> 
</td>
</tr></table>

## Sensor Network System and Visualization Results 
<iframe width="100%" height="700" src="/assets/poster.pdf">If you are seeing this text, the preview of the CV failed. Most likely this happened because your browser does not support this technical feature. In this case, please download the CV using the link above.</iframe>

