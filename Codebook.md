---
title: "Codebook"
output: html_notebook
---

This is a **Codebook** for Getting and Cleaning Data Course Project

The ```run_analysis.R``` script execute the data preparation followed by 5 steps required in the project instruction

1. **Download the dataset**
    * Download the dataset and extract it under folder named ```UCI HAR Dataset```

2. **Create variables and assign data to each variable**
    * ```activities``` <- ```activity_lable.txt```  
    *List of activities performed when corresponding measurements were taken*  
    * ```features``` <- ```features.txt```  
    *The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals*  
    * ```subjext_test``` <- ```test/subject.txt```  
    *contains test data of 9 out of 30 volunteers being observed*  
    * ```y_test``` <- ```test/y_test.txt```  
    *contains test data of activities' code labels*  
    * ```x_text``` <- ```test/x_test.txt```  
    *contains recorded features test data*
    * ```subject_train``` <- ```test/subject_train.txt```  
    *contains train data of 21 out of 30 volunteers being observed*  
    * ```y_train``` <- ```test/y_train.txt```  
    *contains train data of activities' code labels*  
    * ```x_train``` <- ```text/x_train.txt```  
    *contains recorded features train data*
3. **Merges the training and the test sets to create one data set**  
    * ```X``` is created by merging ```x_train``` and ```x_test``` using **rbind()** function  
    * ```Y``` is created by merging ```y_train``` and ```y_test``` using **rbind()** function  
    * ```Subject``` is created by merging ```subject_train``` and ```subject_test``` using **rbind()** function  
    * ```Merged_Data```  is created by merging ```Subject```, ```Y``` and ```X``` using **cbind()** function  
4. **Extract only the measurements on the mean and standard deviation for each measurement**  
    * ```TidyData``` is created by subsetting ```Merged_Data```, selecting only columns: ```subject```, ```code``` and the measurements on the ```mean``` and standard deviation (```std```) for each measurement
5. **Use Descriptive activity names to name the activities in the data set**  
    * Entire numbers in ```code``` column of the ```TidyData``` replaced with corresponding activity taken from second column of the ```activities``` variable  
6. **Appropriately labels the data set with descriptive variable names**  
    * ```code``` column in ```TidyData``` renamed into activities  
    * All `Acc` in column’s name replaced by `Accelerometer` 
    * All `Gyro` in column’s name replaced by `Gyroscope` 
    * All `BodyBody` in column’s name replaced by `Body`  
    * All `Mag` in column’s name replaced by `Magnitude`  
    * All start with character `f` in column’s name replaced by `Frequency`  
    * All start with character `t` in column’s name replaced by `Time`  
7. **From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject**  
    * `Data_Final` is created by sumarizing `TidyData` taking the means of each variable for each activity and each subject, after groupped by subject and activity.  
    * Export `FinalData` into `FinalData.txt` file.


