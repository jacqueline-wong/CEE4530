# Lab 3 for CEE 4530

## Team 10: Victor Khong & Jacqueline Wong ##

### Introduction ###
Our client, Dr. Monroe Weber-Shirk and Jonathan Harris, are expert food scientists who are concerned that our daily diet contains too much additives, particularly the unnecessary use of dye for aesthetic appeal. Whilst dye is generally considered a safe substance to be used in food, overconsumption may lead to certain health problems such as bladder tumors. Children are particularly vulnerable to the detrimental health effects posed by dye. In particular, some brands of fruit punch and strawberry jello, two popular children’s snacks, can contain large amounts of red dye. Hence, the current situation with food dye and human health is very concerning to our client.

Our client has presented our research laboratory with a sample of distilled water that contains the same amount of red dye as one of the most popular fruit punches on the market. Our task is to measure the concentration of red dye in the solution, which will be a first step in supporting their investigations on food dye levels in popular food and beverage items.

Given the properties of the red dye, absorption spectroscopy presented itself as one of the best analytical technique that can be used to accurately determine the concentration of a compound. The theory behind it is that colored solutions absorb light in the visible range and the resulting color of the solution is the spectrum of light that is not absorbed, but transmitted. According to Beer’s law, the attenuation of light in a chemical solution is proportional to the concentration and the length of the path that the light passes through:


### Objectives ###
Our client has presented us with two sets of objectives:
$\bullet$ Investigate the concentration of dye in given solution
$\bullet$ Prepare a $ 1\text{M} \ NaCl $ solution


### Procedures ###
<b>Investigating the concentration of dye in given solution</b>
First, we prepared 0, 1, 2, 5, 10, 20, 50, 100 and 200 mg/L standards of red dye in distilled water. Each standard was created in a 100 mL volumetric flask, with red dye measured using a 10-100 µL pipette. The absorbance of each standard was measured with a photometer in order of increasing concentration as voltages, which were later converted to .

Plotted to determine the effective range of absorbance measurements of the photometer instrument.

<b>Preparing a $ 1M \ NaCl $ solution</b>
First,

### Results ###

<b>1. Plot the titration curve of the t=0 sample with 0.05 N HCl (plot pH as a function of titrant volume). Label the equivalent volume of titrant. Label the 2 regions of the graph where pH changes slowly with the dominant reaction that is occurring. (Place labels with the chemical reactions on the graph in the pH regions where each reaction is occurring.) Note that in a third region of slow pH change no significant reactions are occurring (added hydrogen ions contribute directly to change in pH).</b>

<b>2. Prepare a Gran plot using the data from the titration curve of the t=0 sample. Use linear regression on the linear region or simply draw a straight line through the linear region of the curve to identify the equivalent volume. Compare your calculation of V_e with that was calculated by ProCoDA.</b>

<b>3. Plot the measured ANC of the lake on the same graph as was used to plot the conservative, volatile, and nonvolatile ANC models (see questions 2 to 5 of the Acid Precipitation and Remediation of an Acid Lake lab). Did the measured ANC values agree with the conservative ANC model?</b>

### Discussion ###

### Conclusions ###

"Summarize the results in a few sentences"

### Suggestions ###

```python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
from scipy import optimize
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

def ANC_zeroed(pHguess, ANC):
  return ((epa.ANC_open(pHguess) - ANC).to(u.mol/u.L)).magnitude

def pH_open(ANC):
  return optimize.brentq(ANC_zeroed, 0, 14,args=(ANC))
```
