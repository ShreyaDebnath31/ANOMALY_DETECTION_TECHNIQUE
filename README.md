Title: Anomaly Detection Model for Pump Sensor Readings in Manufacturing Industry


Introduction The manufacturing industry heavily relies on critical assets such as pumps, motors, conveyor belts, and other heavy machinery. The reliability and availability of these assets are crucial for efficient operations and to avoid production loss. Anomalies or failures in these assets can lead to significant financial losses. Therefore, implementing an effective anomaly detection model becomes essential to mitigate risks, prevent unplanned downtime, and optimize maintenance strategies.

Problem Statement The goal of this project is to develop an anomaly detection model using unsupervised learning algorithms to analyse time series sensor readings from a pump. The objective is to detect anomalies in advance and enable proactive maintenance, minimize production losses, reduce unnecessary maintenance, and effectively manage critical components for the pump.

Data Preparation

The dataset consists of sensor readings from 52 sensors installed on the pump.

Link for dataset -  https://www.kaggle.com/datasets/nphantawee/pump-sensor-data

•	Data preprocessing steps included reading the CSV file, converting the timestamp column to datetime format, and dropping irrelevant columns.

•	Missing values were identified, and specific rows containing significant missing data were dropped.

•	The timestamp column was set as the index, and the remaining missing values were replaced with the median value.

•	Visualizations were performed to gain insights into the data distribution, sensor behaviour, and machine status.

 <img width="746" alt="Screenshot 2023-07-07 211028" src="https://github.com/ShreyaDebnath31/ANOMALY_DETECTION_TECHNIQUE/assets/96689098/04516a1c-5123-4860-ae0f-e8c0eb19d568">

 

Exploratory Data Analysis

•	Seaborn countplots were used to visualize the distribution of machine statuses, including 'NORMAL,' 'RECOVERING,' and 'BROKEN.'

 <img width="811" alt="Screenshot 2023-07-07 170813" src="https://github.com/ShreyaDebnath31/ANOMALY_DETECTION_TECHNIQUE/assets/96689098/cfde7bb8-21a7-4bbe-91ca-c50482412dc5">



•	Time series plots were generated for each sensor, with the 'BROKEN' state marked in red 'X' to identify abrupt variations.

<img width="817" alt="Screenshot 2023-07-07 170840" src="https://github.com/ShreyaDebnath31/ANOMALY_DETECTION_TECHNIQUE/assets/96689098/2126f06b-2343-4b88-855d-fbd27c278d00">


 
•	Daily and monthly time series plots were created to observe patterns and fluctuations in sensor readings.

<img width="751" alt="Screenshot 2023-07-07 171204" src="https://github.com/ShreyaDebnath31/ANOMALY_DETECTION_TECHNIQUE/assets/96689098/4149545d-3969-4337-8b53-a7d1a1ff7f2f">


 
•	Time resampling was performed to calculate daily averages, and time series plots with mean and standard deviation were generated.

<img width="787" alt="Screenshot 2023-07-07 171128" src="https://github.com/ShreyaDebnath31/ANOMALY_DETECTION_TECHNIQUE/assets/96689098/b8fbd5fa-76e7-4be8-a97a-125405485ba9">

 

Feature Extraction with PCA

•	Principle Component Analysis (PCA) was utilized to extract the most significant features from the dataset.

•	A pipeline was constructed to scale the data using StandardScaler and perform PCA.

•	The explained variance ratio was analysed to identify the most important principal components.


 <img width="839" alt="Screenshot 2023-07-07 171323" src="https://github.com/ShreyaDebnath31/ANOMALY_DETECTION_TECHNIQUE/assets/96689098/f63fae77-ee2f-464d-b8c7-a8b287cb3c50">


•	A new dataframe, df_new, was created with the extracted features.


Model Selection 


In this step, following learning algorithms were used to detect anomalies.

1.	K-Means Clustering
2.	Isolation Forest

K-Means Clustering
 
 
<img width="812" alt="Screenshot 2023-07-07 190848" src="https://github.com/ShreyaDebnath31/ANOMALY_DETECTION_TECHNIQUE/assets/96689098/95295094-d25a-42e8-91fc-9568f1114dc0">


<img width="811" alt="Screenshot 2023-07-07 190903" src="https://github.com/ShreyaDebnath31/ANOMALY_DETECTION_TECHNIQUE/assets/96689098/eba27e27-a73c-4315-95ce-3753340a5e19">


<img width="712" alt="Screenshot 2023-07-07 191003" src="https://github.com/ShreyaDebnath31/ANOMALY_DETECTION_TECHNIQUE/assets/96689098/d5b5a7a4-9c14-428c-bf7d-592d11ace3a2">



<img width="708" alt="Screenshot 2023-07-07 190927" src="https://github.com/ShreyaDebnath31/ANOMALY_DETECTION_TECHNIQUE/assets/96689098/1910a969-72ba-4125-b3b8-ec06f660a880">


<img width="716" alt="Screenshot 2023-07-07 190936" src="https://github.com/ShreyaDebnath31/ANOMALY_DETECTION_TECHNIQUE/assets/96689098/3719a76c-d3eb-44e6-a5c2-6f9c4236d784">


 <img width="727" alt="Screenshot 2023-07-07 190946" src="https://github.com/ShreyaDebnath31/ANOMALY_DETECTION_TECHNIQUE/assets/96689098/02c4fc6c-50aa-421a-b213-8293d42c82f5">


 
 
 
 

 
  

From the above results using silhouette score able to found that clusters = 3 is well suited.

Assuming that 13% of the entire data set are anomalies, found the distance between each point and centroid, using outlier fraction as 13 found the number of outliers and threshold distance is set as the minimum distance among the number of outliers’ largest distance. 

Then a new column is added in df_new as anomaly_1 which stores 1 for anomaly and 0 for normal.
 
<img width="715" alt="Screenshot 2023-07-07 202906" src="https://github.com/ShreyaDebnath31/ANOMALY_DETECTION_TECHNIQUE/assets/96689098/eb8c33c6-4a41-4eab-8ba4-b69521c53016">



Isolation Forest

Assuming that 13% of the entire data set are anomalies

 

Here I set an outlier fraction as 0.13 and made it equal to contamination
 
<img width="852" alt="Screenshot 2023-07-07 164945" src="https://github.com/ShreyaDebnath31/ANOMALY_DETECTION_TECHNIQUE/assets/96689098/c436399d-6387-4ccc-bdc3-2323e3581ed8">


Conclusion 

The anomaly detection model developed using unsupervised learning algorithms and time series sensor readings can provide valuable insights for maintenance managers in the manufacturing industry. By detecting anomalies in advance, the model enables proactive maintenance, minimizes production losses, and optimizes critical asset management. The findings from this project demonstrate the importance of implementing robust asset management frameworks and reliability engineering practices to ensure the integrity and reliability of critical assets in the manufacturing industry.
                                                                                                                   

                                                                                                         SUBMITTED BY:
                                                                                                         SHREYA DEBNTH
                                                                                                         BTECH CSE 3RD YEAR
