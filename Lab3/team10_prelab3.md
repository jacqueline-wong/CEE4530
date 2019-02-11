# Prelab 3 for CEE 4530

### Team 10: Victor Khong & Jacqueline Wong ###

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

<b> 1. Compare the ability of Cayuga lake and Wolf pond (an Adirondack lake) to withstand an acid rain runoff event (from snow melt) that results in 20% of the original lake water being replaced by acid rain. The acid rain has a pH of 3.5 and is in equilibrium with the atmosphere. The ANC of Cayuga lake is 1.6 meq/L and the ANC of Wolf Pond is 70 μeq/L. Assume that carbonate species are the primary component of ANC in both lakes, and that they are in equilibrium with the atmosphere. What is the pH of both bodies of water after the acid rain input? Remember that ANC is the conservative parameter (not pH!). Hint: You can use the scipy optimize root finding function called brentq. Scipy can’t handle units so the units must be removed using .magnitude.}</b>

As the pH of acid rain is below 4, its ANC can be approximated by:
$$ANC=[H^+] = 10^{-pH}= 10^{-3.2} = 0.000631 \text{ eq/L}$$

```python
ANC_rain = 10**(-3.2) * u.eq/u.L
ANC_CL_0 = 1.6 * u.meq/u.L
ANC_WP_0 = 70 * u.ueq/u.L

ANC_CL = ANC_rain*(0.2) + ANC_CL_0*(0.8)
ANC_WP = ANC_rain*(0.2) + ANC_WP_0*(0.8)

pH_CL = pH_open(ANC_CL)
pH_WP = pH_open(ANC_WP)

print("The pH of Cayuga Lake is", round(pH_CL, 2))
print("The pH of Wolf Pond is", round(pH_WP, 2))
```
The pH of Cayuga Lake is 8.50.
The pH of Wolf Pond is 7.63.

<b> 2. What is the ANC of a water sample containing only carbonates and a strong acid that is at pH 3.2? This requires that you inspect all of the species in the ANC equation (Equation (33)) and determine which species are important.</b>

The equation for acid neutralizing capacity is:
$$ ANC = [HCO_3^-]+2[CO_3^{-2} ]+{[OH}^- ] - [H^+] $$

<u>Insert pH diagram that shows what happens to carbonate and bicarbonate at low pH. Also know that low OH at low pH</u>

As the pH is below 4, its ANC can be approximated by:
$$ANC=[H^+] = 10^{-pH}= 10^{-3.2} = 0.000631 \text{ eq/L}$$

<b> 3. Why is [H+] not a conserved species? </b>

[H<sup>+</sup>] is generally not conserved because it likely to react with there may react with bicarbonate or other species in the water. However, at a very low pH, [H<sup>+</sup>] is generally conserved. </u>

---
Do we know the ANC of the samples? Use CMFR equation

- Graph should go to -0.001
- Should delete comments in data file for lab
