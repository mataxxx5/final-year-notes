---
tags: [CS3330]
title: MatLab Bullshit
created: '2019-11-27T20:27:53.228Z'
modified: '2019-11-28T02:36:10.228Z'
---

# MatLab Bullshit

## Matrices Creation
Creating matrices is annoying, there's several ways to do it and majority are stupid, heres some examples from the lab instructions:
`[1,2,3;4,5,6]` equates to:
  
  |col1|col2|col3|
  |----|----|----|
  |1   |2   |3   |
  |4   |5   |6   |

`[zeros(2,3);1:3]` equates to:

  |col1|col2|col3|
  |----|----|----|
  |0   |0   |0   |
  |0   |0   |0   |
  |1   |2   |3   |
  
  So essentially char `,` denotes next element in the row and `;` denotes a new row, matrices can be conbined with vectors to create other matrices as long as the dimensions for both vectors and matrices are correct 
## Accessing Vectors
accessing vectors work is fairly simple, given vector `u = [0,1,2,3,4,5,6]`. a number or a list can be passed in `u(1)|u(1:4)` such that it identfies the index(es) of the vector for the elements of iterest. Conditionals can also be used to extraxct elements that fit the conditions. some examples :
`u(3) == 2`
`u([3:end]) == [2,3,4,5,6]`
`u(u > 2 & u < 6) == [3,4,5]` 
**Note: that indexes for the elements in vectors and matrices always begin with 1 rather than conventional 0**

## Accessing Matrices
Accessing matrices is similar to acessing vectors, except due to the different number of dimensions, the notation is different where:
`v(r,c)` the `r` represents the rows to access and the `c` represents the columns. So if given matrice x:
  |col1|col2|col3|
  |----|----|----|
  |1   |4   |7   |
  |2   |5   |8   |
  |3   |6   |9   |
the notation `x([2,3], [:])` will select row 2 and 3 and every column in those rows:
  |col1|col2|col3|
  |----|----|----|
  |1   |4   |7   |
  |**2**   |**5**   |**8**   |
  |**3**   |**6**   |**9**   |

## Vectorising Loops
To vectorise loops use:`.` **element-wise** operator on vectors of any dimensions to apply same function on each element inside the vector.

It's similar to list comprehension in python, except it will apply the function to element regardless of the dimension it belongs in

for example,it MatLab:
`v = (v.*6).^3`
reads the same as:
`[ math.pow((x*6), 3) fox x in element_list]`
in Python

operations on a set of elements inside a vector can also be enacted with conditionals, for example:
`u(u<0) = u(u<0) + 1`

In short, elementwise operations, apply functions on all elements of the list and conditions can be used to apply functions to set of elements avoiding the need for `if` statements and `for` and `while` loops.

## Utilities
`size()` - returns matrix size
`length()` - returns vector length
`help [function_name]` - gives info on the function
`whos [variable_name]` - list variable info
`clc` - clears command window
`clear` - clears workspace aswell
`save [filename] [variable_name]` - saves variable to a matlab file name after filename
`[vector_name]'` - transposes the vector row-to-column and vise versa
