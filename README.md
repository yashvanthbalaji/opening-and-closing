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
    cv2.putText(back_img,text='PRIYA',org=(50,300), fontFace=font,fontScale= 5,color=(255,255,255),thickness=25,lineType=cv2.LINE_AA)
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

<img width="792" height="773" alt="image" src="https://github.com/user-attachments/assets/8e4fb828-b06f-44ce-8ba7-8493b71969f3" />

<br>

#### White noise

<img width="793" height="761" alt="image" src="https://github.com/user-attachments/assets/ec05b35a-78ab-4c37-9c10-573f8c7b369c" />

<br>

### Opening operation

<img width="787" height="766" alt="image" src="https://github.com/user-attachments/assets/cc8c5765-53df-416b-8f2f-06e227eb91c8" />

<br>

### Black noise

<img width="794" height="776" alt="image" src="https://github.com/user-attachments/assets/a51505d4-6655-4bb8-b3d1-aaadfd73f548" />

<br>

### Closing operation

<img width="771" height="777" alt="image" src="https://github.com/user-attachments/assets/29e95539-562d-4c15-bf5c-242a719437a4" />

<br>

## Result
Thus the Opening and Closing operation is used in the image using python and OpenCV.
