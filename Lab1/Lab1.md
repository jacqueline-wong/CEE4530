# Lab 1 for CEE 4530

<b> 1. Fill out the attached spreadsheet. Make sure that all calculated values are entered in the spreadsheet as equations. All remaining analysis for the course will be done in Atom using Python! </b>

The attached spreadsheet has been saved and sent as "lab1_data.xlsx".  

<b> 2. Create a graph of absorbance vs. concentration of red dye \#40 in Atom/Markdown using the exported data file. Does absorbance increase linearly with concentration of the red dye? Remove data points from the graph that are outside of the linear region. </b>

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

![linear](https://raw.githubusercontent.com/lw583/CEE4530/master/absorbance.png)

Figure 1: A graph of varying red dye concentration (from 0 to 20 mg/L) against absorbance.


From 0 to 2 mg/L, the absorbance of red dye does not increase linearly, likely due to the these points being under the detection limit of the instrument. From 2 mg/L to 20 mg/L, there appears to be a linear relationship between absorbance and concentration. However, at concentrations higher than 20 mg/L (not graphed), this linear relationship no longer exists, likely due to these points being out of the instrument's measurement range.


<b> 3. What is the value of the extinction coefficient, ε? </b>
The value of the extinction coefficient, ε is


<b> 4. Did you use interpolation or extrapolation to get the concentration of the unknown? </b>
   We used interpolation to get the concentration of the unknown.

<b> 5. What measurement controls the accuracy of the density measurement for the NaCl solution? </b>
   The measurement that controls the accuracy of the density measurement for the NaCl solution is the pipette. The electronic balance has an uncertainty of 0.001 g, the volumetric flask has a

<b> 6. What density did you expect (see prelab 1)? </b>
   The density that we expected was 1038 kg/m<sup>3</sup>.

<b> 7. Approximately what should the accuracy be for the density measurement? </b>

The accuracy for the density measurement should be approximately

(theoretical-experiment/theoretical)

<b> 8. Don’t forget to write a brief paragraph on conclusions and on suggestions using Markdown. </b>


```python
Human error
Range of instrument
Air bubbles
```

<b> 9. Verify that your report and graphs meet the requirements as outlined on the course website. </b>
