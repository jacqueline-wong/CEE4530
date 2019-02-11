# Prelab 3 for CEE 4530

### Team 10: Victor Khong & Jacqueline Wong ###

```python
from aguaclara.core.units import unit_registry as u
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from scipy import stats
```

<b> 1. Compare the ability of Cayuga lake and Wolf pond (an Adirondack lake) to withstand an acid rain runoff event (from snow melt) that results in 20% of the original lake water being replaced by acid rain. The acid rain has a pH of 3.5 and is in equilibrium with the atmosphere. The ANC of Cayuga lake is 1.6 meq/L and the ANC of Wolf Pond is 70 μeq/L. Assume that carbonate species are the primary component of ANC in both lakes, and that they are in equilibrium with the atmosphere. What is the pH of both bodies of water after the acid rain input? Remember that ANC is the conservative parameter (not pH!). Hint: You can use the scipy optimize root finding function called brentq. Scipy can’t handle units so the units must be removed using .magnitude.}</b>

As the pH of acid rain is below 4, its $ANC$ can be approximated by: $$ANC=[H^+]$$

First, need to find the equivalence volume required

$$ V_{e} {\; =}\frac{V_{s} \cdot N_{s} }{N_{t} } $$

where:
$V_e$ = "equivalent" volume, L
$N_s$ = normality of sample, eq/L
$V_s$ = volume of sample, L
$N_t$ = normality of titrant, eq/L

Here, $N_s$ is the acid neutralizing capacity of Cayuga Lake or Wolf Pond, and $N_t$ is the acid neutralizing capacity of the acid rain.

For Cayuga Lake:
$$ V_{e} {\; =}\frac{V_{s} \cdot 0.0016 }{10^{-3.5}} $$
$$ V_{e} {\; =} 5.06V_{s}$$

For Wolf pond:
$$ V_{e} {\; =}\frac{V_{s} \cdot70 \times 10^{-6}}{10^{-3.5}} $$
$$ V_{e} {\; =} 0.221V_{s}$$

Next, we use the following equation to find out the concentration of $H+$ ions.
$$ \left[H^{+} \right]=\frac{N_{t} \left(V_{t} -V_{e} \right)}{\left(V_{s} +V_{t} \right)} $$

As 20% of the original lake water is replaced by acid rain, we know that:

$$V_t = 0.2 V_s$$

where:
$V_t$ = volume of titrant, L

For Cayuga Lake,
$$ \left[H^{+} \right]=\frac{10^{-3.5} \left(0.2V_s -5.06V_s \right)}{\left(V_{s} +0.2V_s \right)} $$

$$ \left[H^{+} \right]=\frac{-0.00154V_s}{1.2V_s} $$

$$ \left[H^{+} \right]=-0.00128 $$

For Wolf Pond,
$$ \left[H^{+} \right]=\frac{10^{-3.5} \left(0.2V_s -0.221V_s \right)}{\left(V_{s} +0.2V_s \right)} $$

Finally, we use the following equation to find out the pH of the lake after the acid rain.
$$ pH = -\log_{10}{[H+]} $$

For Cayuga Lake,
$$ pH = -\log_{10}{-0.00128} $$
$$ pH = -\log_{10}{(-0.00128)} $$

For Wolf Pond,

...

For pH 3...
$$ V_s \times 10^{-3} = 3 \Delta V_t \times N_t $$

<b> 2. What is the ANC of a water sample containing only carbonates and a strong acid that is at pH 3.2? This requires that you inspect all of the species in the ANC equation (Equation (33)) and determine which species are important.</b>

The equation for acid neutralizing capacity is:
$$ ANC = [HCO_3^-]+2[CO_3^{-2} ]+{[OH}^- ] - [H^+] $$

<u>Insert pH diagram that shows what happens to carbonate and bicarbonate at low pH. Also know that low OH at low pH</u>

As the pH of acid rain is below 4, its ANC can be approximated by: $$ANC=[H^+]$$

<b> 3. Why is [H+] not a conserved species? </b>

[H<sup>+</sup>] is generally not conserved because it likely to react with there may react with bicarbonate or other species in the water. However, at a very low pH, [H<sup>+</sup>] is generally conserved. </u>

---
Do we know the ANC of the samples? Use CMFR

Q ANC = Q2 ANC + Q3 ANC
