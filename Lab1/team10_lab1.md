# Lab 1 for CEE 4530

## Introduction ##
Our client, Dr. Monroe Weber-Shirk and Jonathan Harris, are expert food scientists who are concerned that our daily diet contains too much additives, particularly the unnecessary use of dye for aesthetic appeal. Whilst dye is generally considered a safe substance to be used in food, overconsumption may lead to certain health problems such as bladder tumors. Children are particularly vulnerable to the detrimental health effects posed by dye. In particular, some brands of fruit punch and strawberry jello, two popular children’s snacks, can contain large amounts of red dye. Hence, the current situation with food dye and human health is very concerning to our client.

Our client has presented our research laboratory with a sample of distilled water that contains the same amount of red dye as one of the most popular fruit punches on the market. Our task is to measure the concentration of red dye in the solution, which will be a first step in supporting their investigations on food dye levels in popular food and beverage items.

Given the properties of the red dye, absorption spectroscopy presented itself as one of the best analytical technique that can be used to accurately determine the concentration of a compound. The theory behind it is that colored solutions absorb light in the visible range and the resulting color of the solution is the spectrum of light that is not absorbed, but transmitted. According to Beer’s law, the attenuation of light in a chemical solution is proportional to the concentration and the length of the path that the light passes through:

$$ A =  εbc $$

where A is absorbance, ε is the extinction coefficient, b is the path length, and c is the concentration of the solution.

Another concern that our client had was how the effects of the dye on a person varied based on the salt concentration in the drink. The addition of salt increases the electrolyte in drinks and the interactions between electrolytes and dye has not been thoroughly investigated. Our client would like to perform experiment on it and has requested our research laboratory to prepare salt solution of a $ 1M \ NaCl $ solution, as well as determine some of its properties such as density.

#### Objectives ####
Our client has presented us with two sets of objectives:
$\bullet$ Investigate the concentration of dye in given solution
$\bullet$ Prepare a $ 1M \ NaCl $ solution


## Procedures ##
<b>Investigate the concentration of dye in given solution</b>
First, we prepared 0, 1, 2, 5, 10, 20, 50, 100 and 200 mg/L standards of red dye in distilled water. Each standard was created in a 100 mL volumetric flask, with red dye measured using a 10-100 µL pipette. The absorbance of each standard was measured with a photometer in order of increasing concentration as voltages, which were later converted to .

Plotted to determine the effective range of absorbance measurements of the photometer instrument.

<b>Prepare a $ 1M \ NaCl $ solution</b>
First,


## Results ##

The photometer has a limited range of absorbance that can be detected. Based on the relationship between absorption and concentration as stated in Beer's law, this range falls between 0 to 20 mg/L as a linear relationship was observed between concentration and absorbance.

From 0 to 2 mg/L, the absorbance of red dye does not increase linearly, likely due to the these points being under the detection limit of the instrument. From 2 mg/L to 20 mg/L, there appears to be a linear relationship between absorbance and concentration (Figure 1). However, at concentrations higher than 20 mg/L (not graphed), this linear relationship no longer exists, likely due to these points being out of the instrument's measurement range. All supporting data has been included in a spreadsheet named "datasheet.xlsx".

```python
  from aguaclara.core.units import unit_registry as u
  import numpy as np
  import matplotlib.pyplot as plt
  import pandas as pd
  from scipy import stats

  data_file_path = "https://raw.githubusercontent.com/lw583/CEE4530/master/Lab1/absorbance.txt"
  dframe = pd.read_csv(data_file_path,delimiter='\t')

  C = dframe.iloc[:,0].values * u.mg/u.L
  A = dframe.iloc[:,1].values

  slope, intercept, r_value, p_value, std_err = stats.linregress(C,A)
  intercept = intercept
  slope = slope * 1/C.units

  fig, ax = plt.subplots()
  ax.plot(C, A, 'bo', )
  ax.plot(C, slope * C + intercept, 'k-', )
  ax.set(xlabel=list(dframe)[0])
  ax.set(ylabel=list(dframe)[1])
  ax.legend(['Measured', 'Linear regression'])
  ax.grid(True)

  plt.savefig('absorbance.png')
  plt.show()
```

![linear](https://github.com/lw583/CEE4530/blob/master/absorbance.png?raw=true)

Figure 1: A graph of absorbance against red dye concentration. There appears to be a linear relationship between 0 to 20 mg/L that follows Beer's law:

$$ A = εbc $$

Here, $A$ is absorbance, $b$ is path length and $c$ is concentration. $εb$ is the slope of the linear regression in our graph. This is based on the assumption that our linear regression line has an intercept of zero (it is not, but is very close to it). The path length $b$ of the particular instrument used is 19 mm.

In this particular experiment, the absorbance of the unknown solution presented by our clients fell within this range. Thus, we were able to use Beer's law (below) to interpolate a concentration from the unknown solutions's measured absorbance.

```python
b = 19 * u.mm
ε = slope / b
print(ε)
```

The value of the extinction coefficient, $ε$ is -0.00342 L mg<sup>-1</sup> mm<sup>-1</sup>. Given that the unknown solution had an absorbance of -0.670, Beer's law can be rearranged to find its actual concentration.

```python
A = -0.670
c_B = A / (ε*b)
print(c_B)
```

Using Beer's law, the concentration of the unknown solution is around 10.32 mg/L. However, considering that the intercept was not at exactly zero, the linear regression should provide a better result.

```python
c_L = (A - intercept)/ slope
print(c_L)
```

...

```python
actual = 1038.72 * u.m**3
exp = 1038.26 * u.m**3
error = (actual-exp)/actual
accuracy = 100 * (1 - error)
```

Based on the equation, ...

the density that we expected was 1038.72 kg/m<sup>3</sup>. As the density of our solution was 1038.26 kg/m<sup>3</sup>, the accuracy of our measurement is approximately 99.96%.

## Discussion ##

While the laboratory technicians have been well trained to conduct the above procedure, there was still the possibility of error. In terms of instrumental error, ...

The measurement that controls the accuracy of the density measurement for the NaCl solution is the 10-100µL pipette, which has the highest uncertainty amongst the instruments used at 0.8%. The electronic balance has an uncertainty of 0.001 g (~0.017%), the volumetric flask has an uncertainty of 0.16 mL (0.16%).

While experimental accuracy for creating a salt solution was quite high at 99.96%, it is not at 100%. This may be because not every single salt granule weighed may have ended up inside our solution. While the laboratory technicians did their best to transfer all the salt granules into the distilled water, a few may have been left behind on our plastic weighing boat. This error was difficult to tell because the standard weighing boat is white in color. This could be avoided with a different colored boat, but the difference is quite negligible in this case.

Additionally, there was the possibility of having air bubbles inside the photometer, which would affect absorbance measurements. To prevent this, the laboratory technicians made sure to tap the instrument repeatedly to ensure that air bubbles have escaped, and only record when readings have been stabilized.
