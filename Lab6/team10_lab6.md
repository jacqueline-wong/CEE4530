# Lab 6 for CEE 4530

### Team 10: Victor Khong (X hours) & Jacqueline Wong (X hours)

##### 1. Plot the breakthrough curves showing \frac{C}{C_0} versus time. #

![AC1](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab6/Activated_carbon.png)
Figure 1: Breakthrough curves of C/Co against time for different masses of activated carbon and different flow rates.

![AC2](https://raw.githubusercontent.com/lw583/CEE4530/master/Lab6/Activated_carbon_2.png)
Figure 2: Breakthrough curve of C/Co against time for different masses of activated carbon and different flow rates, with a larger x-axis.

##### 2. Find the time when the effluent concentration was 50% of the influent concentration and plot that as a function of the mass of activated carbon used. #

To calculate the time when the effluent concentration was 50% of the influent concentration, we use the following equations.
$$t_{mtz} = t_{water} + t_{ads}$$
$$\frac{L_{column}}{v_{mtz}} = \frac{L_{column}\phi}{v_a} + \frac{L_{column}q_0 M_{adsorbent}}{v_a C_0 V_{column}}$$

##### 3. Calculate the retardation coefficient (R_{adsorption}) based on the time to breakthrough for the columns with and without activated carbon. #

$$R_{adsorption} = \frac{t_{mtz}}{t_{water}} = \frac{v_{pore}}{v_{mtz}} = \frac{v_a}{\phi v_{mtz}}$$

$$R_{adsorption} =1+ \frac{q_0 M_{adsorbent}}{C_0 \phi V_{column}}$$


##### 4. Calculate the quantity of Red Dye #40 that was transferred to the activated carbon based on the influent concentration, flow rate, and 50% breakthrough time. #

##### 5. Calculate the q_0 for each of the columns. Plot this as a function of the mass of activated carbon used. #

##### What did you learn from this analysis? How can you explain the results that you have obtained? What changes to the experimental method do you recommend for next year (or for a project)? #

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
    #C_data is a list of numpy arrays. Thus each of the numpy data arrays can have different lengths to accommodate short and long experiments
    # cycle through all of the files and extract the column of data with oxygen concentrations and the times
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
# plt.legend(mylegend)
plt.savefig('Lab6/Activated_carbon_2')
plt.show()
```

```python
...

mLperrev_Tubing_17 = 2.8 * u.mL/u.revolution
Pump_rpm = 10 * u.revolution/u.min
Q_reddye = Pump_rpm * mLperrev_Tubing_17
Q_reddye.to(u.mL/u.sec)
vol = 20 * u.L
exp_time = vol/Q_reddye
exp_time.to(u.hour)

mass_AC = 29.342 * u.g
```
