# DataMining_project
The dataset consists of audio recordings of 24 professional actors divided by genre. We deeply analyzed the audio tracks by extracting a large and diverse amount of data.

## RAVDESS FEATURES
This dataset was created from the RAVDESS dataset (https://zenodo.org/record/1188976), extracting basic statistics from the original audio data and after transforming it using: differencing, zero-crossing rate, Mel-Frequency Cepstral Coefficients, spectral centroid, and the stft chromagram. Features were extracted from the 2452 wav files. Features are extracted also by dividing each time series into 4 non overlapping windows.

### Features:
- modality (audio-only)
- vocal_channel (speech, song)
- emotion (neutral, calm, happy, sad, angry, fearful, disgust, surprised)
- emotional_intensity (normal, strong). NOTE: There is no strong intensity for the 'neutral' emotion
- statement ("Kids are talking by the door", "Dogs are sitting by the door")
- repetition (1st repetition, 2nd repetition)
- actor (01 to 24)
- sex (M, F)
- filename (name of the corresponding audio file)
- frame_count (the number of frames from the audio sample)

#### Basic statistics
From each audio waveform the following features are extracted: 
sum, mean, std, min, max
q01, q05, q25, q50, q75, q95, q99 (0.01, 0.05 quantiles and so on ...)
kur, skew (kurtosis, skewness)
E.g.:
- the feature "q99" is the 0.99 quantile of the entire original audio file.
- the feature "mean" is the mean of the entire original audio file.

#### Transformations
Each audio file was then transformed using:
- lag1: difference between each observation and the precedent -> difference(t) = observation(t) - observation(t-1)
- zc: zero crossing rate
- mfcc: Mel-Frequency Cepstral Coefficients
- sc: spectral centroid
- stft: stft chromagram
For each of these transform the same features are extracted (sum, mean, std, ...)

#### Naming schema
The features are extracted first at a global level (i.e. for the entire signal), then dividing into 4 equally sized windows. Windows are indicated with the string w1 or w2 or w3 or w4.
E.g., 
- "stft_skew_w4" means the skewness of the stft chromagram of the 4th window of the audio signal;
- "stft_skew" means the skewness of the stft chromagram of the entire audio signal;
- "skew_w1" means the skewness of the 1st window of the original audio signal;
- "skew" means the skewness of the entire original audio signal.
