# Project Report for CEE 4530

### Team 10: Victor Khong & Jacqueline Wong ###

#### Introduction ####

[Victor: Equations used in analysis. I don't think we even used q0.]:#

Adsorption is a unit operation in which surface-active materials in true solution are removed from the solvent by interphase transfer to the surface of an adsorbent particle. This process is employed in environmental engineering practice for removal of various pollutants such as soluble organics, dyes, pesticides and humic substances from wastewater, and for removal of color, taste, and odor-producing compounds from natural waters that are to be used as potable water supplies. Activated carbon is one such adsorbent used in drinking water and wastewater treatment to transfer dissolved species to the solid phase, particularly for the remediation of groundwater contaminated with volatile and nonvolatile organic pollutants (Weber-Shirk, 2019).

Our team is interested in investigating methods to optimize the effectiveness of an adsorption system, in particular how the variation in the way the adsorbent is placed within the column and a change in influent flow rate into the adsorption system affects the effectiveness of the adsorption system in removing a pollutant from the water. This is an interesting problem that has practical applications because our society is constantly faced with the challenge to treat wastewater at a low cost and efficient manner, and activated is not cheap considering that it needs to be continually replaced and that it is not as accessible for treatment plants in developing countries. Higher flow rates allow for more water to be treated at a given time, but this may affect adsorption efficiency. The results of this experiment will enable scientists and engineers to gain a better understanding towards building the most optimal adsorption system for better drinking water and wastewater treatment (Çeçen, 2011).

At any given water and wastewater treatment facility, there is a maximum contaminant level, which operator considers water to be treated at levels lower than the standard. In this experiment, water is considered treated when the concentration of the pollutant in the effluent is less than or equal to 60% of the concentration of the pollutant in the influent, i.e. $\frac{C}{C_0} <= 0.5$.

As our team will vary flow rate across the adsorption column, we are interested in the tradeoff between the amount of water that can be treated given the useful lifespan of the adsorption column decreases with increasing flow rate. This is also synonymous to the amount of water that a factory can bottle and sell until the adsorption column needs to be maintained and replaced. These two factors will directly vary the total amount of water treated and consequently, affect the effectiveness of the adsorption column in treating water.

To calculate the volume of water that is treated, the following equation is used:

$$V=T_{breakthrough}Q$$

where $Q$ is the flow rate of the red dye passing through the adsorbent column and $T_{breakthrough}$ is the time when breakthrough is achieved.

To further extend our results to wastewater of different concentration, our team intends to calculate the mass of adsorbate at the breakthrough time, which is given as:

$$M_{adsorbate} = M_{adsorbent} q_{0}$$

where $M$ is the mass and $q_{0}$ is mass of adsorbate per mass of adsorbent at the breakthrough time.

#### Objectives ####

There are two objectives of this project:
1. Investigate the breakthrough characteristics and equilibrium partitioning of red dye #40 on activated carbon in a continuous flow carbon contactor at a range of different layering patterns given equal proportions of sand and activated carbon by mass in the column.
2. Investigate the relationship between how varying flow rate affects the amount of water that can be “treated” by the adsorption column until the effluent is 60% of the influent concentration.

#### Hypothesis ####

For the first objective, our hypothesis is that for the same mass of adsorbent, the column with adsorbent mixed throughout the column will be the least effective, while the column with the more layers will be the more effective until those layers become too thin.  In Gritti et. al’s 2004 study titled “Effect of the flow rate on the measurement of adsorption data by dynamic frontal analysis”, it states that as flow rate increases, the mass of dye adsorbed increases (Gritti, 2004). However, for flow rate, we believe that this flow rate should not affect the mass of dye adsorbed. Although there already exists a study on this, we are interested in further investigating this claim as too high of a flow rate may also make it more difficult for dye to attach to the pores in activated carbon, and perhaps even render it useless.

In order to achieve the first objective, the adsorbent will be either mixed or separated into even layers throughout the column and the column will be run with the same flow rate. For the second objective, the layering pattern will be the same in the column but flow rate will be varied. To determine which has the better performance for the first objective, we will plot the breakthrough curves of different experiments, and the relative time it takes for the effluent concentration to be 50% of the influent concentration (Weber-Shirk, “Adsorption”). To determine which has the better performance for the second objective, we will determine the amount of water treated based on the time it takes until the effluent is 50% of the influent concentration. This is dependent on the life of the adsorption column and the amount of pollutant absorbed by the adsorbent at any given time in which that water is considered treated.

#### Materials ####

For simplicity, this experiment will utilize a basic adsorption system. The adsorption system will be built using a peristaltic pump, an adsorption column, #17 tubing, and a photometer. The absorbent of the system is activated carbon. The rest of the adsorption column will be filled with sand. There should be equal mass of activated carbon and sand in the adsorption column. The adsorption system will be set up as shown in Figure 1.

![setup_mixed](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/setup_mixed.png)
Figure 1: Diagram of the experimental setup for the trial with activated carbon mixed throughout the column with sand.

#### Experimental Procedure ####

[Victor: Add anything else that we missed]:#

In this experiment, the effectiveness of the adsorption system will be measured in accordance to how clear the water filtered out is and the duration at which the absorbent is able to last. These two factors are important in vital in determining how much pollutant the adsorption system can adsorb with one batch of adsorbent. The concentration of dye in the effluent can be measured using a photometer.

The key design parameters of the experiment is the placement of the adsorbent and the influent flow rate. The experiment would explore the scenarios when the adsorbent is mixed throughout the adsorbent column (Figure 1), and when the adsorbent is separated into 1, 2, 4, 6 and 8 layers (Figure 2, 3) (Table 1). The flow rates that will be experimented on are 15, 20, 25 30, 37.5, 45, 60, 75 and 90 rpm with one layer of activated carbon (Table 2).

![setup_2](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/setup_2.png)
Figure 2: Diagram of the experimental setup for the trial with 2 even layers of activated carbon separated by layers of sand.

![setup_2](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/setup_8.png)
Figure 3: Diagram of the experimental setup for the trial with 8 even layers of activated carbon separated by layers of sand.

Table 1: Experiments conducted with varying layers
|                  | Layers | Flow Rate (mL/s) | Pump (rpm) |
| ---------------- | ------ | ---------------- | ---------- |
| **Control**      | 0      | 0.7              | 15         |
| **Experiment 01** | 1      | 0.7              | 15         |
| **Experiment 02** | 2      | 0.7              | 15         |
| **Experiment 03** | 4      | 0.7              | 15         |
| **Experiment 04** | 6      | 0.7              | 15         |
| **Experiment 05** | 8      | 0.7              | 15         |
| **Experiment 06** | Mixed  | 0.7              | 15         |


Table 2: Experiments conducted with varying flow rate
|                   | Layers | Flow Rate (mL/s) | Pump (rpm) |
| ----------------- | ------ | ---------------- | ---------- |
| **Experiment 07**  | 1      | 0.7              | 15         |
| **Experiment 08**  | 1      | 0.933            | 20         |
| **Experiment 09**  | 1      | 1.167            | 25         |
| **Experiment 10** | 1      | 1.4              | 30         |
| **Experiment 11** | 1      | 1.75             | 37.5       |
| **Experiment 12** | 1      | 2.1              | 45         |
| **Experiment 13** | 1     | 2.8              | 60 |
| **Experiment 14** | 1      | 3.5              | 75 |
| **Experiment 15** | 1      | 4.2              | 90 |

#### Results ####

![Layers 1](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Layers_1.png)
Figure 4:

![Layers 1](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Layers_2.png)
Figure 5:

![Layers 1](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Layers_3.png)
Figure 6:

![Layers 1](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Layers_4.png)
Figure 7: 

[Jacqueline: Graphs with caption]:#
[Jacqueline: Calculate volume treated]:#

[Victor: Go further into description]:#

#### Conclusion ####

[Jacqueline: Diagrams to explain hypothesis]:#

![Layering Hypothesis](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Graphic_5.png)
Figure x: Diagram of ....

![Mixing Hypothesis](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Graphic_6.png)
Figure x: Diagram of ....

#### Suggestions / Comments ####

[Victor: Copy things from slide.]:#

#### References ####

Çeçen, F. & Aktaş, Ö. (2011). Activated Carbon for Water and Wastewater Treatment: Integration of Adsorption and Biological Treatment. Retrieved from https://onlinelibrary.wiley.com/doi/book/10.1002/9783527639441

Gritti, F. & Guiochon, G. (2011). Effect of the flow rate on the measurement of adsorption data by dynamic frontal analysis. Retreived from https://www.sciencedirect.com/science/article/pii/S0021967304014888

Weber-Shirk, M. (2019). Adsorption. Retrieved from https://monroews.github.io/EnvEngLabTextbook/Adsorption/Adsorption.html#prelab-questions

```python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
import aguaclara.core.utility as ut
import aguaclara.core.constants as c
import aguaclara.core.physchem as pc
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from scipy import stats
from scipy import optimize
import collections
import os
from pathlib import Path

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
    metadata = pd.read_csv(dirpath + '/metadata.txt', delimiter='\t')
    filenames = metadata['file name']
    filepaths = [dirpath + '/' + i for i in filenames]

    C_data=[epa.column_of_data(i,epa.notes(i).last_valid_index() + 1,C_column,-1,'mg/L') for i in filepaths]
    time_data=[(epa.column_of_time(i,epa.notes(i).last_valid_index() + 1,-1)).to(u.s) for i in filepaths]

    adsorption_collection = collections.namedtuple('adsorption_results','metadata filenames C_data time_data')
    adsorption_results = adsorption_collection(metadata, filenames, C_data, time_data)
    return adsorption_results

    t_array = np.zeros(len(filenames))
    C_50 = 0.5 * C_0
    for i in range(len(filenames)):
      for j in range(1, C_data[i].size):
        if (C_data[i][j-1] < C_50) and (C_data[i][j] > C_50):
          t_array[i] = (time_data[i][j].magnitude)

# Use adsorption_data function to extract data
C_column = 1
dirpath = "https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Data/"
metadata, filenames, C_data, time_data = adsorption_data(C_column,dirpath)
metadata

# Calculate volume of column based on dimensions
Column_D = 1 * u.inch
Column_A = pc.area_circle(Column_D)
Column_L = 15.2 * u.cm
Column_V = Column_A * Column_L

# Assume this porosity
porosity = 0.4

# Calculate volume of tubing by pumping water through system
mLperrev_Tubing_17 = 2.8 * u.mL/u.revolution
Pump_rpm = 15 * u.revolution/u.min
Tubing_Q = mLperrev_Tubing_17 * Pump_rpm
Tubing_t = 2.5 * u.min
Tubing_V = (Tubing_Q * Tubing_t) - Column_V * (1 - porosity)
Tubing_V.to(u.mL)

Flow_rate = ([metadata['flow (mL/s)'][i] for i in metadata.index])* u.mL/u.s
Layers= ([metadata['layers'][i] for i in metadata.index])
Tubing_HRT = Tubing_V/Flow_rate

# Calculate hydraulic residence time in column
HRT = (porosity * Column_V/Flow_rate).to(u.s)

# Concentration of red dye
C_0 = 50 * u.mg/u.L

# Target concentration
C_45 = 0.45 * C_0

# Subtract first data point
for i in range(np.size(filenames)):
  C_data[i]=C_data[i]-C_data[i][0]

# Plot concentration against time for different layers
plt.plot(time_data[1].to(u.min), C_data[1])
plt.plot(time_data[2].to(u.min), C_data[2])
plt.plot(time_data[3].to(u.min), C_data[3])
plt.plot(time_data[4].to(u.min), C_data[4])
plt.plot(time_data[5].to(u.min), C_data[5])
plt.plot(time_data[6].to(u.min), C_data[6])
plt.xlabel("Time (min)")
plt.ylabel("Concentration (mg/L)")
leg = plt.legend(('1 layer', '2 layers', '4 layers', '6 layers', '8 layers', 'no layers'), loc='best')
plt.savefig("Project/Layers_1.png")
plt.show()

# Plot 1-8 layers
plt.plot(time_data[1].to(u.min), C_data[1])
plt.plot(time_data[2].to(u.min), C_data[2])
plt.plot(time_data[3].to(u.min), C_data[3])
plt.plot(time_data[4].to(u.min), C_data[4])
plt.plot(time_data[5].to(u.min), C_data[5])
#plt.plot(time_data[6].to(u.min), C_data[6])
plt.xlabel("Time (min)")
plt.ylabel("Concentration (mg/L)")
leg = plt.legend(('1 layer', '2 layers', '4 layers', '6 layers', '8 layers', 'no layers'), loc='best')
plt.savefig("Project/Layers_2.png")
plt.show()

# Plot 1 layer and 8 layers
plt.plot(time_data[1].to(u.min), C_data[1])
#plt.plot(time_data[2].to(u.min), C_data[2])
#plt.plot(time_data[3].to(u.min), C_data[3])
#plt.plot(time_data[4].to(u.min), C_data[4])
plt.plot(time_data[5].to(u.min), C_data[5])
#plt.plot(time_data[6].to(u.min), C_data[6])
plt.xlabel("Time (min)")
plt.ylabel("Concentration (mg/L)")
leg = plt.legend(('1 layer', '8 layers'), loc='best')
plt.savefig("Project/Layers_3.png")
plt.show()

# Plot 1 layer and no layers
plt.plot(time_data[1].to(u.min), C_data[1])
#plt.plot(time_data[2].to(u.min), C_data[2])
#plt.plot(time_data[3].to(u.min), C_data[3])
#plt.plot(time_data[4].to(u.min), C_data[4])
#plt.plot(time_data[5].to(u.min), C_data[5])
plt.plot(time_data[6].to(u.min), C_data[6])
plt.xlabel("Time (min)")
plt.ylabel("Concentration (mg/L)")
leg = plt.legend(('1 layer', 'no layers'), loc='best')
plt.savefig("Project/Layers_4.png")
plt.show()

# Plot concentration against time for different flow rates
plt.plot(time_data[6].to(u.min), C_data[6])
plt.plot(time_data[7].to(u.min), C_data[7])
plt.plot(time_data[8].to(u.min), C_data[8])
plt.plot(time_data[9].to(u.min), C_data[9])
plt.plot(time_data[10][0:25].to(u.min), C_data[10][0:25])
plt.plot(time_data[11].to(u.min), C_data[11])
plt.plot(time_data[12].to(u.min), C_data[12])
plt.plot(time_data[13].to(u.min), C_data[13])
plt.plot(time_data[14].to(u.min), C_data[14])
plt.xlabel("Time (min)")
plt.ylabel("Concentration (mg/L)")
plt.ylim(0,24)
leg = plt.legend(('0.7 mL/s','0.933 mL/s','1.167 mL/s', '1.4 mL/s', '1.75 mL/s','2.1 mL/s','2.8 mL/s','3.5 mL/s','4.2 mL/s'), loc='best')
plt.savefig("Project/Flows_1.png")
plt.show()

# Plot concentration against time for higher flow rates
plt.plot(time_data[11].to(u.min), C_data[11])
plt.plot(time_data[12].to(u.min), C_data[12])
plt.plot(time_data[13].to(u.min), C_data[13])
plt.plot(time_data[14].to(u.min), C_data[14])
plt.xlim(right=2,left=0)
plt.xlabel("Time (min)")
plt.ylabel("Concentration (mg/L)")
leg = plt.legend(('2.1 mL/s','2.8 mL/s','3.5 mL/s','4.2 mL/s'), loc='best')
plt.savefig("Project/Flows_2.png")
plt.show()

# Plot concentration against time for lower flow rates
plt.plot(time_data[6].to(u.min), C_data[6])
plt.plot(time_data[7].to(u.min), C_data[7])
plt.plot(time_data[8].to(u.min), C_data[8])
plt.plot(time_data[9].to(u.min), C_data[9])
plt.plot(time_data[10][0:25].to(u.min), C_data[10][0:25])
plt.xlabel("Time (min)")
plt.ylabel("Concentration (mg/L)")
leg = plt.legend(('0.7 mL/s','0.933 mL/s','1.167 mL/s', '1.4 mL/s', '1.75 mL/s'), loc='best')
plt.savefig("Project/Flows_3.png")
plt.show()

# Plot time to C = 0.5 C0 for different flow rates
t_array = np.zeros(len(filenames))
for i in range(len(filenames)):
  for j in range(1, C_data[i].size):
    if (C_data[i][j-1] < C_45) and (C_data[i][j] > C_45):
      t_array[i] = (time_data[i][j].magnitude)

t_array = t_array * u.s
plt.plot(Flow_rate[6:15], (t_array[6:15]).to(u.min), 'o')
plt.xlabel('Flow rate (mL/s)')
plt.ylabel('Time to C/Co = 0.5 (min)')
plt.xlim(right=4.5,left=0)
plt.savefig("Project/Time_Flows.png")
plt.show()

# Plot volume treated until C = 0.5 C0
V_array = t_array[6:15] * Flow_rate[6:15]
plt.plot(Flow_rate[6:15], (V_array).to(u.L), 'o')
plt.xlabel('Flow rate (mL/s)')
plt.ylabel('Volume (L)')
plt.savefig("Project/Volume_Flows_1.png")
plt.show()

# Plot volume treated for lower flow rates
plt.plot(Flow_rate[6:11], (V_array[1:6]).to(u.L), 'o')
plt.xlabel('Flow rate (mL/s)')
plt.ylabel('Volume (L)')
plt.savefig("Project/Volume_Flows_2.png")
plt.show()
```
