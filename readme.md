
# UCI HAR Summary Statistics Project - ReadMe

## Summary
This repository contains my submission of the course project for the [Getting and Cleaning Data](https://www.coursera.org/course/getdata) course, part of the [Johns Hopkins University Data Science Specialization Certificate](https://www.coursera.org/specialization/jhudatascience/1).

For the project, students were asked to compile a summary dataset based on a larger complete dataset from the UC Irvine Machine Learning Repository. The dataset used for this exercise was [Human Activity Recognition Using Smartphones](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones) [1] which contains device readings from a smartphone that was carried by subjects as they performed various movements and activities.

## Files

The repository contains the following files:
* readme.md: This file.
* run_analysis.r: An R script that performs the data manipulations and outputs the resulting dataset.
* CodeBook.md: A data code book that contains descriptions of the output data along with a description of how the output was constructed from the input dataset.
* average_vals.txt: The output dataset generated by running the script on the input data.

## How to Run

Download and unzip the UCI HAR dataset (available [here])(http://archive.ics.uci.edu/ml/machine-learning-databases/00240/UCI%20HAR%20Dataset.zip). Place the run_analysis.r script in the parent directory of the UCI HAR Dataset folder and run it. You should see a success message from the script and notice that the average_vals.txt file has been generated.

## Program Structure

The HAR dataset partitions the data into two sets: the training set and the test set. For our purposes, we wish to combine them into one set in order to summarize the entire dataset, and so the first step in processing each file type is to read in both the training file and the test file and combine them into one dataframe.

The first file, features.txt, contains labels for the 561 features in the observation vector. These features represent readings from the internal motion sensors in the smartphone carried by the subjects. For a detailed discussion of these features please refer to the [UCI HAR website](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones). Since we are only interested in features that represent the mean and standard deviation of the smartphone data, we search the feature labels to find the indices of these particular features and store them for later reference.

Next, we read and combine the observation vectors from the training and test set. These files are named X_train.txt and X_test.txt. We use the stored indices of features we are interested in to include only those in our dataframe. The dataframe is then assigned names corresponding to the names in the original dataset in order to allow the user to cross-reference them easily.

The data for activity and subject identifiers are stored in separate files and so those are read in next. The file names are y_train.txt and y_test.txt for the activity ids, and subject_train.txt and subject_test.txt for the subject ids. Again, the test and training data are combined into one dataframe and a meaningful name is assigned.

Since the activity identifiers are coded numerically, we read in the labels corresponding to each numeric code from the file activity_labels.txt. We then construct a factor variable to store activity codes along with their labels in a more intuitive format.

At this point all the data that we need has been read in. We need to combine the data, summarize it by taking the mean of each feature across all observations that correspond to each combination of subject and activity, and output the resulting dataset. The summary dataframe is created using R's aggregate() function, passing our subject id and activity id vectors as partitioning elements. This function breaks the dataframe up into subsets based on the partitioning elements and applies the summary function (in this case mean()) to each subset. The result is a dataframe where each row corresponds to one combination of subject and activity. This dataframe is then written to the output file average_vals.txt and the script terminates.

## Source Data Citation

[1] Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012