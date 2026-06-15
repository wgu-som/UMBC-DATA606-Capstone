
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

For this project, we will use a deidentified dataset of 1202 patients data in the form of calculated features of their first 15 minutes of recorded vital signs. This data is all coming from the R Adams Cowley Shock Trauma Center in Baltimore. 



---

## References

Trentino, K.M., Farmer, S.L., Leahy, M.F. et al. Systematic reviews and meta-analyses comparing mortality in restrictive and liberal haemoglobin thresholds for red cell transfusion: an overview of systematic reviews. BMC Med 18, 154 (2020). https://doi.org/10.1186/s12916-020-01614-w

Hovaguimian, F., & Myles, P. S. (2016). Restrictive versus liberal transfusion strategy in the perioperative and acute care settings: A context-specific systematic review and meta-analysis of randomized controlled trials. Anesthesiology, 125(1), 46-61. https://doi.org/10.1097/ALN.0000000000001162

Matzek, L. J., Hanson, A. C., Schulte, P. J., Cureton, K. D., Kor, D. J., & Warner, M. A. (2024). Life-threatening hemorrhage as defined by the critical administration threshold in nontraumatic critical bleeding: A descriptive observational study. Transfusion, 64(10), 1841–1850. https://doi.org/10.1111/trf.17996