# Reasoning Before Execution

Write the rule behind each case before you commit your predictions. Replace
every placeholder line below with one to three sentences that name the rule
producing that case's value, type, length, and dimensions. One rule is enough.
After you run and find a miss, add a short correction entry under that case in a
later commit.

## P01
c() makes all the values use one common type, following the order logical, integer, double, and character. Since 3.5 is a double, the whole vector becomes double, giving [1,2,3.5]; it has length 3 and no dimensions.

## P02
Since c() combines the values into one atomic vector and there is a character value, everything is coerced to character. The result is ["1","2","TRUE"], with length 3 and no dimensions.

## P03
R recycles the shorter vector [1,2] to [1,2,1,2] before doing the addition element by element. The result is [11,22,31,42]; all values are integers, so the type is integer, length is 4, and there are no dimensions.

## P04
Positive indices select the requested positions in order, so positions 3 and 1 give third = 9 and first = 8. The result stays integer, has length 2, and has no dimensions.

## P05
A negative index means to exclude that position, so -2L removes the second value, 7, from the vector. This leaves [4,9], which is integer with length 2 and no dimensions.

## P06
is.na(x) | x > 10L gives [FALSE,TRUE,TRUE,FALSE], because TRUE | NA is TRUE, so positions 2 and 3 are selected. The result is [NA,12]; it stays integer, has length 2, and has no dimensions.

## P07
A factor stores integer codes and uses the given levels as labels, so low, high, low corresponds to integer codes 1,2,1. Therefore its type is integer, length is 3, and it has no dimensions.

## P08
A list can keep different types in separate elements, so the integer vector scores and character label stay as they are. There are 2 top-level elements, so the type is list, length is 2, and there are no dimensions.

## P09
A data frame is a list of equal-length columns, so its typeof() is list even though it acts like a data frame. It has 2 columns and 2 rows, giving length 2 and dimensions 2x2.

## P10
The matrix is filled by column, so matrix(1:6, nrow=2L) has storage order 1,2,3,4,5,6, and [10L,20L] is recycled as 10,20,10,20,10,20. The result is `matrix[2x3](11,22,13,24,15,26)`, with integer type, length 6, and dimensions 2x3.

## P11
The vector contains an NA and mean() is not told to remove it, so the result is NA. Since the input is double, the result is double with length 1 and no dimensions.

## P12
With na.rm=TRUE, the missing value is removed before getting the mean, so the mean of 8 and 10 is 9. The result is double, has length 1, and has no dimensions.

## P13
x starts as an integer vector, but assigning the double 2.5 makes R widen the whole atomic vector to double. The result is [1,2.5,3], with length 3 and no dimensions.

## P14
ifelse() chooses 0 for the missing score and doubles the nonmissing scores, giving [14,0,24,8], then values greater than 15 are replaced with 15. The final result is [14,0,15,8], which is double with length 4 and no dimensions.

## P15
The array has dimensions 2x2x2, so it contains 2 * 2 * 2 = 8 integer values stored in order from 1 to 8. Therefore the value is `array[2x2x2](1,2,3,4,5,6,7,8)`, the type is integer, the length is 8, and the dimensions are 2x2x2.

## P16
Index 0L selects nothing, so the result is an empty vector of the same atomic type as the original vector. Therefore the value is [], the type is integer, the length is 0, and there are no dimensions.