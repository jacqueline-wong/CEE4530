# Lab 3 for CEE 4530

## Team 10: Victor Khong & Jacqueline Wong ##

<u>Using data from Irene Sarri & Felix Yang </u>

### Introduction ###
Our clients, Dr. Monroe Weber-Shirk and Jonathan Harris, work under the New York State Department of Environmental Conservation. They are concerned about the large seasonal inputs of acids into lakes in the Adirondack region of New York State, as the acid neutralizing capacity (ANC) may not be sufficient to neutralize these inputs. This occurs when snow from acid precipitation accumulates in winter, which melts and runs off into the lakes in spring.

### Objectives ###
Our clients have presented our research laboratory with the specific case of Wolf Pond, one such lake in the Adirondacks which is of concern. The main objectives of this study are to:

1. Create a model which simulates what happens to Wolf Pond during snow melt, assuming it acts as a Completely Mixed Flow Reactor (CMFR).
2. Determine the changes in the acid neutralizing capacity of Wolf Pond over time.

### Procedures ###

The experimental apparatus consists of an acid snow storage reservoir, peristaltic pump, and lake. In our model, snow is represented by the feed solution and its melting was assumed to be constant, controlled by the peristaltic pump (Figure 1). This feed runs into the lake, and a lake effluent runs out of the lake. For practical reasons, the simulation occurred over 20 minutes.

The acid neutralizing capacity of Wolf Pond is represented by the addition of sodium bicarbonate. The acid snow storage was set at pH 3 to provide a conservative measurement of whether the ANC of Wolf Pond is sufficient. 100-mL grab samples were collected at 0, 5, 10, 15, and 20 minutes for titration to better understand changes in ANC with time.

![apparatus](https://monroews.github.io/EnvEngLabTextbook/_images/Acid_rain_apparatus.png)
Figure 1: Experimental apparatus used to simulate snow melt into Wolf Pond

For the titration, pH was first measured with a pH probe as ANC can be estimated from proton concentration if it is below 4.5. Otherwise, a magnetic stirrer was placed in 50 mL of the sample and increments of 0.05 N HCl was titrated for a Gran plot analysis.

### Results ###

To start the experiment, we must understand our lake. To do so, we plot the measured pH of the lake against the dimensionless residencetime.

![pH](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab2/pHgraph.png)
Figure 2: M

Figure 2 shows the titration curve of the grab sample taken at 0 minutes.

![titration](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab3/Titration_0.png)
Figure 2: A titration curve for the 0 minute grab sample.

The titration curve above shows two regions. The first region is the buffer zone and the reaction $HCO_{3}^{-}+H^+->H_{2}CO_{3}^{-}$ is taking place as shown in the graph. The second region is when the lake has excess $H^+$ ions and the slow pH change is due to the fact that there are no reactions occurring to bring down the pH. Instead, the $H^+$ ions contribute to the decrease in pH directly.

In reality, there should be three regions. The titration curve shows only the second and third region. The first region is not shown in the Figure 2. This region would usually appear around pH 10.

For extra clarity of the interpretation of the results, we also plotted a Gran plot using the data from the titration curve above. To plot the Gran plot, we need to use the following equation for the linear regression:

$${F_1} = \frac{{{V_S} + {V_T}}}{{{V_S}}}{\text{[}}{{\text{H}}^ + }{\text{]}}$$

where $F_1$ is the first gran function, $V_s$ is the volume of the sample, $V_t$ is the volume of the titrant, and $[H^+]$ is the concentration of hydrogen ions.

![gran](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab3/Gran_0.png)
Figure 3: A Gran plot used for analysis of 0 minute sample.

With the Gran plot, we can calculate the equivalent volume using the following formula:

$$V_{eq}=\frac{-intercept}{slope}$$

where the intercept and the slope refers to the y-intercept and slope of Figure 2 respectively. From this, we found that the $V_{eq}$ was 1.7320669438481442 milliliter. This value is shown in Figure 2, the titration curve, as the gray line.

However, our real question and the motive behind our experiment is to determine the ANC of the lake and how the acid rain affects it. There are three models of ANC: conservative, volatile, and nonvolatile.

The ANC models, along with the measured ANC values of the lake are plotted in Figure 4. From Figure 4, we can see how the ANC of the lake would vary based on the hydraulic residence time if the lake was following each of these model respectively.

![ANC](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab3/ANC.png)
Figure 4: ANC models and the measured ANC values in the lake

From Figure 4, the measured ANC values followed closely with the conservative ANC model. The first point was slightly off from the model; however, this can easily be explained by uncertainties in the experiment. Overall, the ANC values agree with the conservative ANC model. Hence, the lake follows the conservative ANC model.

### Discussion ###

"Compare theoretical expectations with your results and discuss reasons for any observed deviations. If the results weren't as expected, suggest reasons why the laboratory results may have differed from theory and suggest improved techniques to obtain more accurate results or modifications to the theory to better describe the experimental conditions.""

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
From this experiment, it was found that the measured ANC values of the lake followed closely with the conservative ANC model. After a equivalent volume of approximately 1.73 mL, the titration curve shows that the lake enters the excess $H^+$ region. With this result, we can determine whether the lake in question will have sufficient ANC for a certain rain event based on the volume of the rain if the acidity of the rain is the same as 0.05 N HCl.

Having said that, it should be noted that in reality, the volume of runoff from snow melt is not constant and a conservative acid precipitation was used to show a more serious scenario of snow melt drastically affecting the lake. Additionally, runoff from snow melt occurs across a much longer time.

For our reactor model, the lakes are not actually CMFR. The assumption made in the experimentation simplified calculations, but do not accurately reflect what happens in the lake. In reality, the top of the lake is likely to be more acidic. There could also be other processes occurring in the lake and its surroundings that could influence the acid neutralizing capacity of the lake.

### Suggestions ###
Our team believes that while the experiment was successful, there were certain things that could be improved upon. One of the difficulties that we had with the experiment was with following the instructions, in particular setting up the experiment. We feel that this could have been made easier for us if a picture of the set up was shown rather than a diagram. Furthermore, experimentation on the magnetic stirrers should be done to ensure that it does not affect the results.

```python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
import aguaclara.core.utility as ut
from scipy import optimize
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from scipy import stats

# Question 1
Gran_data_0 = 'https://raw.githubusercontent.com/lw583/CEE4530/master/Lab3/0_minute_sample.xls'
V_titrant_0, pH_0, V_Sample_0, Normality_Titrant_0, V_equivalent_0, ANC_t0 = epa.Gran(Gran_data_0)

plt.subplots()
plt.plot(V_titrant_0,pH_0,'b-')
plt.axvline(x=V_equivalent_0.magnitude, color='tab:gray', linestyle='dotted')
plt.xlabel('Titrant Volume (mL)')
plt.ylabel('pH')
plt.legend(['data', 'equivalent volume'])

plt.annotate(s='', xy=(0.5,6.8), xytext=(1.25,6.25), arrowprops=dict(color='tab:red', arrowstyle='<->'))
plt.text(0.75, 6.75, 'buffer zone $HCO_{3}^{-}+H^+->H_{2}CO_{3}^{-}$', color='tab:red', fontsize=10)
plt.annotate(s='', xy=(2.75,3.25), xytext=(2,4), arrowprops=dict(color='tab:orange', arrowstyle='<->'))
plt.text(2, 4.25, 'excess H+', color='tab:orange', fontsize=10)

plt.savefig('Lab3/Titration_0.png')
plt.show()

# Question 2
def F1(V_sample,V_titrant,pH):
  return (V_sample + V_titrant)/V_sample * epa.invpH(pH)

F1_data = F1(V_Sample_0,V_titrant_0,pH_0)

slope, intercept, r_value, p_value, std_err = stats.linregress(V_titrant_0[7:9],F1_data[7:9])

intercept = intercept*u.mole/u.L
slope = slope*(u.mole/u.L)/u.mL
V_eq = -intercept/slope
ANC_sample = V_eq*Normality_Titrant_0/V_Sample_0
print('The r value for this curve fit is', ut.round_sf(r_value,5))
print('The equivalent volume was', ut.round_sf(V_eq,2))
print('The acid neutralizing capacity was',ut.round_sf(ANC_sample.to(u.meq/u.L),2))

gran_func=[V_eq.magnitude,V_titrant_0[-1].magnitude]
tit_vol=[0,(V_titrant_0[-1]*slope+intercept).magnitude]

plt.plot(V_titrant_0, F1_data,'o')
plt.plot(gran_func, tit_vol,'r')
plt.xlabel('Titrant Volume (mL)')
plt.ylabel('Gran function (mole/L)')
plt.legend(['data'])

plt.savefig('Lab3/Gran_0.png')
plt.show()

# Question 3
flowrate = 75/15 * u.mL/u.s
mass_total = 4.645 * u.kg
mass_tub = 0.496 * u.kg
density = 997 * u.kg/u.m**3
volume = (mass_total-mass_tub)/density
theta = volume/flowrate

data_file_path = "https://raw.githubusercontent.com/lw583/CEE4530/master/Lab2/lab2_datasheet.txt"
dframe = pd.read_csv(data_file_path,delimiter='\t')
lakepHnotes = epa.notes(data_file_path)
lakepHnotes
start = 8
column = 1
lakepH = epa.column_of_data(data_file_path,start,column)
time = ((epa.column_of_time(data_file_path,start))/theta).to(u.dimensionless)

mass = 623 * u.mg
MW = 84 * u.g/u.mol
lake_vol = 4 * u.L
ANC_0 = mass/(MW*lake_vol)
ANC_in = -10**(-3) * u.eq/u.L
ANC_out = ANC_0*np.exp(-time)+ANC_in*(1-np.exp(-time))

C_T = ANC_0*np.exp(-time)
ANC_closed = epa.ANC_closed(lakepH, C_T)
ANC_open = epa.ANC_open(lakepH).to(u.meq/u.L)

Gran_data_5 = 'https://raw.githubusercontent.com/lw583/CEE4530/master/Lab3/5_minute_sample.xls'
V_titrant_5, pH_5, V_Sample_5, Normality_Titrant_5, V_equivalent_5, ANC_t5 = epa.Gran(Gran_data_5)

Gran_data_10 = 'https://raw.githubusercontent.com/lw583/CEE4530/master/Lab3/10_minute_sample.xls'
V_titrant_10, pH_10, V_Sample_10, Normality_Titrant_10, V_equivalent_10, ANC_t10 = epa.Gran(Gran_data_10)

t0 = (0*u.min)/theta.to(u.min)
t5 = (5*u.min)/theta.to(u.min)
t10 = (10*u.min)/theta.to(u.min)

fig, ax = plt.subplots()
ax.plot(time, ANC_out,'r', time, ANC_closed,'b', time, ANC_open, 'g')
plt.plot(t0, ANC_t0.to(u.meq/u.L), 'k+', markersize=8)
plt.plot(t5, ANC_t5.to(u.meq/u.L),'k+', markersize=8)
plt.plot(t10, ANC_t10.to(u.meq/u.L),'k+', markersize=8)
plt.xlabel('hydraulic residence time')
plt.ylabel('ANC (meq/L)')
plt.legend(['Conservative ANC', 'Nonvolatile ANC', 'Volatile ANC'])

plt.savefig('Lab3/ANC.png')
plt.show()
```
