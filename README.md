# OCR
# By RaghuRama BL
# Task1 Object Detection / Optical Character Recognition (ORC)
# since I am still a biginner I Choose This Task out of given Tasks
# Thanks For Sparks Foundation For Giving me This oppertunity

# Importing Libraries
import cv2
import pytesseract

pytesseract.pytesseract.tesseract_cmd = r'C:\Program Files\Tesseract-OCR\tesseract.exe'
# reading the image
image = cv2.imread("Distorted.PNG")


# Processing the image
# greayScale
def get_grayscale(image):
    return cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)


# thresholding
def thresholding(image):
    return cv2.adaptiveThreshold(gray, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C, cv2.THRESH_BINARY, 31, 11)


gray = get_grayscale(image)
thresh = thresholding(gray)

# Converting The Processed image To Text
text = pytesseract.image_to_string(gray)
print(text)
cv2.imshow("image", gray)
cv2.waitKey(0)
