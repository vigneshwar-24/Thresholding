# Thresholding
## AIM:
To segment the image using global thresholding, adaptive thresholding and Otsu's thresholding using python and OpenCV.

## SOFTWARE REQUIRED:
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

## PROGRAM:
```python
# Load the necessary packages
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the Image and convert to grayscale
image=cv2.imread("images.jpg")
plt.imshow(image)
plt.title('original image')
plt.axis('off')
gray_img=cv2.cvtColor(image,cv2.COLOR_BGR2GRAY)
plt.imshow(gray_img,'gray')
plt.title('Gray image')
plt.axis('off')

# Use Global thresholding to segment the image
ret,thresh_img1=cv2.threshold(gray_img,86,255,cv2.THRESH_BINARY)
ret,thresh_img2=cv2.threshold(gray_img,86,255,cv2.THRESH_BINARY_INV)
ret,thresh_img3=cv2.threshold(gray_img,86,255,cv2.THRESH_TOZERO)
ret,thresh_img4=cv2.threshold(gray_img,86,255,cv2.THRESH_TOZERO_INV)
ret,thresh_img5=cv2.threshold(gray_img,100,255,cv2.THRESH_TRUNC)

# Use Adaptive thresholding to segment the image
thresh_img7=cv2.adaptiveThreshold(gray_img,255,cv2.ADAPTIVE_THRESH_MEAN_C,cv2.THRESH_BINARY,11,2)
thresh_img8=cv2.adaptiveThreshold(gray_img,255,cv2.ADAPTIVE_THRESH_GAUSSIAN_C,cv2.THRESH_BINARY,11,2)

# Use Otsu's method to segment the image 
ret,thresh_img6=cv2.threshold(gray_img,0,255,cv2.THRESH_BINARY+cv2.THRESH_OTSU)

# Display the results
titles=["Gray Image","Threshold Image (Binary)","Threshold Image (Binary Inverse)","Threshold Image (To Zero)"
       ,"Threshold Image (To Zero-Inverse)","Threshold Image (Truncate)","Otsu","Adaptive Threshold (Mean)","Adaptive Threshold (Gaussian)"]
images=[gray_img,thresh_img1,thresh_img2,thresh_img3,thresh_img4,thresh_img5,thresh_img6,thresh_img7,thresh_img8]

for i in range(0,9):
    plt.figure(figsize=(5,5))
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
## OUTPUT:

### Original Image and Grayscale Image
![Capture26](https://user-images.githubusercontent.com/77089276/169644881-04fdec4d-8eab-4987-8c49-2690c45707df.PNG)



### Global Thresholding

![Capture27](https://user-images.githubusercontent.com/77089276/169644886-81979a9d-7d73-432d-b0fa-0dc962f11b0a.PNG)


### Adaptive Thresholding

![Capture28](https://user-images.githubusercontent.com/77089276/169644892-16a3a822-6aba-4f71-aa5e-2389ce2c06ea.PNG)


### Optimum Global Thesholding using Otsu's Method
![Capture29](https://user-images.githubusercontent.com/77089276/169644897-069c8a1c-c0f4-4aae-8ee2-abaa3b1a8306.PNG)





## RESULT:
Thus the images are segmented using global thresholding, adaptive thresholding and optimum global thresholding using python and OpenCV.
