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

molecular mass = -------

<b> 2. Describe your expectations for dissolved oxygen concentration as a function of time during a reaeration experiment. Assume you have added enough sodium sulfite to consume all of the oxygen at the start of the experiment. What would the shape of the curve look like?</b>

question 2
logarithmic

<b> 3. Why is $\hat{k}_{v,l}$ not zero when the gas flow rate is zero? How can oxygen transfer into the reactor even when no air is pumped into the diffuser? </b>

question 3

<b>4. Describe your expectations for $\hat{k}_{v,l}$ as a function of gas flow rate. Do you expect a straight line? Why?</b>

question 4

<b> 5. A dissolved oxygen probe was placed in a small vial in such a way that the vial was sealed. The water in the vial was sterile. Over a period of several hours the dissolved oxygen concentration gradually decreased to zero. Why? (You need to know how dissolved oxygen probes work!)</b>

(?) The dissolved oxygen probe calculates dissolve oxygen based on the change in pressure in the accumulator.

(based on diffusion through the oxygen permeable membrane, such that any oxygen present becomes converted into water. There is a circuit that measures picoamps flowing in the circuit to figure out the rate in which oxygen is turned into water. Oxygen level behind the membrane is zero. Any oxygen is immediately turned into water. It makes a meaningful measurement by using a two point linear calibration)
