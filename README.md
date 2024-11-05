# Report-1
In this repository I am going to present the resolution of Report 1 about the estimation of an Ordinary Least Squares (OLS) regression for the module "Programming and Policy Analysis".

In the first section of the notebook, you can upload any database that presents independent variables and dependent variables.

```python
!pip3 install -U ucimlrepo 

from ucimlrepo import fetch_ucirepo 
  
# fetch dataset 
student_performance = fetch_ucirepo(id=320) 
  
# data (as pandas dataframes) 
X = student_performance.data.features 
y = student_performance.data.targets 
  
# metadata 
print(student_performance.metadata) 
  
# variable information 
print(student_performance.variables) 

print(y)
print (X)

```

For the estimation of parameters, in the first step I create a matrix of ones for the constant in the matrix of independent variales.
In the matrix 'independent', you can change the variables that you wish consider as independent variables. It happens the same with the variable independent, for example instead of 'G3' you could consider 'G2' or'G1'.

```python
# Import some libraries for working in a better way

import pandas as pd
import numpy as np


df=pd.DataFrame(X)
dg=pd.DataFrame(y)

# Matrix of independent variables
independent=df[['age','traveltime','studytime','famrel','freetime','absences']].to_numpy()

# Matrix of dependent variable
dependent=dg[['G3']].to_numpy()
```

In the next sections of the notebook you can obtain automatically the standard errors, t-statistics, p-values and R-square.
