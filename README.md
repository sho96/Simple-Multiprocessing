# Pythonic multiprocessing
Multiprocessing without \_\_name\_\_ == "\_\_main\_\_"
# How to use
## Basics
* Import mp.py file into your script by
```python
import mp
```
* Defile a function you want to run with multiple CPU cores <br>
Example: 
```python
def function(x, y):
    a = 0
    for i in range(x):
        a += i
    return a + y
```
* Run the function using mp.process
```python
results = mp.process(
    function, 
    [(100, 200), (200, 300), (300, 400)]
)
print(results)
```

## Using other libraries with functions on mp.process()
* Calling mp.importLibraries anywhere before mp.process()
```python
mp.importLibraries(__file__)
```

This will import all libraries imported to the running script for the functions that will be run with mp.process() <br>
Notice: However, importing unnecessary libraries can lead to increasing RAM usage
* Specifying 'imports' argunment for mp.process()
```python
results = mp.process(
    processImg, 
    [(100, 200), (200, 300), (300, 400)],
    imports="""
    import numpy as np
    import cv2
    """
)
print(results)
```
With this approach, you can prevent the imports of unnecessary libraries for running the provided functions.<br>
Thus, preventing the increase of RAM usage at the cost of writing a bit more code