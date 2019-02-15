# Lab 2 for CEE 4530


#### Team 10: Victor Khong & Jacqueline Wong ####

```python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
from scipy import optimize
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
```
---
Use CMFR equation to find ANC of the samples

- Graph should go to -0.001
- Should delete comments in data file for lab

---

$K_1 = 10^{-6.3}, \text{ }K_2 = 10^{-10.3}, \text{ }
K_H = 10^{-1.5} \text{ mol L}^{-1} \text{atm}^{-1}, \newline P_{CO_2}=10^{-3.5} \text{ atm}, \text{ }K_w = 10^{-14}$

<b>1. Plot measured pH of the lake versus dimensionless hydraulic residence time (t/θ).</b>

```python
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
time = ((epa.column_of_time(data_file_path,start,-1))/theta).to(u.dimensionless)

fig, ax = plt.subplots()
ax.plot(time,lakepH,'r')
plt.xlabel('hydraulic residence time')
plt.ylabel('pH')

plt.savefig('Lab2/pHgraph.png')
plt.show()
```
![pH](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab2/pHgraph.png)

<b>2. Assuming that the lake can be modeled as a completely mixed flow reactor and that ANC is a conservative parameter, equation (25) can be used to calculate the expected ANC in the lake effluent as the experiment proceeds. Graph the expected ANC in the lake effluent versus the hydraulic residence time (t/θ) based on the completely mixed flow reactor equation with the plot labeled (in the legend) as conservative ANC.</b>

$${ANC}_{{0}} {\; }=\left[{ANC}_{out} - ANC_{in} \cdot \left(1 - {\mathop{e}\nolimits^{-t/\theta}} \right)\right]{\mathop{e}\nolimits^{t/\theta}}$$

Equation 25 above can be rearranged to:
$${ANC}_{out} = {ANC}_{{0}} {\; }{\mathop{e}\nolimits^{-t/\theta}}+ ANC_{in} \cdot \left(1 - {\mathop{e}\nolimits^{-t/\theta}} \right)$$

As $ANC_0$ and $ANC_{in}$ are constants, we can build a new array that varies based on time. But first, $ANC_0$ can be calculated from the 623 mg of sodium bicarbonate in the lake:

```python
mass = 623 * u.mg
MW = 84 * u.g/u.mol
lake_vol = 4 * u.L
ANC_0 = mass/(MW*lake_vol)
```
$$[\text{NaHCO}_3]_ 0 = 623 \text{ mg}{\times }\frac{{1 \text{ mol}} }{{84,000\text{ mg}}} \times\frac{1}{4\text{ L}} = 0.00185 \text{ mol/L} $$

$$[\text{NaHCO}_3]_ 0 = 0.00185 \text{ mol/L} = 0.00185 \text{ eq/L} = ANC_{0}$$

```python
pH_rain = 3
ANC_in = 10**(-pH_rain)
ANC_array = np.zeros(len(time))

for i in range(len(time)):
    ANC_array[i] = ANC_0.magnitude * np.exp(-time[i]) + ANC_in * (1-np.exp(-time[i]))

fig, ax = plt.subplots()
ax.plot(time,ANC_array,'r')
plt.xlabel('hydraulic residence time')
plt.ylabel('ANC')

plt.savefig('Lab2/ANCgraph.png')
plt.show()
```

<b>3. If we assume that there are no carbonates exchanged with the atmosphere during the experiment, then we can calculate ANC in the lake effluent by using equation (14) describing the ANC of a closed system. Calculate the ANC under the assumption of a closed system and plot it on the same graph produced in answering question #3 with the plot labeled (in the legend) as closed ANC.</b>

$$ANC=C_T \left(\alpha_1 +2\alpha_2 \right)+\frac{K_w}{\left[H^+ \right]} - \left[H^+ \right]$$

```python
```

<b>4.If we assume that there is exchange with the atmosphere and that carbonates are at equilibrium with the atmosphere, then we can calculate ANC in the lake effluent by using equation (18) describing the ANC of an open system. Calculate the ANC under the assumption of an open system and plot it on the same graph produced in answering question #3 with the plot labeled (in the legend) as open ANC.</b>

$$ANC=\frac{P_{CO_2} K_H }{\alpha_0 } (\alpha_1 +2\alpha_2 ) + \frac{K_w }{\left[H^+ \right]} - \left[H^+ \right]$$

<b>5. Analyze the data from the second experiment and graph the data appropriately. What did you learn from the second experiment?</b>
