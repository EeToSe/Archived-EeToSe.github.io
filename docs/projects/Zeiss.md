---
layout: default
title: Zeiss Algorithm Development
nav_order: 3
parent: Projects
---

## Phase-shifting deflectometry(折射)

<p align="center">
<img src="/assets/image/Zeiss/PMD.png" width = 600/> <br>
<em> The schematic setup of the system based on phase-shifting deflectometry </em> 
</p>

**Phase-shifting**: We project $N$ fringe patterns, each shifted by $2\pi/N$.

## Three Information Channels
1. "**Slope**": created point by point, which provides in-depth information
   <br><u>Surface defects</u>: dents(压痕), blisters(气泡) and runs. <br>
   "**Curvature**": created by differentiation
   <br><u>geometric defects</u>:  with pronounced edges, like cavities, pits(凹点), notches(凹痕) and scratches
2. "**Modulation**": how strongly the sinusoidal oscillation occurs at a certain point and represents the local gloss level of a surface. 
   <br><u>Defects</u>: matte areas(无光泽区域) such as dirt, scratches and coating(涂层) defects. 
3. "**Grayscale**": exhibits almost no noise as a result of its synthesis from the initial phase-shifted images. 

### How to compute


## [Active Illumination Methods](https://www.youtube.com/watch?v=_Vo9Vcecwo0&list=PL2zRqk16wsdowTcMVNhV0-7RjSOBS4rHO&index=8&ab_channel=FirstPrinciplesofComputerVision)
### Intensity Ratio Method
But what we can get from captured images are image intensities: $\frac{I_1}{I_2} = \frac{\rho \cdot L_1}{\rho \cdot L_2}$
<p align="center">
<img src="/assets/image/Zeiss/intensity_ratio1.png" width = 400/> 
<img src="/assets/image/Zeiss/intensity_ratio2.png" width = 400/> 
</p>
Where $x_p$ is the position of the column in the projected image such that we know which column in your projector is illuminating that point.   

### Phase Shifting Method
<p align="center">
<img src="/assets/image/Zeiss/phase_shifting1.png" width = 400/> 
<img src="/assets/image/Zeiss/phase_shifting2.png" width = 400/> 
<img src="/assets/image/Zeiss/phase_shifting3.png" width = 400/>
<img src="/assets/image/Zeiss/phase_shifting4.png" width = 400/>  
</p>

3 equations and 3 unknowns -> we can solve $x_p$