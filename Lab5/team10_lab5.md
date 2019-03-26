# Water Quality Modelling for Conservative Contaminant Transport in Rivers and Lakes #

## Lab 5 for CEE 4530 ##

## Team 10: Victor Khong (x hours) & Jacqueline Wong (x hours) ##

##### Notes #####

Baffles:

- 5 mm diameter
- 4 x 6 = 24 orifices in parallel.

### Introduction ###
Our clients, Dr. Monroe Weber-Shirk and Jonathan Harris, work under the New York State Department of Environmental Conservation. The New York State Department of Environmental Conservation are concerned with the contaminants that have been released into the lakes and rivers by the industry and our clients have been asked to figure out methods to remove the contaminants. For easy analysis, they have modelled the various contaminated lakes and rivers in the New York State as flow reactors in order to decide what actions should be taken, namely CMFR, PFR and flow dispersion reactor. However, they would like to explore how to model the contaminant under the different types of flow reactors.
The main objectives of this study are to:
1.	Determine the time taken for contaminant to be removed in the different types of flow reactors
2.	Understand how contaminants flow through each of the flow reactors and model them to a high degree of accuracy
3.	Confirm which flow reactor results in the removal of contaminants the quickest
CMFR and PFR are both well-known standardized flow reactors. They can be modeled with equations quite simply. The mass balance for the CMFR is given in equation (52).
$$\rlap{-} V _{r} \frac{dC}{dt} =\left(C_{in} -C\right)Q$$

Assuming the initial concentration of tracer in the reactor is $C_{0} =\frac{C_{tr} \rlap{-} V _{tr} }{\rlap{-} V _{r} }$ and the input concentration is zero $(C_{in} = 0)$, the solution to the differential equation above is equation (53).

$$E_{\left(t\right)}=\frac{C_t{\rlap{-} V }_r}{C_{tr}{\rlap{-} V }_{tr}}=e^{\left(-t/\theta \right)}$$

The dimensionless form of the above equation is given by equation (54).

$$E_{\left(t^{\star} \right)} =\frac{C_{\left(t^{\star} \right)} \rlap{-} V _{r} }{C_{tr} \rlap{-} V _{tr} } ={\mathop{e}\nolimits^{\left(-t^{\star} \right)}}$$

Similarly, the same can be done for PFR. The advection-diffusion equation for PFR is represented by equation (55).
$$\frac{\partial C}{\partial t} =-U\frac{\partial C}{\partial x}$$

The flow dispersion reactor is slightly more complicated. It resembles lakes and rivers more accurately and is a mix between the CMFR and PFR as is the case with lakes and rivers. There are two models for arbitrary mixing level. Assuming open boundary conditions, the advectional-dispersion equation is given by equation (56)
$$\frac{\partial C}{\partial t} ={\rm \; -U}\frac{\partial C}{\partial x} +{\rm \; D}_{{\rm d}} \frac{\partial ^{2} C}{\partial x^{2}}$$

Given complete mixing in the y-z plane and advective and dispersive transport only in the x direction, the above differential equation is resolved into equation (57).

$${\rm C(x,t)\; }={\rm \; }\frac{M}{A\sqrt{4\pi D_{d} t} } \exp \left[\frac{-x'^{2} }{4D_{d} t} \right]$$

This can be converted into dimensionless form as in equation (63).

$$E_{\left(t^{\star} \right)} =\sqrt{\frac{Pe}{4\pi t^{\star} } } \exp \left[\frac{-\left(1-t^{\star} \right)^{2} Pe}{4t^{\star} } \right]$$

The Peclet number for the open boundary condition and the closed boundary condition is also different. The Peclet number for the open boundary condition is given by equation (58).

$$Pe=\frac{UL}{D_{d}}$$

For the closed boundary condition, the Peclet number is given by equation (69)

$$Pe=2N$$

### Procedures ###

...

Using multivariable nonlinear regression, a best fit between the experimental data and two models was obtained by minimising the sum of squared errors. This was done by using curve-fitting functions written by the programmers of our firm, called "epa.Solver_AD_Pe" for the advective dispersion model and "epa.Solver_CMFR_N" for the completely-mixed flow reactors in series. These functions minimise the errors by varying the values of average residence time $\theta$, (mass of tracer/reactor volume), and either the number of CMFR in series or the Peclet number.

### Results and Discussion ###

For the first experiment with one CMFR, it appears that the actual data does not fit well on the CMFR model, although the start and end points correspond well (Figure 1). Here, the initial decrease in actual measured dye concentrations is much greater than the model.

![CMFR1](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab5/CMFR1.png)
Figure 1: Graph of dye concentration against time for the actual measured dye in one CMFR reactor and its corresponding CMFR model.

For the second experiment with one baffle placed in the reactor, it appears that ...

![CMFR2](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab5/CMFR2.png)
Figure 2: Graph of dye concentration against time for the actual measured dye in the reactor with one baffle, its corresponding CMFR model and advective dispersion model.

![CMFR3](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab5/CMFR3.png)
Figure 3: Graph of dye concentration against time for the actual measured dye in the reactor with two baffles, its corresponding CMFR model and advective dispersion model.

Unfortunately for the case with four CMFR reactors in series (using three baffles in between), data...

![CMFR4](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab5/CMFR4.png)
Figure 3: Graph of dye concentration against time for the actual measured dye in the reactor with four baffles.

<b> 2. Explain which model fits best and discuss those results based on your expectations...
3. Compare the trends in the estimated values of N and Pe across your set of experiments. How did your chosen reactor modifications effect dispersion?
Report the values of t^{\star} at F = 0.1 for each of your experiments. Do they meet your expectations?
4. Evaluate whether there is any evidence of “dead volumes” or “short circuiting” in your reactor.
5. Make a recommendation for the design of a full scale chlorine contact tank. As part of your recommendation discuss the parameter you chose to vary as part of your experimentation and what the optimal value was determined to be.</b>

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
CMFR_2_firstrow = CMFR_2_firstrow + 10
CMFR_2_time_data = (epa.column_of_time(CMFR_2_path,CMFR_2_firstrow,-1)).to(u.s)
CMFR_2_concentration_data = epa.column_of_data(CMFR_2_path,CMFR_2_firstrow,1,-1,'mg/L')

CMFR_2_concentration_data = CMFR_2_concentration_data - CMFR_2_concentration_data[0]
CMFR_2_mass = 3592 * u.g - 1168 * u.g
CMFR_2_V = CMFR_1_mass/rho
CMFR_2_Q = 380 * u.mL/u.min
CMFR_2_theta_hydraulic = (CMFR_2_V/CMFR_2_Q).to(u.s)
CMFR_2_C_bar_guess = np.max(CMFR_2_concentration_data)/2

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
CMFR_3_firstrow = epa.notes(CMFR_3_path).last_valid_index() + 1
CMFR_3_firstrow = CMFR_3_firstrow + 10
CMFR_3_time_data = (epa.column_of_time(CMFR_3_path,CMFR_3_firstrow,-1)).to(u.s)
CMFR_3_concentration_data = epa.column_of_data(CMFR_3_path,CMFR_3_firstrow,1,-1,'mg/L')

CMFR_3_concentration_data = CMFR_3_concentration_data - CMFR_3_concentration_data[0]
CMFR_3_mass = 3490 * u.g - 1267 * u.g
CMFR_3_V = CMFR_1_mass/rho
CMFR_3_Q = 380 * u.mL/u.min
CMFR_3_theta_hydraulic = (CMFR_3_V/CMFR_3_Q).to(u.s)
CMFR_3_C_bar_guess = np.max(CMFR_3_concentration_data)/2

CMFR_3_CMFR = epa.Solver_CMFR_N(CMFR_3_time_data, CMFR_3_concentration_data, CMFR_3_theta_hydraulic, CMFR_3_C_bar_guess)
CMFR_3_CMFR.C_bar
CMFR_3_CMFR.N
CMFR_3_CMFR.theta.to(u.s)

CMFR_3_CMFR_model = (CMFR_3_CMFR.C_bar*epa.E_CMFR_N(CMFR_3_time_data/CMFR_3_CMFR.theta, CMFR_3_CMFR.N)).to(u.mg/u.L)

CMFR_3_AD = epa.Solver_AD_Pe(CMFR_3_time_data, CMFR_3_concentration_data, CMFR_3_theta_hydraulic, CMFR_3_C_bar_guess)
CMFR_3_AD.C_bar
CMFR_3_AD.Pe
CMFR_3_AD.theta

print('The model estimated mass of tracer injected was',ut.round_sf(CMFR_3_AD.C_bar*CMFR_3_V ,2) )
print('The model estimate of the Peclet number was', CMFR_3_AD.Pe)
print('The tracer residence time was',ut.round_sf(CMFR_3_AD.theta ,2))
print('The ratio of tracer to hydraulic residence time was',(CMFR_3_AD.theta/CMFR_3_theta_hydraulic).magnitude)

CMFR_3_AD_model = (CMFR_3_AD.C_bar*epa.E_Advective_Dispersion((CMFR_3_time_data/CMFR_3_AD.theta).to_base_units(), CMFR_3_AD.Pe)).to(u.mg/u.L)

plt.plot(CMFR_3_time_data.to(u.s), CMFR_3_concentration_data.to(u.mg/u.L),'r')
plt.plot(CMFR_3_time_data.to(u.s), CMFR_3_CMFR_model,'b')
plt.plot(CMFR_3_time_data.to(u.s), CMFR_3_AD_model,'g')
plt.xlabel(r'$time (min)$')
plt.ylabel(r'Concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(['Measured dye','CMFR Model', 'AD Model'])
plt.savefig('Lab5/CMFR3.png')
plt.show()

############################

CMFR_4_path = 'https://raw.githubusercontent.com/lw583/CEE4530/master/Lab5/lab5_cmfr_4.xls'
CMFR_4_firstrow = epa.notes(CMFR_4_path).last_valid_index() + 1
CMFR_4_firstrow = CMFR_4_firstrow + 10
CMFR_4_time_data = (epa.column_of_time(CMFR_4_path,CMFR_4_firstrow,-1)).to(u.s)
CMFR_4_concentration_data = epa.column_of_data(CMFR_4_path,CMFR_4_firstrow,1,-1,'mg/L')

CMFR_4_concentration_data = CMFR_4_concentration_data - CMFR_4_concentration_data[0]
CMFR_4_mass = 2298 * u.g - 1371 * u.g
CMFR_4_V = CMFR_1_mass/rho
CMFR_4_Q = 380 * u.mL/u.min
CMFR_4_theta_hydraulic = (CMFR_4_V/CMFR_4_Q).to(u.s)
CMFR_4_C_bar_guess = np.max(CMFR_4_concentration_data)/2

#CMFR_4_CMFR = epa.Solver_CMFR_N(CMFR_4_time_data, CMFR_4_concentration_data, CMFR_4_theta_hydraulic, CMFR_4_C_bar_guess)
#CMFR_4_CMFR.C_bar
#CMFR_4_CMFR.N
#CMFR_4_CMFR.theta.to(u.s)

#CMFR_4_CMFR_model = (CMFR_4_CMFR.C_bar*epa.E_CMFR_N(CMFR_4_time_data/CMFR_4_CMFR.theta, CMFR_4_CMFR.N)).to(u.mg/u.L)

#CMFR_4_AD = epa.Solver_AD_Pe(CMFR_4_time_data, CMFR_4_concentration_data, CMFR_4_theta_hydraulic, CMFR_4_C_bar_guess)
#CMFR_4_AD.C_bar
#CMFR_4_AD.Pe
#CMFR_4_AD.theta

#print('The model estimated mass of tracer injected was',ut.round_sf(CMFR_4_AD.C_bar*CMFR_4_V ,2) )
#print('The model estimate of the Peclet number was', CMFR_4_AD.Pe)
#print('The tracer residence time was',ut.round_sf(CMFR_4_AD.theta ,2))
#print('The ratio of tracer to hydraulic residence time was',(CMFR_4_AD.theta/CMFR_4_theta_hydraulic).magnitude)

#CMFR_4_AD_model = (CMFR_4_AD.C_bar*epa.E_Advective_Dispersion((CMFR_4_time_data/CMFR_4_AD.theta).to_base_units(), CMFR_4_AD.Pe)).to(u.mg/u.L)

plt.plot(CMFR_4_time_data.to(u.s), CMFR_4_concentration_data.to(u.mg/u.L),'r')
#plt.plot(CMFR_4_time_data.to(u.s), CMFR_4_CMFR_model,'b')
#plt.plot(CMFR_4_time_data.to(u.s), CMFR_4_AD_model,'g')
plt.xlabel(r'$time (min)$')
plt.ylabel(r'Concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(['Measured dye','CMFR Model', 'AD Model'])
plt.savefig('Lab5/CMFR4.png')
plt.show()
```

### Conclusions ###
From this experiment, it was found that ...

### Suggestions ###
Our team believes that while the experiment was successful, there were certain things that could be improved upon. One of the difficulties that we had with the experiment was with following the instructions, in particular setting up the experiment. We feel that this could have been made easier for us if a clearer picture of the set up was shown instead. From the one provided, it was difficult to tell which components were supposed to connect to each other, especially with the peristaltic pump. Furthermore, the instructions should provide more detail to ensure that the probe is in the right place as we had to repeat our experiments multiple times due to this mistake.

### Appendix ###
