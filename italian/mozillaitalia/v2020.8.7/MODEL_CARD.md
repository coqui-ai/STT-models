# Model card for Italian STT

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

- Person or organization developing model: Originally trained and released by the [Mozilla Italia](https://github.com/MozillaItalia) Community.
- Model language: Italian / italiano / `it`
- Model date: August 7, 2020
- Model type: `Speech-to-Text`
- Model version: `2020.8.7`
- Compatible with 🐸 STT version: `v0.9.3`
- License: CC0
- Citation details: `@techreport{italian-stt, author = {Mozilla Italia}, title = {Italian STT 2020.8.7}, institution = {Coqui}, address = {\url{https://github.com/coqui-ai/STT-models}} year = {2021}, month = {April}, number = {STT-IT-2020.8.7} }`
- Where to send questions or comments about the model: You can leave an issue on [`STT-model` issues](https://github.com/coqui-ai/STT-models/issues), open a new discussion on [`STT-model` discussions](https://github.com/coqui-ai/STT-models/discussions), or chat with us on [Gitter](https://gitter.im/coqui-ai/).

## Intended use

Speech-to-Text for the [Italian Language](https://en.wikipedia.org/wiki/Italian_language) on 16kHz, mono-channel audio.

## Performance Factors

Factors relevant to Speech-to-Text performance include but are not limited to speaker demographics, recording quality, and background noise. Read more about STT performance factors [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data).

## Metrics

STT models are usually evaluated in terms of their transcription accuracy, deployment Real-Time Factor, and model size on disk.

#### Transcription Accuracy

The following Word Error Rates and Character Error Rates are reported by [Mozilla Italia](https://github.com/MozillaItalia/DeepSpeech-Italian-Model/releases/tag/2020.08.07) (the transfer learning model).

|Test Corpus|WER|CER|
|-----------|---|---|
|Common Voice|28.7\%|11.8\%|
|M-AILABS|15.0\%|4.2\%|

#### Real-Time Factor

Real-Time Factor (RTF) is defined as `processing-time / length-of-audio`. The exact real-time factor of an STT model will depend on the hardware setup, so you may experience a different RTF.

Recorded average RTF on laptop CPU: `1.0`

#### Model Size

`model.pbmm`: 181M
`model.tflite`: 46M

### Approaches to uncertainty and variability

Confidence scores and multiple paths from the decoding beam can be used to measure model uncertainty and provide multiple, variable transcripts for any processed audio.

## Training data

This model was trained on:

1. ~130 hours of the Common Voice Italian dataset
2. ~127 hours of the M-AILABS Italian dataset

## Evaluation data

The Model was evaluated on Common Voice and M-AILABS.

## Ethical considerations

Deploying a Speech-to-Text model into any production setting has ethical implications. You should consider these implications before use.

### Demographic Bias

You should assume every machine learning model has demographic bias unless proven otherwise. For STT models, it is often the case that transcription accuracy is better for men than it is for women. If you are using this model in production, you should acknowledge this as a potential issue.

### Surveillance

Speech-to-Text may be mis-used to invade the privacy of others by recording and mining information from private conversations. This kind of individual privacy is protected by law in may countries. You should not assume consent to record and analyze private speech.

## Caveats and recommendations

Machine learning models (like this STT model) perform best on data that is similar to the data on which they were trained. Read about what to expect from an STT model with regard to your data [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data). 

In most applications, it is recommended that you [train your own language model](https://stt.readthedocs.io/en/latest/LANGUAGE_MODEL.html) to improve transcription accuracy on your speech data.
