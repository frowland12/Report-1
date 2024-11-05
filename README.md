# Report-1
In this repository I am going to present the resolution of Report 1 about the estimation of an Ordinary Least Squares (OLS) regression for the module "Programming and Policy Analysis".

## How to run the code?

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
In the matrix 'independent', you can change the variables that you wish consider as explonatory variables, for example extraction some variables or adding anothers like 'interntet' or 'romantic'. It happens the same with the variable dependent, for example instead of 'G3' you could consider 'G2' or 'G1'.

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

## Interpretation of the results

In this regression $$\beta_0$$ means that when all the independent variables are $$0$$ (age, traveltime, studytime, freetime and abscences), the value of $$G3$$ will be $$15.3557$$. $$\beta_1$$ means that if a student is aged with one additional year, the score of $$G3$$ will change $$-0.2462774$$, mantaining all the anothers independent variables constants. $$\beta_2$$ means that if a student has an additional minute in his travel from home to school, the score of $$G3$$ will change $$-0.4708$$, mantaining all the anothers independent variables constants.
The standard errors are relatively low, therefore the estimations of $$\beta$$ are relatively confident (the highest value is the standar error of $$\beta_0$$). The aforementioned will impacti directly in t-stattistics because lower standard errors will cause higher t-stattics, therefore are significative different to 0. This will lead to lower p-values ($$p<0.05$$), so the estimation of coefficients are statisticaly significatives.
Finally, $$R^2$$ is the percentage of variability of dependent variable that could be explained by the independent variables. In this case I have a $$R^2=0.1042$$ , therefore a $$10.42 %$$ of dependent variable could be explained with this fit, which is a bit low.

## Challenges and interesting observations



