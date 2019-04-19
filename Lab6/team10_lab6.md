# Lab 6 for CEE 4530

### Team 10: Victor Khong (X hours) & Jacqueline Wong (X hours)

##### 1. Plot the breakthrough curves showing $\frac{C}{C_0}$ versus time. #

![sand](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab6/Sand_column.png)
Figure 2: Breakthrough curves of C/Co against time for column of sand with no activated carbon at different flow rates.

![AC1](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab6/Activated_carbon.png)
Figure 2: Breakthrough curves of C/Co against time for different masses of activated carbon and different flow rates.

![AC2](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab6/Activated_carbon_2.png)
Figure 3: Breakthrough curve of C/Co against time for different masses of activated carbon and different flow rates, with a larger x-axis.

![AC3](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab6/Activated_carbon_3.png)
Figure 3: Breakthrough curve of C/Co against time for different masses of activated carbon and different flow rates, with a smaller x-axis.

##### 2. Find the time when the effluent concentration was 50% of the influent concentration and plot that as a function of the mass of activated carbon used. #

![time](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab6/Time_graph.png)
Figure 4: **VICTOR**

Using different flow rates, hard to see relationship. Replot those with flow rate around 0.5 mL/s **VICTOR**

![time2](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab6/Time_graph_2.png)
Figure 5: **VICTOR**

Better relationship. Greater mass, greater time. **VICTOR**

##### 3. Calculate the retardation coefficient $R_{adsorption}$ based on the time to breakthrough for the columns with and without activated carbon. #

##### 4. Calculate the quantity of Red Dye #40 that was transferred to the activated carbon based on the influent concentration, flow rate, and 50% breakthrough time. #

##### 5. Calculate the $q_0$ for each of the columns. Plot this as a function of the mass of activated carbon used. #

To calculate the retardation coefficient based on the time to breakthrough for the columns with and without activated carbon, we use the following equation:

$$R_{adsorption} = \frac{t_{mtz}}{t_{water}}$$

To calculate the $q_0$ for each of the columns, we use the following equation:

$$q_0 = \left(R_{adsorption} - 1\right) \frac{C_0 \phi V_{column}}{M_{adsorbent}}$$

Thus, to calculate the quantity of red dye #40 that was transferred to the activated carbon based based on the influent concentration, flow rate, and 50% breakthrough time, we use the following equation:

$$M_{adsorbate} = M_{adsorbent} q_{0}$$

| Mass of AC (g) | Flow rate (mL/s) | $R_{adsorption}$ | $q_0$ | $M_{adsorbate}$ |
| --- | --- | --- | ---- | --- |
| 0.5 | 0.5 | 0.0742 | x | x |
| 0.6 | 0.5 | 0.0649 | x | x |
| 1.7 | 0.5 | 0.2058 | x | x |
| 2.0 | 0.466 | 0.3207 | x | x |
| 4.0 | 0.466 | 0.0426 | x | x |
| 13.8 | 2.6 | 0.0630 | x | x |
| 15.0 | 0.5 | 0.3278 | x | x |
| 15.6 | 2.6 | 0.0760 | x | x |
| 29.3 | 0.467 | 0.3953 | x | x |

**VICTOR**

```python
q0_array
M_absorbate_array
```
![q0](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab6/q0_graph.png)
Figure 6: ...

#### Conclusions ####

##### What did you learn from this analysis? How can you explain the results that you have obtained?

**VICTOR**

#### Suggestions ####

##### What changes to the experimental method do you recommend for next year (or for a project)?

From Figures 1, 2, 3 and 4, it can be seen that different teams used different flow rates. While it is educational to see how very high flow rates render the adsorption column effectively useless, to compare the breakthrough curves by varying the mass of activated carbon, perhaps it would be good to explicitly state the flow rate that should be used, as well as the setting in revolutions per minute (rpm) for the peristaltic pump.

Another suggestion is to label the diagram of the setup to state which connection uses a T-shaped connector and which one uses a T-shaped valve, as we initially spent a bit of time being confused about which one would go where since we had a limited number of each item.. Additionally, there were no instructions about how the T-shaped valves themselves worked in the textbook, so adding these in the instructions would be good as well.

It would also be good to identify the maximum amount of activated carbon that can be placed in the adsorption column such that the experiment can be completed within one lab session. We saw teams using small amounts of activated carbon without any sand in the column, resulting in activated carbon "floating" and being suspended in the column while water was pumped through. While it seemed clear for us to fill the gaps with sand, perhaps the instructions could make it more clear to do so.

```python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
import aguaclara.core.physchem as pc
import aguaclara.core.utility as ut
import numpy as np
import matplotlib.pyplot as plt
import collections
import os
from pathlib import Path
import pandas as pd

# Question 1
def adsorption_data(C_column, dirpath):
    """This function extracts the data from folder containing tab delimited
    files of adsorption data. The file must be the original tab delimited file.

    Parameters
    ----------
    C_column : int
        index of the column that contains the dissolved oxygen concentration
        data.
    dirpath : string
        path to the directory containing aeration data you want to analyze
    Returns
    -------
    filepaths : string list
        all file paths in the directory sorted by flow rate
    time_data : numpy array list
        sorted list of numpy arrays containing the times with units of seconds
    Examples
    --------
    """
    #return the list of files in the directory
    metadata = pd.read_csv(dirpath + '/metadata.txt', delimiter='\t')
    filenames = metadata['file name']
    #extract the flowrates from the filenames and apply units
    #sort airflows and filenames so that they are in ascending order of flow rates


    filepaths = [dirpath + '/' + i for i in filenames]

    C_data=[epa.column_of_data(i,epa.notes(i).last_valid_index() + 1,C_column,-1,'mg/L') for i in filepaths]
    time_data=[(epa.column_of_time(i,epa.notes(i).last_valid_index() + 1,-1)).to(u.s) for i in filepaths]

    adsorption_collection = collections.namedtuple('adsorption_results','metadata filenames C_data time_data')
    adsorption_results = adsorption_collection(metadata, filenames, C_data, time_data)
    return adsorption_results

C_column = 1
dirpath = "https://raw.githubusercontent.com/monroews/CEE4530/master/Examples/data/Adsorption"

metadata, filenames, C_data, time_data = adsorption_data(C_column,dirpath)
metadata
Column_D = 1 * u.inch
Column_A = pc.area_circle(Column_D)
Column_L = 15.2 * u.cm
Column_V = Column_A * Column_L
#I'm guessing at the volume of water in the tubing, in the photometer, and in the space above and below the column. This parameter could be adjusted!
Tubing_V = 60 * u.mL
Flow_rate = ([metadata['flow (mL/s)'][i] for i in metadata.index])* u.mL/u.s
Mass_carbon= ([metadata['carbon (g)'][i] for i in metadata.index])* u.g
Tubing_HRT = Tubing_V/Flow_rate
#to make things simple we are assuming that the porosity is the same for sand and for activated carbon. That is likely not true!
porosity = 0.4
C_0 = 50 * u.mg/u.L

#estimate the HRT for all of the columns
HRT = (porosity * Column_V/Flow_rate).to(u.s)

#zero the concentration data by subtracting the value of the first data point from all data points. Do this in each data set.
for i in range(np.size(filenames)):
  C_data[i]=C_data[i]-C_data[i][0]


#Create a graph of the columns that didn't have any activated carbon
mylegend = []
for i in range(np.size(filenames)):
  if (metadata['carbon (g)'][i] == 0):
    plt.plot(time_data[i]/HRT[i] - Tubing_HRT[i]/HRT[i], C_data[i]/C_0,'-');
    mylegend.append(str(metadata['flow (mL/s)'][i]) + ' mL/s')

plt.xlabel(r'$\frac{t}{\theta}$')
plt.xlim(right=3,left=0)
plt.ylabel(r'Red dye concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(mylegend)
plt.savefig('Lab6/Sand_column')
plt.show()

# create a graph of the columns that had different masses of activated carbon. Note that this includes systems with different flow rates!
mylegend =[]
for i in range(np.size(filenames)):
  if (metadata['carbon (g)'][i] != 0):
    plt.plot(time_data[i]/HRT[i] - Tubing_HRT[i]/HRT[i], C_data[i]/C_0,'-');
    mylegend.append(str(ut.round_sf(metadata['carbon (g)'][i],3)) + ' g, ' + str(ut.round_sf(metadata['flow (mL/s)'][i],2)) + ' mL/s')

plt.xlabel(r'$\frac{t}{\theta}$')
plt.xlim(right=875,left=0)
plt.ylabel(r'Red dye concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(mylegend)
plt.savefig('Lab6/Activated_carbon_2')
plt.show()

mylegend =[]
for i in range(np.size(filenames)):
  if (metadata['carbon (g)'][i] != 0):
    plt.plot(time_data[i]/HRT[i] - Tubing_HRT[i]/HRT[i], C_data[i]/C_0,'-');
    mylegend.append(str(ut.round_sf(metadata['carbon (g)'][i],3)) + ' g, ' + str(ut.round_sf(metadata['flow (mL/s)'][i],2)) + ' mL/s')

plt.xlabel(r'$\frac{t}{\theta}$')
plt.xlim(right=10,left=0)
plt.ylabel(r'Red dye concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(mylegend)
plt.savefig('Lab6/Activated_carbon_3')
plt.show()

# Question 2
t_array = np.zeros(len(filenames))
C_50 = 0.5 * C_0
for i in range(len(filenames)):
  for j in range(1, C_data[i].size):
    if (C_data[i][j-1] < C_50) and (C_data[i][j] > C_50):
      t_array[i] = (time_data[i][j].magnitude)

plt.plot(Mass_carbon, t_array, 'o')
plt.xlabel('Activated carbon (g)')
plt.ylabel('Time to C/Co = 0.5 (s)')
plt.savefig('Lab6/Time_graph')
plt.show

t_array_2 = np.zeros(len(filenames))
for i in range(len(filenames)):
  for j in range(1, C_data[i].size):
    if (C_data[i][j-1] < C_50) and (C_data[i][j] > C_50):
      if (Flow_rate[i]).magnitude < 0.6:
        t_array_2[i] = (time_data[i][j].magnitude)
      else:
        t_array_2[i] = float('nan')

plt.plot(Mass_carbon, t_array_2, 'o')
plt.xlabel('Activated carbon (g)')
plt.ylabel('Time to C/Co = 0.5 (s)')
plt.savefig('Lab6/Time_graph_2')
plt.show

# Question 3

Flow_rate
V_array = t_array[0:4] * u.sec * Flow_rate[0:4]
V_sum = 0 * u.mL

for i in range(len(V_array)):
  V_sum = V_sum + V_array[i]

avg_V = V_sum/len(V_array)

t_w_0_5 = avg_V/Flow_rate[1]
t_w_2_6 = avg_V/Flow_rate[2]

t_mtz = t_array * u.sec

Mass_carbon
Mass_carbon[4:13]

R_array = t_mtz[4:13]/t_w_0_5
Flow_rate
len(R_array)
R_array[5] = t_mtz[9]/t_w_2_6
R_array[7] = t_mtz[11]/t_w_2_6
R_array[8] = t_mtz[12]/t_w_2_6
R_array

# Question 5
q0_array = np.zeros(len(R_array))
q0_array = (R_array-1) * C_0.to(u.g/u.L) * phi * (Column_V).to(u.L) /Mass_carbon[4:13]
q0_array

plt.plot(Mass_carbon[4:13], q0_array, 'o')
plt.xlabel('Mass of AC (g)')
plt.ylabel(r'$q_0$')
plt.savefig('Lab6/q0_graph')
plt.show()

# Question 4
M_absorbate_array = Mass_carbon[4:13]*q0_array
```

```python
# Notes while conducting the actual experiment
mLperrev_Tubing_17 = 2.8 * u.mL/u.revolution
Pump_rpm = 10 * u.revolution/u.min
Q_reddye = Pump_rpm * mLperrev_Tubing_17
Q_reddye.to(u.mL/u.sec)
vol = 20 * u.L
exp_time = vol/Q_reddye
exp_time.to(u.hour)

mass_AC = 29.342 * u.g
```
