# Dataset

To download Speech Commands Data Set from Kaggle, you need to:

1. Go to https://www.kaggle.com/c/tensorflow-speech-recognition-challenge/rules and accept the rules.
2. Go to your Kaggle account page and download and setup the api key.
3. `pip install kaggle`
4. `kaggle competitions download -c tensorflow-speech-recognition-challenge` to start download.
5. Unzip the train folder in the `wav_data` folder.

For convenience, we've added preprocessed spectrograms dataset in the repo as the weight is reasonnable. 
