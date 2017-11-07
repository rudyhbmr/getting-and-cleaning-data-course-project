# Getting and Cleaning Data Course Project
This repo serves as a course project for the `Getting and Cleaning Data` course in Coursera.

## Introduction
The purpose of this project is to demonstrate our ability to collect, work with, and clean a data set. The data used in this course project represents data collected from the accelerometers from the Samsung Galaxy S smartphone. A full description of the data used in this project can be found at [The UCI Machine Learning Repository](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones)

[The specific source data used in this project can be found here.](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip)

## Project Overview
The R script, run_analysis.R, found in this repo does the following in R Studio. (Note that the source data has to be downloaded beforehand and for the user to set the working directory in R Studio to where the source data is located)

-Read the relevent data sets needed for the analysis.
-Merge the data sets and assign appropriate column names
-From the merged data set, extract only columns of feature measurements that measure particular mean or standard deviation, the subjects that performed the experiment as well as the specific activity performed.
-Rename activity data values based on the labels given in `activity_labels.txt`.
-Rename variable names of features to be more decriptive and clean.
-Lastly, create a second, independent tidy data set called `averages_tidydata.txt` with the average of each variable for each activity and each subject.

