# hurst
### Hurst exponent evaluation and R/S-analysis

This is a small python-module for analysing __random walks__ and evaluating the __Hurst exponent (H)__.

H = 0.5 — random data.  
0.5 < H < 1.0 — persistent behavior.  
0 < H < 0.5 — anti-persistent behavior.  

### Usage
```python
import matplotlib.pyplot as plt
import numpy as np
import matplotplotlib.pyplot as plt
from hurst import compute_Hc, random_walk

#  Use random_walk() function or generate random walk series manually:
series = np.empty(shape=(99999,))  # create an empty array
series[0] = 0.  # initialize the first element with some value
for i in range(1,len(series)):
    series[i] = series[i-1] + np.random.randn()

#  Evaluate Hurst equation
H, c, data = hurst.compute_Hc(series)

#  Plot
f, ax = plt.subplots()
ax.plot(data[0], c*data[0]**H, color="deepskyblue")
ax.scatter(data[0], data[1], color="purple")
ax.set_xscale('log')
ax.set_yscale('log')
ax.set_xlabel('Time interval')
ax.set_ylabel('R/S ratio')
ax.grid(True)
plt.show()

print("H={:.4f}, c={:.4f}".format(H,c))
```


![R/S analysis](examples/regression.png?raw=true "R/S analysis")

```H=0.4964, c=1.4877```

### Brownian motion, persistent and antipersistent random walks
You can generate random walks with `random_walk()` function as following:

#### Brownian ####
```brownian = random_walk(99999, proba=0.5)```


![Brownian motion](examples/Brownian_motion.png?raw=true "Brownian motion")

#### Persistent ####
```persistent = random_walk(99999, proba=0.7)```


![Persistent random walk](examples/Persistent.png?raw=true "Persistent random walk")

#### Antipersistent ####
```antipersistent = random_walk(99999, proba=0.3)```


![Antipersistent random walk](examples/Antipersistent.png?raw=true "Antipersistent random walk")
