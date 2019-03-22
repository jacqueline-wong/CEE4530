# Water Quality Modelling for Conservative Contaminant Transport in Rivers and Lakes #

## Lab 5 for CEE 4530 ##

## Team 10: Victor Khong (x hours) & Jacqueline Wong (x hours) ##

##### Notes #####

For CMFR:

- 2547 g
- 1074 g

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
CMFR_Q = 380 * u.mL/u.min

CMFR_1_theta_hydraulic = (CMFR_1_V/CMFR_Q).to(u.s)
CMFR_1_C_bar_guess = np.max(CMFR_1_concentration_data)

#The Solver_CMFR_N will return the initial tracer concentration,
#residence time, and number of reactors in series.
#This experiment was for a single reactor and so we expect N to be 1!
CMFR_1_CMFR = epa.Solver_CMFR_N(CMFR_1_time_data, CMFR_1_concentration_data, CMFR_1_theta_hydraulic, CMFR_1_C_bar_guess)
#use dot notation to get the 3 elements of the tuple that are in CMFR.

print('The model estimated mass of tracer injected was',ut.round_sf((CMFR_1_CMFR.C_bar*CMFR_1_V).to(u.mg) ,2) )
print('The model estimate of the number of reactors in series was', CMFR_1_CMFR.N)
print('The tracer residence time was',ut.round_sf(CMFR_1_CMFR.theta ,2))
print('The ratio of tracer to hydraulic residence time was',(CMFR_1_CMFR.theta/CMFR_1_theta_hydraulic).magnitude)

#create a model curve given the curve fit parameters.

CMFR_1_CMFR_model = CMFR_1_CMFR.C_bar * epa.E_CMFR_N(CMFR_1_time_data/CMFR_1_CMFR.theta,CMFR_1_CMFR.N)

plt.plot(CMFR_1_time_data.to(u.min), CMFR_1_concentration_data.to(u.mg/u.L),'r')
plt.plot(CMFR_1_time_data.to(u.min), CMFR_1_CMFR_model,'b')
plt.xlabel(r'$time (min)$')
plt.ylabel(r'Concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(['Measured dye','CMFR Model'])
plt.savefig('Lab5/CMFR1.png')
plt.show()

#Load a data file for a reactor with baffles.

####### HERE ONWARDS IS JUST MONROE EXAMPLE

zone_baffle_path = 'https://raw.githubusercontent.com/monroews/CEE4530/master/Examples/data/Dispersion_example.xls'
one_baffle_firstrow = epa.notes(one_baffle_path).last_valid_index() + 1
one_baffle_time_data = (epa.column_of_time(one_baffle_path,one_baffle_firstrow,-1)).to(u.s)
one_baffle_concentration_data = epa.column_of_data(one_baffle_path,one_baffle_firstrow,1,-1,'mg/L')

#I noticed that the initial concentration measured by the photometer wasn't
#zero. This suggests that there may have been a small air bubble in the
#photometer or perhaps there was some other anomoly that was causing the
#photometer to read a concentration that was higher than was actually present in
#the reactor. To correct for this I subtracted the initial concentration reading
#from all of the data. This was based on the assumption that the concentration
#measurement error persisted for the entire experiment.#

one_baffle_concentration_data = one_baffle_concentration_data - one_baffle_concentration_data[0]
one_baffle_V = 2.25*u.L
one_baffle_Q = 380 * u.mL/u.min
one_baffle_theta_hydraulic = (one_baffle_V/one_baffle_Q).to(u.s)
one_baffle_C_bar_guess = np.max(one_baffle_concentration_data)/2
#use solver to get the CMFR parameters
one_baffle_CMFR = epa.Solver_CMFR_N(one_baffle_time_data, one_baffle_concentration_data, one_baffle_theta_hydraulic, one_baffle_C_bar_guess)
one_baffle_CMFR.C_bar
one_baffle_CMFR.N
one_baffle_CMFR.theta.to(u.s)

#Create the CMFR model curve based on the scipy.optimize curve_fit
#parameters. We do this with dimensions so that we can plot both models and
#the data on the same graph. If we did this in dimensionless space it wouldn't
#be possible to plot everything on the same plot because the values used to
#create dimensionless time and dimensionless concentration are different for
#the two models.
one_baffle_CMFR_model = (one_baffle_CMFR.C_bar*epa.E_CMFR_N(one_baffle_time_data/one_baffle_CMFR.theta, one_baffle_CMFR.N)).to(u.mg/u.L)

#use solver to get the advection dispersion parameters
one_baffle_AD = epa.Solver_AD_Pe(one_baffle_time_data, one_baffle_concentration_data, one_baffle_theta_hydraulic, one_baffle_C_bar_guess)
one_baffle_AD.C_bar
one_baffle_AD.Pe
one_baffle_AD.theta

print('The model estimated mass of tracer injected was',ut.round_sf(one_baffle_AD.C_bar*one_baffle_V ,2) )
print('The model estimate of the Peclet number was', one_baffle_AD.Pe)
print('The tracer residence time was',ut.round_sf(one_baffle_AD.theta ,2))
print('The ratio of tracer to hydraulic residence time was',(one_baffle_AD.theta/one_baffle_theta_hydraulic).magnitude)

#Create the advection dispersion model curve based on the solver parameters
one_baffle_AD_model = (one_baffle_AD.C_bar*epa.E_Advective_Dispersion((one_baffle_time_data/one_baffle_AD.theta).to_base_units(), one_baffle_AD.Pe)).to(u.mg/u.L)

#Plot the data and the two model curves.
plt.plot(one_baffle_time_data.to(u.s), one_baffle_concentration_data.to(u.mg/u.L),'r')
plt.plot(one_baffle_time_data.to(u.s), one_baffle_CMFR_model,'b')
plt.plot(one_baffle_time_data.to(u.s), one_baffle_AD_model,'g')
plt.xlabel(r'$time (min)$')
plt.ylabel(r'Concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(['Measured dye','CMFR Model', 'AD Model'])
# plt.savefig('Lab5/Dispersion.png')
plt.show()
```

### Conclusions ###
From this experiment, it was found that ...

### Suggestions ###
Our team believes that while the experiment was successful, there were certain things that could be improved upon. One of the difficulties that we had with the experiment was with following the instructions, in particular setting up the experiment. We feel that this could have been made easier for us if a clearer picture of the set up was shown instead. From the one provided, it was difficult to tell which components were supposed to connect to each other, especially with the peristaltic pump. Furthermore, the instructions should provide more detail to ensure that the probe is in the right place as we had to repeat our experiments multiple times due to this mistake.

### Appendix ###
