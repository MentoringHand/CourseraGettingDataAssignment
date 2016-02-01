# Introduction

This repository created for an assignment as part of the Coursera course <a href="https://www.coursera.org/learn/data-cleaning/">Getting and Cleaning data</a>.

The data set present is a tidier data that is downloaded from <a href="https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip">https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip</a>.

* <b>Dataset</b>: activity_subject_summary.txt

* <b>Description</b>: This is the data set with the average of each measurement for each activity and each subject.

* <b>Code Used for Transformation</b>: run_analysis.R

## Description of the code

The analysis function reads the files from the actual dataset and transforms to our needs to make tidier data set which can be used for analysis.


* Read the features list from features.txt file. There are some duplicate columns which will cause problems while filtering based on column name. So a unique columnn concatenating both the column values is created. This unique column will be used as header for the dataset.

	features <- tbl_df(read.table("UCI HAR Dataset/features.txt", stringsAsFactors=FALSE, col.names = c("fid", "fnm"))) %>% 
	            mutate(varname = paste(fid,fnm))
</code>

  * Load different activities in a data frame.
  
<code>
activities <- read.table("UCI HAR Dataset/activity_labels.txt", stringsAsFactors=FALSE, col.names = c("activity", "activityname"))
</code>

  # Data provided is scattered in three different files. These files are identified with format x_* , subject*, and y_*.
  # Set corresponding column names.
  
  # Get the test data from X_test, subject_test, y_test and column bind them all to get single table with test data.
  xtest <- read.table("UCI HAR Dataset/test/X_test.txt", stringsAsFactors=FALSE)
  names(xtest) <- features$varname
  xtestsubject <- read.table("UCI HAR Dataset/test/subject_test.txt", stringsAsFactors=FALSE, col.names = c("subject"))
  xtestactivity <- read.table("UCI HAR Dataset/test/y_test.txt", stringsAsFactors=FALSE, col.names = c("activity"))
  xtest <- cbind(xtestsubject, xtestactivity, xtest)

  # Get the test data from X_train, subject_train, y_train and column bind them all to get single table with train data.
  xtrain <- read.table("UCI HAR Dataset/train/X_train.txt", quote="\"", comment.char="", stringsAsFactors=FALSE)
  names(xtrain) <- features$varname
  xtrainsubject <- read.table("UCI HAR Dataset/train/subject_train.txt", quote="\"", comment.char="", stringsAsFactors=FALSE, col.names = c("subject"))
  xtrainactivity <- read.table("UCI HAR Dataset/train/y_train.txt", quote="\"", comment.char="", stringsAsFactors=FALSE, col.names = c("activity"))
  xtrain <- cbind(xtrainsubject, xtrainactivity, xtrain)
  
  # Combine the test and train data using rowbind and select only those columsn that end with std() and mean() to 
  # get the standard deviation and mean of individual measurements.
  xall <- tbl_df(rbind(xtest, xtrain)) %>%
          select (1, 2, ends_with("-std()"), ends_with("-mean()") )

  # Join the result data with activities table to resolve the activityId to actual name and remove the
  # activity column as it is redundant.
  x3 <- select(tbl_df(merge(activities, xs)), -activity)
  
  # Make the names removing unnecessary punctuations and meaning less numbers.
  names(x3) <- gsub("\\(\\)", "",gsub("^[0-9]{3} ", "",names(x3)))

  # At this point of time the data frame x3 is the tidier data that can be used for any further analysis.
  
  # As there are multiple obervations for particular activity and subject. To get mean over each 
  # combination we set group_by over x3 on activityname and subject. Then summarise the 
  # data with mean function group by activityname and subject.
  activity_subject_summary <- group_by(x3, activityname, subject) %>% summarise_each(c("mean"))
  
  # Write the end result to a file.
  write.table(activity_subject_summary, file = "activity_subject_summary.txt", row.names=FALSE)
}

