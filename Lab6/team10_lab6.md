# Lab 6 for CEE 4530

### Team 10: Victor Khong (1 hours) & Jacqueline Wong (1.5 hours) ###

##### 1. Plot the breakthrough curves showing \frac{C}{C_0} versus time. #

##### 2. Find the time when the effluent concentration was 50% of the influent concentration and plot that as a function of the mass of activated carbon used. #

##### 3. Calculate the retardation coefficient (R_{adsorption}) based on the time to breakthrough for the columns with and without activated carbon. #

##### 4. Calculate the quantity of Red Dye #40 that was transferred to the activated carbon based on the influent concentration, flow rate, and 50% breakthrough time. #

##### 5. Calculate the q_0 for each of the columns. Plot this as a function of the mass of activated carbon used. #

##### What did you learn from this analysis? How can you explain the results that you have obtained? What changes to the experimental method do you recommend for next year (or for a project)? #

```python
from aguaclara.core.units import unit_registry as u
import aguaclara.core.physchem as pc
import aguaclara.core.utility as ut

mLperrev_Tubing_17 = 2.8 * u.mL/u.revolution
Pump_rpm = 10 * u.revolution/u.min
Q_reddye = Pump_rpm * mLperrev_Tubing_17
Q_reddye.to(u.mL/u.sec)
vol = 20 * u.L
exp_time = vol/Q_reddye
exp_time.to(u.hour)

mass_AC = 29.342 * u.g

```
