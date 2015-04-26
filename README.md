##Piecewise Smooth image approximation by minimizing the mumford-shah functional with the Ambrosio-Tortorelli approach ##
```python
import cv2
from AmbrosioTortorelliMinimizer import *
```
Use it on a grayscale image:
```python
img = cv2.imread("image.jpg", 0)
solver = AmbrosioTortorelliMinimizer(c, alpha = 1000, beta = 0.01, 
epsilon = 0.01)
image, edges = solver.minimize()
```
Or on a color image:
```python
img = cv2.imread("image.jpg", 1)
result, edges = [], []
for c in cv2.split(img):
	solver = AmbrosioTortorelliMinimizer(c, alpha = 1000, beta = 0.01, 
	epsilon = 0.01)
	
	f, v = solver.minimize()
	result.append(f)
	edges.append(v)

image = cv2.merge(result)
edges = np.maximum(*edges)
```
![enter image description here](https://raw.githubusercontent.com/jacobgil/Ambrosio-Tortorelli-Minimizer/master/images/trees.jpg)![enter image description here](https://raw.githubusercontent.com/jacobgil/Ambrosio-Tortorelli-Minimizer/master/images/trees1000_0.01_0.001_result.jpg)


![enter image description here](https://raw.githubusercontent.com/jacobgil/Ambrosio-Tortorelli-Minimizer/master/images/star.jpg)![enter image description here](https://raw.githubusercontent.com/jacobgil/Ambrosio-Tortorelli-Minimizer/master/images/star100_0.01_0.01_result.jpg)
![enter image description here](https://raw.githubusercontent.com/jacobgil/Ambrosio-Tortorelli-Minimizer/master/images/kitty.jpg)![enter image description here](https://raw.githubusercontent.com/jacobgil/Ambrosio-Tortorelli-Minimizer/master/images/kitty1000_0.01_0.01_result.jpg)
