# Lab 1 for CEE 4530

1. Fill out the attached spreadsheet. Make sure that all calculated values are entered in the spreadsheet as equations. All remaining analysis for the course will be done in Atom using Python!

2. Create a graph of absorbance vs. concentration of red dye \#40 in Atom/Markdown using the exported data file. Does absorbance increase linearly with concentration of the red dye? Remove data points from the graph that are outside of the linear region.

```python
  # Find a set of data that includes units (or make one up!) that could reasonably be fit with linear regression.
  # Save the data to a tab delimited file in your atom project workspace.
  # Load the data from the file into a Pandas dataframe.
  from aguaclara.core.units import unit_registry as u
  import numpy as np
  import matplotlib.pyplot as plt
  import pandas as pd
  from scipy import stats

  dframe = pd.read_csv("lab1_data.xlsx",delimiter='\t')

  # Plot the data and the linear regression line.
  # Make sure to handle units carefully and to attach units to the linear regression line.
  C = dframe.iloc[:,0].values * u.mg/u.L
  A = dframe.iloc[:,1].values

  slope, intercept, r_value, p_value, std_err = stats.linregress(C,A)
  intercept = intercept * A.units
  slope = slope * A.units/C.units

  fig, ax = plt.subplots()
  ax.plot(C, A, 'bo', )
  ax.plot(C, slope * C + intercept, 'k-', )
  ax.set(xlabel=list(dframe)[0])
  ax.set(ylabel=list(dframe)[1])
  ax.legend(['Measured', 'Linear regression'])
  ax.grid(True)

  plt.savefig('linear.png')
  plt.show()

  # Add a figure in Markdown showing the graph you produced.
  # Show the linear regression equation that you obtained using latex.
  print(slope)
  print(intercept)
```

![linear](https://github.com/lw583/CEE4530/blob/master/turbidity.png?raw=true)

Figure 1: A graph of varying aluminium sulfate concentration against turbidity.
