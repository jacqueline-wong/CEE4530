# Lab 2 for CEE 4530


#### Team 10: Victor Khong & Jacqueline Wong ####

<u>Using data from Irene Sarri & Felix Yang </u>

```python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
from scipy import optimize
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
```

$K_1 = 10^{-6.3}\newline K_2 = 10^{-10.3}\newline
K_H = 10^{-1.5} \text{ mol L}^{-1} \text{atm}^{-1} \newline P_{CO_2}=10^{-3.5} \text{ atm}\newline K_w = 10^{-14}$

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
theta.to(u.hr)
lakepHnotes = epa.notes(data_file_path)
lakepHnotes
start = 8
column = 1
lakepH = epa.column_of_data(data_file_path,start,column)
time = ((epa.column_of_time(data_file_path,start))/theta).to(u.dimensionless)

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
ANC_in = -10**(-3) * u.eq/u.L
ANC_out = ANC_0*np.exp(-time)+ANC_in*(1-np.exp(-time))
fig, ax = plt.subplots()
ax.plot(time,ANC_out,'r')
plt.xlabel('hydraulic residence time')
plt.ylabel('ANC')

plt.savefig('Lab2/ANCgraph.png')
plt.show()
```

![ANC](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab2/ANCgraph.png)

<b>3. If we assume that there are no carbonates exchanged with the atmosphere during the experiment, then we can calculate ANC in the lake effluent by using equation (14) describing the ANC of a closed system. Calculate the ANC under the assumption of a closed system and plot it on the same graph produced in answering question #3 with the plot labeled (in the legend) as closed ANC.</b>

$$ANC=C_T \left(\alpha_1 +2\alpha_2 \right)+\frac{K_w}{\left[H^+ \right]} - \left[H^+ \right]$$

where

$$C_T = \left[H_2{CO}_3^* \right] + \left[{HCO}_3^- \right]+\left[{CO}_3^{-2} \right]$$

$$\alpha_0 =\frac{1}{1+\frac{K_1 }{[H^+]} +\frac{K_1 K_2}{[H^+]^2} }$$

$$ \alpha_1 = \frac{1}{\frac{[H^+]}{K_1} + 1 + \frac{K_2}{[H^+]}} $$

$$\alpha_2 = \frac{1}{\frac{[H^+]^2 }{K_1 K_2} +\frac{[H^+]}{K_2} + 1}$$

```python
C_T = ANC_0*np.exp(-time)
ANC_closed = epa.ANC_closed(lakepH, C_T)

fig, ax = plt.subplots()
ax.plot(time, ANC_out,'r', time,ANC_closed,'b')
plt.xlabel('hydraulic residence time')
plt.ylabel('ANC')
plt.legend(['Expected ANC', 'Closed ANC'])

plt.savefig('Lab2/ANCclosed.png')
plt.show()

```
![ANC Closed](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab2/ANCclosed.png)

<b>4.If we assume that there is exchange with the atmosphere and that carbonates are at equilibrium with the atmosphere, then we can calculate ANC in the lake effluent by using equation (18) describing the ANC of an open system. Calculate the ANC under the assumption of an open system and plot it on the same graph produced in answering question #3 with the plot labeled (in the legend) as open ANC.</b>

$$ANC=\frac{P_{CO_2} K_H }{\alpha_0 } (\alpha_1 +2\alpha_2 ) + \frac{K_w }{\left[H^+ \right]} - \left[H^+ \right]$$

$$C_T = \frac{P_{CO_2} K_H}{\alpha_0}$$

```python
ANC_open = epa.ANC_open(lakepH)
fig, ax = plt.subplots()
ax.plot(time, ANC_out,'r', time, ANC_closed,'b', time, ANC_open, 'g')
plt.xlabel('hydraulic residence time')
plt.ylabel('ANC')
plt.legend(['Expected ANC', 'Closed ANC', 'Open ANC'])

plt.savefig('Lab2/ANCopen.png')
plt.show()
```

![ANC Open](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab2/ANCopen.png)

<b>5. Analyze the data from the second experiment and graph the data appropriately. What did you learn from the second experiment?</b>

In the second experiment, sodium bicarbonate was replaced with calcium carbonate to give the same acid neutralizing capacity.

```python
dfp = "https://raw.githubusercontent.com/lw583/CEE4530/master/Lab2/lab2_datasheet2.txt"
df = pd.read_csv(dfp,delimiter='\t')

lakepHnotes2 = epa.notes(dfp)
lakepHnotes2
start = 8
end = 350
column = 1
lakepH2 = epa.column_of_data(dfp,start,column,end)
time2 = ((epa.column_of_time(dfp,start,end))/theta).to(u.dimensionless)

fig, ax = plt.subplots()
ax.plot(time2,lakepH2,'r')
plt.xlabel('hydraulic residence time')
plt.ylabel('pH')

plt.savefig('Lab2/pHgraph2.png')
plt.show()
```
![pH Graph 2](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab2/pHgraph2.png)

As it can be seen on the graph, the pH dropped very fast and thus experiment was stopped quickly. This was because the calcium carbonate did not dissolve and remained on the sides of the tank. Thus, the actual ANC in the tank was much lower than what it was  calculated to be.

#### Questions ####

<b>1. What do you think would happen if enough NaHCO3 were added to the lake to maintain an ANC greater than 50μeq/L for 3 residence times with the stirrer turned off? How much NaHCO3 would need to be added?</b>

If the stirrer was turned off, not all of the sodium bicarbonate will end up dissolving different parts of lake will have different pH. The ANC will remain at the bottom of the lake, while the top of the lake will be very acidic. <u>Thus, a lot more sodium bicarbonate would need to be added to give the same result.</u>

<b>2. What are some of the complicating factors you might find in attempting to remediate a lake using CaCO3? Below is a list of issues to consider.

- extent of mixing
- solubility of CaCO3 (find the solubility and compare with NaHCO3)
- density of CaCO3 slurry (find the density of CaCO3)</b>

CaCO3 is hard to dissolve. This is shown in the results of our experiment (Question 5), where the CaCO3 was not dissolved at all. The solubility of CaCO3 is ___________ whereas the solubility of NaHCO3 is _____________.

Furthermore, since the density of CaCO3 is high, most of the CaCO3 will sink to the bottom of the lake. This means that CaCO3 is likely not well mixed in the lake as the lake will be highly concentrated at the bottom of the lake and not really concentrated at the top of the lake.

As a result of its low solubility, there will be an inability to mix the CaCO3 well in the lake. There will be regions of much higher concentration at the bottom of the lake and regions of much lower concentration at the top of the lake. This would cause the lake to be "over-remediated" at parts of the lake, but not remediated at all at other parts of the lake.
