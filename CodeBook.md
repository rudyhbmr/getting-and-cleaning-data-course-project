# Code Book

The data set that this code book pertains to is located in the `averages_tidydata.txt` file of this repository.

See the `README.md` file of this repository for background information on this data set.

The structure of the data set is described in the [Data](#data) section, its variables are listed in the [Variables](#variables) section, and the transformations that were carried out to obtain the data set based on the source data are presented in the [Transformations](#transformations) section.

## Data <a name="data"></a>

The `averages_tinydata.txt` data file is a text file, containing space-separated values.

## Feature Variables <a name="variables"></a>

Each row contains, for a given subject and activity, 66 averaged signal measurements.

### Identifiers <a name="identifiers"></a>

- `subject`

	Subject identifier, integer, ranges from 1 to 30.

- `activity`

	Activity identifier, string with 6 possible values: 
	- `WALKING`: subject was walking
	- `WALKING_UPSTAIRS`: subject was walking upstairs
	- `WALKING_DOWNSTAIRS`: subject was walking downstairs
	- `SITTING`: subject was sitting
	- `STANDING`: subject was standing
	- `LAYING`: subject was laying

### Average of measurements <a name="average-measurements"></a>

All measurements are floating-point values, normalised and bounded within [-1,1].

Prior to normalisation, acceleration measurements (variables containing `Accelerometer`) were made in *g*'s (9.81 m.s⁻²) and gyroscope measurements (variables containing `Gyroscope`) were made in radians per second (rad.s⁻¹).

Magnitudes of three-dimensional signals (variables containing `Magnitude`) were calculated using the Euclidean norm.

The measurements are classified in two domains:

- Time-domain signals (variables prefixed by `time`), resulting from the capture of accelerometer and gyroscope raw signals.

- Frequency-domain signals (variables prefixed by `frequency`), resulting from the application of a Fast Fourier Transform (FFT) to some of the time-domain signals.

#### Time-domain signals

-timeBodyAccelerometerMeanX
-timeBodyAccelerometerMeanY
-timeBodyAccelerometerMeanZ
-timeBodyAccelerometerStandardDeviationX
-timeBodyAccelerometerStandardDeviationY
-timeBodyAccelerometerStandardDeviationZ
-timeGravityAccelerometerMeanX
-timeGravityAccelerometerMeanY
-timeGravityAccelerometerMeanZ
-timeGravityAccelerometerStandardDeviationX
-timeGravityAccelerometerStandardDeviationY
-timeGravityAccelerometerStandardDeviationZ
-timeBodyAccelerometerJerkMeanX
-timeBodyAccelerometerJerkMeanY
-timeBodyAccelerometerJerkMeanZ
-timeBodyAccelerometerJerkStandardDeviationX
-timeBodyAccelerometerJerkStandardDeviationY
-timeBodyAccelerometerJerkStandardDeviationZ
-timeBodyGyroscopeMeanX
-timeBodyGyroscopeMeanY
-timeBodyGyroscopeMeanZ
-timeBodyGyroscopeStandardDeviationX
-timeBodyGyroscopeStandardDeviationY
-timeBodyGyroscopeStandardDeviationZ
-timeBodyGyroscopeJerkMeanX
-timeBodyGyroscopeJerkMeanY
-timeBodyGyroscopeJerkMeanZ
-timeBodyGyroscopeJerkStandardDeviationX
-timeBodyGyroscopeJerkStandardDeviationY
-timeBodyGyroscopeJerkStandardDeviationZ
-timeBodyAccelerometerMagnitudeMean
-timeBodyAccelerometerMagnitudeStandardDeviation
-timeGravityAccelerometerMagnitudeMean
-timeGravityAccelerometerMagnitudeStandardDeviation
-timeBodyAccelerometerJerkMagnitudeMean
-timeBodyAccelerometerJerkMagnitudeStandardDeviation
-timeBodyGyroscopeMagnitudeMean
-timeBodyGyroscopeMagnitudeStandardDeviation
-timeBodyGyroscopeJerkMagnitudeMean
-timeBodyGyroscopeJerkMagnitudeStandardDeviation

#### Frequency-domain signals

-frequencyBodyAccelerometerMeanX
-frequencyBodyAccelerometerMeanY
-frequencyBodyAccelerometerMeanZ
-frequencyBodyAccelerometerStandardDeviationX
-frequencyBodyAccelerometerStandardDeviationY
-frequencyBodyAccelerometerStandardDeviationZ
-frequencyBodyAccelerometerJerkMeanX
-frequencyBodyAccelerometerJerkMeanY
-frequencyBodyAccelerometerJerkMeanZ
-frequencyBodyAccelerometerJerkStandardDeviationX
-frequencyBodyAccelerometerJerkStandardDeviationY
-frequencyBodyAccelerometerJerkStandardDeviationZ
-frequencyBodyGyroscopeMeanX
-frequencyBodyGyroscopeMeanY
-frequencyBodyGyroscopeMeanZ
-frequencyBodyGyroscopeStandardDeviationX
-frequencyBodyGyroscopeStandardDeviationY
-frequencyBodyGyroscopeStandardDeviationZ
-frequencyBodyAccelerometerMagnitudeMean
-frequencyBodyAccelerometerMagnitudeStandardDeviation
-frequencyBodyAccelerometerJerkMagnitudeMean
-frequencyBodyAccelerometerJerkMagnitudeStandardDeviation
-frequencyBodyGyroscopeMagnitudeMean
-frequencyBodyGyroscopeMagnitudeStandardDeviation
-frequencyBodyGyroscopeJerkMagnitudeMean
-frequencyBodyGyroscopeJerkMagnitudeStandardDeviation

## Transformations <a name="transformations"></a>

The zip file containing the source data is located at [https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip).

The following transformations were applied to the source data by running the `run_analysis.R` script.

1. The training and test sets were merged to create one data set.
1. The measurements on the mean and standard deviation (i.e. signals containing the strings `mean` and `std`) were extracted from the merged data set.
1. The activity identifiers (originally coded as integers between 1 and 6) were replaced with descriptive activity names based on `activity_labels.txt`.
1. The variable names were replaced with descriptive variable names using the following set of rules:
	- Special characters (i.e. `(`, `)`, and `-`) were removed
	- The initial `f` and `t` were expanded to `frequency` and `time` respectively.
	- `Acc`, `Gyro`, `Mag`, `Freq`, , `BodyBody`, `mean`, and `std` were replaced with `Accelerometer`, `Gyroscope`, `Magnitude`, `Frequency`, `Body`, `Mean`, and `StandardDeviation` respectively.
1. From the data set in step 4, the final data set was created with the average of each variable for each activity and each subject.
