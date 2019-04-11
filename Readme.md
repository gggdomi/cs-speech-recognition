# Dataset

To download Speech Commands Data Set from Kaggle, you need to:

1. Go to https://www.kaggle.com/c/tensorflow-speech-recognition-challenge/rules and accept the rules.
2. Go to your Kaggle account page and download and setup the api key.
3. `pip install kaggle`
4. `kaggle competitions download -c tensorflow-speech-recognition-challenge` to start download.
5. Unzip the train folder in the `wav_data` folder.

For convenience, we've added preprocessed spectrograms dataset in the repo as the weight is reasonnable. 


Note : dans la tâche du kaggle 20 des 31 classes sont regroupées dans une catégorie "autres" de sorte qu'on n'en prédit que 12. Pas (encore) fait ici pour l'instant, mais ça ne change pas grand-chose et c'est facile à mettre en place au moment du chargement du dataset si on juge ça intéressant (si on veut publier un score sur Kaggle par exemple)

Fichiers :
- `wav_to_spectrograms.ipynb` : génère des train / val / test set à partir des fichiers wav dans `spectrograms/`
- `wav-compile.ipynb` : génère un fichier contenant tous les wav par dataset pour un usage direct par les NN
- `keras-conv-wav.ipynb` : convnet avec les wav en entrée. takes a while to train with mediocre results
- `keras-rnn-spec.ipynb` : rnn sur les spectrograms. Does not train.
- `keras-resnet-spec.ipynb` : resnet sur les spectrograms. Marche pas mal. À tester avec des poids d'imagenet
- `generate-deepspeech-csv.ipynb` : pour préparer le fine-tuning de DeepSpeech. 
- @Swiff pour les notebooks de DeepSpeech. Stratégie DeepSpeech : 
    1. faire tourner sur toutes les wav pour avoir un fichier filename -> prediction (texte, pas catégorie). 
    2. Fine-tune DeepSpeech si possible. 
    3. refaire 1. avec le nouveau réseau et comparer la diff.
    4. train un shallow network en sortie de DS pour faire le mapping texte -> catégorie, voir si meilleure accuracy après fine-tuing ou pas.
