# Edge-Linking-using-Hough-Transformm
## Aim:
To write a Python program to detect the lines using Hough Transform.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:

Import all the necessary modules for the program.
### Step2:

Load a image using imread() from cv2 module.
### Step3:

Convert the image to grayscale.
### Step4:

Using Canny operator from cv2,detect the edges of the image.
### Step5:

Using the HoughLinesP(),detect line co-ordinates for every points in the images.Using For loop,draw the lines on the found co-ordinates.Display the image.
## Program
```py
import numpy as np
import cv2
import matplotlib.pyplot as plt

# READ THE IMAGE IN COLOR
img_c = cv2.imread("sevenwonder.jpg")
# CONVERT THE COLOR FROM BGR TO RGB
img_c = cv2.cvtColor(img_c, cv2.COLOR_BGR2RGB)
# CONVERT THE COLOR IMAGE TO GRAYSCALE
gray = cv2.cvtColor(img_c, cv2.COLOR_RGB2GRAY)
# APPLY GAUSSIAN BLUR TO REDUCE NOISE
gray = cv2.GaussianBlur(gray, (3, 3), 0)
```
```py
# DISPLAY ORIGINAL AND GRAY IMAGES
plt.figure(figsize=(8, 8))
plt.subplot(1, 2, 1)
plt.imshow(img_c)
plt.title("Original Image")
plt.axis("off")
plt.subplot(1, 2, 2)
plt.imshow(gray, cmap='gray')
plt.title("Gray Image")
plt.axis("off")
plt.show()
```
```py
# CANNY EDGE DETECTION
canny = cv2.Canny(gray, 120, 150)

# DISPLAY THE CANNY IMAGE
plt.figure(figsize=(5, 8))
plt.imshow(canny, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis("off")
plt.show()
```
```py
# HOUGH LINE TRANSFORM
lines = cv2.HoughLinesP(canny, 1, np.pi / 180, threshold=80, minLineLength=50, maxLineGap=250)

# DRAW THE DETECTED LINES ON THE ORIGINAL IMAGE
for line in lines:
    x1, y1, x2, y2 = line[0]
    cv2.line(img_c, (x1, y1), (x2, y2), (255, 0, 0), 3)  # Red color lines

```
```py
# DISPLAY THE RESULT IMAGE WITH LINES
plt.figure(figsize=(5, 8))
plt.imshow(img_c)
plt.title("Result Image")
plt.axis("off")
plt.show()
```
## Output

### Input image and grayscale image
<img width="770" height="282" alt="image" src="https://github.com/user-attachments/assets/3284a9a0-3173-4f47-8feb-fb130893b04a" />


### Canny Edge detector output
<img width="468" height="366" alt="image" src="https://github.com/user-attachments/assets/e2e9c5b1-cec0-41ab-8c8c-8214846917d9" />


### Display the result of Hough transform
<img width="502" height="361" alt="image" src="https://github.com/user-attachments/assets/9a97717f-0563-4ea8-a221-d52e8a568fec" />


## Result
The final result will be your original image with detected straight lines overlaid in red.
