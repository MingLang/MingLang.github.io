---
layout: post
title: Linear regression and polynomial regression with Python and R in Power BI
category: Power BI
tags: [Power Query, Python, R]
--- 

You can run Python scripts or R scripts in Power BI Desktop, which makes running regression models much easier. Here are examples of running regressions in Power BI Desktop.

The functions used are ```Python.Execute("Python script", [dataset=#"Table"])``` and ```R.Execute("R script", [dataset=#"Table"])```

## Linear regression

```python
# 'dataset' holds the input data for this script

import pandas as pd
import statsmodels.api as sm
import numpy as np

X = sm.add_constant(dataset['cbm'])
y = dataset['dwt']

model = sm.OLS(y, X).fit()
intercept = model.params[0]
slope = model.params[1]
data = {'intercept':[intercept], 'slope':[slope]}
df = pd.DataFrame(data)
```

```R
# 'dataset' holds the input data for this script

lm1 = lm(dwt~cbm, dataset)
intercept = lm1$coefficients[1]
slope = lm1$coefficients[2]
df = data.frame(intercept, slope)
```

## Polynomial regression

```python
# 'dataset' holds the input data for this script

import pandas as pd
import numpy as np
from sklearn.preprocessing import PolynomialFeatures
import statsmodels.api as sm

polynomial_features= PolynomialFeatures(degree=2)
y = dataset['dwt']
x = dataset['teu']
x = x[:,np.newaxis]
xp = polynomial_features.fit_transform(x)
model = sm.OLS(y, xp).fit()
intercept = model.params[0]
beta1= model.params[1]
beta2= model.params[2]
data = {'intercept':[intercept], 'x':[beta1], 'x2':[beta2]}
df = pd.DataFrame(data)
```

```R
# 'dataset' holds the input data for this script

lm1 = lm(dwt~teu + I(teu^2), dataset)
intercept = lm1$coefficients[1]
x = lm1$coefficients[2]
x2 = lm1$coefficients[3]
df = data.frame(intercept, x, x2)
```