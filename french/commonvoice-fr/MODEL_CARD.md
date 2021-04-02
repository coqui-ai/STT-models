# Model card for French STT

Jump to section:

- [Model details](#model-details)
- [Intended use](#intended-use)
- [Performance Factors](#performance-factors)
- [Metrics](#metrics)
- [Training data](#training-data)
- [Evaluation data](#evaluation-data)
- [Ethical considerations](#ethical-considerations)
- [Caveats and recommendations](#caveats-and-recommendations)

## Model details

- Person or organization developing model: Originally trained and released by [Alexandre Lissy](https://github.com/lissyx) under the [commonvoice-fr](https://github.com/common-voice/commonvoice-fr) project
- Model date: Accessed from [Github](https://github.com/common-voice/commonvoice-fr/releases/tag/fr-v0.6) on March 31, 2021
- Model type: `Speech-to-Text`
- Model version: `0.6`
- Code: [commonvoice-fr](https://github.com/common-voice/commonvoice-fr)
- License: MPL 2.0
- Citation details: `@misc{commonvoice-fr,
author = {Lissy, Alexandre},
title = {Common Voice FR},
publisher = {Github},
journal = {GitHub repository},
howpublished = {\url{https://github.com/common-voice/commonvoice-fr/releases/tag/fr-v0.6}},
commit = {5a0f61baf112620286b30319eb7000c57d8a20d0}
}`
- Where to send questions or comments about the model: You can leave an issue on [`STT-model` issues](https://github.com/coqui-ai/STT-models/issues), open a new discussion on [`STT-model` discussions](https://github.com/coqui-ai/STT-models/discussions), or chat with us on [Gitter](https://gitter.im/coqui-ai/).

## Intended use

Speech-to-Text for the [French Language](https://en.wikipedia.org/wiki/French_language) on 16kHz, mono-channel audio.

## Performance Factors

Factors relevant to Speech-to-Text performance include but are not limited to speaker demographics, recording quality, and background noise. Read more about STT performance factors [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data).

## Metrics

STT models are usually evaluated in terms of their transcription accuracy, deployment Real-Time Factor, and model size on disk.

#### Transcription Accuracy

The following Word Error Rates (WER) are reported on [Github](https://github.com/common-voice/commonvoice-fr/releases/tag/fr-v0.6).

|Test Corpus|WER|CER|
|-----------|---|---|
|African_Accented_French_test.csv|44.9\%|24.2\%|
|M-AILABS|9.7\%|2.7\%|
|trainingspeech|20.0\%|6.0\%|
|Common Voice|30.1\%|14.3\%|
|LinguaLibre|5.9\%|1.8\%|
|CCPMF|48.7\%|30.4\%|

#### Real-Time Factor

Real-Time Factor (RTF) is defined as `proccesing-time / length-of-audio`. The exact real-time factor of an STT model will depend on the hardware setup, so you may experience a different RTF.

Recorded average RTF on laptop CPU: ``

#### Model Size

`model.pbmm`: 181M
`model.tflite`: 46M

### Approaches to uncertainty and variability

Confidence scores and multiple paths from the decoding beam can be used to measure model uncertainty and provide multiple, variable transcripts for any processed audio.

## Training data

This French STT model was trained on the following corpora:

1. Lingua Libre (~40h)
2. Common Voice FR (v2) (~490h, en autorisant jusqu'à 32 duplicatas)
3. Training Speech (~180h)
4. African Accented French (~15h)
5. M-AILABS French (~315h)
6. Centre de Conférence Pierre Mendès France (~300h)

Total : ~1340h

## Evaluation data

The model was tested on the following corpora.

1. Lingua Libre
2. Common Voice FR (v2)
3. Training Speech
4. African Accented French
5. M-AILABS French
6. Centre de Conférence Pierre Mendès France

## Ethical considerations

Deploying a Speech-to-Text model into any production setting has ethical implications. You should consider these implications before use.

### Demographic Bias

You should assume every machine learning model has demographic bias unless proven otherwise. For STT models, it is often the case that transcription accuracy is better for men than it is for women. If you are using this model in production, you should acknowledge this as a potential issue.

### Surveillence

Speech-to-Text may be mis-used to invade the privacy of others by recording and mining information from private conversations. This kind of individual privacy is protected by law in may countries. You should not assume consent to record and analyze private speech.

## Caveats and recommendations

Machine learning models (like this STT model) perform best on data that is similar to the data on which they were trained. Read about what to expect from an STT model with regard to your data [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data). 

In most applications, it is recommended that you [train your own language model](https://stt.readthedocs.io/en/latest/LANGUAGE_MODEL.html) to improve transcription accuracy on your speech data.
