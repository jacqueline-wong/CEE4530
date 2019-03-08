# Lab 4 for CEE 4530

#### Team 10: Victor Khong & Jacqueline Wong ####

<b> 1. Eliminate the data from each data set when the dissolved oxygen concentration was less than 2 mg/L. This will ensure that all of the sulfite has reacted. Also remove the data when the dissolved oxygen concentration was greater than 6 mg/L to reduce the effect of measurement errors when the oxygen deficit is small.</b>

Please refer to Appendix for code used.

<b> 2. Plot a representative subset of the data showing dissolved oxygen vs. time. Perhaps show 5 plots on one graph.</b>

![DO](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab4/DOsubset.png)

<b>Figure 1</b>: Plots of dissolved oxygen against time for airflows of 100, 225, 525, 700 and 925 µmol/s. Generally, as airflow increases, less time is taken to reach saturated oxygen level. Each curve appears to be in a logarithmic-like shape, but lower airflows result in more linear-like shapes.

<b> 3. Calculate C⋆ based on the average water temperature, barometric pressure, and the equation from environmental processes analysis called O2_sat. C⋆=PO2 exp(1727T−2.105) where T is in Kelvin, PO2 is the partial pressure of oxygen in atmospheres, and C⋆ is in mg/L.</b>

Given an average water temperature of 22˚C and atmospheric pressure, C* is calculated to be 8.90 mg/L. Please refer to Appendix for code used.

<b> 4. Estimate k̂<sub>v,l</sub> using linear regression and equation (103) for each data set.</b>

Equation (103) of a simple gas transfer model is:
$$\ln \frac{C^{* } -C}{C^{* } -C_{0} } =-\hat{k}_{v,l} (t-t_{0} )$$

As the datasets have been manipulated such that the start of each aeration begins at time 0 (i.e. t<sub>0</sub> = 0), it can be simplified to:

$$\ln \frac{C^{* } -C}{C^{* } -C_{0} } =-\hat{k}_{v,l}\text{ }t$$

The equation can be linearized by plotting $\ln \frac{C^{* } -C}{C^{* } -C_{0} }$ against $t$. $-\hat{k}_{v,l}$ can be found by taking the negative of the slope. Please refer to Appendix for code used.

<b> 5. Create a graph with a representative plot showing the model curve (as a smooth curve) and the data from one experiment. You will need to derive the equation for the concentration of oxygen as a function of time based on equation (103).</b>

From the previous question, equation (103) can be further rearranged to be expressed in terms of the concentration of oxygen:

$$ C = C^{* } - (C^{* } - C_0)e^{-\hat{k}_{v,l}\text{ }t} $$

Given that C* and C<sub>0</sub> are constants, and k̂<sub>v,l</sub> was previously estimated, the above rearrangement can be used. We will be using the airflow at 225.0 µmol/s as the representative plot.

![model](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab4/model.png)

<b>Figure 2</b>: Plots of actual dissolved oxygen and model dissolved oxygen model against time for airflow of 225 µmol/s.

It can be seen that our model overestimates the time it takes to reaerate. Furthermore, we see that the curve for actual dissolved oxygen is less smooth compared to the curve for the model. This is expected due to uncertainties within the experiment and extraneous factors that we are unable to control.

<b> 6. Plot k̂<sub>v,l</sub> as a function of airflow rate (μmol/s).</b>

![k_vl](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab4/k_vl.png)

<b>Figure 3</b>: Plots of estimated k̂<sub>v,l</sub> against airflow rates.

While there is not a clear trend, appears that apart from some anomalies, k̂<sub>v,l</sub> increases with airflow rate. This makes sense as the more air is pumped per unit time, the more oxygen is pumped and the greater the volumetric gas transfer coefficient.

<b> 7. Plot OTE as a function of airflow rate (μmol/s) with the oxygen deficit (C⋆−C) set at 6 mg/L.</b>

The oxygen transfer efficiency can be calculated using the equation
$$OTE=\frac{\hat{k}_{v,l} \left(C^{* } -C\right)VRT}{MW_{O_{2} } Q_{air} P_{air} f_{O_{2} }}$$

![OTE](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab4/OTE.png)

<b>Figure 4</b>: Plots of oxygen transfer efficiency against airflow rates.

While there is not a clear trend, appears that apart from some anomalies, oxygen transfer efficiency decreases with airflow rate. This makes sense as the more oxygen is pumped per unit time, the faster it rises and escapes into the air above the water.

<b> 8. Comment on the oxygen transfer efficiency and the trend or trends that you observe.</b>

From <b>Figure 4</b>, the oxygen transfer efficiency is considerably low, and consistently below 50%. This is expected as the height of water and consequently the duration in which the oxygen can be dissolved into the water is very short. As a result, most of the oxygen will be released into the air directly above the water surface.

A general trend that we observed is that the greater the air flow rate, the greater the rate of increase in dissolved oxygen as shown in <b>Figure 1</b>. As airflow increases, less time is taken to reach saturated oxygen level. Each curve appears to be in a logarithmic-like shape, but lower airflows result in more linear-like shapes, with airflow of 100 μmol/s almost entirely linear. There is an exception with the air flow rate of 925µmol/s where the rate of increase in dissolved oxygen is actually lower than 525µmol/s and 700µmol/s. However, this may simply be a case where the experiment was not conducted properly and resulted in inaccurate data. Another trend is that the middle three curves are not jagged in shape whereas the two curves on either end is not, but rather smooth. This may simply be due to disruptions in the experiment or random uncertainties to do with the experimental apparatus.

Another trend that I observed is that the greater the air flow rate, the lower the oxygen transfer efficiency. This is reasonable as the surface area with which oxygen can be transferred into the water is approximately the same for air flow rates; yet, even at low air flow rates, 100% oxygen transfer efficiency cannot be reached. Hence, by increasing the air flow rate and consequently increasing the oxygen available for transfer but not changing the rate at which oxygen can transfer will result in lower oxygen transfer efficiency.

<b> 9. Propose a change to the experimental apparatus that would increase the efficiency.</b>

A change to the experimental apparatus that would increase the efficiency is using a larger container but filling the same volume of water such that a larger airflow rate could be used without the water overflowing from the container and disrupting our results. This would enable us to test for more airflow rates since the dissolved oxygen concentration increases at a greater rate with a higher airflow rate. However, since we still would like to test a range of airflow rate values, each airflow rate value currently used in this experiment can be increased by the same magnitude, for example by 50µmol/s or by 50%. This change in experimental apparatus would also enable us to test for a larger range of airflow rate values so there is greater flexibility in choosing the air flow rate values.

<b> 10. Verify that your report and graphs meet the requirements.</b>

We have verified that the report and graphs meet the requirements.

#### Discussion ####

To record data with ProCoDA, we must understand how it works as ProCoDA works in a specific manner. There are several stages before we could record data, one of which ProCoDA is "prepare to calibrate" and "calibrate". The experiment begins from the "prepare to calibrate" state. The "prepare to calibrate" state will switch to the "calibrate" state when the accumulator pressure is greater than the minimum calibration pressure given the data average interval of 0.1 s. After calibration, ProCoDA will switch to the "Pause" state. This happens when the accumulator pressure is greater than the maximum calibration pressure given the data average interval of 0.1 s. The way that ProCoDA knows to switch the "Pause" state to next state, which is "Aerate" is through the "New Rule" in ProCoDA, when elapsed time in the current state is greater than the elapsed time to calibrate to aeration lag.

Given that multiple states require the maximum calibration pressure to determine whether or not to switch to the next state, it is important for us to determine an equation to calculate the maximum calibration pressure. The following equation is the equation we used to calculate the maximum calibration pressure in this experiment.

$$\frac{\text{max cal}}{\text{source}} \times \text{source pressure}$$

This is better than using a constant for the maximum calibration pressure as the source pressure may change.

Another important calculation that we need to know is the predicted pressure in the accumulator when it is filled at a constant mass flow rate. ProCoDA calculates this for us by using the air flow model. Its inputs are minimum calibration pressure, maximum calibration pressure and fill time. Using the ramp function, it goes from minimum pressure to maximum pressure over the fill time linearly. The equation is as follows:

$$\frac{\text{max cal pressure}-\text{min cal pressure}}{\text{fill time}}$$

In our experiment, a critical component is the "air valve control". "Air valve control" is what we used to control the solenoid valves. The two states that use it are "Aerate" and "Fill accumulator". The inputs to the "air valve control" are air slope, air flow rate, accumulator pressure and source pressure.

To show our understanding of the ProCoDA program, we have also written a ProCoDA program that cycles between two states that aerate for 15 s and then pause for 10 s, which we have already shown to the TA.

#### Conclusions ####

Overall, for this experiment, we found out that the greater the air flow rate, the greater the rate of increase in dissolved oxygen concentration and the lower the oxygen transfer efficiency.

#### Suggestions ####

As mentioned in Question 9, using a larger container but filling the same volume of water is beneficial to the experiment. The problem with the current experimental apparatus is that water often has a chance to overflow at high air flow rates, which would disrupt our experiment. To counter for this, we are forced to used lower air flow rates. By using a larger container but filling the same volume of water, it would increase the efficiency because a larger airflow rate could be used without the water overflowing from the container and disrupting our results. This would enable us to test for more airflow rates since the dissolved oxygen concentration increases at a greater rate with a higher airflow rate. However, since we still would like to test a range of airflow rate values, each airflow rate value currently used in this experiment can be increased by the same magnitude, for example by 50µmol/s or by 50%. This change in experimental apparatus would also enable us to test for a larger range of airflow rate values so there is greater flexibility in choosing the air flow rate values.

Another suggestion is to include more pictures and diagrams in the instructions. We felt that pictures of different components and diagrams would have clarified some of the instructions and made it easier for us to follow the instructions step-by-step. This would have enabled us to complete the experiment with less mistakes and with greater efficiency.

#### Appendix ####

```python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
import aguaclara.core.utility as ut
import aguaclara.core.constants as c
import aguaclara.core.physchem as pc
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from scipy import stats
from scipy import optimize
import collections
import os
from pathlib import Path

def aeration_data(DO_column, dirpath):
    """This function extracts the data from folder containing tab delimited
    files of aeration data. The file must be the original tab delimited file.
    All text strings below the header must be removed from these files.
    The file names must be the air flow rates with units of micromoles/s.
    An example file name would be "300.xls" where 300 is the flowr ate in
    micromoles/s. The function opens a file dialog for the user to select
    the directory containing the data.

    Parameters
    ----------
    DO_column : int
        index of the column that contains the dissolved oxygen concentration
        data.

    dirpath : string
        path to the directory containing aeration data you want to analyze

    Returns
    -------
    filepaths : string list
        all file paths in the directory sorted by flow rate

    airflows : numpy array
        sorted array of air flow rates with units of micromole/s attached

    DO_data : numpy array list
        sorted list of numpy arrays. Thus each of the numpy data arrays can
        have different lengths to accommodate short and long experiments

    time_data : numpy array list
        sorted list of numpy arrays containing the times with units of seconds"""

    filenames = os.listdir(dirpath)
    airflows = ((np.array([i.split('.', 1)[0] for i in filenames])).astype(np.float32))
    idx = np.argsort(airflows)
    airflows = (np.array(airflows)[idx])*u.umole/u.s
    filenames = np.array(filenames)[idx]
    filepaths = [os.path.join(dirpath, i) for i in filenames]
    DO_data=[epa.column_of_data(i,0,DO_column,-1,'mg/L') for i in filepaths]
    time_data=[(epa.column_of_time(i,0,-1)).to(u.s) for i in filepaths]
    aeration_collection = collections.namedtuple('aeration_results','filepaths airflows DO_data time_data')
    aeration_results = aeration_collection(filepaths, airflows, DO_data, time_data)
    return aeration_results

# Question 1

DO_column = 2
dirpath = "Lab4/Aeration"
filepaths, airflows, DO_data, time_data = aeration_data(DO_column,dirpath)

DO_min = 2 * u.mg/u.L
DO_max = 6 * u.mg/u.L
for i in range(airflows.size):
  idx_start = (np.abs(DO_data[i]-DO_min)).argmin()
  idx_end = (np.abs(DO_data[i]-DO_max)).argmin()
  time_data[i] = time_data[i][idx_start:idx_end] - time_data[i][idx_start]
  DO_data[i] = DO_data[i][idx_start:idx_end]

# Question 2

plt.figure('ax',(10,7))
plt.plot(time_data[0], DO_data[0],'-')
plt.plot(time_data[4], DO_data[4],'-')
plt.plot(time_data[11], DO_data[11],'-')
plt.plot(time_data[15], DO_data[15],'-')
plt.plot(time_data[22], DO_data[22],'-')
plt.xlabel(r'time (s)')
plt.ylabel(r'Oxygen concentration (mg/L)')
leg = plt.legend((airflows[0].magnitude,airflows[4].magnitude,airflows[11].magnitude,airflows[15].magnitude,airflows[22].magnitude), loc='best')
plt.savefig('Lab5/DOsubset.png')
plt.show()

# Question 3

T = 22 * u.degC
P_air = 1 * u.atm
C_star = epa.O2_sat(P_air, T)
C_star

# Question 4

k_vl = np.zeros(airflows.size)
C_0 = 2 * u.mg/u.L

for i in range(airflows.size):
  DO_data_temp = DO_data[i]
  x = time_data[i]
  y = np.log((C_star - DO_data_temp)/(C_star - C_0)).magnitude
  slope, intercept, r_value, p_value, std_err = stats.linregress(x, y)
  k_vl[i] = -slope

k = k_vl / u.sec

# Question 5

C_model = np.zeros(airflows.size)
for i in range(len(time_data)):
  C = C_star-(C_star-C_0)*np.exp((-k[4]*time_data[4][i]).magnitude)
  C_model[i] = C.magnitude

t_model = np.linspace(0,max(time_data[4]),len(C_model))
plt.figure('ax',(10,7))
plt.plot(time_data[4], DO_data[4],'-')
plt.plot(t_model, C_model)
plt.xlabel(r'time (s)')
plt.ylabel(r'Oxygen concentration (mg/L)')
leg = plt.legend(('Actual data', 'Model'), loc='best')
plt.savefig('Lab4/model.png')
plt.show()

# Question 6

plt.figure('ax',(10,7))
plt.plot(airflows, k_vl,'-')
plt.xlabel(r'Airflow rate (μmol/s)')
plt.ylabel(r'k_v,l (1/s)')
plt.savefig('Lab4/k_vl.png')
plt.show()

# Question 7

R = 8.314 * u.J/u.mol/ u.K
OD = 6 * u.mg/u.L
MW_O2 = 32 * u.g/u.mol
V = 750 * u.mL
f_O2 = 0.21
OTE = (k_vl * OD * V * R * T)/(MW_O2 * airflows * P_air * f_O2)
plt.figure('ax',(10,7))
plt.plot(airflows, OTE,'-')
plt.xlabel(r'Airflow rate(μmol/s)')
plt.ylabel(r'OTE')
plt.savefig('Lab4/OTE.png')
plt.show()
```
