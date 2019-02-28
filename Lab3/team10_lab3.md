# Lab 3 for CEE 4530

## Team 10: Victor Khong & Jacqueline Wong (2) ##

<u>Using data from Irene Sarri & Felix Yang </u>

### Introduction ###
Our clients, Dr. Monroe Weber-Shirk and Jonathan Harris, work under the New York State Department of Environmental Conservation. They are concerned about the large seasonal inputs of acids into lakes in the Adirondack region of New York State, as the acid neutralizing capacity (ANC) may not be sufficient to neutralize these inputs. This occurs in spring when snow that accumulates in winter melts and runs off into the lakes.

### Objectives ###
Our clients have presented our research laboratory with the specific case of Wolf Lake, one such lake in the Adirondacks which is of concern. The main objectives of this study are to:

1. Create a model which simulate what happens to Wolf Lake during snow melt.
2. Determine the changes in acid neutralizing capacity of Wolf Lake with time.

### Procedures ###

- Created model and ran it, assuming Completely Mixed Flow Reactor (CMFR)
- Collected samples
- Measured ANC of samples with pH >4.5 using titration

### Results ###

<b>1. Plot the titration curve of the t=0 sample with 0.05 N HCl (plot pH as a function of titrant volume). Label the equivalent volume of titrant. Label the 2 regions of the graph where pH changes slowly with the dominant reaction that is occurring. (Place labels with the chemical reactions on the graph in the pH regions where each reaction is occurring.) Note that in a third region of slow pH change no significant reactions are occurring (added hydrogen ions contribute directly to change in pH).</b>

![titration](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab3/Titration_0.png)

$${F_1} = \frac{{{V_S} + {V_T}}}{{{V_S}}}{\text{[}}{{\text{H}}^ + }{\text{]}}$$
$$ANC=\frac{V_e N_t }{V_s }$$

```python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
import aguaclara.core.utility as ut
from scipy import optimize
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from scipy import stats

Gran_data_0 = 'https://raw.githubusercontent.com/lw583/CEE4530/master/Lab3/0_minute_sample.xls'
V_titrant, pH, V_Sample, Normality_Titrant, V_equivalent, ANC = epa.Gran(Gran_data_0)

plt.plot(V_titrant,pH,'b-')
plt.xlabel('Titrant Volume (mL)')
plt.ylabel('pH')
plt.legend(['data'])

plt.savefig('Lab3/Titration_0.png')
plt.show()

def F1(V_sample,V_titrant,pH):
  return (V_sample + V_titrant)/V_sample * epa.invpH(pH)

F1_data = F1(V_Sample,V_titrant,pH)

slope, intercept, r_value, p_value, std_err = stats.linregress(V_titrant[7:9],F1_data[7:9])

intercept = intercept*u.mole/u.L
slope = slope*(u.mole/u.L)/u.mL
V_eq = -intercept/slope
ANC_sample = V_eq*Normality_Titrant/V_Sample
print('The r value for this curve fit is', ut.round_sf(r_value,5))
print('The equivalent volume was', ut.round_sf(V_eq,2))
print('The acid neutralizing capacity was',ut.round_sf(ANC_sample.to(u.meq/u.L),2))

gran_func=[V_eq.magnitude,V_titrant[-1].magnitude]
tit_vol=[0,(V_titrant[-1]*slope+intercept).magnitude]

plt.plot(V_titrant, F1_data,'o')
plt.plot(gran_func, tit_vol,'r')
plt.xlabel('Titrant Volume (mL)')
plt.ylabel('Gran function (mole/L)')
plt.legend(['data'])

plt.savefig('Lab3/Gran_0.png')
plt.show()
```

<b>2. Prepare a Gran plot using the data from the titration curve of the t=0 sample. Use linear regression on the linear region or simply draw a straight line through the linear region of the curve to identify the equivalent volume. Compare your calculation of V_e with that was calculated by ProCoDA.</b>

<b>3. Plot the measured ANC of the lake on the same graph as was used to plot the conservative, volatile, and nonvolatile ANC models (see questions 2 to 5 of the Acid Precipitation and Remediation of an Acid Lake lab). Did the measured ANC values agree with the conservative ANC model?</b>

### Discussion ###

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

"Summarize the results in a few sentences"

### Suggestions ###

set up with picture rather than diagram

```python
# Put all Python code here at the end
```
