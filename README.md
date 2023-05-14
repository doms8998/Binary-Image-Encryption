# Binary-Image-Encryption
# Introduction:
The above code is a Python script that creates a binary image sequence from a given binary input file, and then converts it into a video. The main motive of this code is to visually represent the binary data in the form of a video.

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
