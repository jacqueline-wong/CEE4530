# Lab 1 for CEE 4530
#### Victor Khong and Jacqueline Wong ####

<b> 1. Fill out the attached spreadsheet. Make sure that all calculated values are entered in the spreadsheet as equations. All remaining analysis for the course will be done in Atom using Python! </b>

All supporting data has been included in a spreadsheet named "datasheet.xlsx".

<b> 2. Create a graph of absorbance vs. concentration of red dye \#40 in Atom/Markdown using the exported data file. Does absorbance increase linearly with concentration of the red dye? Remove data points from the graph that are outside of the linear region.</b>

<b> Insert scatter plot then justify reasoning for deleting points </b>

Figure 1: A graph of absorbance against red dye concentration.

```python
  from aguaclara.core.units import unit_registry as u
  import numpy as np
  import matplotlib.pyplot as plt
  import pandas as pd
  from scipy import stats

  dfp = "https://raw.githubusercontent.com/lw583/CEE4530/master/Lab1/scatter.txt"
  df = pd.read_csv(dfp,delimiter='\t')

  c = dframe.iloc[:,0].values * u.mg/u.L
  a = dframe.iloc[:,1].values

  slope, intercept, r_value, p_value, std_err = stats.linregress(c,a)
  intercept = intercept
  slope = slope * 1/C.units

  fig, ax = plt.subplots()
  ax.plot(C, A, 'bo', )
  ax.set(xlabel=list(dframe)[0])
  ax.set(ylabel=list(dframe)[1])
  ax.legend(['Measured', 'Linear regression'])
  ax.grid(True)

  plt.savefig('scatter.png')
  plt.show()
```

![linear](https://github.com/lw583/CEE4530/blob/master/scatter.png?raw=true)

```python  
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

Figure 2: A graph of absorbance against red dye concentration for concentration ranging from 0 mg/L to 20 mg/L. There appears to be a linear relationship between 0 to 20 mg/L that follows Beer's law.

The photometer has a limited range of absorbance that can be detected. From 0 to 2 mg/L, the absorbance of red dye does not increase linearly, likely due to the these points being under the detection limit of the instrument. From 2 mg/L to 20 mg/L, there appears to be a linear relationship between absorbance and concentration (Figure 1). However, at concentrations higher than 20 mg/L (not graphed), this linear relationship no longer exists, likely due to these points being out of the instrument's measurement range.

<b> 3. What is the value of the extinction coefficient, ε?</b>

```python
b = 19 * u.mm
ε = slope / b
print(ε)
```
The extinction coefficient $ε$ is -0.00342 L mg<sup>-1</sup> mL <sup>-1</sup>.

<b> 4. Did you use interpolation or extrapolation to get the concentration of the unknown?</b>

We used interpolation to get the unknown concentration as it fell within the range that the photometer could measure (i.e. its absorbance fell within the points that had an observed linear relationship).

```python
c_L = (A - intercept)/ slope
print(c_L)
```

Thus, the concentration of the unknown solution is about 11.15 mg/L.

<b> 5. What measurement controls the accuracy of the density measurement for the NaCl solution? </b>

The measurement that controls the accuracy of the density measurement for the NaCl solution is the 10-100µL pipette, which has the highest uncertainty amongst the instruments used at 0.8%. The electronic balance has an uncertainty of 0.001 g (~0.017%), the volumetric flask has an uncertainty of 0.16 mL (0.16%).

<b> 6. What density did you expect (see prelab 2)?</b>

The density that we expected was 1038.72 kg/m<sup>3</sup>

<b> 7. Approximately what should the accuracy be for the density measurement?</b>

```python
actual = 1038.72 * u.m**3
exp = 1038.26 * u.m**3
error = (actual-exp)/actual
accuracy = 100 * (1 - error)
```

The density that we expected was 1038.72 kg/m<sup>3</sup>. As the density of our solution was 1038.26 kg/m<sup>3</sup>, the accuracy of our measurement is approximately 99.96%.

<b> 8. Don’t forget to write a brief paragraph on conclusions and on suggestions using Markdown.</b>

In conclusion, a linear decreasing relationship was found between absorbance and concentration of solution for solutions with concentration in the range of 0$\frac{mg}{L}$ to 20 $\frac{mg}{L}$. The concentration of the unknown solution is found to be 11.15 $\frac{mg}{L}$. The density of the $1M$ salt solution created was 1038.26 kg/m<sup>3</sup>.

While the instruments are of high accuracy and precision, and we followed the procedure carefully, there was still the possibility of human error in this experiment.

The experimental accuracy for creating a salt solution was quite high at 99.96%, it is not at 100%. This may be because not every single salt granule weighed may have ended up inside our solution. While we did our best to transfer all the salt granules into the distilled water, a few may have been left behind on our plastic weighing boat. This error was difficult to tell because the standard weighing boat is white in color. This could be avoided with a different colored boat, but the difference is quite negligible in this case.

Additionally, there was the possibility of having air bubbles inside the photometer, which would affect absorbance measurements. To prevent this, the we made sure to tap the instrument repeatedly to ensure that air bubbles have escaped, and only record when readings have been stabilized.

Overall, the experiment went quite well and the results obtained were fairly accurate.

<b> 9. Verify that your report and graphs meet the requirements as outlined on the course website.</b>

...

the density that we expected was 1038.72 kg/m<sup>3</sup>. As the density of our solution was 1038.26 kg/m<sup>3</sup>, the accuracy of our measurement is approximately 99.96%.
