# Code Book #

## Data Set Information ##

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years.
Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a
smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured
3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz.
The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned
into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data.

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width
sliding windows of 2.56 sec and 50% overlap (128 readings/window).
The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass
filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore
a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables
from the time and frequency domain.

## Attribute Information ##

For each record in the dataset it is provided:

* Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration.
* Triaxial Angular velocity from the gyroscope.
* A 561-feature vector with time and frequency domain variables.
* Its activity label.
* An identifier of the subject who carried out the experiment.

## Section 1. Merge the training and the test sets to create one data set. ##

After setting the source directory for the files, we first download the file from the specified Url and then unzip it.
Later we read into tables the data located in :

* features.txt
* activity_labels.txt
* subject_train.txt
* x_train.txt
* y_train.txt
* subject_test.txt
* x_test.txt
* y_test.txt

Assign column names and merge to create one data set using the rbind() and the cbind().

## Section 2. Extract only the measurements on the mean and standard deviation for each measurement. ##

We then extract only those column labels containing mean or standard deviation using the grep(".*mean.*|.*std.*", ).
We then subset this data to keep only the necessary columns.

## Section 3. Use descriptive activity names to name the activities in the data set. ##

We replace short activity names in the data set with the descriptive activity names that are easier for the 
user to understand by reading the activity_labels.txt.

## Section 4. Appropriately label the data set with descriptive activity names. ##

Use gsub function for pattern replacement to clean up the data labels.

## Section 5. Create a second, independent tidy data set with the average of each variable for each activity and each subject. ##

Per the project instructions, we need to produce only a data set with the average of each veriable for each activity and subject.

## Identifiers ##
The following variables were created and used in the R script run_analysis.R : 

* url - to store the url of the file to be downloaded
* path_ref - to store the path of the unzipped folder containg the data set
* files - stores the list of the files in the UCI HAR Dataset
* dataActivityTest - stores data of Y_test.txt
* dataActivityTrain - stores data of Y_train.txt
* dataSubjectTest - stores data of Subject_test.txt
* dataSubjectTrain - stores data of Subject_train.txt
* dataFeaturesTest - stores data of X_test.txt
* dataFeaturesTrain - stores data of X_train.txt
* dataSubject - it rbinds() the dataSubjectTest and dataSunjectTrain
* dataActivity - it rbinds() the dataActivityTest and dataActivitryTrain
* dataFeatures - it rbinds() the dataFeaturesTest and dataFeatureTrain
* dataCombine - it's the temporary variable
* Data - the whole BIG data set as per the requirements specified
* Data2 - the data ser as per the requirements specified

## Activity Labels ##

* WALKING (value 1): subject was walking during the test
* WALKING_UPSTAIRS (value 2): subject was walking up a staircase during the test
* WALKING_DOWNSTAIRS (value 3): subject was walking down a staircase during the test
* SITTING (value 4): subject was sitting during the test
* STANDING (value 5): subject was standing during the test
* LAYING (value 6): subject was laying down during the test
