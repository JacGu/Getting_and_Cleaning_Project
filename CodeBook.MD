# Introduction

The script `run_analysis.R` performs the 5 steps required to clean and then obtain the required output.

* Data is first merged using the `rbind()` function. 
* Then, only those columns with the mean and standard deviation measures are taken from the whole dataset. After extracting these columns, they are given the correct names, taken from `features.txt`.
* As activity data is data with values 1 to 6, we take the activity names and IDs from `activity_labels.txt` and they are substituted in the dataset.
* Columns with unclear names are replaced.
* A new dataset is generated, containing all average measures for each subject and activity type. This data set is called `tidy_data.txt`.

# Variables

* `x_train`, `y_train`, `x_test`, `y_test`, `subject_train` and `subject_test` host the raw data from the downloaded data file.
* `x_data`, `y_data` and `subject_data` merge the raw data to be further analysied.
* `features` contains the correct names for the `x_data` dataset, which are applied to the column names stored in `mean_and_std_features`, a numeric vector used to extract the desired data.
* The same is done with activity names through the `activities` variable.
* `all_data` merges `x_data`, `y_data` and `subject_data`.
* `tidy_data` contains the relevant averages which will be later stored in a `.txt` file. `ddply()` from the plyr package is used to apply `colMeans()` and ease the development.
