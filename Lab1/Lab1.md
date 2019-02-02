# Lab 1 for CEE 4530

1. Fill out the attached spreadsheet. Make sure that all calculated values are entered in the spreadsheet as equations. All remaining analysis for the course will be done in Atom using Python!

The attached spreadsheet has been saved and sent as "lab1_data.xlsx".  

2. Create a graph of absorbance vs. concentration of red dye \#40 in Atom/Markdown using the exported data file. Does absorbance increase linearly with concentration of the red dye? Remove data points from the graph that are outside of the linear region.


3. What is the value of the extinction coefficient, ε?


The value of the extinction coefficient, ε is


4. Did you use interpolation or extrapolation to get the concentration of the unknown?
   We used interpolation to get the concentration of the unknown.

5. What measurement controls the accuracy of the density measurement for the NaCl solution?
   The measurement that controls the accuracy of the density measurement for the NaCl solution is the pipette.

6. What density did you expect (see prelab 2)?
   The density that we expected was1038 kg/m^3.

7. Approximately what should the accuracy be for the density measurement?

The accuracy for the density measurement should be approximately

8. Don’t forget to write a brief paragraph on conclusions and on suggestions using Markdown.

```python
Human error
Range of instrument
Air bubbles
```


9. Verify that your report and graphs meet the requirements as outlined on the course website.

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

Figure 1: A graph of varying red dye concentration against absorbance.
