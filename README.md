#OCR it!!!
=============================================================================================================
###Language:Python 3.6.1 |Anaconda 4.4.0
=============================================================================================================
##Libraries i have used:
*+Numpy(pip install numpy)
*+CV2(pip install opencv-python)
*+pytesseract(pip install pytesseract)
*+imutils(pip install imutils)
*+time(pip install times)
(included in requirments_full.txt file)
==============================================================================================================


##Procedure:
--------------------------------------------------------------------------------------------------------------
### Main Funtion:

The image is loaded as img using the funtion imread from CV2 lib
the image is of resolution 1600*1200 which is harder to process, consumes more time and introduces a lot of noises.
to resolve this issue we have resized the image to half of its resolution.
a found_text variable is initilized and set to False as this variable indicates whether a text is dected or not
rotation_angle variable is initilized to 0 as in first iteration the image is not rotated
a while loop is introduced. the while loop breaks if a text is found is the image.
the image and rotation_angle is sent to preprocessImage funtion which will preprocess the image and returns
back a image which has gone through all the preprocessing steps included in the preprocessImage funtion
that image is fed to the image_to_string funtion of the pytesseract library which returns text if it could detect any text
if text is present then found_text variable is set to True else the rotation_angle is incremented by 1
after the text is detected the while loop will break and the program continues
the text is stored in a txt file for future reference.
the preprocessed image is stored in the disk for closer examination if required.
-------------------------------------------------------------------------------------------------------------------
### **preprocessImage funtion**
this funtion takes 2 parameter. one is image and 2nd is rotationangle
the image is first rotated according to the rotation_angle variable. in the 1st iteration it is 0 so the image stays the same.
the rotated image is thresholded.if a pixel value is greater than a threshold value(85), it is assigned one value(255)else 0
then Bilateral filtering is applied on the threshold image to reduce noise while keeping edges sharp as these are  a
mojor factor while performing OCR
Adaptive Thresholding is applied as image has different lighting conditions in different areas.
a kernal of size 1*1 is created for Morphological operation
Morphological Closing is performed to reduce the black pixels and get a clarity image
the result is returned to the main program.

