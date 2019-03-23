# Water Quality Modelling for Conservative Contaminant Transport in Rivers and Lakes #

## Lab 5 for CEE 4530 ##

## Team 10: Victor Khong (x hours) & Jacqueline Wong (x hours) ##

##### Notes #####

For 2 CMFR:

- 3592 g
- 1168 g

For 3 CMFR:

- 3490 kg
- 1267 g

For 4 CMFR:

- 2298 g
- 1371 g

Baffles:

- 5 mm diameter
- 4 x 6 = 24 orifices in parallel.

### Introduction and Objectives ###
Our clients, Dr. Monroe Weber-Shirk and Jonathan Harris, work under the New York State Department of Environmental Conservation. They are interested in modelling

various lakes in rivers ...
CMFR for lakes, and various plug-flow rivers/streams of various sizes.
concern about contaminant transport

The main objectives of this study are to:

1. Create a model which simulates what happens to Wolf Pond during snow melt, assuming it acts as a Completely Mixed Flow Reactor (CMFR).
2. Determine ...

Put theory here.

### Procedures ###

...

### Results and Discussion ###

...

```python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
import aguaclara.core.utility as ut
from scipy import optimize
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from scipy import stats

CMFR_1_path = 'https://raw.githubusercontent.com/lw583/CEE4530/master/Lab5/lab5_cmfr_1.xls'
epa.notes(CMFR_1_path)
CMFR_1_firstrow = epa.notes(CMFR_1_path).last_valid_index() + 1
CMFR_1_firstrow
CMFR_1_firstrow = CMFR_1_firstrow + 10

CMFR_1_time_data = (epa.column_of_time(CMFR_1_path,CMFR_1_firstrow,-1)).to(u.s)

CMFR_1_concentration_data = epa.column_of_data(CMFR_1_path,CMFR_1_firstrow,1,-1,'mg/L')

rho = 997 * u.kg/u.m**3
CMFR_1_mass = 2547 * u.g - 1074 * u.g
CMFR_1_V = CMFR_1_mass/rho
CMFR_1_V.to(u.L)
CMFR_1_Q = 380 * u.mL/u.min

CMFR_1_theta_hydraulic = (CMFR_1_V/CMFR_1_Q).to(u.s)
CMFR_1_C_bar_guess = np.max(CMFR_1_concentration_data)

CMFR_1_CMFR = epa.Solver_CMFR_N(CMFR_1_time_data, CMFR_1_concentration_data, CMFR_1_theta_hydraulic, CMFR_1_C_bar_guess)

print('The model estimated mass of tracer injected was',ut.round_sf((CMFR_1_CMFR.C_bar*CMFR_1_V).to(u.mg) ,2) )
print('The model estimate of the number of reactors in series was', CMFR_1_CMFR.N)
print('The tracer residence time was',ut.round_sf(CMFR_1_CMFR.theta ,2))
print('The ratio of tracer to hydraulic residence time was',(CMFR_1_CMFR.theta/CMFR_1_theta_hydraulic).magnitude)

CMFR_1_CMFR_model = CMFR_1_CMFR.C_bar * epa.E_CMFR_N(CMFR_1_time_data/CMFR_1_CMFR.theta,CMFR_1_CMFR.N)

plt.plot(CMFR_1_time_data.to(u.min), CMFR_1_concentration_data.to(u.mg/u.L),'r')
plt.plot(CMFR_1_time_data.to(u.min), CMFR_1_CMFR_model,'b')
plt.xlabel(r'$time (min)$')
plt.ylabel(r'Concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(['Measured dye','CMFR Model'])
plt.savefig('Lab5/CMFR1.png')
plt.show()


CMFR_2_path = 'https://raw.githubusercontent.com/lw583/CEE4530/master/Lab5/lab5_cmfr_2.xls'
CMFR_2_firstrow = epa.notes(CMFR_2_path).last_valid_index() + 1
CMFR_2_time_data = (epa.column_of_time(CMFR_2_path,CMFR_2_firstrow,-1)).to(u.s)
CMFR_2_concentration_data = epa.column_of_data(CMFR_2_path,CMFR_2_firstrow,1,-1,'mg/L')

CMFR_2_concentration_data = CMFR_2_concentration_data - CMFR_2_concentration_data[0]
CMFR_2_mass = 3592 * u.g - 1168 * u.g
CMFR_2_V = CMFR_1_mass/rho
CMFR_2_Q = 380 * u.mL/u.min
CMFR_2_theta_hydraulic = (CMFR_2_V/CMFR_2_Q).to(u.s)
CMFR_2_C_bar_guess = np.max(CMFR_2_concentration_data)/2
#use solver to get the CMFR parameters
CMFR_2_CMFR = epa.Solver_CMFR_N(CMFR_2_time_data, CMFR_2_concentration_data, CMFR_2_theta_hydraulic, CMFR_2_C_bar_guess)
CMFR_2_CMFR.C_bar
CMFR_2_CMFR.N
CMFR_2_CMFR.theta.to(u.s)

CMFR_2_CMFR_model = (CMFR_2_CMFR.C_bar*epa.E_CMFR_N(CMFR_2_time_data/CMFR_2_CMFR.theta, CMFR_2_CMFR.N)).to(u.mg/u.L)

CMFR_2_AD = epa.Solver_AD_Pe(CMFR_2_time_data, CMFR_2_concentration_data, CMFR_2_theta_hydraulic, CMFR_2_C_bar_guess)
CMFR_2_AD.C_bar
CMFR_2_AD.Pe
CMFR_2_AD.theta

print('The model estimated mass of tracer injected was',ut.round_sf(CMFR_2_AD.C_bar*CMFR_2_V ,2) )
print('The model estimate of the Peclet number was', CMFR_2_AD.Pe)
print('The tracer residence time was',ut.round_sf(CMFR_2_AD.theta ,2))
print('The ratio of tracer to hydraulic residence time was',(CMFR_2_AD.theta/CMFR_2_theta_hydraulic).magnitude)

CMFR_2_AD_model = (CMFR_2_AD.C_bar*epa.E_Advective_Dispersion((CMFR_2_time_data/CMFR_2_AD.theta).to_base_units(), CMFR_2_AD.Pe)).to(u.mg/u.L)

plt.plot(CMFR_2_time_data.to(u.s), CMFR_2_concentration_data.to(u.mg/u.L),'r')
plt.plot(CMFR_2_time_data.to(u.s), CMFR_2_CMFR_model,'b')
plt.plot(CMFR_2_time_data.to(u.s), CMFR_2_AD_model,'g')
plt.xlabel(r'$time (min)$')
plt.ylabel(r'Concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(['Measured dye','CMFR Model', 'AD Model'])
plt.savefig('Lab5/CMFR2.png')
plt.show()

CMFR_3_path = 'https://raw.githubusercontent.com/lw583/CEE4530/master/Lab5/lab5_cmfr_3.xls'
CMFR_2_firstrow = epa.notes(CMFR_2_path).last_valid_index() + 1
CMFR_2_time_data = (epa.column_of_time(CMFR_2_path,CMFR_2_firstrow,-1)).to(u.s)
CMFR_2_concentration_data = epa.column_of_data(CMFR_2_path,CMFR_2_firstrow,1,-1,'mg/L')

CMFR_2_concentration_data = CMFR_2_concentration_data - CMFR_2_concentration_data[0]
CMFR_2_mass = 3592 * u.g - 1168 * u.g
CMFR_2_V = CMFR_1_mass/rho
CMFR_2_Q = 380 * u.mL/u.min
CMFR_2_theta_hydraulic = (CMFR_2_V/CMFR_2_Q).to(u.s)
CMFR_2_C_bar_guess = np.max(CMFR_2_concentration_data)/2
#use solver to get the CMFR parameters
CMFR_2_CMFR = epa.Solver_CMFR_N(CMFR_2_time_data, CMFR_2_concentration_data, CMFR_2_theta_hydraulic, CMFR_2_C_bar_guess)
CMFR_2_CMFR.C_bar
CMFR_2_CMFR.N
CMFR_2_CMFR.theta.to(u.s)

CMFR_2_CMFR_model = (CMFR_2_CMFR.C_bar*epa.E_CMFR_N(CMFR_2_time_data/CMFR_2_CMFR.theta, CMFR_2_CMFR.N)).to(u.mg/u.L)

CMFR_2_AD = epa.Solver_AD_Pe(CMFR_2_time_data, CMFR_2_concentration_data, CMFR_2_theta_hydraulic, CMFR_2_C_bar_guess)
CMFR_2_AD.C_bar
CMFR_2_AD.Pe
CMFR_2_AD.theta

print('The model estimated mass of tracer injected was',ut.round_sf(CMFR_2_AD.C_bar*CMFR_2_V ,2) )
print('The model estimate of the Peclet number was', CMFR_2_AD.Pe)
print('The tracer residence time was',ut.round_sf(CMFR_2_AD.theta ,2))
print('The ratio of tracer to hydraulic residence time was',(CMFR_2_AD.theta/CMFR_2_theta_hydraulic).magnitude)

CMFR_2_AD_model = (CMFR_2_AD.C_bar*epa.E_Advective_Dispersion((CMFR_2_time_data/CMFR_2_AD.theta).to_base_units(), CMFR_2_AD.Pe)).to(u.mg/u.L)

plt.plot(CMFR_2_time_data.to(u.s), CMFR_2_concentration_data.to(u.mg/u.L),'r')
plt.plot(CMFR_2_time_data.to(u.s), CMFR_2_CMFR_model,'b')
plt.plot(CMFR_2_time_data.to(u.s), CMFR_2_AD_model,'g')
plt.xlabel(r'$time (min)$')
plt.ylabel(r'Concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(['Measured dye','CMFR Model', 'AD Model'])
plt.savefig('Lab5/CMFR2.png')
plt.show()
```

### Conclusions ###
From this experiment, it was found that ...

### Suggestions ###
Our team believes that while the experiment was successful, there were certain things that could be improved upon. One of the difficulties that we had with the experiment was with following the instructions, in particular setting up the experiment. We feel that this could have been made easier for us if a clearer picture of the set up was shown instead. From the one provided, it was difficult to tell which components were supposed to connect to each other, especially with the peristaltic pump. Furthermore, the instructions should provide more detail to ensure that the probe is in the right place as we had to repeat our experiments multiple times due to this mistake.

### Appendix ###
