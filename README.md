# Thresholding
## Aim
To segment the image using global thresholding, adaptive thresholding and Otsu's thresholding using python and OpenCV.

## Software Required
1. Anaconda - Python 3.7
2. OpenCV

## ALGORITHM:

### Step 1:
Load the necessary packages.

### Step 2:
Read the Image and convert to grayscale.

### Step 3:
Use Global thresholding to segment the image.

### Step 4:
Use Adaptive thresholding to segment the image.

### Step 5:
Use Otsu's method to segment the image.

### Step 6:
Display the results.

## Program
```
# Load the necessary packages
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the Image and convert to grayscale
image=cv2.imread("taiga.jpg",1)
image=cv2.cvtColor(image,cv2.COLOR_BGR2RGB)
image_gray=cv2.imread("taiga.jpg",0)

# Use Global thresholding to segment the image
ret,thresh_white1=cv2.threshold(image_gray,86,255,cv2.THRESH_BINARY)
ret,thresh_white2=cv2.threshold(image_gray,86,255,cv2.THRESH_BINARY_INV)
ret,thresh_white3=cv2.threshold(image_gray,86,255,cv2.THRESH_TOZERO)
ret,thresh_white4=cv2.threshold(image_gray,86,255,cv2.THRESH_TOZERO_INV)
ret,thresh_white5=cv2.threshold(image_gray,100,255,cv2.THRESH_TRUNC)

# Use Otsu's method to segment the image 
ret,thresh_white6=cv2.threshold(image_gray,0,255,cv2.THRESH_BINARY+cv2.THRESH_OTSU)

# Use Adaptive thresholding to segment the image
thresh_white7=cv2.adaptiveThreshold(image_gray,255,cv2.ADAPTIVE_THRESH_MEAN_C,cv2.THRESH_BINARY,11,2)
thresh_white8=cv2.adaptiveThreshold(image_gray,255,cv2.ADAPTIVE_THRESH_GAUSSIAN_C,cv2.THRESH_BINARY,11,2)

# Display the results
titles=["Gray Image","Threshold Image (Binary)","Threshold Image (Binary Inverse)","Threshold Image (To Zero)"
       ,"Threshold Image (To Zero-Inverse)","Threshold Image (Truncate)","Otsu","Adaptive Threshold (Mean)","Adaptive Threshold (Gaussian)"]
images=[image_gray,thresh_white1,thresh_white2,thresh_white3,thresh_white4,thresh_white5,thresh_white6,thresh_white7,thresh_white8]
for i in range(0,9):
    plt.figure(figsize=(10,10))
    plt.subplot(1,2,1)
    plt.title("Original Image")
    plt.imshow(image)
    plt.axis("off")
    plt.subplot(1,2,2)
    plt.title(titles[i])
    plt.imshow(cv2.cvtColor(images[i],cv2.COLOR_BGR2RGB))
    plt.axis("off")
    plt.show()
```

## Output

### Original Image
![image](https://user-images.githubusercontent.com/75234912/169960345-2cc5754e-bf0b-49bd-a015-29dd48569e07.png)

### Global Thresholding
![image](https://user-images.githubusercontent.com/75234912/169960516-f95c5cb1-dd55-4cf7-88da-1797e4a85246.png)
![image](https://user-images.githubusercontent.com/75234912/169960600-6062f527-c56f-497e-85c5-df0597747049.png)


### Adaptive Thresholding
![image](https://user-images.githubusercontent.com/75234912/169960713-ce4681dd-f2d5-4bb9-af57-f1bfb0a8fe90.png)


### Optimum Global Thesholding using Otsu's Method
![image](https://user-images.githubusercontent.com/75234912/169960778-9bc561b8-a0e7-4fcf-b525-c44f2504275c.png)


## Result
Thus the images are segmented using global thresholding, adaptive thresholding and optimum global thresholding using python and OpenCV.

