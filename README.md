## Band Classification

This is a repository for the semester project of Machine Learning Course in MSc AI NCSR. This project aims to classify 5 different progressive metal bands.

### Data collection

Data were collected from youtube URLs. The wav file was extracted from the URL and added to a wav processing software. In the software, a riff was extracted. Every riff contained musical instruments (guitar, bass, drums) but not human voice. This was done on purpose to inspect if classification can be achieved without the voice bias of an artist-band.

### Data preproccesing

Each wav file(instance) was trimmed to 8.00 seconds 

### Feature Extraction

Feautures were extracted using pyAudioAnalysis module [1]. In particular, Short term features were extracted and the feature vector consisted of their mean, and std.

[1] https://github.com/tyiannak/pyAudioAnalysis

### Feature Selection

For the feature selection proccess, features were dropped using spearman's corellation coefficient. For a pair of features that had coefficient value > threshold, the first feature was dropped.

### Cross validation on the whole dataset

Since the each band had limited number of classes (50) train-test split was not implemented. Instead cross validation was used with many iteration to check the robustness of the data-models. Three pipelines were implemented: default features, features after LDA and features after PCA.
* Repeated shuffle stratification on the whole dataset (80-20 split).
* Scaling using MinMax scaler.
* Models = LR, KNN, SVM
* Grid search, hyperparameter tuning based on mean F1 macro of all splits.