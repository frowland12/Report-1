# Report-1
In this repository I am going to present the resolution of Report 1 about the estimation of an Ordinary Least Squares (OLS) regression for the module "Programming and Policy Analysis".

In the first section of the notebook, you can upload any database that presents independent variables and dependent variables.

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
