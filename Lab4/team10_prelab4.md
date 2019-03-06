# Prelab 4 for CEE 4530

### Team 10: Victor Khong (3 hours) & Jacqueline Wong (2 hours) ###

<b>1. Calculate the change in hydraulic grade line between baffled sections of a reactor with a flow rate of 380 mL/min. The reactor baffles are perforated with 6 holes 1 mm in diameter. Is the flow through these orifices in series or in parallel? Do you multiply the head loss for one orifice by the number of orifices to get the total head loss? Are the orifices in parallel or in series? Use the pc.head_orifice function to calculate the head loss through an orifice. The vena contracta for the orifice can be found at aguaclara.core.constants.VC_ORIFICE_RATIO. Why would 6 holes 1 mm in diameter not be a good design for this reactor?</b>

The flow through these orifices are parallel as the orifices on the reactor baffle are in parallel. Using equation (84) in the textbook, the change in head loss can be calculated from:

$$d_{orifice} =\sqrt{\frac{4Q_{reactor} }{\pi n_{orifice} K_{orifice} \sqrt{2g\Delta h} } }$$

$${d_{orifice}}^2 \pi n_{orifice} K_{orifice} = \frac{4Q_{reactor}}{\sqrt{2g\Delta h}}$$

$$ \sqrt{2g\Delta h}= \frac{4Q_{reactor}}{{d_{orifice}}^2 \pi n_{orifice} K_{orifice}}$$

$$ \Delta h= \frac{1}{2g}(\frac{4Q_{reactor}}{{d_{orifice}}^2 \pi n_{orifice} K_{orifice}})^2$$

$$ \Delta h= \frac{1}{2g}(\frac{Q_{reactor}}{A_{orifice} n_{orifice} K_{orifice}})^2$$

The "pc.head_orifice" function does not take into account the number of orifices in its definition. In order to use this function to calculate total head loss, the area of each orifice does not need to be multiplied by the number of holes. This is also equivalent to dividing the reactor flow rate by the number of holes.

Thus, the total head loss is 0.232 m. From this, we can tell that having 6 holes of 1 mm in diameter would not be a good design because 6 holes is not enough to lower the head loss to a sufficient level. It would cause it to overflow (We measured it during the office hours.) The head loss needs to be lowered even more and so more holes would made the design better and feasible. However, we should try to maximize head loss still. By increasing the number of holes, we are just trying to prevent excessive head loss such that it will overflow.

<b>2. On a single graph plot the exit age distribution (E(t⋆)) for a reactor that operates as a 1-dimensional advection-dispersion reactor with Peclet numbers of 1, 10, and 100 (there will be three plots on the graph and thus a legend is required). The x-axis should be t⋆ from 0.0 to 3.0. Comment on the shapes of the curves as a function of the Peclet number. Note that the advective dispersion equation is undefined for t⋆=0. Use the epa.E_Advective_Dispersion(t,Pe) function.</b>

![EA](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab4/ExitAge.png)
Figure 1: Exit age against time for Peclet numbers of 1, 10, and 100.

From the graph above, it can be seen that the greater the Peclet number, the greater the peak exit age. The curve for Peclet number 100 has a prominent peak at approximately 1 second whereas the curve for Peclet number 1 barely has a peak (If we had to say that there was a peak, it would be at approximately 0.2 second). This brings us to another pattern that can be noticed from the graph. The greater the Peclet number, the greater the time is when the peak exit age is reached. One more thing that can be noticed is the shape of the curve. The greater the Peclet number, the more symmetrical the curve is. The curve for Peclet number 100 is almost entirely symmetrical whereas the curve for Peclet number 10 and Peclet number 1 is obviously skewed, with the curve for Peclet number 1 being more skewed than the curve for Peclet number 10.

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

# Question 1
holes = 6
Diam = 1 * u.mm
RatioVCOrifice = c.VC_ORIFICE_RATIO
FlowRate = 380 * u.mL/u.min
headloss = pc.head_orifice(Diam, RatioVCOrifice, FlowRate/holes)
headloss

# Question 2
Pe_1 = 1
Pe_10 = 10
Pe_100 = 100

start = 0.0000000000001
stop = 3
t = np.linspace(start, stop, 100)

E_1 = epa.E_Advective_Dispersion(t, Pe_1)
E_10 = epa.E_Advective_Dispersion(t, Pe_10)
E_100 = epa.E_Advective_Dispersion(t, Pe_100)

plt.plot(t, E_1, 'b-', linewidth = 2)
plt.plot(t, E_10, 'r-', linewidth = 2)
plt.plot(t, E_100, 'g-', linewidth = 2)
plt.ylabel('Exit age', fontsize=15)
plt.xlabel('Time (sec)', fontsize=15)
leg = plt.legend(('Peclet number = 1', 'Peclet number = 10', 'Peclet number = 100'), loc='best')
plt.savefig('Lab4/ExitAge.png')
plt.show()
```
