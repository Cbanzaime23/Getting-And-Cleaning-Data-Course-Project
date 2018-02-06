# Getting and Cleaning Data Course Project: codebook

The purpose of this project is to demonstrate ability to collect, work with, and clean a data set. 
The goal is to prepare tidy data that can be used for later analysis. Required to submit: 1) a tidy data set as described below, 
2) a link to a Github repository with script for performing the analysis, and 3) a code book that describes the variables, 
the data, and any transformations or work that performed to clean up the data called CodeBook.md.


## Data Processing Steps
### The R script(`run_analysis.R`) for this Course Project includes the following data processing steps

1. Downloading and unzipping dataset
    * Download the raw data if the it is not yet available in the working directory
    * Unzip the zip file
  
2. Merging the training and the test sets to create one data set
    * Read traning tables from train folder inside of `UCI HAR Dataset`
    * Read testing tables from test folder inside of `UCI HAR Dataset`
    * Reading feature vector from `UCI HAR Dataset`
    * Reading activity labels from `UCI HAR Dataset`
    * Assigning column names for train datasets and test datasets
    * Merge datasets using cbind and rbind
  
3. Extracting only the measurements on the mean and standard deviation for each measurement
    * Create vector that will have a value "TRUE" for the columns names that matched the ff. regular expressions:
    `activityId`, `subjectId`, `mean..`, `std`
    * Subset `activityId`, `subjectId`, `mean..`,`std..` columns
    * Merging the `For_Mean_And_Std` dataframe and `activityLabels` by `activityId`

4. Appropriately labels the data set with descriptive variable names

5. Creating a second, independent tidy data set with the average of each variable for each activity and each subject:
    * Writing second tidy data set in txt file
    * The location of the file will be in the working directory
    * Read the tidy data from working directory
    

## The raw data 
### The raw data for this project will contains the following column names and file names

#### Identifiers

  * `subject` - The ID of the test subject
  * `activity` - The type of activity performed when the corresponding measurements were taken

#### Measurements
I made modification on the measurements(column names) of the raw data to have a descriptive variable name
Using the gsub function, I made some parts of the column names to be more explicit

    * `gsub("^t", "time", names(setActivityNames))`
    * `gsub("^f", "frequency", names(setActivityNames))`
    * `gsub("Acc", "Accelerometer", names(setActivityNames))`
    * `gsub("Gyro", "Gyroscope", names(setActivityNames))`
    * `gsub("Mag", "Magnitude", names(setActivityNames))`
    * `gsub("BodyBody", "Body", names(setActivityNames))`

To make the following more readable

  * `tBodyAccMeanX`
  * `tBodyAccMeanY`
  * `tBodyAccMeanZ`
  * `tBodyAccStdX`
  * `tBodyAccStdY`
  * `tBodyAccStdZ`
  * `tGravityAccMeanX`
  * `tGravityAccMeanY`
  * `tGravityAccMeanZ`
  * `tGravityAccStdX`
  * `tGravityAccStdY`
  * `tGravityAccStdZ`
  * `tBodyAccJerkMeanX`
  * `tBodyAccJerkMeanY`
  * `tBodyAccJerkMeanZ`
  * `tBodyAccJerkStdX`
  * `tBodyAccJerkStdY`
  * `tBodyAccJerkStdZ`
  * `tBodyGyroMeanX`
  * `tBodyGyroMeanY`
  * `tBodyGyroMeanZ`
  * `tBodyGyroStdX`
  * `tBodyGyroStdY`
  * `tBodyGyroStdZ`
  * `tBodyGyroJerkMeanX`
  * `tBodyGyroJerkMeanY`
  * `tBodyGyroJerkMeanZ`
  * `tBodyGyroJerkStdX`
  * `tBodyGyroJerkStdY`
  * `tBodyGyroJerkStdZ`
  * `tBodyAccMagMean`
  * `tBodyAccMagStd`
  * `tGravityAccMagMean`
  * `tGravityAccMagStd`
  * `tBodyAccJerkMagMean`
  * `tBodyAccJerkMagStd`
  * `tBodyGyroMagMean`
  * `tBodyGyroMagStd`
  * `tBodyGyroJerkMagMean`
  * `tBodyGyroJerkMagStd`
  * `fBodyAccMeanX`
  * `fBodyAccMeanY`
  * `fBodyAccMeanZ`
  * `fBodyAccStdX`
  * `fBodyAccStdY`
  * `fBodyAccStdZ`
  * `fBodyAccMeanFreqX`
  * `fBodyAccMeanFreqY`
  * `fBodyAccMeanFreqZ`
  * `fBodyAccJerkMeanX`
  * `fBodyAccJerkMeanY`
  * `fBodyAccJerkMeanZ`
  * `fBodyAccJerkStdX`
  * `fBodyAccJerkStdY`
  * `fBodyAccJerkStdZ`
  * `fBodyAccJerkMeanFreqX`
  * `fBodyAccJerkMeanFreqY`
  * `fBodyAccJerkMeanFreqZ`
  * `fBodyGyroMeanX`
  * `fBodyGyroMeanY`
  * `fBodyGyroMeanZ`
  * `fBodyGyroStdX`
  * `fBodyGyroStdY`
  * `fBodyGyroStdZ`
  * `fBodyGyroMeanFreqX`
  * `fBodyGyroMeanFreqY`
  * `fBodyGyroMeanFreqZ`
  * `fBodyAccMagMean`
  * `fBodyAccMagStd`
  * `fBodyAccMagMeanFreq`
  * `fBodyBodyAccJerkMagMean`
  * `fBodyBodyAccJerkMagStd`
  * `fBodyBodyAccJerkMagMeanFreq`
  * `fBodyBodyGyroMagMean`
  * `fBodyBodyGyroMagStd`
  * `fBodyBodyGyroMagMeanFreq`
  * `fBodyBodyGyroJerkMagMean`
  * `fBodyBodyGyroJerkMagStd`
  * `fBodyBodyGyroJerkMagMeanFreq`

#### Activity Labels

  * `WALKING` (value `1`): subject was walking during the test
  * `WALKING_UPSTAIRS` (value `2`): subject was walking up a staircase during the test
  * `WALKING_DOWNSTAIRS` (value `3`): subject was walking down a staircase during the test
  * `SITTING` (value `4`): subject was sitting during the test
  * `STANDING` (value `5`): subject was standing during the test
  * `LAYING` (value `6`): subject was laying down during the test
