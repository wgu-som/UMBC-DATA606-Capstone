
# Using Machine Learning to Predict Need of Blood Transfusions with Patient Vital Signs Features
### Prepared for UMBC Data Science Master Degree Capstone by Dr Chaojie (Jay) Wang  
### William Gu
### https://github.com/wgu-som/UMBC-DATA606-Capstone

---

## Background

Blood is a valuable resorce in hospitals. There have been several studies dedicated to reviewing restrictive and liberal blood transfusion strategies and those have largely shown that giving patients more blood
than necessary does not usually improve outcomes. Modern clinical practice focuses on giving the right patient the right amount of blood at the right time, in this way making the most of their resources while still
saving as many patients as possible. This project will attempt to see if machine learning techniques can aid clinicians in making decisions on whether or not a patient will need blood transfusions based on their vital signs. We will mainly be focusing on the Critical Administration Threshold (CAT) which is defined as the usage of 3 or more units of packed red blood cells (PRBCs) within 1 hour. CAT has historically been used as a way to identify critically bleeding patients so we would like to see if our machine learning process can distinguish a CAT patient vs a non CAT patient. If time allows, I would also like to see if the model can predict whether a patient will receive any amount of blood (not just CAT).

## Data

For this project, we will use a deidentified dataset of 1202 patients data in the form of calculated features of their first 15 minutes of recorded vital signs. This patients in this dataset are all coming from the R Adams Cowley Shock Trauma Center in Baltimore. The frequency of the vital signs is 1/6 Hz for trend values and 240Hz for waveform values. The dataset is in tabular format in an Excel sheet with size 1202x428 with each row representing a patient and each column representing a feature. It may seem like a lot of features, though many are repeated for multiple vital signs (5 number summaries/percentiles/etc) and a significant number will likely be removed in the feature selection process. Due to not having raw data, the size of the data set is relatively small at only about 40MB. I have also included a table with demographics summaries for the CAT and non CAT populations including age, gender, race, and injury types.

### Data Dictionary  
id - String; Number that represents each patient in the form P2_XXXX  
CAT - **Target variable** String; YES if patient met CAT, NO if not  
Any Blood - **Target variable** String; YES if patient recieved any amount of blood, NO if not  

Features:  
The following features are shared over all trend vital signs (HR, SPO2p, SBP, MBP, DBP, RESP, SI, PP) in the form [Vital Sign]_[Feature]  
Mean - Float; Numerical average of vital signs  
STD - Float; Standard deviation of vital signs  
Variance - Float; Variance of vital signs  
Min - Int; Lowest value of vital signs  
Max - Int; Highest value of vital signs  
CoeffOfVar - Float; Coefficient of Variance of vital signs  
10pctl/20pctl.../90pctl - Float; 10th through 90th percentiles of vital signs  
1stquartile - Float; 1st quartile of vital signs  
3rdquartile - Float; 3rd quartile of vital signs  
IQR - Float; Interquartile range of vital signs (3rd quartile - 1st quartile)  
Skewness - Float; Skewness of vital signs (Asymmetry of the probability distribution about its mean)  
Kurtosis - Float; Kurtosis of vital signs (Degree of tailedness in the probability distribution)  
pct_gtX - Float; Percentage of time vital signs were greater than X  
pct_ltX - Float; Percentage of time vital signs were less than X  
Dose_gtX - Float; Area above the curve of the percentage of time vital signs were greater than X  
Dose_ltX - Float; Area above the curve of the percentage of time vital signs was less than X  
ShannonEntropy Float; Shannon entropy measurement of uncertainty/randomness in vital signs  

The following features are shared over the waveform vital signs (ECG2w, PPGw) in the form [Vital Sign]_[Feature]  
meanNN - Float; Mean Normal-to-Normal in vital signs (mean time between consecutive normal R-waves)  
minNN - Float; Lowest Normal-to-Normal in vital signs  
maxNN - Float; Highest Normal-to-Normal in vital signs  

The following features are also shared over waveform vital signs, but are different algorithms for Heart Rate Variability (welch, lomb, ar) in the form [Vital Sign]\_FD\_[Algorithm]_[Feature]  
avlf - Float; Frequency Domain of algorithm's power spectral density estimation at very low frequency
alf - Float; Frequency Domain of algorithm's power spectral density estimation at low frequency

---

## References

Trentino, K.M., Farmer, S.L., Leahy, M.F. et al. Systematic reviews and meta-analyses comparing mortality in restrictive and liberal haemoglobin thresholds for red cell transfusion: an overview of systematic reviews. BMC Med 18, 154 (2020). https://doi.org/10.1186/s12916-020-01614-w

Hovaguimian, F., & Myles, P. S. (2016). Restrictive versus liberal transfusion strategy in the perioperative and acute care settings: A context-specific systematic review and meta-analysis of randomized controlled trials. Anesthesiology, 125(1), 46-61. https://doi.org/10.1097/ALN.0000000000001162

Matzek, L. J., Hanson, A. C., Schulte, P. J., Cureton, K. D., Kor, D. J., & Warner, M. A. (2024). Life-threatening hemorrhage as defined by the critical administration threshold in nontraumatic critical bleeding: A descriptive observational study. Transfusion, 64(10), 1841–1850. https://doi.org/10.1111/trf.17996