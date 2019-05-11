# Utilizing layering and flow rate variation to improve existing adsorption treatment strategies #

### Final Project Report for CEE 4530 ###

### Team 10: Victor Khong & Jacqueline Wong ###

![Photo 1](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Photo_1.jpg)

![Photo 2](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Photo_2.jpg)

#### Introduction ####

Adsorption is a unit operation in which surface-active materials in true solution are removed from the solvent by interphase transfer to the surface of an adsorbent particle. This process is employed in environmental engineering practice for removal of various pollutants such as soluble organics, dyes, pesticides and humic substances from wastewater, and for removal of color, taste, and odor-producing compounds from natural waters that are to be used as potable water supplies. Activated carbon is one such adsorbent used in drinking water and wastewater treatment to transfer dissolved species to the solid phase, particularly for the remediation of groundwater contaminated with volatile and nonvolatile organic pollutants (Weber-Shirk, 2019).

Our team is interested in investigating methods to optimize the effectiveness of an adsorption system, in particular how the variation in the way the adsorbent is placed within the column and a change in influent flow rate into the adsorption system affects the effectiveness of the adsorption system in removing a pollutant from the water. This is an interesting problem that has practical applications because our society is constantly faced with the challenge to treat wastewater at a low cost and efficient manner, and activated carbon is not cheap considering that it needs to be continually replaced and that it is not as accessible for treatment plants in developing countries. Higher flow rates allow for more water to be treated at a given time, but this may affect adsorption efficiency. The results of this experiment will enable us to gain a better understanding towards building a more optimal adsorption system for better drinking water and wastewater treatment (Çeçen, 2011).

At any given water and wastewater treatment facility, there is a maximum contaminant level, which operator considers water to be treated at levels lower than the standard. In this experiment, water is considered treated when the concentration of the pollutant in the effluent is less than or equal to 50% of the concentration of the pollutant in the influent, i.e. $\frac{C}{C_0} <= 0.5$.

Furthermore, our team is interested in the tradeoff between the amount of water that can be treated given the useful lifespan of the adsorption column decreases with increasing flow rate. This is also synonymous to the amount of water that a factory can bottle and sell until the adsorption column needs to be maintained and replaced. These two factors will directly vary the total amount of water treated and consequently, affect the effectiveness of the adsorption column in treating water.

To calculate the volume of water that is treated, $V_{treated}$ the following equation is used:

$$V_{treated}=t_{breakthrough} \times Q$$

where $Q$ is the flow rate of the red dye passing through the adsorbent column and $t_{breakthrough}$ is the time when breakthrough is achieved.

#### Objectives ####

There are two main objectives of this project:
1. Investigate the breakthrough characteristics and equilibrium partitioning of red dye #40 on activated carbon in a continuous flow carbon contactor at a range of different layering patterns given equal proportions of sand and activated carbon by mass in the column.
2. Investigate the relationship between varying flow rate and how it affects the amount of water that can be "treated" by the adsorption column until the effluent is 50% of the influent concentration.

#### Hypothesis ####

For the first objective, our hypothesis is that for the same mass of adsorbent, the column with adsorbent mixed throughout the column will be the least effective, while the column with the more layers will be the more effective until those layers become too thin as there is a chance that the red dye will not come into contact with an activated carbon granule if it is thoroughly mixed with sand.  

For our second objective, in Gritti et. al’s 2004 study titled “Effect of the flow rate on the measurement of adsorption data by dynamic frontal analysis”, it states that as flow rate increases, the mass of dye adsorbed increases (Gritti, 2004). However, we believe that this flow rate should not affect the mass of dye adsorbed. Although there already exists a study on this, we are interested in further investigating this claim as we expect that too high of a flow rate may make it more difficult for dye to attach to the pores in activated carbon, and perhaps even render it useless.

In order to achieve the first objective, the adsorbent will be either mixed or separated into even layers throughout the column and the column will be run with the same flow rate. For the second objective, the layering pattern will be the same in the column but flow rate will be varied. To determine which has the better performance for the first objective, we will plot the breakthrough curves of different experiments, and the relative time it takes for the effluent concentration to be 50% of the influent concentration (Weber-Shirk, “Adsorption”). To determine which has the better performance for the second objective, we will determine the amount of water treated based on the time it takes until the effluent is 50% of the influent concentration, $V_{treated}$. This is dependent on the life of the adsorption column and the amount of pollutant absorbed by the adsorbent at any given time in which that water is considered treated.

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

|                   | Layers | Flow Rate (mL/s) | Pump (rpm) |
| ----------------- | ------ | ---------------- | ---------- |
| **Control**       | 0      | 0.7              | 15         |
| **Experiment 01** | 1      | 0.7              | 15         |
| **Experiment 02** | 2      | 0.7              | 15         |
| **Experiment 03** | 4      | 0.7              | 15         |
| **Experiment 04** | 6      | 0.7              | 15         |
| **Experiment 05** | 8      | 0.7              | 15         |
| **Experiment 06** | Mixed  | 0.7              | 15         |

Table 2: Experiments conducted with varying flow rate

|                   | Layers | Flow Rate (mL/s) | Pump (rpm) |
| ----------------- | ------ | ---------------- | ---------- |
| **Experiment 07** | 1      | 0.7              | 15         |
| **Experiment 08** | 1      | 0.933            | 20         |
| **Experiment 09** | 1      | 1.167            | 25         |
| **Experiment 10** | 1      | 1.4              | 30         |
| **Experiment 11** | 1      | 1.75             | 37.5       |
| **Experiment 12** | 1      | 2.1              | 45         |
| **Experiment 13** | 1      | 2.8              | 60         |
| **Experiment 14** | 1      | 3.5              | 75         |
| **Experiment 15** | 1      | 4.2              | 90         |

#### Results ####

As mentioned above, the first part of this project aims to investigate the breakthrough characteristics of a continuous flow carbon contactor at a range of different layering patterns given equal proportions of sand and activated carbon by mass in the column (Table 1). The concentration of red dye was plotted against time for Experiments 1-6 (Figure 4).

![Layers 1](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Layers_1.png)

Figure 4: Graph of red dye concentration against time for all layering experiments at 0.7 mL/s.

For Experiments 1-5, which all 1, 2, 4, 6 or 8 alternating layers of activated carbon and sand, it can be seen that most of the breakthrough curves have very similar shapes (Figure 5). Although our team tried to ensure that the peristaltic pump would pump red dye instead of reverse osmosis water once logging began, there were slight variations with when the concentration of red dye began to change. However, this is mostly negligible as it can still be seen that the curves still look very similar.

![Layers 2](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Layers_2.png)

Figure 5: Graph of red dye concentration against time for 1, 2, 4, 6 and 8 layers at 0.7 mL/s.

For better visualization, the two experiments with the most different number of layers (which also happen to have fewer air bubble spikes) were plotted (Figure 6). It can be seen that even the experiment with 1 layer of activated carbon and the experiment with 8 layers of activated carbon have almost identical breakthrough curves. Thus, this data suggests that contrary to our hypothesis, there there was no observed difference in adsorption efficiency by varying the number of alternating layers of activated carbon and sand.

![Layers 3](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Layers_3.png)

Figure 6: Graph of red dye concentration against time for 1 layer and 8 layers at 0.7 mL/s.

However, despite the mostly similar breakthrough curves in Figure 4, there is one particular plot in brown of the breakthrough curve with no layers (i.e. activated carbon and sand mixed thoroughly throughout the adsorption column) that appears to have a lower slope. Plotting this against the experiment with 1 layer of activated carbon, it can be seen that the breakthrough curve for the mixing experiment is indeed at a lower gradient (Figure 7). This suggests that while there is no difference between the number of layers, thoroughly mixing activated carbon and sand throughout the column results in a visible improvement in adsorption efficiency.

![Layers 4](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Layers_4.png)

Figure 7: Graph of red dye concentration against time for 1 layer and no layers (mixed) at 0.7 mL/s.

One hypothesis that was developed to explain this phenomenon is that thorough mixing allowed for more uniform red dye concentration within the column due to the greater distance between activated carbon granules.

![Layering Hypothesis](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Graphic_5.png)

Figure 8: Diagram of the similar adsorption mechanism for 1, 2, 4, 6 and 8 layers of activated carbon alternating between layers of sand.

For the proposed adsorption mechanism in experiments with layers of activated carbon, the dark red line on the right side represents the distribution of red dye concentration between the two activated carbon granules (Figure 8). As red dye is diffusing into the pores of the activated carbon granules, concentration is lower next to the activated carbon granules and higher in between, resulting in a less uniform distribution.

![Mixing Hypothesis](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Graphic_6.png)

Figure 9: Diagram of adsorption mechanism for no layers, i.e. thorough mixing of activated carbon and sand throughout the column.

On the other hand, for the proposed adsorption mechanism in the experiment with no layers of activated carbon (i.e. thorough mixing with sand), the dark red line on the right side represents the distribution of red dye concentration between an activated carbon granule and sand particle (Figure 9). Red dye concentration is lower next to the activated carbon granules but higher in the spacing between and next to the sand particle, as sand has negligible adsorption properties. This results in more uniform distribution compared to the previous scenario.

Assuming that the rate at which red dye is adsorbed by the activated carbon granule is a function of diffusion into its pores, this could be a rate limiting step. The more uniform the distribution of red dye, the better the diffusion. Thus, the experiment with thorough mixing of activated carbon and sand performed better than the experiments with alternating layers.

However, it is also worth noting that the number of layers in this experiment is generally in the lower range. Perhaps a difference in performance may only be seen at a much greater number of layers (e.g. 100 layers), since thorough mixing is analogous to having infinite layers.

The second part of this project aims to investigate the relationship between varying flow rate and how it affects the amount of water that can be treated by the adsorption column until the effluent is 50% of the influent concentration given a single layer of the same mass of activated carbon in the column (Table 2). The concentration of red dye was plotted against time for Experiments 7-15 (Figure 10).

![Flows 1](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Flows_1.png)

Figure 10: Graph of red dye concentration against time for all flow rate experiments with 1 layer of activated carbon between layers of sand.

From Figure 10, it can be seen that as the flow rate increases, the less time it takes to reach breakthrough, as was expected in our second hypothesis. As the shapes of all the breakthrough curves are difficult to see, Figure 11 shows the breakthrough curves for the higher flow rates and Figure 12 shows those for the lower flow rates.

![Flows 2](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Flows_2.png)

Figure 11: Graph of red dye concentration against time for higher flow rates.

![Flows 3](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Flows_3.png)

Figure 12: Graph of red dye concentration against time for lower flow rates.

In terms of the time it takes for the time until the effluent concentration is 50% of the influent concentration, $t_{breakthrough}$, it can be seen to decrease with increasing flow rate (Figure 13). While flow rates above 2.1 mL/s breakthrough immediately, there appears to be a curve that could fit this relationship with time to C/C~0~ = 0.5 for lower flow rates.

![Time 1](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Time_Flows_1.png)

Figure 13: Graph of the time is takes for effluent concentration to be 50% of influent concentration for different flow rates.

Using the trendline function on Microsoft Excel, the following fourth-order polynomial curve was found to be a good estimate (R^2^ = 0.99662) of the time to breakthrough (in minutes), $\hat{t}_{breakthrough}$, based on varying flow rates (in milliliters per second), $Q$, between 0.7-2.1 mL/s:

$$ \hat{t}_{breakthrough} = 15.411 Q^4 - 99.682 Q^3 + 247.54 Q^2 - 289.24 Q + 139.21 $$

![Time 2](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Time_Flows_2.png)

Figure 14: Graph of the time is takes for effluent concentration to be 50% of influent concentration for the lower flow rates.

However, despite the fact that the fourth-order polynomial curve fits the data nicely, this is only an empirical model that calculated based on observations limited to the investigation. It does not explain any of the theory behind the physical-chemical processes that result in this pattern.

The time that it takes for effluent concentration to be 50% of influent concentration cannot be used as a good comparison of results because flow rate is different. Thus, in order to normalize these values, the total volume of water "treated", $V_{treated}$, will be plotted as well (Figure 15). Similarly, it can be seen that even with this normalization, as the flow rate increases, the less volume of water the system can treat until breakthrough.

![Volume 1](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Volume_Flows_1.png)

Figure 15: Graph of the volume of water treated until effluent concentration is 50% of influent concentration for different flow rates.

Again using the trendline function on Microsoft Excel, the following second-order polynomial curve was found to be a good estimate (R^2^ = 0.99172) of the total volume of water treated (in liters), $\hat{V}_{treated}$, based on varying flow rates (in milliliters per second), $Q$, between 0.7-2.1 mL/s:

$$ \hat{V}_{treated} = 0.32871 Q^2 - 1.7472 Q + 2.2185 $$

![Volume 2](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/Volume_Flows_2.png)

Figure 16: Graph of the volume of water treated until effluent concentration is 50% of influent concentration for lower flow rates.

Even though the fact that the second-order polynomial curve fits the data nicely, this is still only an empirical model that calculated based on observations limited to the investigation. It does not explain any of the theory behind the physical-chemical processes that result in this pattern.

Regardless, this data suggests that even though flow rate allows for more water to pass through the adsorption column at a given time, in order to best utilize the system, the lowest flow rate possible is the optimum choice in this scenario. In terms of real-life application, perhaps even on a large-scale, it would be best for treatment plants to operate the adsorption system with the lowest flow rate as possible that can still meet consumer needs.

#### Conclusion ####

[Victor: Summarize the results in a few sentences. Directly connect this to the two objectives]:#

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
from scipy.optimize import curve_fit
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
plt.ylim(0,22)
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
plt.ylim(0,23)
plt.xlabel("Time (min)")
plt.ylabel("Concentration (mg/L)")
leg = plt.legend(('0.7 mL/s','0.933 mL/s','1.167 mL/s', '1.4 mL/s', '1.75 mL/s'), loc='best')
plt.savefig("Project/Flows_3.png")
plt.show()

t_array = np.zeros(len(filenames))
for i in range(len(filenames)):
  for j in range(1, C_data[i].size):
    if (C_data[i][j-1] < C_45) and (C_data[i][j] > C_45):
      t_array[i] = (time_data[i][j].magnitude)

t_array = t_array * u.sec
HRT_array = (porosity * Column_V/Flow_rate).to(u.s)

x_array = np.linspace(0.7, 2.1, 100)
y_array_1 = 15.411 * x_array**4 - 99.682 * x_array**3 + 247.54 * x_array**2 - 289.24 * x_array + 139.21
y_array_1 = y_array_1 * u.min

# Plot time to C = 0.5 C0 for different flow rates
plt.plot(Flow_rate[6:15], (t_array[6:15]).to(u.min), 'o')
plt.xlabel('Flow rate (mL/s)')
plt.ylabel('Time to C/Co = 0.5 (min)')
leg = plt.legend(('Data points','Curve fit', 'Line fit'), loc='best')
plt.savefig("Project/Time_Flows_1.png")
plt.show()

# Plot time to C = 0.5 C0 for lower flow rates
plt.plot(Flow_rate[6:12], (t_array[6:12]).to(u.min), 'o')
plt.plot(x_array, y_array_1, 'r-')
plt.xlabel('Flow rate (mL/s)')
plt.ylabel('Time to C/Co = 0.5 (min)')
leg = plt.legend(('Data points','Curve fit'), loc='best')
plt.savefig("Project/Time_Flows_2.png")
plt.show()

slope, intercept, r_value, p_value, std_err = stats.linregress(Flow_rate[6:12],V_array[0:6])
y_array_2 = x_array * slope + intercept
y_array_2 = y_array_2 * u.mL

y_array_3 = 0.3287 * x_array**2 - 1.7472 * x_array + 2.2185
y_array_3 = y_array_3 * u.L

# Plot volume treated until C = 0.5 C0
V_array = t_array[6:15] * Flow_rate[6:15]
plt.plot(Flow_rate[6:15], (V_array).to(u.L), 'o')
plt.xlabel('Flow rate (mL/s)')
plt.ylabel('Volume (L)')
plt.savefig("Project/Volume_Flows_1.png")
plt.show()

# Plot volume treated for lower flow rates
plt.plot(Flow_rate[6:12], (V_array[0:6]).to(u.L), 'o')
#plt.plot(x_array, y_array_2.to(u.L), '-')
plt.plot(x_array, y_array_3.to(u.L), '-')
plt.xlabel('Flow rate (mL/s)')
plt.ylabel('Volume (L)')
leg = plt.legend(('Data points', 'Curve fit'), loc='best')
plt.savefig("Project/Volume_Flows_2.png")
plt.show()
```
