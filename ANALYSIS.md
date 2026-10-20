# Vector and Scalar Evaluation

## Tracing Grace's NA

Take c(Ada = 8, Grace = NA, Linus = 12, Barbara = 4). In clean_scores_vector(), three whole-vector steps run in order. First, scores[is.na(scores)] <- 0 uses a logical mask to change Grace's NA to 0 while every other element is untouched. Second, scores * 2 doubles all four values at once, so Grace stays 0. Third, scores[scores > 20] <- 20 caps Linus's 24 at 20, and Grace's 0 fails the test. The function never refers to position 2.

In clean_scores_scalar(), Grace is reached on the second pass of the for loop. The score is extracted, is.na(score) is TRUE, so result is 0 and the doubling is skipped. The line adjusted_scores[[i]] <- result writes it back and keeps the names. Both functions return Ada 16, Grace 0, Linus 20, Barbara 8.

## Operations on all elements at once

In the vector version, is.na(scores), scores * 2, and scores > 20 each process the whole vector in one expression. The two subassignments then replace every marked position in one step.

## Loop order and recycling

The scalar version goes through positions 1 to 4 in order, and each pass only reads and writes its own element. Since no pass depends on another, the order does not change the final answer. The vector is only partially cleaned while the loop runs, while every element is at the same stage in the vector version.

Recycling would matter if a step used a vector shorter than scores. Here, 2 and 20 have length one, so R repeats them across all elements. If scores * 2 was written as scores * c(2,3), the 2 and 3 would alternate, so Barbara would be multiplied by 3. The same applies to scores[is.na(scores)] <- c(0,1) if there were four NA values, where 0 and 1 would cycle through the marked positions. If the lengths do not divide evenly, R gives a warning but still returns a result. The scalar loop does not use recycling because each pass works with one value.

## Which version to keep

Overall, clean_scores_vector() is the better version to keep. It is shorter, and each line follows one rule, which is to replace missing values, double, then cap. For example, scores * 2 followed by scores[scores > 20] <- 20 does in two lines what the scalar loop's min(2 * score, 20) does for each element. R applies these operations to the whole vector, which is usually faster than a loop. The scalar loop would be more useful when the result of one element depends on the previous element, since a vector expression cannot always directly express that.
