The script "run_analysis.R" downloads and unzips the UCI HAR Dataset directly into the working directory. 
From this dataset, the following files are utilized:

"features.txt": IDs and Names for the 561 unique attributes measured
"activity_labels.txt": IDs and Names for the 6 unique activities performed
"subject_train.txt": Subject number, for each instance recorded in the training set
"y_train.txt": Activity ID, for each instance recorded in the training set
"X_train.txt": Values for for the 561 unique attributes measured, for each instance recorded in the training set
"subject_test.txt": Subject number, for each instance recorded in the test set
"y_test.txt": Activity ID, for each instance recorded in the test set
"X_test.txt": Values for for the 561 unique attributes measured, for each instance recorded in the test set 

The following steps were performed using these aformentioned files to create the resulting dataset desired:
Import "features.txt" as features.
Filter features to include only attributes that are means or standard deviations.
Import "activity_labels.txt" as activity. Name columns as "ID" and "activity".
Import "subject_train.txt" as subject_train. Name column as "subject".
Import "y_train.txt" as y_train. Name column as "ID".
Import "X_train.txt" as X_train.
Filter X_train to include only attributes that are included in features.
Name columns in X_train using the Names in features.
Combine subject_train, y_train, and X_train by column to create the training set df_train.
Repeat steps 4-9 using the "test" files instead of the "train" files to create the test set df_test.
Combine df_train and df_test by row to create the dataset df.
Merge activity into df based on the "ID" column in both.
Remove the "ID" column from df.
Gather all columns in df into rows, except "subject" and "activity", with the key as "feature" and the values as "measurement".
Separate the "feature" column and its contents into 3 columns: "feature", "function", and "axis".
Group df by "subject", "activity", "feature", "function", and "axis".
Calculate the mean for each group in df.
Spread df with the key as "function" and the values as "measurement".
Rename the columns "mean()" and "std()" as "mean" and "std", respectively. 

The resulting data set includes the following variables:
subject: ID of the volunteer recorded
activity: Description of activity performed
feature: Description of the attribute recorded
axis: Axis of the attribute recorded, where applicable
mean: Average of the mean measurement
std: Average of the standard deviation measurements
