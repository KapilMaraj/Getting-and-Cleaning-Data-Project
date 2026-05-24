This code book describes the data, variables, and transformations performed by `run_analysis.R` to clean up the UCI HAR Dataset.

* `subject`: The ID of the test subject (integer, ranges from 1 to 30).
* `activity`: The type of activity performed when the measurements were taken (Factor with 6 levels: WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING).

The remaining variables represent the average (mean) of the mean and standard deviation measurements from the original accelerometer and gyroscope 3-axial signals. Examples include:
* `tBodyAcc.mean...X`
* `tBodyAcc.std...Y`
* `fBodyAcc.mean...Z`

1. Merged the training and test sets using `rbind()` to create unified feature, label, and subject datasets.
2. Combined subjects, labels, and features horizontally using `cbind()`.
3. Extracted only the measurements on the mean and standard deviation for each measurement using `select(contains("mean"), contains("std"))`.
4. Replaced numeric activity codes (1 to 6) with descriptive activity names from `activity_labels.txt`.
5. Grouped the data by `subject` and `activity` to calculate the average of each variable using `summarise(across(everything(), mean))`.
6. Exported the data to `FinalData.txt`.
