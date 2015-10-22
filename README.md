# GetData_PeerAssessment1

This repository contains the following required scripts and files for Getting and Cleaning Data Peer Assessment 1 :

  1. CodeBook.md---This file is a code book that describes the variable, the data and work performed to clean up the data in this analysis

  2. run_analysis.R----This script contains the codes used to come up with a tidy data set required in step1 of the Peer Assessment. To run the script, please save the Samsung data in your working directory.  

The Samsung data can be obtained from    https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip 

The script can do the following:

    1.1 Merges the training and the test sets to create one data set.
    1.2 Extracts only the measurements on the mean and standard deviation for each measurement. 
    1.3 Uses descriptive activity names to name the activities in the data set
    1.4 Appropriately labels the data set with descriptive variable names. 
    1.5 From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.
    1.6 Save data obtained in 1.5 as a text file named 'Ave_by_activity_subject.txt'


In order to understand interrelation of each file, please refer to the documentations contained in the samsung dataset under folder UCI HAR Dataset. The files are the ff:
--README.txt,features.txt,features_info.txt


