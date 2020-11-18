# 3D-Printing-Part-Placement-Tool
For a more visual presentation of the tool, please see the PowerPoint presentation present in "3D-Printing-Part-Placement-Tool/3D Part Placing Tool Presentation (EN).pptx"

# A. Problem Description
A common problem in the manufacturing industry of today is: 
"How to place X parts in a 3D printing tray so that we can obtain the maximum amount of sets?"

The manual placement of parts that relies on the experience who's placing is quite time consuming and more often than not yields poor results. This problem served as a motivation to create a decision support tool that would perform this task in a more efficient and effective manner.

In this case the focus was in Sequential FDM which means that the 3D Printer will print each part one at a time and using the Fusion Deposition technology. It's a problem that fits into the Nesting Problems subcategory of the Cutting and Packing Problems. It is the optimization of a 2D layout but with 3D constraints related to the printer's movements.

The problem at hand can be summed in the following sentence: 
"Given a set of parts of irregular geometry and small dimension, what is the layout or part placement in the printing tray that maximizes the number of sets and parts?"

Constraints:
  * The printer's head cannot collide with any of the parts during printing;
  * No part can be superimposed on another one;
  * Part's skirts must not superimpose each other.

The problem as a whole can be divided into 2 subproblems: the geometric problem and the combinatory problem.
  
# B. Solution

  ## B.0. Rasterization App
  This app produces .txt files that can be used by the VBA Excel app. It takes as an input the 3D model of the part and converts them into 2D matrixes were 1 means that there is part and 0 means empty space. This app was developed by another colleague from the Polytechnic Institute of Porto.
  
  ## B.1. Constructive Heuristic
  The constructive heuristic allows the tool to get an initial solution for the problem which will be improved afterwards. The heuristic starts with a bottom-right placement of the parts and sequences them by increading height. This is to avoid colision of the printing head with the previously placed parts.
  
  ## B.2. Tabu Search
  The method chosen to generate neighbors was the Adjacent Pairwise Interchange. The aspiration criteria was not implemented in this Tabu Search algorithm.
  
  ## B.3. Visual Representation
  In order to better visualize the solution obtained, a graphical output was made that represents a top-view of the printing tray and the respective layout of the parts.
  The method used for the part representation was the Raster Method which originally stated that a 1 simbolizes where some part is and 0 codifies empty space.
  In this case, the tool was created so that it presents the height of the part instead of 1.
  
# C. Using the Tool
  The G-Code file is a file that can be obtained from softwares like Ultimaker Cura and that describe the movements of the printer to print the part.
  1. First, the G-Code file of the parts needs to be transformed into a .txt file. To do that, use the command line tool in the folder "g-code-processor" and follow the instructions present in readme.md file. You can set the x and y resolution and some other parameters.
  2. After that, open the Excel tool in the folder "3D Part Placing Tool" named "3D Part Placing Tool.xlsm" and add the .txt files of the parts, introduce their heights and add your printer's characteristics if necessary. 
  3. You can now run the tool and it will generate a solution for the parts imported, printer characteristics and resolution in the configurations.
  
# D. Future Work
  - Being able to obtain certain characteristics of the parts, printer and printing settings from the G-Code file such as:
      - Height of the part;
      - Quality of the printing for each part (layer thickness);
      - Distance from the part to its skirt;
      - Skirt Width;
      - Printer's Dimensions.
  - Giving the user the option to choose the positioning rule and suggesting which is more appropriate considering the printer's characteristics.
  - Execute the Raster Method without the external app;
  - Part Rotation in the Tabu Search Metaheuristic (the function that does that is already made).
