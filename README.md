# OPENING AND CLOSING
## Aim
To implement Opening and Closing using Python and OpenCV.

## Software Required
1. Anaconda - Python 3.7
2. OpenCV
## Algorithm:
### Step1:
<br>
Import the necessart packages like cv2, numpy and matplotlib

### Step2:
<br>
Create the text using cv2.putText function.

create a image using numpy zeros width 600x600.

set the orgin, font, font scale, color, font thickness and line type.

### Step3:
<br>
Create the structuring element.

define the function as display_image.

set the figure size.

add subplot 111 (available function).

### Step4:
<br>
Use the Opening Opearation.

create kernel using numpy ones.

create white noise.

display it.

using morphologyEx function include white noise image, cv2.MORPH_OPEN function for opening and kernel.

display it.

### Step5:
<br>
Use the Closing Opearation.

create kernel using numpy ones.

create black noise.

display it.

using morphologyEx function include black noise image, cv2.MORPH_CLOSE function for closing and kernel.

display it.
 
## Program:

``` Python
# Import the necessary packages
import cv2
import numpy as np
import matplotlib.pyplot as plt


# Create the Text using cv2.putText
def load_image():
    back_img =np.zeros((600,600))
    font = cv2.FONT_HERSHEY_SIMPLEX
    cv2.putText(back_img,text='BALAJI',org=(50,300), fontFace=font,fontScale= 5,color=(255,255,255),thickness=25,lineType=cv2.LINE_AA)
    return back_img


# Create the structuring element
def display_image(image):
    fig = plt.figure(figsize=(12,10))
    ax = fig.add_subplot(111)
    ax.imshow(image,cmap='gray')
    plt.show()

image=load_image()

display_image(image)

# Use Opening operation
kernel=np.ones((5,5))
white_noise=np.random.randint(low=0,high=2,size=(600,600))
white_noise=white_noise*255
white_noise_image=white_noise+image
display_image(white_noise_image)

opening = cv2.morphologyEx(white_noise_image, cv2.MORPH_OPEN, kernel)
display_image(opening)

# Use Closing Operation
black_noise=np.random.randint(low=0,high=2,size=(600,600))
black_noise=black_noise*-255
black_noise_image=image+black_noise
black_noise_image[black_noise_image==-255]=0
display_image(black_noise_image)

closing = cv2.morphologyEx(black_noise_image, cv2.MORPH_CLOSE, kernel)
display_image(closing)

```
## Output:

#### Input

<img width="706" height="690" alt="Screenshot 2025-11-18 084611" src="https://github.com/user-attachments/assets/63b4af87-1015-4063-b62b-cebbdad8dae5" />

<br>

#### White noise

<img width="694" height="679" alt="Screenshot 2025-11-18 084701" src="https://github.com/user-attachments/assets/bba11ce2-0a63-4d29-b353-cd58b6eb5697" />

<br>

### Opening operation

<img width="714" height="675" alt="Screenshot 2025-11-18 084743" src="https://github.com/user-attachments/assets/194b7f09-9b7b-4c02-93cb-f903088b8601" />

<br>

### Black noise

<img width="701" height="687" alt="Screenshot 2025-11-18 084754" src="https://github.com/user-attachments/assets/18f30f45-09ab-4d40-bd72-54310d09107d" />

<br>

### Closing operation

<img width="744" height="694" alt="Screenshot 2025-11-18 084836" src="https://github.com/user-attachments/assets/8811c56e-3090-4695-a52f-4f0298736532" />

<br>

## Result
Thus the Opening and Closing operation is used in the image using python and OpenCV.
