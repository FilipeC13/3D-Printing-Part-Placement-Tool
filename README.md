# 3D-Printing-Part-Placement-Tool
This is a tool that places produces a layout of the placement of 3D parts using a custom heuristic followed by the Tabu Search metaheuristic.

# A. Problem Description
A common problem in the manufacturing industry of today is: 
"How to place X parts in a 3D printing tray so that we can obtain the maximum amount of sets?"

The manual placement of parts that relies on the experience who's placing is quite time consuming and more often than not yields poor results. This problem served as a motivation to create a decision support tool that would perform this task in a more efficient and effective manner.

In this case the focus was in Sequential FDM which means that the 3D Printer will print each part one at a time and using the Fusion Deposition technology. It's a problem that fits into the Nesting Problems subcategory of the Cutting and Packing Problems. It is the optimization of a 2D layout but with 3D constraints related to the printer's movements.

The problem at hand can be summed in the following sentence: 
"Given a set of parts of irregular geometry and small dimension, what is the layout or part placement in the printing tray that maximizes the number of sets?"

Constraints: 
  The printer's head cannot collide with any of the parts during printing;
  No part can be superimposed on another one;
  Part's skirts must not superimpose each other.

The problem as a whole can be divided into 2 subproblems: the geometric problem and the combinatory problem. The following image illustrates this:


Geometric Representation
  The method used for the part representation was the Raster Method which originally stated that a 1 simbolizes where some part is and 0 codifies empty space as in the following figure:
  
  In this case, the tool was created so that it presents the height of the part instead of 1 as in the following figure:
  
# B. Solution

  ## B.1. Constructive Heuristic
  The constructive heuristic allows the tool to get an initial solution for the problem which will be improved afterwards. The heuristic starts with a bottom-right placement of the parts and sequences them by increading height. This is to avoid colision of the printing head with the previously placed parts.
  
  ## B.2. Tabu Search
  The method chosen to generate neighbors was the Adjavent Pairwise Interchange which is represented in the following image:
  
  ## B.3. Visual Representation
  
# C. Testing
  ## C.1. Phase 1 - 2 Simple Geometry Parts
  ## C.2. Phase 2 - 2 Medium Complexity Geometry Parts
  ## C.3. Phase 3 - 4 Complex Geometry Parts 
  The Set of Parts is SHAPES in Oliveira, Gomes, & Ferreira, 2000. The following figure represents the parts:
  
# D. Future Work
  - Being able to obtain certain characteristics of the parts, printer and printing settings from the G-Code file such as:
      . Height of the part;
      . Quality of the printing for each part (layer thickness);
      . Distance from the part to its skirt;
      . Skirt Width;
      . Printer's Dimensions.
  - Giving the user the option to choose the positioning rule and suggesting which is more appropriate considering the printer's characteristics.
  - Execute the Raster Method without the external app;
  - Part Rotation in the Tabu Search Metaheuristic (the function that does that is already made).
