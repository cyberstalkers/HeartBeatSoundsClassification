HeartBeat Sounds Classification  
---
**Introduction**  
"Heart Diseases" refers to a broad spectrum of diseases, and coronary heart disease is the major cause of death among them. Millions of people experience irregular or abnormal heartbeats, called arrhythmias. Most of the time, they are harmless and happen in healthy people free of heart disease. However, some abnormal heart rhythms can be serious or even deadly. Hence, improving the accuracy of diagnosing as arrhythmias is of great importance to medical science.  

The dataset Heartbeat Sounds comes from [Kaggle](https://www.kaggle.com/kinguistics/heartbeat-sounds). Data was gathered in real-world situations and frequently contains background noise of every conceivable type.   

The problem is of particular interest to machine learning researchers as it involves classification of audio sample data. The differences between heart sounds corresponding to different heart symptoms can be extremely subtle and challenging to separate. Success in classifying this form of data requires extremely robust classifiers. Despite its medical significance, to date this is a relatively unexplored application for machine learning.  

**Approach Description**  
1. Preprocessing: construct low-pass filter to remove noise; data stratification.
2. Classification training: LDA, SVM, Random forest and CNN.
3. Evaluation.  

**Programming**  
Python  

**Results**  
1. LDA  

#|Accuracy%|Artifact Sens.%|Artifact Spec.%|Extrahls Sens.%|Extrahls Spec.%|Murmur Sens.%|Murmur Spec.%|Normal Sens%| Normal Spec.%  
---|---|---|--- |--- |--- |--- |--- |--- |---   
1|6.45| 0| 38| 0| 75| 22.22| 72.73| 0| 100  
2|19.35| 10 |76.19 |40 |69.23| 25 |65.22 |12.5 |82.61  
3|26 |32| 64.29 |18 |75 |21.25| 85.65 |27.5 |75.22  
4| 50 |／ |／ |／ |／| ／| ／| ／ |／  

*Multilabel-indicator is not supported for confusion matrix, so we cannot get sensitivity and specificity for model 4*  
LDA model performed well at separating Artifact and Normal classes. The specificity rate of Murmur is also remarkable.  

2. SVM: Accuracy rate of different kernels used with different dataset  

Kernel|Original| Lowpass filter| Lowpass + stratified  
---|---|---|---  
linear| 19%| 29%| 35%  
poly| 13%| 32%| 35%  
rbf| 16%| 23%| 32%    

Not much difference between using different kernels and different dataset.  

3. Random Forest  

#|Accuracy%|Artifact Sens.%|Artifact Spec.%|Extrahls Sens.%|Extrahls Spec.%|Murmur Sens.%|Murmur Spec.%|Normal Sens%| Normal Spec.%  
---|---|---|--- |--- |--- |--- |--- |--- |---   
1| 38.39| 65 |49.05| 0 |100 |86.25| 79.57| 16.25| 96.09  
2| 42.26| 60 |60 |0 |99.62 |82.5 |67.39 |6.25 |91.74  
3| 48.71 |／ |／ |／ |／| ／| ／| ／ |／   

Random Forest model has an accuracy rate around 49%, and good at separating Artifact and Murmur classes.  

4. CNN  

Model|Accuracy rate %  
---|---  
1: Original dataset| 64.5  
2: 1+lowpass filter| **80.6**   
3: 2+stratification| 77.4   
