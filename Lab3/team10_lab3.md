# Lab 3 for CEE 4530

## Team 10: Victor Khong (8 hours) & Jacqueline Wong (12 hours) ##

<u>Using data from Irene Sarri & Felix Yang </u>

### Introduction and Objectives ###
Our clients, Dr. Monroe Weber-Shirk and Jonathan Harris, work under the New York State Department of Environmental Conservation. They are concerned about the large seasonal inputs of acids into lakes in the Adirondack region of New York State, as the acid neutralizing capacity (ANC) may not be sufficient to neutralize these inputs. This occurs when snow from acid precipitation accumulates in winter, which melts and runs off into the lakes in spring.

Our clients have presented our research laboratory with the specific case of Wolf Pond, one such lake in the Adirondacks which is of concern. The main objectives of this study are to:

1. Create a model which simulates what happens to Wolf Pond during snow melt, assuming it acts as a Completely Mixed Flow Reactor (CMFR).
2. Determine the changes in the acid neutralizing capacity of Wolf Pond over time.
3. Determine if ANC follows a volatile or nonvolatile model.

We will be assuming the lake is a CMFR (completely mixed flow reactor) and that ANC is conservative, the influent ANC can be calculated from the following equation given pH is below 4.5:

$$ pH = -log{[H+]}$$
$$ ANC_{in} ≅−[H+]$$

The expected effluent ANC can be rearranged and calculated from the CMFR mass balance equation to:

$${ANC}_{{0}} {\; }=\left[{ANC}_{out} - ANC_{in} \cdot \left(1 - {\mathop{e}\nolimits^{-t/\theta}} \right)\right]{\mathop{e}\nolimits^{t/\theta}}$$

$${ANC}_{out}=\frac{{ANC}_{{0}}}{{\mathop{e}\nolimits^{t/\theta}}} + ANC_{in} \cdot \left(1 - {\mathop{e}\nolimits^{-t/\theta}} \right){\; }$$

We will also be including a second model, which will be a closed system. This takes into account reactions, but assumes that there are no carbonates exchanged with the atmosphere during the experiment. The ANC in the lake effluent can be calculated from:

$$ANC=C_T \left(\alpha_1 +2\alpha_2 \right)+\frac{K_w}{\left[H^+ \right]} - \left[H^+ \right]$$

where

$$C_T = \left[H_2{CO}_3^* \right] + \left[{HCO}_3^- \right]+\left[{CO}_3^{-2} \right]$$

$$\alpha_0 =\frac{1}{1+\frac{K_1 }{[H^+]} +\frac{K_1 K_2}{[H^+]^2} }$$

$$ \alpha_1 = \frac{1}{\frac{[H^+]}{K_1} + 1 + \frac{K_2}{[H^+]}} $$

$$\alpha_2 = \frac{1}{\frac{[H^+]^2 }{K_1 K_2} +\frac{[H^+]}{K_2} + 1}$$

Our third model will be an open system, which assumes that there are carbonates exchanged in equilibrium with the atmosphere during the experiment. The ANC in the lake effluent can be calculated from:

$$ANC=\frac{P_{CO_2} K_H }{\alpha_0 } (\alpha_1 +2\alpha_2 ) + \frac{K_w }{\left[H^+ \right]} - \left[H^+ \right]$$

$$C_T = \frac{P_{CO_2} K_H}{\alpha_0}$$

### Procedures ###

The experimental apparatus consists of an acid snow storage reservoir, peristaltic pump, and lake. In our model, snow is represented by the acid feed solution and its melting was assumed to be constant, controlled by the peristaltic pump to have a flow rate of 267 mL/min(Figure 1). This feed runs into the lake, and a lake effluent runs out of the lake. For practical reasons, the simulation occurred over 20 minutes rather than multiple months.


Given that recent studies from our clients have confirmed the acid neutralizing capacity of Wolf Pond as typically 1.85 meq/L, this was represented by the addition of 623 mg sodium bicarbonate in a 4L lake (we later repeated this with calcium carbonate). The acid snow storage was set at pH 3 to provide a conservative measurement of whether the ANC of Wolf Pond is sufficient. 100-mL grab samples were collected at 0, 5, 10, 15, and 20 minutes for titration to better understand changes in ANC with time.

![apparatus](https://monroews.github.io/EnvEngLabTextbook/_images/Acid_rain_apparatus.png)
Figure 1: Experimental apparatus used to simulate snow melt into Wolf Pond

For the titration, pH was first measured with a pH probe as ANC can be estimated from proton concentration if it is below 4.5. Otherwise, a magnetic stirrer was placed in 50 mL of the sample and increments of 0.05 N HCl was titrated for a Gran plot analysis.

### Results and Discussion ###

To start the experiment, we must first understand the changes in pH in our lake. To do so, we plotted the measured pH of the lake against the dimensionless residence time.

![pH](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab2/pHgraph.png)
Figure 2: pH of the lake against its dimensionless residence time.

It can be seen that pH decreases slowly from 0 to 0.75 hydraulic residence time, but reaches an equivalence point between 0.75 and 1.00 hydraulic residence time, and continues decreasing as more acid is added.

Since the pH of the acid precipitation is 3 (below 4.5),

$$ [H+] = 10^{-3} $$
$$ANC_{in} ≅ -10^{-3} $$

With this conservative assumption, we graphed the expected ANC in the lake effluent against the hydraulic residence time as shown in Figure 3.

![ANC](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab2/ANCgraph.png)
Figure 3: Assumption of conservative lake ANC against the hydraulic residence time

As mentioned above, assuming that there are no carbonates exchanged with the atmosphere during the experiment (i.e. closed system), the ANC in the lake effluent can be calculated with:

$$ANC=C_T \left(\alpha_1 +2\alpha_2 \right)+\frac{K_w}{\left[H^+ \right]} - \left[H^+ \right]$$

Again, to visualize the results, we plot it onto Figure 4.

![ANC Closed](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab2/ANCclosed.png)
Figure 4: Conservative model and closed system (nonvolatile) models of lake ANC

Also mentioned above is the open system assumption. With this assumption, we use a different equation, namely the following equation, to calculate the lake effluent.

$$ANC=\frac{P_{CO_2} K_H }{\alpha_0 } (\alpha_1 +2\alpha_2 ) + \frac{K_w }{\left[H^+ \right]} - \left[H^+ \right]$$

$$C_T = \frac{P_{CO_2} K_H}{\alpha_0}$$

We plotted the results onto the same plot as the results for ANC of the lake under closed system for comparison in Figure 5.

![ANC Open](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab2/ANCopen.png)

Figure 5: Conservative model, closed system (nonvolatile) and open system (volatile) models of lake ANC

To understand the lake in greater detail, we also experimented with calcium carbonate in place of sodium bicarbonate to give the same acid neutralizing capacity of the lake.

![pH Graph 2](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab2/pHgraph2.png)
Figure 6: pH of the lake against its dimensionless residence time using calcium carbonate instead of sodium bicarbonate.

As it can be seen from Figure 6, the pH dropped very fast and thus experiment was stopped quickly. This was because the calcium carbonate did not dissolve and remained on the sides of the tank. Thus, the actual ANC in the tank was much lower than what it was calculated to be.

However, the real motive behind the experiment is to figure out how the acid rain will affect the ANC of the lake. Figure 7 shows the titration curve of the grab sample taken at 0 minutes.

![titration](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab3/Titration_0.png)
Figure 7: A titration curve for the 0 minute grab sample.

The titration curve above shows two regions. The first region is the buffer zone and the reaction $HCO_{3}^{-}+H^+->H_{2}CO_{3}^{-}$ is taking place as shown in the graph. The second region is when the lake has excess $H^+$ ions and the slow pH change is due to the fact that there are no reactions occurring to bring down the pH. Instead, the $H^+$ ions contribute to the decrease in pH directly.

In reality, there should be three regions. The titration curve shows only the second and third region. The first region is not shown in the Figure 7. This region would usually appear around pH 10.

For extra clarity of the interpretation of the results, we also plotted a Gran plot using the data from the titration curve above. To plot the Gran plot, we need to use the following equation for the linear regression:

$${F_1} = \frac{{{V_S} + {V_T}}}{{{V_S}}}{\text{[}}{{\text{H}}^ + }{\text{]}}$$

where $F_1$ is the first gran function, $V_s$ is the volume of the sample, $V_t$ is the volume of the titrant, and $[H^+]$ is the concentration of hydrogen ions.

![gran](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab3/Gran_0.png)
Figure 8: A Gran plot used for analysis of 0 minute sample.

With the Gran plot, we can calculate the equivalent volume of titrant using the following formula:

$$V_{eq}=\frac{-intercept}{slope}$$

where the intercept and the slope refers to the y-intercept and slope of Figure 7 respectively. From this, we found that the $V_{eq}$ was 1.73 mL. This value is shown in Figure 7, the titration curve, as the gray line.

However, our real question and the motive behind our experiment is to determine the ANC of the lake and how the acid rain affects it. There are three models of ANC: conservative, volatile (close system), and nonvolatile (open system).

The ANC models, along with the measured ANC values of the lake are plotted in Figure 4. From Figure 9, we can see how the ANC of the lake would vary based on the hydraulic residence time if the lake was following each of these model respectively.

![ANC](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab3/ANC.png)
Figure 9: ANC models and the measured ANC values in the lake

From Figure 9, the measured ANC values followed closely with the volatile ANC model. The first point was slightly off from the model; however, this is likely due to uncertainties in the experiment. One such source of uncertainty would be the volumetric pipette for titration. Overall, the ANC values agree with the conservative ANC model. Hence, the lake follows the conservative ANC model.

### Conclusions ###
From this experiment, it was found that the measured ANC values of the lake followed closely with the conservative ANC model. After a equivalent volume of approximately 1.73 mL, the titration curve shows that the lake enters the excess $H^+$ region. With this result, we can determine whether the lake in question will have sufficient ANC to buffer for snow melt in spring. Because our simulation goes beyond buffer zone into low levels of pH, it can be concluded that Wolf Pond does not have enough ANC. This would affect aquatic life.

Having said that, it should be noted that in reality, the volume of runoff from snow melt is not constant and a more acidic precipitation was used to show a more serious scenario of snow melt drastically affecting the lake. Additionally, runoff from snow melt occurs across a much longer time.

For our reactor model, the lakes are not actually CMFR. The assumption made in the experimentation simplified calculations, but do not accurately reflect what happens in the lake. In reality, the top of the lake is likely to be more acidic. There could also be other processes occurring in the lake and its surroundings that could influence the acid neutralizing capacity of the lake.

### Suggestions ###
Our team believes that while the experiment was successful, there were certain things that could be improved upon. One of the difficulties that we had with the experiment was with following the instructions, in particular setting up the experiment. We feel that this could have been made easier for us if a picture of the set up was shown rather than a diagram. Furthermore, testing of the magnetic stirrers should be done to ensure that it is grounded and does not affect the results in the future, as we had to use another team's data because of this.

### Appendix ###
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
t15 = (15*u.min)/theta.to(u.min)
t20 = (20*u.min)/theta.to(u.min)

ANC_t15 = ANC_0*np.exp(-t15)+ANC_in*(1-np.exp(-t15))
ANC_t20 = ANC_0*np.exp(-t20)+ANC_in*(1-np.exp(-t20))

fig, ax = plt.subplots()
ax.plot(time, ANC_out,'r', time, ANC_closed,'b', time, ANC_open, 'g')
plt.plot(t0, ANC_t0.to(u.meq/u.L), 'k+', markersize=8)
plt.plot(t5, ANC_t5.to(u.meq/u.L),'k+', markersize=8)
plt.plot(t10, ANC_t10.to(u.meq/u.L),'k+', markersize=8)
plt.plot(t15, ANC_t15.to(u.meq/u.L),'k+', markersize=8)
plt.plot(t20, ANC_t20.to(u.meq/u.L),'k+', markersize=8)
plt.xlabel('hydraulic residence time')
plt.ylabel('ANC (meq/L)')
plt.legend(['Conservative ANC', 'Nonvolatile ANC', 'Volatile ANC', 'Sample ANC'])

plt.savefig('Lab3/ANC.png')
plt.show()
```
