# Lab 3 for CEE 4530

## Team 10: Victor Khong & Jacqueline Wong ##

### Introduction ###
Our clients, Dr. Monroe Weber-Shirk and Jonathan Harris, work under the New York State Department of Environmental Conservation. They are concerned about the large seasonal inputs of acids into lakes in the Adirondack region of New York State, as the acid neutralizing capacity (ANC) may not be sufficient to neutralize these inputs. This occurs in spring when snow that accumulates in winter melts and runs off into the lakes.

Our client has presented our research laboratory with the case of Wolf Lake, one such lake in the Adirondacks which is of concern. Our task is to simulate

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
