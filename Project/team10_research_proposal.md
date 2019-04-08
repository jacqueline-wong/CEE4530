# Research Proposal for CEE 4530

### Team 10: Victor Khong & Jacqueline Wong ###

Write your research proposal in Atom. You can begin defining variables and calculating parameters as you design your proposed research. This research proposal can then evolve into your final report.

#### Introduction ####

Activated carbon is use
- Intro/context – What is the problem? Why is it important?

Our team is interested in investigating methods to optimize the
- Objectives – What is the hypothesis? What will you do to test the hypothesis?
- Experimental plan including – How will you measure it?
- Key design parameters
    - flow rates
    - volumes
    - concentrations
    - range of parameters that you are varying etc.
- Timeline of tasks/experiments
- Possible hurdles/challenges
- Refs to primary, review, and other literature and possibly to previous years’ projects
- Resources needed to conduct experiments – What tools will you use?
- Expectations/Anticipated results
- References/Bibiliography

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
