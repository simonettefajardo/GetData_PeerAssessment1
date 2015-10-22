##3) a code book that describes the variables, the data, and any transformations or work 
##that you performed to clean up the data called CodeBook.md. 

##This repo explains how all of the scripts work and how they are connected.  



##1. Merges the training and the test sets to create one data set.

###1.1 Read all files and  store in separate dataframes
    
    ####read activity_labels  and features files

    activity_labels<-read.csv('UCI HAR Dataset/activity_labels.txt',sep=" ",header=FALSE)
    features<-read.csv('UCI HAR Dataset/features.txt',sep=" ",header=FALSE)

    ####read train folder files :
    X_train<-read.csv('UCI HAR Dataset/train/X_train.txt',sep = "",header = FALSE)
    y_train<-read.csv('UCI HAR Dataset/train/y_train.txt',sep = "",header = FALSE)
    subject_train<-read.csv('UCI HAR Dataset/train/subject_train.txt',sep = "",header = FALSE)
    body_acc_x_train<-read.csv('UCI HAR Dataset/train/Inertial Signals/body_acc_x_train.txt',sep = "",header = FALSE)
    body_acc_y_train<-read.csv('UCI HAR Dataset/train/Inertial Signals/body_acc_y_train.txt',sep = "",header = FALSE)
    body_acc_z_train<-read.csv('UCI HAR Dataset/train/Inertial Signals/body_acc_z_train.txt',sep = "",header = FALSE)
    body_gyro_x_train<-read.csv('UCI HAR Dataset/train/Inertial Signals/body_gyro_x_train.txt',sep = "",header = FALSE)
    body_gyro_y_train<-read.csv('UCI HAR Dataset/train/Inertial Signals/body_gyro_y_train.txt',sep = "",header = FALSE)
    body_gyro_z_train<-read.csv('UCI HAR Dataset/train/Inertial Signals/body_gyro_z_train.txt',sep = "",header = FALSE)
    total_acc_x_train<-read.csv('UCI HAR Dataset/train/Inertial Signals/total_acc_x_train.txt',sep = "",header = FALSE)
    total_acc_y_train<-read.csv('UCI HAR Dataset/train/Inertial Signals/total_acc_y_train.txt',sep = "",header = FALSE)
    total_acc_z_train<-read.csv('UCI HAR Dataset/train/Inertial Signals/total_acc_z_train.txt',sep = "",header = FALSE)

    ####read test folder files:
    X_test<-read.csv('UCI HAR Dataset/test/X_test.txt',sep = "",header = FALSE)
    y_test<-read.csv('UCI HAR Dataset/test/y_test.txt',sep = "",header = FALSE)
    subject_test<-read.csv('UCI HAR Dataset/test/subject_test.txt',sep = "",header = FALSE)
    body_acc_x_test<-read.csv('UCI HAR Dataset/test/Inertial Signals/body_acc_x_test.txt',sep = "",header = FALSE)
    body_acc_y_test<-read.csv('UCI HAR Dataset/test/Inertial Signals/body_acc_y_test.txt',sep = "",header = FALSE)
    body_acc_z_test<-read.csv('UCI HAR Dataset/test/Inertial Signals/body_acc_z_test.txt',sep = "",header = FALSE)
    body_gyro_x_test<-read.csv('UCI HAR Dataset/test/Inertial Signals/body_gyro_x_test.txt',sep = "",header = FALSE)
    body_gyro_y_test<-read.csv('UCI HAR Dataset/test/Inertial Signals/body_gyro_y_test.txt',sep = "",header = FALSE)
    body_gyro_z_test<-read.csv('UCI HAR Dataset/test/Inertial Signals/body_gyro_z_test.txt',sep = "",header = FALSE)
    total_acc_x_test<-read.csv('UCI HAR Dataset/test/Inertial Signals/total_acc_x_test.txt',sep = "",header = FALSE)
    total_acc_y_test<-read.csv('UCI HAR Dataset/test/Inertial Signals/total_acc_y_test.txt',sep = "",header = FALSE)
    total_acc_z_test<-read.csv('UCI HAR Dataset/test/Inertial Signals/total_acc_z_test.txt',sep = "",header = FALSE)

###1.2 Append each test data to corresponding train data
    X_train_test_append<-rbind(X_train,X_test)
    y_train_test_append<-rbind(y_train,y_test)
    colnames(subject_test)<-colnames(subject_train)
    subject_train_test_append<-rbind(subject_train,subject_test)
    body_acc_x_train_test_append<-rbind(body_acc_x_train,body_acc_x_test)
    body_acc_y_train_test_append<-rbind(body_acc_y_train,body_acc_y_test)
    body_acc_z_train_test_append<-rbind(body_acc_z_train,body_acc_z_test)
    body_gyro_x_train_test_append<-rbind(body_gyro_x_train,body_gyro_x_test)
    body_gyro_y_train_test_append<-rbind(body_gyro_y_train,body_gyro_y_test)
    body_gyro_z_train_test_append<-rbind(body_gyro_z_train,body_gyro_z_test)
    total_acc_x_train_test_append<-rbind(total_acc_x_train,total_acc_x_test)
    total_acc_y_train_test_append<-rbind(total_acc_y_train,total_acc_y_test)
    total_acc_z_train_test_append<-rbind(total_acc_z_train,total_acc_z_test)
    
###1.3 Label columns of dataframes obtained in step 1.2
    colnames(X_train_test_append)<-features$V2
    colnames(subject_train_test_append)<-c("subject_id")
    colnames(y_train_test_append)<-c("activity_id")
    colnames(activity_labels)<-c("activity_id","activity")
    colnames(body_acc_x_train_test_append)<-gsub("V","body_acc_x_train_test",names(body_acc_x_train_test_append))
    colnames(body_acc_y_train_test_append)<-gsub("V","body_acc_y_train_test",names(body_acc_y_train_test_append))
    colnames(body_acc_z_train_test_append)<-gsub("V","body_acc_z_train_test",names(body_acc_z_train_test_append))
    colnames(body_gyro_x_train_test_append)<-gsub("V","body_gyro_x_train_test",names(body_gyro_x_train_test_append))
    colnames(body_gyro_y_train_test_append)<-gsub("V","body_gyro_y_train_test",names(body_gyro_y_train_test_append))
    colnames(body_gyro_z_train_test_append)<-gsub("V","body_gyro_z_train_test",names(body_gyro_z_train_test_append))
    colnames(total_acc_x_train_test_append)<-gsub("V","total_acc_x_train_test",names(total_acc_x_train_test_append))
    colnames(total_acc_y_train_test_append)<-gsub("V","total_acc_y_train_test",names(total_acc_y_train_test_append))
    colnames(total_acc_z_train_test_append)<-gsub("V","total_acc_z_train_test",names(total_acc_z_train_test_append))
    
###1.4 Merge dataframes into one dataset
    
    ##merge test data with subject data
    X_subject<-cbind(subject_train_test_append,X_train_test_append)
   
    ##merge Inertial signals dataframes
    inertial_signals<-cbind(body_acc_x_train_test_append,
                            body_acc_y_train_test_append,
                            body_acc_z_train_test_append,
                            body_gyro_x_train_test_append,
                            body_gyro_y_train_test_append,
                            body_gyro_z_train_test_append,
                            total_acc_x_train_test_append,
                            total_acc_y_train_test_append,
                            total_acc_z_train_test_append)
    ##merge all dataframes into one dataframe
    All_data_merged<-cbind(X_subject,y_train_test_append,inertial_signals)
    
    
###2. Extracts only the measurements on the mean and standard deviation for each measurement.    
   
   All_data_mean_std<-All_data_merged[,c(1:7,42:46,81:86,122:127,162:166,202:203,215:216,228:229,241:242,254:255,267:272,346:351,425:430,504:505,517:518,530:531,543:544)]   

###3. Uses descriptive activity names to name the activities in the data set
   
   All_data_merged_labelled<-merge(activity_labels,All_data_merged,by=c("activity_id"))
    
###4. Appropriately labels the data set with descriptive variable names. 
    
    ##done in step 1.3 Label columns of dataframes obtained .....RE: All_data_merged_labelled
    
###5. From the data set in step 4, creates a second, independent tidy data set 
###with the average of each variable for each activity and each subject.
    
    ##load dplyr library
    library(dplyr)
   
    ##Group Data by activity and by subject_id
    by_activity_subject<-group_by(All_data_merged_labelled,activity,subject_id)
    
    ##Get mean of each variable column by applying summarise_each
    Ave_by_activity_subject<-summarise_each(by_activity_subject,funs(mean))
    
    ##write resulting table into a text file  Ave_by_activity_subject.txt
    write.table(Ave_by_activity_subject,file="Ave_by_activity_subject.txt",row.names = FALSE)