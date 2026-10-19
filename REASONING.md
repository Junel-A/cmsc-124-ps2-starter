# Reasoning

## P01
The coercion ladder runs logical, integer, double, character. The 3.5 is a double, so TRUE becomes 1 and 2L becomes 2. The value is [1,2,3.5], type double, length 3, no dimensions.

## P02
The string "2" is character, the top of the ladder, so every element becomes character, and TRUE becomes "TRUE". The value is ["1","2","TRUE"], type character, length 3, no dimensions.

## P03
The shorter vector c(1L,2L) is recycled across four positions, so we add 1,2,1,2. Integer plus integer stays integer. The value is [11,22,31,42], length 4, no dimensions.

## P04
Indexing with c(3L,1L) picks positions 3 then 1, in that order, and the names stay attached. The value is [third=9,first=8], type integer, length 2, no dimensions.

## P05
A negative index excludes a position, so -2L removes the 7. The value is [4,9], type integer, length 2, no dimensions.

## P06
is.na(x) is F,T,F,F and x > 10L is F,NA,T,F. For OR, TRUE | NA is TRUE, so the combined mask is F,T,T,F. It selects the NA and the 12. The value is [NA,12], type integer, length 2, no dimensions.

## P07
A factor stores integer codes plus level labels, so typeof is integer even though class is factor. Levels follow the order supplied: low, high. Length is 3 and there are no dimensions.

## P08
A list can hold unlike items, and length counts top-level elements. It has two items, scores and label. The type is list, length 2, no dimensions.

## P09
A data frame is a list of equal-length columns, so typeof is list and length counts the 2 columns. Its dimensions are 2 rows by 2 columns, so dim is 2x2.

## P10
A matrix is a plain vector with a dim attribute, filled by columns, so the stored order is 1:6. c(10L,20L) recycles down that order as 10,20,10,20,10,20. Integer plus integer stays integer. The value is matrix[2x3](11,22,13,24,15,26), length 6, dim 2x3.

## P11
Arithmetic with a missing value gives a missing value, so mean of data containing NA is NA. NA_real_ is a double, so the type is double. The value is [NA], length 1, no dimensions.

## P12
na.rm = TRUE removes the missing value first, so the mean of 8 and 10 is 9. The mean is a double of length 1 with no dimensions.

## P13
1:3 is an integer vector. Assigning the double 2.5 into position 2 widens the whole vector to double, which is a mixed-mode assignment. The value is [1,2.5,3], type double, length 3, no dimensions.

## P14
ifelse gives 14,0,24,8, because the NA position takes the yes value 0 and the others are doubled. The subassignment then caps anything above 15 at 15, so 24 becomes 15. The value is [14,0,15,8], type double, length 4, no dimensions.

## P15
An array is an atomic vector with a dim attribute, stored down the columns. 1:8 is integer, so the type is integer. Length is 8 and dim is 2x2x2.

## P16
Index 0 selects nothing and returns a zero-length vector of the same atomic type. The value is [], type integer, length 0, no dimensions.
