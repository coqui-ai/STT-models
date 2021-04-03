# Model card for Catalan STT

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

- Person or organization developing model: Originally trained and released by [Ciaran O'Reilly](https://github.com/ccoreilly)
- Model date: Accessed from [Github](https://github.com/ccoreilly/deepspeech-catala/releases/tag/0.14.0) on March 31, 2021
- Model type: `Speech-to-Text`
- Model version: `v0.14.0`
- Compatible with 🐸 STT version: `v0.9.3`
- Code: [deepspeech-catala](https://github.com/ccoreilly/deepspeech-catala)
- License: MIT
- Citation details: `@misc{catalan-ccoreilly,
author = {O'Reilly,Ciaran},
title = {Deepspeech Català},
publisher = {Github},
journal = {deepspeech-catala},
howpublished = {\url{https://github.com/ccoreilly/deepspeech-catala}}
commit = {21da2be7cace9f87ac2445e51b82703d1fee0849}
}`
- Where to send questions or comments about the model: You can leave an issue on [`STT-model` issues](https://github.com/coqui-ai/STT-models/issues), open a new discussion on [`STT-model` discussions](https://github.com/coqui-ai/STT-models/discussions), or chat with us on [Gitter](https://gitter.im/coqui-ai/).

## Intended use

Speech-to-Text for the [Catalan Language](https://en.wikipedia.org/wiki/catalan_language) on 16kHz, mono-channel audio.

## Performance Factors

Factors relevant to Speech-to-Text performance include but are not limited to speaker demographics, recording quality, and background noise. Read more about STT performance factors [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data).

## Metrics

STT models are usually evaluated in terms of their transcription accuracy, deployment Real-Time Factor, and model size on disk.

#### Transcription Accuracy

The following Word Error Rates (WER) are reported on [Github](https://github.com/ccoreilly/deepspeech-catala#wer-del-dataset-test-de-cada-model).

|Test Dataset | WER|
|-------------|----|
|Common Voice 6.1 + ParlamentParla | 13,29\%|
|Google Crowdsourced | 9,05\%|
|Sant Jordi | 18,84\%|

#### Real-Time Factor

Real-Time Factor (RTF) is defined as `proccesing-time / length-of-audio`. The exact real-time factor of an STT model will depend on the hardware setup, so you may experience a different RTF.

Recorded average RTF on laptop CPU: `.71`

#### Model Size

`model.pbmm`: 181M
`model.tflite`: 46M

### Approaches to uncertainty and variability

Confidence scores and multiple paths from the decoding beam can be used to measure model uncertainty and provide multiple, variable transcripts for any processed audio.

## Training data

This model was trained on [Catalan Common Voice 6.1](commonvoice.mozilla.org/datasets) and [ParlamentParla Clean](https://www.openslr.org/59/).

## Evaluation data

The model was tested on [Catalan Common Voice 6.1](commonvoice.mozilla.org/datasets), [ParlamentParla Clean](https://www.openslr.org/59/), the [Catalan Google Crowdsourced Corpus](https://www.openslr.org/69/), and a private corpus ([Sant Jordi](https://github.com/ccoreilly/deepspeech-catala#corpus-emprats)).

## Ethical considerations

Deploying a Speech-to-Text model into any production setting has ethical implications. You should consider these implications before use.

### Demographic Bias

You should assume every machine learning model has demographic bias unless proven otherwise. For STT models, it is often the case that transcription accuracy is better for men than it is for women. If you are using this model in production, you should acknowledge this as a potential issue.

### Surveillance

Speech-to-Text may be mis-used to invade the privacy of others by recording and mining information from private conversations. This kind of individual privacy is protected by law in may countries. You should not assume consent to record and analyze private speech.

## Caveats and recommendations

Machine learning models (like this STT model) perform best on data that is similar to the data on which they were trained. Read about what to expect from an STT model with regard to your data [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data). 

In most applications, it is recommended that you [train your own language model](https://stt.readthedocs.io/en/latest/LANGUAGE_MODEL.html) to improve transcription accuracy on your speech data.
