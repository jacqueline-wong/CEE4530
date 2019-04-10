# Research Proposal for CEE 4530

### Team 10: Victor Khong (5 hours) & Jacqueline Wong (5 hours) ###

Write your research proposal in Atom. You can begin defining variables and calculating parameters as you design your proposed research. This research proposal can then evolve into your final report.

#### Introduction ####

Adsorption is a unit operation in which surface-active materials in true solution are removed from the solvent by interphase transfer to the surface of an adsorbent particle. This process is employed in environmental engineering practice for removal of various pollutants such as soluble organics, dyes, pesticides and humic substances from wastewaters, and for removal of color, taste, and odor-producing compounds from natural waters that are to be used as potable water supplies. Activated carbon is one such adsorbent used in drinking water and wastewater treatment to transfer dissolved species to the solid phase, particularly for the remediation of groundwater contaminated with volatile and nonvolatile organic pollutants (Weber-Shirk, 2019).

Our team is interested in investigating methods to optimize the effectiveness of an adsorption system, in particular how the variation in the way the adsorbent is placed within the column and a change in influent flow rate into the adsorption system affects the effectiveness of the adsorption system in removing a pollutant from the water. This is an interesting problem that has practical applications because our society is constantly faced with the challenge to treat wastewater at a low cost and efficient manner, and activated is not cheap considering that it needs to be continually replaced and that it is not as accessible for treatment plants in developing countries. Higher flow rates allow for more water to be treated at a given time, but this may affect adsorption efficiency. The results of this experiment will enable scientists and engineers to gain a better understanding towards building the most optimal adsorption system for better drinking water and wastewater treatment (Çeçen, 2011).

At any given water and wastewater treatment facility, there is a maximum contaminant level, which operator considers water to be treated at levels lower than the standard. In this experiment, water is considered treated when the concentration of the pollutant in the effluent is less than or equal to 60% of the concentration of the pollutant in the influent, i.e. $\frac{C}{C_0} <= 0.6$.

As our team will vary flow rate across the adsorption column, we are interested in the tradeoff between the amount of water that can be treated given the useful lifespan of the adsorption column decreases with increasing flow rate. This is also synonymous to the amount of water that a factory can bottle and sell until the adsorption column needs to be maintained and replaced. These two factors will directly vary the total amount of water treated and consequently, affect the effectiveness of the adsorption column in treating water.


#### Objectives ####

There are two objectives of this project:
1. Investigate the breakthrough characteristics and equilibrium partitioning of red dye #40 on activated carbon in a continuous flow carbon contactor at a range of different layering patterns given equal proportions of sand and activated carbon by mass in the column.
2. Investigate the relationship between how varying flow rate affects the amount of water that can be “treated” by the adsorption column until the effluent is 60% of the influent concentration.


#### Expectations ####

For the first objective, our hypothesis is that for the same mass of adsorbent, the column with adsorbent mixed throughout the column will be the least effective, while the column with the more layers will be the more effective until those layers become too thin.  In Gritti et. al’s 2004 study titled “Effect of the flow rate on the measurement of adsorption data by dynamic frontal analysis”, it states that as flow rate increases, the mass of dye adsorbed increases (Gritti, 2004). However, for flow rate, we believe that this flow rate should not affect the mass of dye adsorbed. Although there already exists a study on this, we are interested in further investigating this claim as too high of a flow rate may also make it more difficult for dye to attach to the pores in activated carbon, and perhaps even render it useless.

In order to achieve the first objective, the adsorbent will be either mixed or separated into even layers throughout the column and the column will be run with the same flow rate. For the second objective, the layering pattern will be the same in the column but flow rate will be varied. To determine which has the better performance for the first objective, we will plot the breakthrough curves of different experiments, and the relative time it takes for the effluent concentration to be 60% of the influent concentration (Weber-Shirk, “Adsorption”). To determine which has the better performance for the second objective, we will determine the amount of water treated based on the time it takes until the effluent is 60% of the influent concentration. This is dependent on the life of the adsorption column and the amount of pollutant absorbed by the adsorbent at any given time in which that water is considered treated.


#### Resources Needed ####

For simplicity, this experiment will utilize a basic adsorption system. The adsorption system will be built using a peristaltic pump, an adsorption column, #17 tubing, and a photometer. The absorbent of the system is activated carbon. The rest of the adsorption column will be filled with sand. There should be equal mass of activated carbon and sand in the adsorption column. The adsorption system will be set up as shown in Figure 1.

![setup_mixed](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/setup_mixed.png)
Figure 1: Diagram of the experimental setup for the trial with activated carbon mixed throughout the column with sand.

#### Experimental Plan ####

In this experiment, the effectiveness of the adsorption system will be measured in accordance to how clear the water filtered out is and the duration at which the absorbent is able to last. These two factors are important in vital in determining how much pollutant the adsorption system can adsorb with one batch of adsorbent. The concentration of dye in the effluent can be measured using a photometer.

The key design parameters of the experiment is the placement of the adsorbent and the influent flow rate. The experiment would explore the scenarios when the adsorbent is mixed throughout the adsorbent column (Figure 1), and when the adsorbent is separated into 2, 4, 6, 8, and 10 layers (Figure 2). The flow rates that will be experimented on are 10, 20, 40, 60, and 80 rpm with one layer of activated carbon.


![setup_2](https://raw.githubusercontent.com/lw583/CEE4530/master/Project/setup_2.png)
Figure 2: Diagram of the experimental setup for the trial with 2 even layers of activated carbon separated by layers of sand.

#### Timeline ####

##### 04/12 F:
Preparation - Set-up column and calibrate photometer.
Experiment 1 - Control with no AC at 10 rpm.

##### 04/15 M:
Experiment 2 - Thoroughly mixed AC at 10 rpm.

##### 04/17 W:
Experiment 3 - 2 layers of AC at 10 rpm.
Experiment 4 - 4 layers of AC at 10 rpm.

##### 04/19 F:
Experiment 5 - 6 layers of AC at 10 rpm.

##### 04/22 M:
Experiment 6 - 8 layers of AC at 10 rpm.

##### 04/24 W:
Experiment 7 - 10 layers of AC at 10 rpm.
Experiment 8 - 1 layer of AC at 10 rpm.

##### 04/26 F:
Experiment 9 - 1 layer of AC at 20 rpm.

##### 04/29 M:
Experiment 10 - 1 layer of AC at 40 rpm.

##### 05/01 W:
Experiment 11 - 1 layer of AC at 60 rpm.
Experiment 12 - 1 layer of AC at 80 rpm.

##### 05/03 F:
Experiment / Analysis - May have to repeat Experiments 1-10

##### 05/06 M:
Experiment / Analysis - May have to repeat Experiments 1-10


#### Possible Challenges ####

There is a possibility that our experiment will not yield any meaningful results, particularly for the first objective as after discussing with Monroe, his hypothesis is that nothing will change. Hence, we have prepared back-up ideas to alter our experiment as with the second objective. There is also difficulty in ensuring the quality of absorbent used will be exactly the same. Hence, each experiment will have trials to ensure that the result collected is accurate.


#### References ####

Çeçen, F. & Aktaş, Ö. (2011). Activated Carbon for Water and Wastewater Treatment: Integration of Adsorption and Biological Treatment. Retrieved from https://onlinelibrary.wiley.com/doi/book/10.1002/9783527639441

Gritti, F. & Guiochon, G. (2011). Effect of the flow rate on the measurement of adsorption data by dynamic frontal analysis. Retreived from https://www.sciencedirect.com/science/article/pii/S0021967304014888

Weber-Shirk, M. (2019). Adsorption. Retrieved from https://monroews.github.io/EnvEngLabTextbook/Adsorption/Adsorption.html#prelab-questions
