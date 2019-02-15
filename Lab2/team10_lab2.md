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

The influent ANC can be calculated from:

$$ pH = -log{[H+]}$$
$$ ANC_{in} ≅−[H+]$$

Since the pH of the acid rain is 3,

$$ [H+] = 10^{-3} $$
$$ ANC_{in} ≅ -10^{-3} $$

The effluent ANC can be calculated from:

$${ANC}_{{0}} {\; }=\left[{ANC}_{out} - ANC_{in} \cdot \left(1 - {\mathop{e}\nolimits^{-t/\theta}} \right)\right]{\mathop{e}\nolimits^{t/\theta}}$$

$${ANC}_{out}=\frac{{ANC}_{{0}}}{{\mathop{e}\nolimits^{t/\theta}}} + ANC_{in} \cdot \left(1 - {\mathop{e}\nolimits^{-t/\theta}} \right){\; }$$

```python
mass = 623 * u.mg
MW = 84 * u.g/u.mol
lake_vol = 4 * u.L
ANC_0 = mass/(MW*lake_vol)
ANC_in = -10**(-3)
t = np.arange(0,10,1)
ANC_out = np.zeros(len(t))

for i in t:
  ANC_out[i] = ANC_0.magnitude/np.exp(i)+ANC_in*(1-np.exp(-i))

fig, ax = plt.subplots()
ax.plot(t,ANC_out,'r')
plt.xlabel('hydraulic residence time')
plt.ylabel('lake effluent ANC')

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
