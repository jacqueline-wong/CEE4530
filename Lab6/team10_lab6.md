# Lab 6 for CEE 4530

### Team 10: Victor Khong (1 hours) & Jacqueline Wong (1.5 hours) ###

asdf

```python
from aguaclara.core.units import unit_registry as u

# Prelab 6
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

#
mass_AC = 29.342 * u.g
mass_dye = q_0 * mass_AC
vol_dye = mass_dye * 0.050 * u.g/L
```
