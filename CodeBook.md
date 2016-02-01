#Introduction

The result of the data set submitted as part of this assignment is created from data downloaded from <a href="https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip">https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip</a>.

* <b>Dataset</b>: activity_subject_summary.txt

* <b>Description</b>: This is the data set with the average of each measurement for each activity and each subject.

The orginal data set contains multiple measurements from the experiments carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 

<ol>
<li><b>activityname             </b>: Character : This column consists of 6 different values WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING</li>
<li><b>subject                  </b>: integer : This column represents the subject involved in the experiment. There are altogether 30 volunteers. Each volunteer is identified by a number 1 through 30.  </li>
<li><b>tBodyAccMag-std          </b>: number : Average value of this measurement for given subject and given activity   </li>
<li><b>tGravityAccMag-std       </b>: number : Average value of this measurement for given subject and given activity   </li>
<li><b>tBodyAccJerkMag-std      </b>: number : Average value of this measurement for given subject and given activity   </li>
<li><b>tBodyGyroMag-std         </b>: number : Average value of this measurement for given subject and given activity  </li>
<li><b>tBodyGyroJerkMag-std     </b>: number : Average value of this measurement for given subject and given activity  </li>
<li><b>fBodyAccMag-std          </b>: number : Average value of this measurement for given subject and given activity  </li>
<li><b>fBodyBodyAccJerkMag-std  </b>: number : Average value of this measurement for given subject and given activity  </li>
<li><b>fBodyBodyGyroMag-std     </b>: number : Average value of this measurement for given subject and given activity  </li>
<li><b>fBodyBodyGyroJerkMag-std </b>: number : Average value of this measurement for given subject and given activity  </li>
<li><b>tBodyAccMag-mean         </b>: number : Average value of this measurement for given subject and given activity  </li>
<li><b>tGravityAccMag-mean      </b>: number : Average value of this measurement for given subject and given activity  </li>
<li><b>tBodyAccJerkMag-mean     </b>: number : Average value of this measurement for given subject and given activity  </li>
<li><b>tBodyGyroMag-mean        </b>: number : Average value of this measurement for given subject and given activity  </li>
<li><b>tBodyGyroJerkMag-mean    </b>: number : Average value of this measurement for given subject and given activity  </li>
<li><b>fBodyAccMag-mean         </b>: number : Average value of this measurement for given subject and given activity  </li>
<li><b>fBodyBodyAccJerkMag-mean </b>: number : Average value of this measurement for given subject and given activity  </li>
<li><b>fBodyBodyGyroMag-mean    </b>: number : Average value of this measurement for given subject and given activity  </li>
<li><b>fBodyBodyGyroJerkMag-mean</b>: number : Average value of this measurement for given subject and given activity  </li>
</ol>

###Legend
The column names can be understood following the description below
*<b>t</b>: Any column starting with t represent time domain signals.
*<b>f</b>: Any column starting with f represent frequency domain signals.
*<b>BodyAcc</b>: Rerepsent measuremetn corresponding to body acceleration signals.
*<b>GravityAcc</b>: Rerepsent measuremetn corresponding to gravity acceleration signals.
*<b>Mag</b>: Represent magnitude.


