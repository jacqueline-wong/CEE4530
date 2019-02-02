# Lab 1 for CEE 4530

```python
  # Find a set of data that includes units (or make one up!) that could reasonably be fit with linear regression.
  # Save the data to a tab delimited file in your atom project workspace.
  # Load the data from the file into a Pandas dataframe.
  from aguaclara.core.units import unit_registry as u
  import numpy as np
  import matplotlib.pyplot as plt
  import pandas as pd
  from scipy import stats
  data_file_path = "https://raw.githubusercontent.com/lw583/CEE4530/master/turbidity.txt"
  dframe = pd.read_csv(data_file_path,delimiter='\t')

  # Plot the data and the linear regression line.
  # Make sure to handle units carefully and to attach units to the linear regression line.
  C = dframe.iloc[:,0].values * u.mg/u.L
  T = dframe.iloc[:,1].values * u.NTU

  slope, intercept, r_value, p_value, std_err = stats.linregress(C,T)
  intercept = intercept * T.units
  slope = slope * T.units/C.units

  fig, ax = plt.subplots()
  ax.plot(C, T, 'bo', )
  ax.plot(C, slope * C + intercept, 'k-', )
  ax.set(xlabel=list(dframe)[0])
  ax.set(ylabel=list(dframe)[1])
  ax.legend(['Measured', 'Linear regression'])
  ax.grid(True)

  plt.savefig('turbidity.png')
  plt.show()

  # Add a figure in Markdown showing the graph you produced.
  # Show the linear regression equation that you obtained using latex.
  print(slope)
  print(intercept)
```

![linear](https://github.com/lw583/CEE4530/blob/master/turbidity.png?raw=true)

Figure 1: A graph of varying aluminium sulfate concentration against turbidity.

$$T = 15.72 \frac{\text {NTU  L}}{\text {mg}} \times C - 1.188 \text{ NTU} $$
