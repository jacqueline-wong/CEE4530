# Water Quality Modelling for Conservative Contaminant Transport in Rivers and Lakes #

## Lab 5 for CEE 4530 ##

## Team 10: Victor Khong (x hours) & Jacqueline Wong (x hours) ##

### Introduction ###

Our clients, Dr. Monroe Weber-Shirk, Jonathan Harris and Lily Falk work under the New York State Department of Environmental Conservation. The New York State Department of Environmental Conservation are concerned with the contaminants that have been released into the lakes and rivers by the industry and our clients have been asked to figure out methods to remove the contaminants. For easy analysis, they have modeled the various contaminated lakes and rivers in the New York State as flow reactors in order to decide what actions should be taken, namely CMFR, PFR and flow dispersion reactor. However, they would like to explore how to model the contaminant under the different types of flow reactors. Furthermore, they are interested in designing a reactor and a deep understanding of the different types of flow reactors is needed to do so.

The main objectives of this study are to:

1.	Determine the time taken for contaminant to be removed in the different types of flow reactors
2.	Understand how contaminants flow through each of the flow reactors and model them to a high degree of accuracy
3.	Confirm which flow reactor results in the removal of contaminants the quickest
4. Modify the reactor to obtain a maximum value of t⋆ at F = 0.1.
5. Obtain appropriate experimental data and compare data with appropriate models

CMFR and PFR are both well-known standardized flow reactors. They can be modeled with equations quite simply.

The mass balance for the CMFR is given in equation (52).
$$\rlap{-} V_{r} \frac{dC}{dt} =\left(C_{in} -C\right)Q$$

Assuming the initial concentration of tracer in the reactor is $C_{0} =\frac{C_{tr} \rlap{-} V_{tr} }{\rlap{-} V_{r} }$ and the input concentration is zero $(C_{in} = 0)$, the solution to the differential equation above is equation (53).

$$E_{\left(t\right)}=\frac{C_t{\rlap{-} V }_r}{C_{tr}{\rlap{-} V }_{tr}}=e^{\left(-t/\theta \right)}$$

The dimensionless form of the above equation is given by equation (54).

$$E_{\left(t^{\star} \right)} =\frac{C_{\left(t^{\star} \right)} \rlap{-} V_{r} }{C_{tr} \rlap{-} V_{tr} } ={\mathop{e}\nolimits^{\left(-t^{\star} \right)}}$$

Similarly, the same can be done for PFR. The advection-diffusion equation for PFR is represented by equation (55).
$$\frac{\partial C}{\partial t} =-U\frac{\partial C}{\partial x}$$

The flow dispersion reactor is slightly more complicated. It resembles lakes and rivers more accurately and is a mix between the CMFR and PFR as is the case with lakes and rivers. There are two models for arbitrary mixing level. Assuming open boundary conditions, the advectional-dispersion equation is given by equation (56)
$$\frac{\partial C}{\partial t} ={\rm \; -U}\frac{\partial C}{\partial x} +{\rm \; D}_{{\rm d}} \frac{\partial ^{2} C}{\partial x^{2}}$$

Given complete mixing in the y-z plane and advection and dispersive transport only in the x direction, the above differential equation is resolved into equation (57).

$${\rm C(x,t)\; }={\rm \; }\frac{M}{A\sqrt{4\pi D_{d} t} } \exp \left[\frac{-x'^{2} }{4D_{d} t} \right]$$

This can be converted into dimensionless form as in equation (63).

$$E_{\left(t^{\star} \right)} =\sqrt{\frac{Pe}{4\pi t^{\star} } } \exp \left[\frac{-\left(1-t^{\star} \right)^{2} Pe}{4t^{\star} } \right]$$

The Peclet number for the open boundary condition and the closed boundary condition is also different. The Peclet number for the open boundary condition is given by equation (58).

$$Pe=\frac{UL}{D_{d}}$$

For the closed boundary condition, the Peclet number is given by equation (69)

$$Pe=2N$$

In our experiment, we used red dye as our contaminant. The reason we chose red dye rather than other “contaminants” is because it is easy to perform the experiment with. It is non-toxic at low dosage and can be clearly seen by our eyes so we could make a good judgement as to when to stop the experiment. More importantly, it is inert and since we are exploring the physical process, it would be ideal for us to ignore any chemical processes of contaminants in the water. Different contaminants have different chemical reactions.

To design the reactor, it is critical that we know the head loss through the pores of the baffles, which is given by equation (81). It is an equation for a orifice.

$$Q_{orifice} =K_{orifice} A_{orifice} \sqrt{2g\Delta h}$$

Translating the equation for a single orifice, the equation for the entire reactor is given by equation (83).

$$Q_{reactor} =n_{orifice} K_{orifice} \frac{\pi d_{orifice}^{2} }{4} \sqrt{2g\Delta h}$$

Another critical thing that needs to be considered is the diameter of the orifices, which is given by equation (84).

$$d_{orifice} =\sqrt{\frac{4Q_{reactor} }{\pi n_{orifice} K_{orifice} \sqrt{2g\Delta h} } }$$

With these parameters known, a simple reactor can be designed.

### Procedures ###

The experimental apparatus consists of the flow reactor, peristaltic pump, baffles and photometer. In our model, the contaminant is represented by red dye and its removal is represented by the decrease in concentration of the red dye in the flow reactor. There was a constant influent that runs into the flow reactor and a constant effluent that runs out of the flow reactor. For practical reasons, the simulation occurred over within a short period of time (under 10 minutes) rather than multiple years. The experimental set up is shown in Figure 1.

![setup](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab5/experimentalsetup.png)
Figure 1: Experimental setup showing the flow reactor and peristaltic pump and photometer.

Given that recent studies from our clients have confirmed the contaminant concentration in the influent is approximately 30 mg/L, this was represented by an addition of __________ mg of #40 red dye solution. The experiment was repeated for each of the  different flow reactor model by changing the design slightly. The CMFR required no baffles and the PFR included the addition of 2 baffles in the flow reactor. For the flow dispersion reactor, we included 3 baffles in the flow reactor. The concentration of the effluent was recorded using the photometer and the experimental data was collected until the concentration of the red dye in the effluent was deemed to be low enough to be considered removed from the flow reactor.

Using multivariable nonlinear regression, a best fit between the experimental data and two models was obtained by minimising the sum of squared errors. This was done by using curve-fitting functions written by the programmers of our firm, called "epa.Solver_AD_Pe" for the advection dispersion model and "epa.Solver_CMFR_N" for the completely-mixed flow reactors in series. These functions minimise the errors by varying the values of average residence time $\theta$, (mass of tracer/reactor volume), and either the number of CMFR in series or the Peclet number.

### Results and Discussion ###

For the first experiment with one CMFR, it appears that the actual data does not fit well on the CMFR model, although the start and end points correspond well (Figure 2). Here, the initial decrease in actual measured dye concentrations is much greater than the model. In this experiment,

![CMFR1](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab5/CMFR1.png)
Figure 2: Graph of dye concentration against time for the actual measured dye in one CMFR reactor and its corresponding CMFR model.

For the second experiment with one baffle placed in the reactor, the measured dye concentration indeed appears to fit the CMFR model much better than the AD model (Figure 4).  

![CMFR2](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab5/CMFR3.png)
Figure 3: Graph of dye concentration against time for the actual measured dye in the reactor with one baffle, its corresponding CMFR model and advection dispersion model.

For the third experiment with two baffles placed in the reactor, the measured dye concentration appears to remain stagnant between 1-3 minutes (Figure 3). This was likely due to an air bubble being trapped in the photometer, which resulted in the later spike. While it is difficult to tell which model is better suited due to poor data, the first minute follows the CMFR model better than the AD model.

![CMFR3](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab5/CMFR2.png)
Figure 4: Graph of dye concentration against time for the actual measured dye in the reactor with two identical baffle, its corresponding CMFR model and advection dispersion model.

Unfortunately for the fourth and final experiment with three identical baffles placed in the reactor, there was an error with data collection, likely due to a trapped air bubble, as measured dye concentration dropped at around the first minute and spiked at about the second minute (Figure 5). This poor quality data resulted in the measured dye points being unable to fit both the CMFR model nor the AD model. However, the initial slop was constant and later decreases, suggesting a similar shape to that of a CMFR model.

![CMFR4](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab5/CMFR4.png)
Figure 5: Graph of dye concentration against time for the actual measured dye in the reactor with four baffles.

Despite, some spikes and data collection errors due to issues such as air bubbles being trapped in the photometer, it appears that the CMFR model fit better than the AD model across the relevant experiments. This was expected since our reactor resembles a closed boundary system more than an open boundary system, since the reactor is has a much larger volume and different diffusion or dispersion coefficient compared to the entrance or exit.

Estimated values of N were calculated from the CMFR model while estimated values of Pe were calculated from the AD model. For the second experiment, which had one baffle placed in the reactor, N = 2.09 while Pe = 0.010. For the third experiment, which had two identical baffles placed in the reactor, N = 2.30 while Pe = 0.010.

While it is difficult to compare the values of N and Pe since only data collected two experiments were able to fit into the curve models, it appears that the N for the estimated number of reactors for the one baffle experiment is 2, which is expected, while the N for the two baffle experiment is 2.3. It is good that this number is larger than that for two baffles, but we expected it to be closer to 3. On the other hand, for the Peclet numbers, they appear to be about the same.

#### Report the values of t^{\star} at F = 0.1 for each of your experiments. Do they meet your expectations? ####

10 seconds
15 seconds
15 seconds
35 seconds

Explanation, attach graphs
...

In our reactor, there was no evidence of "short circuiting". The influent was mixed throughout most of the container before flowing out as effluent as different parts of the flow reactor was seen to turn red visibly. There was no evidence of red dye seeping between the wall of the reactor and the baffle instead of flowing through the orifices. This was one of the reason we decided to use red dye as our contaminant.

However, there was some evidence of "dead volumes". During the running of the experiment, the red dye took much longer to reach the corner of the container. This is because this volume does not mix with the rest of the volume in the container well. This would have affected the experiment in some ways. We tried to counter this problem by including a magnetic stirrer. However, in reality, there are "dead volumes" in lakes and rivers so we are not too worried about the fact that there are "dead volumes" in our flow reactor.

To design a full scale chlorine tank, we would need to determine the size of the flow reactor, the diameter and the head loss across each orifice on the baffles, the number of orifices on each baffles, and the number of baffles. The goal of a chlorine contact tank is to maximize the inactivation of pathogens by maximizing the contact time between the chlorine and the pathogens before the water is sent to the distribution system. A large flow reactor would make for a better full scale chlorine contact tank.

As part of our experimentation, the parameters that could be varied are the number of orifices on each baffle and the diameter of each orifice, and the number of baffles. The optimal value of baffles in the reactor was not determined from the experiment. We found that the more baffles added, the better the flow reactor was. Hence, the ideal design of the full scale chlorine contact tank would include as many baffle as possible.


### Conclusions ###

From this experiment, it was found that the CMFR model fit best...

However, it is not good at modeling rivers, which are better modeled by the PFR model.

### Suggestions ###

Our team believes that while the experiment was successful, there were certain things that could be improved upon. One of the difficulties that we had with the experiment was with following the instructions, in particular setting up the experiment. We feel that this could have been made easier for us if a clearer picture of the set up was shown instead. From the one provided, it was difficult to tell which components were supposed to connect to each other, especially with the peristaltic pump. Furthermore, the instructions should provide more detail to ensure that the probe is in the right place as we had to repeat our experiments multiple times due to this mistake. In particular, the instructions should also specify that the photometer should be placed behind the last baffle for the PFR experiment. Although this is intuitive, we made the mistake the first time we did it, which resulted in us having to repeat the experiment again.

Our team also thinks that we can model the CMFR and PFR more accurately than we did in the experiment. With regards to CMFR, we believe that a container that is more “square” in shape would be better over the rectangular container we used. For the PFR, we felt that adding more baffles into the container would definitely be closer to the ideal PFR.

Some other suggestions we had to expand on the experiment is to change the concentration of the red dye in the experiment to see whether the removal of contaminant is proportional to the concentration of contaminant in the water. It would also be a good idea to do the experiment using different contaminants other than red dye and see whether it would yield different results. This would also be helpful for us to see the accuracy of our model of the different types of flow reactors and consequently, their applicability in the lakes and rivers in the New York State and other places as well.

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

C_tracer = 10 * u.mg/u.L
V_tracer = 0.8 * u.mL

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

CMFR_1_E = ((CMFR_1_concentration_data*CMFR_1_V)/(C_tracer*V_tracer)).to(u.dimensionless)
CMFR_1_dimensionless_time = CMFR_1_time_data/CMFR_1_theta_hydraulic
plt.plot(CMFR_1_dimensionless_time.to(u.dimensionless), CMFR_1_E.to(u.dimensionless),'r')
plt.xlabel(r'Dimensionless Residence Time')
plt.ylabel(r'E')
plt.savefig('Lab5/CMFR1_CMFR_E.png')
plt.show()

CMFR_1_F = np.zeros(CMFR_1_E.size)
for i in range (CMFR_1_E.size):
  CMFR_1_F[i] = np.trapz(CMFR_1_E[0:i], CMFR_1_dimensionless_time[0:i])
  if CMFR_1_F[i] <.1:
    print("F is not over 0.1 at " +str(CMFR_1_dimensionless_time[i]))
  else:
    print("F is over 0.1 at " +str(CMFR_1_dimensionless_time[i]))

CMFR_1_tstar = (0.04288*CMFR_1_theta_hydraulic).to(u.seconds)
CMFR_1_tstar
plt.plot(CMFR_1_dimensionless_time.to(u.dimensionless), CMFR_1_F,'r')
plt.xlabel(r'Dimensionless Residence Time')
plt.ylabel(r'F')
plt.savefig('Lab5/CMFR1_CMFR_F.png')
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

plt.plot(CMFR_2_time_data.to(u.min), CMFR_2_concentration_data.to(u.mg/u.L),'r')
plt.plot(CMFR_2_time_data.to(u.min), CMFR_2_CMFR_model,'b')
plt.plot(CMFR_2_time_data.to(u.min), CMFR_2_AD_model,'g')
plt.xlabel(r'$time (min)$')
plt.ylabel(r'Concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(['Measured dye','CMFR Model', 'AD Model'])
plt.savefig('Lab5/CMFR2.png')
plt.show()

CMFR_2_E = ((CMFR_2_concentration_data*CMFR_2_V)/(C_tracer*V_tracer*1/3)).to(u.dimensionless)
CMFR_2_dimensionless_time = CMFR_2_time_data/CMFR_2_theta_hydraulic
plt.plot(CMFR_2_dimensionless_time.to(u.dimensionless), CMFR_2_E.to(u.dimensionless),'r')
plt.xlabel(r'Dimensionless Residence Time')
plt.ylabel(r'E')
plt.savefig('Lab5/CMFR2_CMFR_E.png')
plt.show()

CMFR_2_F = np.zeros(CMFR_2_E.size)
for i in range (CMFR_2_E.size):
  CMFR_2_F[i] = np.trapz(CMFR_2_E[0:i], CMFR_2_dimensionless_time[0:i])
  if CMFR_2_F[i] <.1:
    print("F is not over 0.1 at " +str(CMFR_2_dimensionless_time[i]))
  else:
    print("F is over 0.1 at " +str(CMFR_2_dimensionless_time[i]))

CMFR_2_tstar = (0.06431*CMFR_1_theta_hydraulic).to(u.seconds)
CMFR_2_tstar
plt.plot(CMFR_2_dimensionless_time.to(u.dimensionless), CMFR_2_F,'r')
plt.xlabel(r'Dimensionless Residence Time')
plt.ylabel(r'F')
plt.savefig('Lab5/CMFR2_CMFR_F.png')
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

plt.plot(CMFR_3_time_data.to(u.min), CMFR_3_concentration_data.to(u.mg/u.L),'r')
plt.plot(CMFR_3_time_data.to(u.min), CMFR_3_CMFR_model,'b')
plt.plot(CMFR_3_time_data.to(u.min), CMFR_3_AD_model,'g')
plt.xlabel(r'$time (min)$')
plt.ylabel(r'Concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(['Measured dye','CMFR Model', 'AD Model'])
plt.savefig('Lab5/CMFR3.png')
plt.show()

CMFR_3_E = ((CMFR_3_concentration_data*CMFR_3_V)/(C_tracer*V_tracer*1/2)).to(u.dimensionless)
CMFR_3_dimensionless_time = CMFR_3_time_data/CMFR_3_theta_hydraulic
plt.plot(CMFR_3_dimensionless_time.to(u.dimensionless), CMFR_3_E.to(u.dimensionless),'r')
plt.xlabel(r'Dimensionless Residence Time')
plt.ylabel(r'E')
plt.savefig('Lab5/CMFR3_CMFR_E.png')
plt.show()

CMFR_3_F = np.zeros(CMFR_3_E.size)
for i in range (CMFR_3_E.size):
  CMFR_3_F[i] = np.trapz(CMFR_3_E[0:i], CMFR_3_dimensionless_time[0:i])
  if CMFR_3_F[i] <.1:
    print("F is not over 0.1 at " +str(CMFR_3_dimensionless_time[i]))
  else:
    print("F is over 0.1 at " +str(CMFR_3_dimensionless_time[i]))

CMFR_3_tstar = (0.06431*CMFR_3_theta_hydraulic).to(u.seconds)
CMFR_3_tstar
plt.plot(CMFR_3_dimensionless_time.to(u.dimensionless), CMFR_3_F,'r')
plt.xlabel(r'Dimensionless Residence Time')
plt.ylabel(r'F')
plt.savefig('Lab5/CMFR3_CMFR_F.png')
plt.show()

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

plt.plot(CMFR_4_time_data.to(u.min), CMFR_4_concentration_data.to(u.mg/u.L),'r')
#plt.plot(CMFR_4_time_data.to(u.s), CMFR_4_CMFR_model,'b')
#plt.plot(CMFR_4_time_data.to(u.s), CMFR_4_AD_model,'g')
plt.xlabel(r'$time (min)$')
plt.ylabel(r'Concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(['Measured dye','CMFR Model', 'AD Model'])
plt.savefig('Lab5/CMFR4.png')
plt.show()

CMFR_4_E = ((CMFR_4_concentration_data*CMFR_4_V)/(C_tracer*V_tracer*1/4)).to(u.dimensionless)
CMFR_4_dimensionless_time = CMFR_4_time_data/CMFR_4_theta_hydraulic
plt.plot(CMFR_4_dimensionless_time.to(u.dimensionless), CMFR_4_E.to(u.dimensionless),'r')
plt.xlabel(r'Dimensionless Residence Time')
plt.ylabel(r'E')
plt.savefig('Lab5/CMFR4_CMFR_E.png')
plt.show()

CMFR_4_F = np.zeros(CMFR_4_E.size)
for i in range (CMFR_4_E.size):
  CMFR_4_F[i] = np.trapz(CMFR_4_E[0:i], CMFR_4_dimensionless_time[0:i])
  if CMFR_4_F[i] <.1:
    print("F is not over 0.1 at " +str(CMFR_4_dimensionless_time[i]))
  else:
    print("F is over 0.1 at " +str(CMFR_4_dimensionless_time[i]))

CMFR_3_tstar = (0.1501*CMFR_3_theta_hydraulic).to(u.seconds)
CMFR_3_tstar
plt.plot(CMFR_3_dimensionless_time.to(u.dimensionless), CMFR_3_F,'r')
plt.xlabel(r'Dimensionless Residence Time')
plt.ylabel(r'F')
plt.savefig('Lab5/CMFR3_CMFR_F.png')
plt.show()
```

Baffles:

- 5 mm diameter
- 4 x 6 = 24 orifices in parallel.
