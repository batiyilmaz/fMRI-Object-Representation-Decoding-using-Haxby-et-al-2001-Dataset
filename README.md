# fMRI Object Representation Decoding using [Haxby et al. (2001)](https://pubmed.ncbi.nlm.nih.gov/11577229/) Dataset

[Haxby et al. (2001)](https://pubmed.ncbi.nlm.nih.gov/11577229/)


## Descriptions of Project Stages

**Preprocessing**

During the preliminary stage, the data of subjects 1-4 from the [Haxby et al. (2001)](https://pubmed.ncbi.nlm.nih.gov/11577229/) dataset were downloaded and subsetting was carried out to contain all the available 8 non-rest classes for the outcome variables. The preprocessing was performed by standardizing and detrending the predictor variable, functional Nifti images with BOLD data by using NiftiMasker() class/function from nilearn (Abraham et al., 2014). The rest of the analyses extensively employed classes/functions from scikit-learn (Pedregosa et al., 2011). Finally, a leave-one-run-out multi-class classification scheme was established to split the training and test set data for the processing.

**Data Analysis**

#### Classifier Performance Comparison (Multinomial Logistic Regression vs. Linear SVM using One-vs-Rest and One-vs-One Multi-Class Classification)

The prediction performance of the L2-penalized multinomial logistic regression was compared with L2-penalized linear support vector machine (SVM) classifiers with one-vs-rest and one-vs-one multi-class classification strategies respectively.

**Mean decoding accuracy for various classifiers**

Overall, the best performing model has been found to be the linear SVM with a one-vs-rest multi-class classification strategy with 55.09% mean decoding accuracy (see Figure 1).

![Figure 1](https://github.com/batiyilmaz/fMRI-Object-Representation-Decoding-Project-Haxby-et-al-2001-Dataset/blob/main/Figures/Figure_1.png)

**Subject variability**

  For the multinomial logistic regression, the final decoding performance of the 1st subject revealed 60.07% accuracy; 2nd subject showed 50.12% accuracy whereas the 3rd subject had 50.81% and, finally the model predicted with 48.61% accuracy for the 4th subject. In the case of linear SVM with one-vs-rest strategy, the model demonstrated 61.92% (Subject 1), 53.24% (Subject 2), 54.05% (Subject 3), and 51.16% (Subject 4) accuracy for each subject respectively. 

  Finally, the linear SVM with one-vs-one strategy had the predictive performance of 50.23%, 40.97%, 46.64%, and 41.32% accuracy for each subject respectively.
  
#### Decoding Accuracy (Percent True Positives) for the Individual Classes

#### Nested Cross-Validation Scheme for Finding the Optimal C Parameter

##### Decoding using the Optimal C

**References**

Abraham, A., Pedregosa, F., Eickenberg, M., Gervais, P., Mueller, A., Kossaifi, J., ... Varoquaux, G. (2014). Machine learning for neuroimaging with scikit-learn. Frontiers in Neuroinformatics, 8(14), 1-10.

Bishop, M. C. (2006). Linear models for regression. (In Jordan, M., Kleinberg, J., & Schölkoph, B. (Eds.)), Pattern recognition and machine learning. (1st ed., pp. 145-146). New York: Springer

Haxby, J. V, Gobbini, M. I., Furey, M. L., Ishai, A., Schouten, J. L., & Pietrini, P. (2001). Distributed and overlapping representations of faces and objects in ventral temporal cortex. Science, 293(5539), 2425–2430.

Pedregosa, F., Varoquaux, G., Gramfort, A., Michel, V., Thirion, B., Grisel, O., ... Duchesnay, É. (2011). Scikit-learn: Machine learning in Python. Journal of Machine Learning Research, 12, 2825–2830.

Rhys, I. H. (2020). Regression. (In Michaels, M., Warren, D., Dragosavljevic, A., Weidert, L., & Taylor, T. (Eds.)), Machine learning with R, the tidyverse, and mlr. (1st ed., pp. 258-261). New York, Shelter Island: Manning Publications.

Varoquaux, G., Raamana, R. P., Engemann, D., Hoyos-Idrobo, A., Schwartz, Y., & Thirion, B. (2016). Assessing and tuning brain decoders: cross-validation, caveats, and guidelines. NeuroImage, 10, 1-15.

#### Code Organization
