[[Matplotlib]]
#**Difference between `scatter` and `plot` in Matplotlib**

## ✅ **1. `plt.scatter()` — draws individual POINTS**

- Shows each (x, y) as a **dot/marker**
    
- No line connecting them
    
- Good for **datasets**, **clusters**, **classification points**, etc.
    

Example:

`plt.scatter(x, y)`

Result:  
🔵🔵🔵 points everywhere, not connected.

---

## ✅ **2. `plt.plot()` — draws a LINE (and optionally markers)**

- Connects the points in the given order
    
- Good for **curves**, **functions**, **trends**, **time series**
    

Example:

`plt.plot(x, y)`

Result:  
A continuous line through the points.

---

# 🔥 Quick visual examples

### Scatter:

`plt.scatter(x, y)`

### Plot:

`plt.plot(x, y)`

### If you want plot to look like scatter:

`plt.plot(x, y, 'o')     # markers only, no line`

### If you want scatter + line:

`plt.plot(x, y) plt.scatter(x, y)`