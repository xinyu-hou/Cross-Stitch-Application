# Cross-Stitch Application

## About/Overview
Building on top of Project 3 and Project 4, this project added a few more supported operations (i.e., replace a color, remove a color, generate a pattern using user selected DMC colors) and a view. This program is now considered to be a full MVC application. Things that this program can do are listed in the next section.

## List of Features
![Display Menu](https://github.com/xinyu-hou/Cross-Stitch-Application/blob/main/res/DisplayMenu.png)
* Loading and Saving Images
![Load an Image](https://github.com/xinyu-hou/Cross-Stitch-Application/blob/main/res/DisplayOriginalImage.png)
    * Images are represented by a 3D array of integers. 
    * With 8-bit channels, each value is between 0 and 255.
* Image Filter
    * Image Blur
        * The filter can be repeated applied to an image to blur it further. 
    * Image Sharpen
        * Sharpening an image accentuates edges (the boundaries between regions of high contrast). 
        * The filter can be repeated applied to an image to sharpen it further. 
    * Customized Filter Method
        * Users can design their own kernel and filter the image with it.      
* Color Transformation
    * Greyscale
        * Convert a color image into a greyscale image.  
    * Sepia Tone
        * Convert a color image into a sepia-toned iamge.   
    * Customized Linear Color Transformation Method
        * Users can design their own linear color transformation matrix and apply it to the image.
* Color Density Reduction
    * Dither
        * Reducing the number of colors in the image while matining the essence of the image. Valid numbers of color choices in this program: 2, 4, 8, 16, 32, 64, 128, 256. 
* Image Mosaic
![Display Mosaic Result](https://github.com/xinyu-hou/Cross-Stitch-Application/blob/main/res/MosaicDisplayResult.png)
    * Convert a color image into a mosaic image. 
* Image Pixelation
    * Convert a color image into a pixelated image. 
* Pattern Generation
![Display Pattern Result](https://github.com/xinyu-hou/Cross-Stitch-Application/blob/main/res/PatternDisplayResult.png)
    * Generate cross-stitch pattern from a pixelated image. 
* Clamping Values
    * Editing an image many cause some values to be outside the valid range (i.e., 0-255). Clamping prevents these values from overflowing and underflowing.   
* The user interface exposes all the required image-processing and cross-stitch features of the program via a menu. This includes blur, sharpen, greyscale, sepia, dithering, mosaics, pixelation, and the ability to create cross-stitch patterns, as well as load images and save both images and patterns. 
* The user can see the image that is being processed on the screen. If the image is bigger than the area allocated to it in your graphical user interface, then the user can scroll the image using the scrollbars.
* The user interface is able to display cross-stitch patterns using the DMC floss colors to the screen.
* The user interface provides the ability to exchange one color for another in a cross-stitch pattern by clicking on the color in a displayed pattern and allowing the user to select a different color from the DMC color options.
* The user interface provides the ability to pick one color in a cross-stitch pattern that will then be removed from the pattern completely. The pixels of that color would be replaced with a blank pixel.
* The user is able to specify the image to be loaded and saved. 
* The user interface provides a way for a user to interactively create and execute a batch-script.
![Customize a Batch File](https://github.com/xinyu-hou/Cross-Stitch-Application/blob/main/res/DisplayCreateBatchFile.png)
![Display Batch File Execution Result](https://github.com/xinyu-hou/Cross-Stitch-Application/blob/main/res/DisplayBatchFileResult.png)
* When the user specifies an operation, its result is visible to the user. A pop-up window will show up informing the user whether the operation is successful.
* Each user interaction or user input is reasonably user-friendly. After each operation is finished, a pop-up window will inform the user whether the operation is successful.
* Extra credit operations
    * When displaying the cross-stitch pattern to the screen, the interface displays the symbol and the DMC floss color at the same time.
    * Provide the user the ability to select the DMC color palette to use in an image. Do this by providing the ability for the user to select the DMC color thread colors that they have on hand and then substitute each color in the actual pattern with one that the user has indicated that they have on hand.

## How to Run
ATTENTION: 
Please do NOT run the ProjectFiveDriver.java or the Program.jar file in Eclipse.
Running this file in Eclipse requires the res/ prefix on each filename parameter.
Running the RunMe.jar file in the Terminal solves this problem.
### How to Run the JAR File
The Program.jar file is located in res/ directory. 
To run the program in the Terminal, cd to the res/ directory and then run one of the following lines:

java -jar Program.jar -interactive

java -jar Program.jar -script batchFile1.txt

(The student puts a batchFil1.txt in the res/ directory. Users can substitute the file name with their desired batch file.)

### What Arguments are Needed to Run the JAR file, What Do They Mean?
The Program.jar file takes two types of arguments. The first one opens the given script file, execute it and then shut down. The argument format is:

java -jar Program.jar -script path-of-script-file

The second one opens the graphical user interface. The argument format is:

java -jar Program.jar -interactive

Any other command-line arguments are invalid: in these cases the program displays an error message suitably and quit.

## How to Use the Program
Examples of how to use functionality in this porgram are included in the ProjectFiveDriver file. The example run walks through all the functionality listed in the **List of Features** section.

### Instructions on How to Use Functionality
In order to use the batch file controller functionality in this program, users first need to create their batch files and store their desired commands in there. 

Then, construct the controller. Pass the file as parameter. 

Finally, the controller will read all the eligible commands from the batch file and execute them in order.

## Description of Example Runs
The Driver class, ProjectFiveDriver.java is in the src/images/model directory. If the user chooses to use the GUI. All the supported operations are listed in the Menu. 

In order to perform any operation on the image, users first need to load an image by clicking the "Load Image" option in the Menu. 

Then, users can perform the other operations such as blur, sharpen, greyscale, sepia, dither, mosaic, pixelation. 

Users can also generate a cross stitch pattern by using the "With Default Palette" or "With Customized Palette". "With Customized Palette" option allows the user to pick their own DMC color selection. 

"Pattern Tools" contains two operations that can be done on the pattern: "Replace a Color" and "Remove a Color". In order to use the two operations, users need to select a pixel on the pattern first. 

At the end, users can save their editted image and pattern to their desired files by choosing either "Save Image" or "Save Pattern".

The example run using the batch file controller demonstrates all the functionality listed in the **List of Features** section in order. The resulting images are saved in the res/ directory. 
Executing the commands from batchFile1.txt, the program will do the following things:
* Load image1.
* Apply blur filter to image1.
* Save image1-blur.
* Load image1.
* Apply blur filter to image1.
* Apply blur filter agagin.
* Save image1-blur-twice.
* Load image1.
* Apply sharpen filter to image1.
* Save image1-sharpen.
* Load image1.
* Apply greyscale to image1.
* Save image1-greyscale.
* Load image1.
* Apply sepia to image1.
* Save image1-sepia.
* Load image1.
* Apply dither 8 to image1.
* Save image1-dither8.
* Load image1.
* Apply dither 2 to image1.
* Save image1-dither2.
* Load image1.
* Apply mosaic 570 to image1.
* Save image1-mosaic570.
* Load image1.
* Apply pixelate 50 to image1.
* Save image1-pixelate50.
* Load image1.
* Generate pattern 50 from image1.
* Save image1-pattern50.txt.

## Design/Model Changes
After receiving feedbacks from the previous two projects and reading Piazza posts during Project 5 Implementation, the student made the following changes:
1. Added private helper methods to avoid long functions and code duplication.
2. Made changes to the constructor in the Controller class so that it is clearer to find out the input and the output.
3. Adhere to the Single Responsbility Principle by having two controllers. One takes care of batch file script. The other takes care of the Graphical User Interface.
4. I deleted the ImagePanel class from my Project 5 UML Diagram. I found out that a JLabel + a JScrollPane will get the job done more easily.
5. Since Project 5 instruction says that the users get to choose when they want to save a pattern, I modified the ImageModelImpl class so that the program only saves a pattern when the user asks it to do so. 

## Assumptions
Assumptions made during program development and implementation:
1. After saving an image, users need to load a new image before performing any operations.
2. After removing a color from the pattern, users can no longer pick the blank pixel, represented by a "." symbol.
3. When replacing a color in the pattern, users can only choose from the current DMC color selection. 
4. After generating a cross stitch pattern, users cannot perform operations such as blur, sharpen, greyscale, etc. unless they upload a new image.

## Limitations
There are no limiations of this program. It fulfills all the requirements listed in the program instruction.

## Image Use Authorization
All the images that are used in this project were taken by the student. The student authorized their use in the project.
