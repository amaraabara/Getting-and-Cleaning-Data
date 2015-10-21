---
title: "README"
author: "Amara"
date: "21 October 2015"
output: html_document
---

#### READ ME for run_analysis.R

This document provides a detailed description of the code within the run_analysis.R
script which was used to transform various data sets obtained from the Smartlab 
experiment into one tidy data set. 

For a description of the experiment run by Smartlab, please visit:
http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones

Also, for detailed descriptions of the variables used, please refer to the Code Book 
which can be located in the Git repository.

_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ 

The following steps and substeps below were used to create run_analysis.R which in turn 
generates tidyData.txt:

Note: The steps provided below have been excuted sequentially in run_analysis.R. This 
should enable the reader follow along quite easily.

1. Merge the training and the test sets to create one data set.

        a. Read all data sets related to the training and set data sets in. These inclcude: 
        
        	i. X_train.txt
        	ii. y_train.txt
        	iii. subject_train.txt
        	iv. activity_labels.txt
        	v. features.txt
        	vi. X_test.txt
        	vii. y_test.txt
        	viii. subject_test.txt
        
        b. Merge X_train and X_test using rbind 
        
        c. Merge y_train and y_test using rbind 
        
        d. Merge subject_train and subject_test using rbind
        
        e. Update the column names in the y and subject data sets to descriptive names
        
        d. Merge all 3 data sets into one data set using cbind 


2. Extracts only the measurements on the mean and standard deviation for each measurement. 
        
        a. Update the names of the data_set columns (col 3 - col 563) with the names provided
        in features.txt
        
        b. Using the grep function extract only the measurements on the mean and std into
        data_set.ex. Note: meanFreq as I believe this relates to the frequency of the mean not 
        the mean itself.


3. Uses descriptive activity names to name the activities in the data set.
        
        a. Extract the descriptive names of activiies into a list
        
        b. Assign the descriptive names to the activity column data_set.ex


4. Appropriately labels the data set with descriptive variable names. 

        a. Make the variable names more descriptive via the following:
        	i. Exclude all punctuations in the names
        	ii. Change "mean" and "std" to "Mean" and "Std" to maintain 
        	consistency in the format. 


5. From the data set in step 4, creates a second, independent tidy data set with the average
   of each variable for each activity and each subject.

        a. Using the dplyr package, find the requested average using group_by(), 
        summarise_each()
        and arrange. Once done, convert the output of this transformation into a data frame.
        
        b. Wite the output dataframe into a text file in the working directory


#### Conclusion

The data set obtained from the above steps complies with tidy data principles from week 1. 
It is of a long form with the the following dimension: 180 rows, 68 columns. 

To confirm compliance with the stipulated tidy data principles, the uploaded text file should 
be read into R and viewed using the code below:

```{r, eval=FALSE}
test.read <- read.table("tidyData.txt", header = TRUE)
View(test.read)
```


