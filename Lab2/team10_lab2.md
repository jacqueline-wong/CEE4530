# Lab 2 for CEE 4530

Do we know the ANC of the samples? Use CMFR equation

- Graph should go to -0.001
- Should delete comments in data file for lab

<b> 1. How many grams of NaHCO3 would be required to keep the ANC levels in a lake above 50 μeq/L for 3 hydraulic residence times given an influent pH of 3.0 and a lake volume of 4 L, if the current lake ANC is 0 μeq/L?</b>

Assuming that the lake is well mixed, the mass balance in the lake is given as:

$$ Q\left(ANC_{in}  - ANC_{out} \right) =  \rlap{-} V \frac{d(ANC)}{dt} $$

The Acid Neutralizing Capacity of the lake influent can be estimated from pH because it is below 4.3. Thus, an influent of pH 3.0 can be converted into:

$$ANC_{in} = -\left[H^+ \right] = -0.001 \text{ eq/L}$$

The solution to the mass balance differential equation for a well-mixed lake is:

$$ANC_{out} = ANC_{in} \cdot \left(1 - {\mathop{e}\nolimits^{-t/\theta\;}} \right)+ ANC_{0} \cdot {\mathop{e}\nolimits^{-t/\theta}}$$

For 3 hydraulic residence times:

$$0.000050 \text{ eq/L} = -0.001 \text{ eq/L} \cdot \left(1 - {\mathop{e}\nolimits^{-3}} \right)+ ANC_{0} \cdot {\mathop{e}\nolimits^{-3}}$$

Rearranging the equation and solving for $ANC_{0}$, we get:

$$ {ANC}_{{0}} =\left[{0.000050}+{0.001}\cdot \left(1-{\mathop{e}\nolimits^{-3}} \right)\right]{\mathop{e}\nolimits^{3}} =  0.02009 \text{ eq/L} $$

The quantity of sodium bicarbonate required can be calculated from:

$$ [\text{NaHCO}_3]_{0} = ANC_{0} $$

$$ \frac{{0.02009 \text{ mol}\; NaHCO}_3 }{\text{L}} {\times }\frac{{84\; \text{g}\; NaHCO}_3 }{{\text{ mol}\; NaHCO}_3 } {\times \; 4\; \text{L}\; =\; 6.75 \; \text{g\; NaHCO}_3} $$
