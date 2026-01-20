# IMGD 5010 Assignment 1

This document details instructions for creating simple images through a list of pre-defined binary instructions.

The format of the instruction will be in a sequence of four(4) 3-bit numbers (an octet) that may be read as follows
 
> xxx xxx xxx xxx
> 
>  [row position] [column position] [image] [colour]
 
The first three octets are required but the fourth is optional

The default for colour is black on a white background.  The last [colour] octet is optional, it is only used if a different colour is required for that particular location

## Row and Column Locations
Using a 3-bit number for the row and column locations will define an 8x8 grid which will create a square of 64 units as displayed:

![grid.png](https://github.com/MVChin/IMGD-5010-Assignment-1/blob/images/grid.png?raw=true)

Row positions will be read from bottom to top and columns are read from left to right. Therefore location of the square indicated above will be 111 000


Using row-column locations makes the grid expandable in both directions by simply increasing the number of bits used. Increasing the row block from 3 bits to 4 bits, increases the number of rows from 8 to 16

## Images
This image mapping is as shown below
![Image-list.png](https://github.com/MVChin/IMGD-5010-Assignment-1/blob/images/Image-list.png)

## Colours
The default colour for the instruction is black.  The fourth octet is used to define colour for the selected location only.  If only three octets are detected then the language will default to black on a white background.

The colour mappings are as shown
![Colour.png](https://github.com/MVChin/IMGD-5010-Assignment-1/blob/images/Colour.png)
# Example

The image below is an example of the type of picture that may be created using the listed components in the Images section.

![Example.png](https://github.com/MVChin/IMGD-5010-Assignment-1/blob/images/Example.png)

To draw the single filled yellow square inside an outlined square that is 3 x 3 large, the following instructions would be:
 
011 100 001 011 *yellow square*

*Bottom of the square*  
001 011 010  
001 100 010  
001 101 010  
*Left side of the square*  
010 011 011  
011 011 011  
100 011 011  
*Top of the square*

101 011 100

101 100 100

101 101 100

*Right side of the square*

010 101 101

011 101 101

100 101 101


# Limitations
The use of mapping a predefined images to a location to create a larger image has the limitation of not being able to combining images at a single location.  For example, a single location cannot have both the top line AND the left side outlined.  
