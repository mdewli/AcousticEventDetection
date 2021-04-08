# UrbanSoundClassification
Classifying 10 differrent urban sounds: 'car_horn', 'dog_bark', 'gun_shot', 'street_music', 'siren', 'air_conditioner', 'jackhammer', 'engine_idling', 'children_playing', 'drilling', using covolution neural networks

Data can be downloaded/accessed from here: https://www.kaggle.com/chrisfilo/urbansound8k

We extracted audio features : mfccs ( mel cepstral coeeficienst, stfts (short time fourier transform) and melpectrograms for each audio file). However, we used
mfccs to train the model. The input features were then converted to a 3d tensor by adding one more axis to 2d input, to mimic the shape of an RGB image because we were working with convolutional
neural networks generally used to classify image data. 

This dataset contains 8732 labeled sound excerpts (<=4s) of urban sounds from 10 classes: air_conditioner, car_horn, children_playing, dog_bark, drilling, enginge_idling, gun_shot, jackhammer, siren, and street_music. The classes are drawn from the urban sound taxonomy. For a detailed description of the dataset and how it was compiled please refer to our paper.
All excerpts are taken from field recordings uploaded to www.freesound.org. The files are pre-sorted into ten folds (folders named fold1-fold10) to help in the reproduction of and comparison with the automatic classification results reported in the article above.



In addition to the sound excerpts, a CSV file containing metadata about each excerpt is also provided.

AUDIO FILES INCLUDED
8732 audio files of urban sounds (see description above) in WAV format. The sampling rate, bit depth, and number of channels are the same as those of the original file uploaded to Freesound (and hence may vary from file to file).

META-DATA FILES INCLUDED
UrbanSound8k.csv
This file contains meta-data information about every audio file in the dataset. This includes:

slicefilename:
The name of the audio file. The name takes the following format: [fsID]-[classID]-[occurrenceID]-[sliceID].wav, where:
[fsID] = the Freesound ID of the recording from which this excerpt (slice) is taken
[classID] = a numeric identifier of the sound class (see description of classID below for further details)
[occurrenceID] = a numeric identifier to distinguish different occurrences of the sound within the original recording
[sliceID] = a numeric identifier to distinguish different slices taken from the same occurrence

fsID:
The Freesound ID of the recording from which this excerpt (slice) is taken

start
The start time of the slice in the original Freesound recording

end:
The end time of slice in the original Freesound recording

salience:
A (subjective) salience rating of the sound. 1 = foreground, 2 = background.

fold:
The fold number (1-10) to which this file has been allocated.

classID:
A numeric identifier of the sound class:
0 = airconditioner 1 = carhorn
2 = childrenplaying 3 = dogbark
4 = drilling
5 = engineidling 6 = gunshot
7 = jackhammer
8 = siren
9 = street_music

class:
The class name: airconditioner, carhorn, childrenplaying, dogbark, drilling, engineidling, gunshot, jackhammer,
siren, street_music.

BEFORE YOU DOWNLOAD: AVOID COMMON PITFALLS!
Since releasing the dataset we have noticed a couple of common mistakes that could invalidate your results, potentially leading to manuscripts being rejected or the publication of incorrect results. To avoid this, please read the following carefully:

Don't reshuffle the data! Use the predefined 10 folds and perform 10-fold (not 5-fold) cross validation
The experiments conducted by vast majority of publications using UrbanSound8K (by ourselves and others) evaluate classification models via 10-fold cross validation using the predefined splits*. We strongly recommend following this procedure.
Why?
If you reshuffle the data (e.g. combine the data from all folds and generate a random train/test split) you will be incorrectly placing related samples in both the train and test sets, leading to inflated scores that don't represent your model's performance on unseen data. Put simply, your results will be wrong.
Your results will NOT be comparable to previous results in the literature, meaning any claims to an improvement on previous research will be invalid. Even if you don't reshuffle the data, evaluating using different splits (e.g. 5-fold cross validation) will mean your results are not comparable to previous research.

Don't evaluate just on one split! Use 10-fold (not 5-fold) cross validation and average the scores
We have seen reports that only provide results for a single train/test split, e.g. train on folds 1-9, test on fold 10 and report a single accuracy score. We strongly advise against this. Instead, perform 10-fold cross validation using the provided folds and report the average score.
Why?
Not all the splits are as "easy". That is, models tend to obtain much higher scores when trained on folds 1-9 and tested on fold 10, compared to (e.g.) training on folds 2-10 and testing on fold 1. For this reason, it is important to evaluate your model on each of the 10 splits and report the average accuracy.
Again, your results will NOT be comparable to previous results in the literature.

Acknowledgements
We kindly request that articles and other works in which this dataset is used cite the following paper:

J. Salamon, C. Jacoby and J. P. Bello, "A Dataset and Taxonomy for Urban Sound Research", 22nd ACM International Conference on Multimedia, Orlando USA, Nov. 2014.

More information at https://urbansounddataset.weebly.com/urbansound8k.html
