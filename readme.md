
# UCI HAR Summary Statistics Project - ReadMe

## Summary
This repository contains my submission of the course project for the [Getting and Cleaning Data](https://www.coursera.org/course/getdata) course, part of the [Johns Hopkins University Data Science Specialization Certificate](https://www.coursera.org/specialization/jhudatascience/1).

For the project, students were asked to compile a summary dataset based on a full dataset from the UC Irvine Machine Learning Repository. The dataset used for this exercise was [Human Activity Recognition Using Smartphones](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones) which contains device readings from a smartphone that was carried by subjects as they performed various movements and activities.

## Files

The repository contains the following files:
* readme.md: This file.
* run_analysis.r: An R script that performs the data manipulations and outputs the resulting dataset.
* CodeBook.md: A data code book that contains descriptions of the output data along with a description of how the output was constructed from the input dataset.
* average_vals.txt: The output dataset generated by running the script on the input data.

## How to Run

Download and unzip the UCI HAR dataset (available [here](http://archive.ics.uci.edu/ml/machine-learning-databases/00240/UCI%20HAR%20Dataset.zip). Place the run_analysis.r script in the parent directory of the UCI HAR Dataset folder and run it. You should see a success message from the script and notice that the average_vals.txt file has been generated.