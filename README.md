# Binary-Image-Encryption
# Introduction:
The above code is a Python script that creates a binary image sequence from a given binary input file, and then converts it into a video. The main motive of this code is to  Convert a file like a pdf file or a word file into a binary a code and encrypt data in the image format or viedo format . Certainly! Here is a more detailed explanation of the process you described:

1. Converting a File to Binary Code
To convert a file to binary code, you need to read the file's contents and then represent those contents as a series of 1's and 0's. This is done using the built-in functions of Python for reading files, such as `open()`, `read()`, and `close()`. Once you have read the file, you can then use the `bin()` function to convert the contents to binary code.

For example, let's say you have a file called "example.txt" that is 1 GB in size. You could use the following code to read the contents of the file and convert them to binary:


with open('example.txt', 'rb') as f:
    file_contents = f.read()

binary_code = ''.join(format(byte, '08b') for byte in file_contents)


This code opens the file in binary mode (`'rb'`) and reads its contents into the `file_contents` variable. The `format()` function is then used to convert each byte of the file to a binary string, with each string being 8 characters long (`'08b'`). The resulting binary strings are then joined together into a single string using `join()`.

2. Saving Binary Code as an Image
Once you have converted the file to binary code, you can save that code as an image file using an image manipulation library, such as Pillow. 

To do this, you first need to create an image object using Pillow, specifying the dimensions of the image you want to create. You can then iterate through the binary code, pixel by pixel, and set the color of each pixel based on the value of the corresponding bit in the binary code.

For example, here is some code that creates a 1024x1024 pixel image and sets the color of each pixel based on the corresponding bit in the binary code:


from PIL import Image

image_width = 1024
image_height = 1024

binary_len = len(binary_code)
image_size = image_width * image_height

if binary_len > image_size:
    raise ValueError('Binary code too long for image size')

image = Image.new('1', (image_width, image_height))

for i in range(binary_len):
    x = i % image_width
    y = i // image_width

    pixel_value = int(binary_code[i])
    image.putpixel((x, y), pixel_value)


This code first checks to make sure that the length of the binary code is not greater than the number of pixels in the image. If it is, an error is raised.

The code then creates a new image object using Pillow's `Image.new()` function, specifying that the image should be a 1-bit black and white image (`'1'`), with the specified dimensions. 

The code then iterates through each bit of the binary code, calculating the corresponding x and y coordinates of the pixel that represents that bit. It sets the color of that pixel to black (`0`) if the bit is `0`, or white (`1`) if the bit is `1`, using the `putpixel()` function of the image object.

Finally, the code saves the image to disk using the `save()` function of the image object, specifying the desired filename and file format (e.g. 'image.png'). 

And that's it! You have now converted a 1 GB file to binary code and saved that code as an image file using Python code.

# Code Explanation:
The code is divided into four parts: calculating the size of the input file, converting the binary data into a binary string, creating the binary image sequence, and finally converting it into a video.

Part 1: Calculating the size of the input file
The first part of the code calculates the size of the input file using the `os.path.getsize()` function, which returns the size of the file in bytes. The size of the file is then printed to the console.

Part 2: Converting the binary data into a binary string
The second part of the code reads the binary data from the input file and converts it into a string of zeros and ones using the `format()` and `join()` functions. Each byte of the binary data is converted to an 8-bit binary string, which is then concatenated to form a single string.

Part 3: Creating the binary image sequence
The third part of the code creates a folder named "binary_images" and populates it with a sequence of binary images. The image resolution is set to 3840x2160, and the size of each image is calculated based on the resolution. For each image in the sequence, the corresponding portion of the binary string is extracted, and converted into a list of integers representing the pixel values of the image. Finally, each list of pixel values is used to create an image object using the `PIL.Image.new()` function, and saved to a file in the "binary_images" folder.

Part 4: Converting the binary image sequence into a video
The final part of the code uses the `cv2.VideoWriter()` function from the OpenCV library to create a video from the binary image sequence. The video resolution is set to 3840x2160, and the frame rate is set to 60 fps. The video is created by looping through each image in the "binary_images" folder, resizing it to the desired resolution using the `cv2.resize()` function, and adding it to the video using the `cv2.VideoWriter.write()` function. Finally, the video writer is released using the `cv2.VideoWriter.release()` function.

# Conclusion:
This Python script provides a simple way to visually represent binary data in the form of a video. It reads binary data from a file, converts it into a sequence of binary images, and then creates a video from the image sequence using the OpenCV library.
