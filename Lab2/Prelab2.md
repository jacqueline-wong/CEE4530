# Prelab 2 for CEE 4530

<b> 1. How many grams of NaHCO3 would be required to keep the ANC levels in a lake above 50 μeq/L for 3 hydraulic residence times given an influent pH of 3.0 and a lake volume of 4 L, if the current lake ANC is 0 μeq/L?</b>

Since volume is fixed, 3 hydraulic residence time is given as:

$$ 3\theta = \frac{V}{\frac{1}{3}Q}$$

Assuming that the lake is well mixed, the mass balance in the lake is given as:

$$ Q\left(ANC_{in}  - ANC_{out} \right) =  \rlap{-} V \frac{d(ANC)}{dt} $$

The influent pH of 3.0 can be converted into equivalence.

$$ANC_{in} = -\left[H^+ \right] = -0.001 eq/L$$

The solution to the mass balance differential equation is:

$$ANC_{out} \; =\; ANC_{in} \; \cdot \; \left(1\; -\; {\mathop{e}\nolimits^{-t/\theta \; \; }} \right)+\; ANC_{0} \; \cdot \; {\mathop{e}\nolimits^{-t/\theta \; }}$$

$$0.000050 \; =\; -0.001 \; \cdot \; \left(1\; -\; {\mathop{e}\nolimits^{-t/\theta \; \; }} \right)+\; 0 \; \cdot \; {\mathop{e}\nolimits^{-t/\theta \; }}$$

_____


$$ ANC = \frac{{(equivalent\; vol.)(normality\; of\; titrant)}}{{(vol.\; of\; sample)}} $$

$$ 50 \text{ µeq/L}= \frac{{(equivalent\; vol.)(normality\; of\; titrant)}}{{4\text { L}}} $$






$$ {ANC}_{{0}} {\; }=\left[{ANC}_{out} - ANC_{in} \cdot \left(1 - {\mathop{e}\nolimits^{-t/\theta}} \right)\right]{\mathop{e}\nolimits^{t/\theta}}$$

$$ {ANC}\cong -\left[{H}^{+} \right] $$




Substituting into equation :eq:`eq_ANC0_CMFR`:

$$ {ANC}_{{0}} {\; }=\left[{0.000050}+{0.001\; }\cdot \left(1\; -\; {\mathop{e}\nolimits^{-1}} \right)\right]{\mathop{e}\nolimits^{1}} = 1.854 meq/L $$

$$ [\text{NaHCO}_3]_{0} = ANC_{0} $$

$$ \frac{{1.854\; \text{m mol}\; NaHCO}_3 }{\text{L}} {\times }\frac{{84.007\; \text{mg}\; NaHCO}_3 }{{\text{m mol}\; NaHCO}_3 } {\times \; 4\; \text{L}\; =\; 623\; \text{mg\; NaHCO}_3} $$
