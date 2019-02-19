# Prelab 4 for CEE 4530

### Team 10: Victor Khong & Jacqueline Wong ###

```python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
from scipy import optimize
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
```

<b>1. Calculate the mass of sodium sulfite needed to reduce all the dissolved oxygen in 600 mL of pure water in equilibrium with the atmosphere and at 22˚C.</b>

The reaction between oxygen and sulfite is:

$$\text{O}_{{2}} +\text{2SO}_{{3}}^{-{2}} \stackrel{{cobalt}}{\longrightarrow}\text{2SO}_{{4}}^{-{2}}$$

Thus, the mass of sodium sulfite needed to deoxygenate 1 g of oxygen is:

$$\frac{{\text{mol}\; \text{O}}_{{2}} }{{32\; \text{g}\; } } \times \frac{{2\; \text{mol\; Na}_{{2}} \text{SO}_{{3}}} }{{\text{mol}\; O}_{{2}} } \times \frac{{126\; \text{g}}}{{\text{mol Na}}_{{2}}\text{SO}_{{3}} } =\frac{{\; 7.875\; \text{g\; Na}_{{2}} \text{SO}_{{3}}} }{{\text{g O}_{2}} }$$

```python
MW_O2 = 32 * u.g/u.mol
MW_Na2SO3 = 126 * u.g/u.mol
ratio = (1/MW_O2)*2*(MW_Na2SO3)
ratio
```

The mass of dissolved oxygen in 600 mL of pure water in equilibrium with the atmosphere at 22˚C can then be calculated. The air pressure here is 1 atm.

```python
P_air = 1 * u.atm
temp = 22 * u.degC
conc_O2 = epa.O2_sat(P_air, temp)

vol = 600 * u.mL
mass_O2 = conc_O2 * vol
mass_O2.to(u.mg)
```

As the mass of dissolved oxygen in pure water is 5.338 mg. The amount of sodium sulfite required for deoxygenation can then be found.

```python
mass_Na2SO3 = ratio * mass_O2
mass_Na2SO3.to(u.mg)
```

Thus, at least 42.034 mg of sodium sulfite is required.

<b> 2. Describe your expectations for dissolved oxygen concentration as a function of time during a reaeration experiment. Assume you have added enough sodium sulfite to consume all of the oxygen at the start of the experiment. What would the shape of the curve look like?</b>

We would expect the shape of the curve describing the dissolved oxygen concentration as a function of time to look logarithmic in nature, but will flatten out rather than increase forever as it approaches the saturation level. Initially, the oxygen concentration would increase rapidly before increasing at a slower rate. The reason for this is because the oxygen concentration will slowly approach saturation level and when the oxygen concentration approaches saturation level, it becomes harder for oxygen to dissolve.

<b> 3. Why is $\hat{k}_{v,l}$ not zero when the gas flow rate is zero? How can oxygen transfer into the reactor even when no air is pumped into the diffuser? </b>

The reason why $\hat{k}_{v,l}$ is not zero when the gas flow rate is zero is because the gas does not need to flow in order for gas to exchange oxygen. As long as direct contact, oxygen will be exchanged and $\hat{k}_{v,l}$ will not be zero. Oxygen can transfer into the reactor even when no air is pumped into the diffuser because diffusers are either made of porous materials, for example, ceramic and plastic membranes, or non-porous materials, in which case a hole in the pipe. Both scenarios enable oxygen to flow into the reactor without additional need for pump.

<b>4. Describe your expectations for $\hat{k}_{v,l}$ as a function of gas flow rate. Do you expect a straight line? Why?</b>

My expectation is that 

<b> 5. A dissolved oxygen probe was placed in a small vial in such a way that the vial was sealed. The water in the vial was sterile. Over a period of several hours the dissolved oxygen concentration gradually decreased to zero. Why? (You need to know how dissolved oxygen probes work!)</b>

The dissolved oxygen probe calculates dissolved oxygen based on the fact that an applied potential of 0.8V can reduce oxygen to water:

$$4 e^- + 4 H^+ + O_2 \;\mathrm{\to}\; 2 H_2O$$

The rate at which oxygen diffuses through the membrane is proportional to the oxygen concentration in the solution, and its eventual reduction to water produces a current that is measured by the meter.

After several hours, all the dissolved oxygen in the vial will be reduced to water at the silver cathode of the probe, and there will be none left to produce a current that can be measured by the probe, thus gradually decreasing to a zero reading.
