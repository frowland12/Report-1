# Report-1
In this repository I am going to present the resolution of Report 1 about the estimation of an Ordinary Least Squares (OLS) regression for the module "Programming and Policy Analysis".

## How to run the code?

In the first section of the notebook, you can upload any database that presents independent variables and dependent variables.

```python
%pip install pandas openpyxl

import pandas as pd

RFM_df = pd.read_excel('C:/Users/FRowland/Desktop/JN/student-mat.xlsx')
RFM_df.head()

```

For the estimation of parameters, in the first step I create a matrix of ones for the constant in the matrix of independent variales.
In the matrix 'independent', you can change the variables that you wish consider as explonatory variables, for example extraction some variables or adding anothers like 'interntet' or 'romantic'. It happens the same with the variable dependent, for example instead of 'G3' you could consider 'G2' or 'G1'.

```python
# Import some libraries for working in a better way

import pandas as pd
import numpy as np

# Matrix of dependent variable
dg=pd.DataFrame(RFM_df)
dependent=dg[['G3']].to_numpy()

# Matrix of independent variables
independent=dg[['age','traveltime','studytime','famrel','freetime','absences']].to_numpy()
```

In the next sections of the notebook you can obtain automatically the standard errors, t-statistics, p-values and R-square.

## Interpretation of the results

In this regression $$\beta_0$$ means that when all the independent variables are $$0$$ (age, traveltime, studytime, freetime and abscences), the value of $$G3$$ will be $$18.8248$$. $$\beta_1$$ means that if a student is aged with one additional year, the score of $$G3$$ will change $$-0.6126$$, mantaining all the anothers independent variables constants. $$\beta_2$$ means that if a student has an additional minute in his travel from home to school, the score of $$G3$$ will change $$-0.6138$$, mantaining all the anothers independent variables constants.
The standard errors are relatively low, therefore the estimations of $$\beta$$ are relatively confident (the highest value is the standar error of $$\beta_0$$). The aforementioned will impact directly in t-stattistics because lower standard errors will cause higher t-stattics, therefore are significatively different to 0. This will lead to lower p-values ($$p<0.05$$), so the estimation of coefficients are statisticaly significatives.
Finally, $$R^2$$ is the percentage of variability of dependent variable that could be explained by the independent variables. In this case I have a $$R^2=0.0532$$ , therefore a $$5.32$$\% of dependent variable could be explained with this fit, which is a bit low.

## Challenges and interesting observations

My main difficulties in solving this report is using Python without libraries. I think it could be interesting to calculate the estimation of coefficients, standard errors, t-statistics, p-values and $$R^2$$ only using some loops with for or while, but I have some troubles with those codes. By contrast, I think it would be less efficient to use loops for writing this code.

## Testing output with Stata

For obtaining the same results in Stata, first you should import the database from Excel:

```stata
import excel "C:\Users\FRowland\Desktop\JN\student-mat.xlsx", sheet("Hoja1") firstrow
```

Next, you should run the regression with the code:

```stata
regress G3 age traveltime studytime famrel freetime absences
```


