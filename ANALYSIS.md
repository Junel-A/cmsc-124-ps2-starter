# Vector vs Scalar Cleaning

## Tracing Grace's NA

Take c(Ada = 8, Grace = NA, Linus = 12, Barbara = 4). In clean_scores_vector(), three whole-vector steps run in order. First, scores[is.na(scores)] <- 0 uses a logical mask to change Grace's NA to 0 while every other element is untouched. Second, scores * 2 doubles all four values at once, so Grace stays 0. Third, scores[scores > 20] <- 20 caps Linus's 24 at 20, and Grace's 0 fails the test. The function never refers to position 2.

In clean_scores_scalar(), Grace is reached on the second pass of the for loop. The score is extracted, is.na(score) is TRUE, so result is 0 and the doubling is skipped. The line adjusted_scores[[i]] <- result writes it back and keeps the names. Both functions return Ada 16, Grace 0, Linus 20, Barbara 8.

## Operations on all elements at once

In the vector version, is.na(scores), scores * 2, and scores > 20 each process the whole vector in one expression. The two subassignments then replace every marked position in one step.