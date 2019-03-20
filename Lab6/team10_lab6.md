# Prelab 6 for CEE 4530

### Team 10: Victor Khong (1 hours) & Jacqueline Wong (1.5 hours) ###

<b> 1. A carbon column is packed with 15 cm of activated carbon and then used to remove 50 mg/L of red dye #40. The approach velocity is 1 mm/s, the porosity is 0.4, and the bulk density of the activated carbon is 0.5 g/cm3. How long will it take for the mass transfer zone to travel to the bottom of the carbon column? </b>

According to equation (89), the relationship between the velocity in the pores and velocity above the porous fixed bed is:

$$\phi v_{pore} = v_a$$

This can be rearranged to find the velocity in the pores:

$$v_{pore} = \frac{v_a}{\phi}$$

As we know that the length of the column is 15 cm, the time it takes for the water to travel to the bottom of the carbon column can be calculated with the following equation:

$$ t_{water} = \frac{distance}{v_{pore}}$$

From equation (95), the retardation factor is defined as the ratio of the time for the mass transfer zone, $t_{mtz}$ to travel through the bed divided by the time for water to travel through the bed, $t_{water}$:

$$R_{adsorption} = \frac{t_{mtz}}{t_{water}}$$

As we are given $v_{a}$, $\rho_{bulk}$, $\phi$ and $C_0$, the retardation factor can also be calculated from equation (96):

$$R_{adsorption}\cong \frac{v_a q_0 \rho_{bulk \; adsorbent}}{\phi v_a C_0} =\frac{q_0 \rho_{bulk \; adsorbent}}{\phi C_0}$$

Taking this retardation factor, the time it takes for the mass transfer zone to travel to the bottom of the carbon column, $t_{mtz}$ can be calculated from:

$$t_{mtz} = R_{adsorption} \times t_{water}$$

Thus, the time it takes for the mass transfer zone to travel to the bottom of the carbon column, $t_{mtz}$, is about $$33.3 hours$$

```python
from aguaclara.core.units import unit_registry as u

# Question 1
phi = 0.4
vel_a = 1 * u.mm/u.sec
vel_pore = vel_a / phi

dist = 15 * u.cm
t_water = dist / vel_pore

rho_b = 0.5 * u.g/u.cm**3
C_0 = 50 * u.mg/u.L
q_0 = 0.080
R_ads = (q_0 * rho_b)/(phi * C_0)

t_mtz = R_ads * t_water
t_mtz.to(u.hour)

mass_AC = 29.342 * u.g
mass_dye = q_0 * mass_AC
vol_dye = mass_dye * 0.050 * u.g/L
```
