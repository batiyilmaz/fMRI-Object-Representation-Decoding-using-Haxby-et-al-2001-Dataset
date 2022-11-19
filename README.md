# fMRI Object Representation Decoding using [Haxby et al. (2001)](https://pubmed.ncbi.nlm.nih.gov/11577229/) Dataset

## Project Stages with Detailed Descriptions

**Preprocessing**

During the preliminary stage, the data of subjects 1-4 from the [Haxby et al. (2001)](https://pubmed.ncbi.nlm.nih.gov/11577229/) dataset were downloaded and subsetting was carried out to contain all the available 8 non-rest classes for the outcome variables. The preprocessing was performed by standardizing and detrending the predictor variable, functional Nifti images with BOLD data by using NiftiMasker() class/function from nilearn [(Abraham et al., 2014)](https://www.frontiersin.org/articles/10.3389/fninf.2014.00014/full?ref=https://githubhelp.com). The rest of the analyses extensively employed classes/functions from scikit-learn [(Pedregosa et al., 2011)](https://arxiv.org/abs/1201.0490). Finally, a leave-one-run-out multi-class classification scheme was established to split the training and test set data for the processing.

**Data Analysis**

#### Classifier Performance Comparison (Multinomial Logistic Regression vs. Linear SVM using One-vs-Rest and One-vs-One Multi-Class Classification)

The prediction performance of the L2-penalized multinomial logistic regression was compared with L2-penalized linear support vector machine (SVM) classifiers with one-vs-rest and one-vs-one multi-class classification strategies respectively.

**Mean decoding accuracy for various classifiers**

Overall, the best performing model has been found to be the linear SVM with a one-vs-rest multi-class classification strategy with 55.09% mean decoding accuracy (**see Figure 1**).

![Figure 1](https://github.com/batiyilmaz/fMRI-Object-Representation-Decoding-Project-Haxby-et-al-2001-Dataset/blob/main/Figures/Figure_1.png)

**Subject variability**

For the multinomial logistic regression, the final decoding performance of the 1st subject revealed 60.07% accuracy; 2nd subject showed 50.12% accuracy whereas the 3rd subject had 50.81% and, finally the model predicted with 48.61% accuracy for the 4th subject. In the case of linear SVM with one-vs-rest strategy, the model demonstrated 61.92% (Subject 1), 53.24% (Subject 2), 54.05% (Subject 3), and 51.16% (Subject 4) accuracy for each subject respectively. 

Finally, the linear SVM with one-vs-one strategy had the predictive performance of 50.23%, 40.97%, 46.64%, and 41.32% accuracy for each subject respectively.
  
#### Decoding Accuracy (Percent True Positives) for the Individual Classes

The decoding accuracy pattern for all eight individual non-rest object categories were compared for each classification approach by percent true positive scores were taken into the account. Percent true positives were found by calculating True Positives (TP) / (TP + False Negatives (FN)), thus yielding a recall/sensitivity score.

In the context of multinomial logistic regression, the object categories were decoded with varying accuracies of 35% (bottle), 48% (cat), 37% (chair), 67% (face), 80% (house), 30% (scisssors), 75% (scrambled pictures), 47% (shoe) respectively.

Linear SVM with a one-vs-rest strategy revealed the decoding accuracies of 34% (bottle), 52% (cat), 39% (chair), 74% (face), 83% (house), 33% (scissors), 76% (scrambled pictures), 50% (shoe).
Lastly, linear SVM with a one-vs-one strategy showed the decoding accuracy pattern of 30% (bottle), 38% (cat), 35% (chair), 59% (face), 69% (house), 26% (scissors), 59% (scrambled pictures), and 43% (shoe).

Overall, face, house, and scrambled pictures object categories were decoded better than other categories for each of the three classifiers (**see Figure 2**).

![Figure 2](https://github.com/batiyilmaz/fMRI-Object-Representation-Decoding-Project-Haxby-et-al-2001-Dataset/blob/main/Figures/Figure_2.png)

#### Nested Cross-Validation Scheme for Finding the Optimal C Parameter

The multi-class approach and the decoder that provided the best results in the problem 1a has been found to be the linear SVM with a one-vs-rest multi-class classification strategy, hence for the following task, the same decoder has been employed to set up a nested cross validation scheme for the hyperparameter tuning/optimization process in order to find the best C (regularization hyperparameter) value and initialize a new decoding process.

The nested cross validation scheme included 9 cross-validation fold for the inner loop which
was used to set the regularization hyperparameter C and 4 cross validation fold for the outer loop for providing the final prediction accuracy. This structure was repeated for 4 times and adapted by each subject in the dataset correspondingly (**see Figure 3**).

![Figure 3](https://github.com/batiyilmaz/fMRI-Object-Representation-Decoding-Project-Haxby-et-al-2001-Dataset/blob/main/Figures/Figure_3.png)

**Decoding using the Optimal C**

Consequently, decoding with the best C parameters (final accuracy for the outer loop for each subject) yielded the predictive performances of 58.33% (Subject 1), 50.11% (Subject 2), 50.57% (Subject 3), and 47.22% (Subject 4). In addition, the group mean decoding accuracy was 51.56%.

### Code Organization
The code for the data preprocessing as well as processing stages are provided in the same subdirectory (**Code**). Furthermore, figures demonstrated in the **README** section can be found in the subdirectory called **Figures**. The code was written in Python using the combination of Atom text and source code editor and Google Colaboratory.
