# Lab 4 for CEE 4530

#### Team 10: Victor Khong & Jacqueline Wong ####

```python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
import aguaclara.core.utility as ut
import aguaclara.core.constants as c
import aguaclara.core.physchem as pc
from scipy import optimize
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from scipy import stats
```

<b> 1. Eliminate the data from each data set when the dissolved oxygen concentration was less than 2 mg/L. This will ensure that all of the sulfite has reacted. Also remove the data when the dissolved oxygen concentration was greater than 6 mg/L to reduce the effect of measurement errors when the oxygen deficit is small.</b>

<b> 2. Plot a representative subset of the data showing dissolved oxygen vs. time. Perhaps show 5 plots on one graph.</b>

<b> 3. Calculate C⋆ based on the average water temperature, barometric pressure, and the equation from environmental processes analysis called O2_sat. C⋆=PO2e(1727T−2.105) where T is in Kelvin, PO2 is the partial pressure of oxygen in atmospheres, and C⋆ is in mg/L.</b>

<b> 4. Estimate k̂ v,l using linear regression and equation (103) for each data set.</b>

<b> 5. Create a graph with a representative plot showing the model curve (as a smooth curve) and the data from one experiment. You will need to derive the equation for the concentration of oxygen as a function of time based on equation (103).</b>

<b> 6. Plot k̂ v,l as a function of airflow rate (μmole/s).</b>

<b> 7. Plot OTE as a function of airflow rate (?mole/s) with the oxygen deficit (C⋆−C) set at 6 mg/L.</b>

<b> 8. Comment on the oxygen transfer efficiency and the trend or trends that you observe.</b>

<b> 9. Propose a change to the experimental apparatus that would increase the efficiency.</b>

<b> 10. Verify that your report and graphs meet the requirements.</b>

<b> (include discussion of below questions) </b>

1. Under what condition does ProCoDA switch from the “prepare to calibrate” state to the “calibrate” state?

ProCoDA switches from the "prepare to calibrate" state to the "calibrate" state when the accumulator pressure is greater than the minimum calibration pressure given the data average interval of 0.1 s.

2. Under what condition does ProCoDA switch from the “calibrate” state to the “Pause” state?

ProCoDA switches from the "calibrate" state to the "Pause" state when the accumulator pressure is greater than the maximum calibration pressure given the data average interval of 0.1 s.

3. How does the “Pause” state know which state to go to next?

ProCoDA switches from the "Pause" state to the next state "Aerate" because of the "New Rule" in ProCoDA, when elapsed time in the current state is greater than the elapsed time to calibrate to aeration lag.

4. What is the equation that is used to calculate the maximum calibration pressure and why is this equation better than using a constant for the maximum calibration pressure?

The equation used to calculate the maximum calibration pressure is:

$$\frac{\text{max cal}}{\text{source}} \times \text{source pressure}$$

This is better than using a constant for the maximum calibration pressure as the source pressure may change.

5. Explain how ProCoDA calculates the predicted pressure in the accumulator when it is filled at a constant mass flow rate.

ProCoDA calculates predicted pressure in the accumulator using the air flow model. Its inputs are minimum calibration pressure, maximum calibration pressure and fill time. Using the ramp function, it goes from minimum pressure to maximum pressure over the fill time linearly.

$$\frac{\text{max cal pressure}-\text{min cal pressure}}{\text{fill time}}$$

6. What are the inputs to the “air valve control”?

The inputs to the "air valve control" are air slope, air flow rate, accumulator pressure and source pressure.

7. What does “air valve control” control and which two states use it?

"Air valve control" controls the solenoid valves. The two states that use it are "Aerate" and "Fill accumulator".

8. Write a ProCoDA program that cycles between two states that aerate for 15 s and then pause for 10 s. Show the TA!

### Conclusions ###

### Suggestions ###

### Appendix ###
