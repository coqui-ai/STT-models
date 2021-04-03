# Model card for German STT

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

- Person or organization developing model: Originally trained by [Aashish Agarwal](https://github.com/AASHISHAG) and released under the [deepspeech-german](https://github.com/AASHISHAG/deepspeech-german) project.
- Model date: Accessed from [deepspeech-german](https://github.com/AASHISHAG/deepspeech-german) on March 31, 2021
- Model type: `Speech-to-Text`
- Model version: `v0.9.0`
- Compatible with 🐸 STT version: `v0.9.3`
- Code: [deepspeech-german](https://github.com/AASHISHAG/deepspeech-german)
- License: Apache 2.0
- Citation details: `@inproceedings{agarwal-zesch-2019-german,
author = "Aashish Agarwal and Torsten Zesch",
title = "German End-to-end Speech Recognition based on DeepSpeech",
booktitle = "Preliminary proceedings of the 15th Conference on Natural Language Processing (KONVENS 2019): Long Papers",
year = "2019",
address = "Erlangen, Germany",
publisher = "German Society for Computational Linguistics \& Language Technology",
pages = "111--119"
}`
- Where to send questions or comments about the model: You can leave an issue on [`STT-model` issues](https://github.com/coqui-ai/STT-models/issues), open a new discussion on [`STT-model` discussions](https://github.com/coqui-ai/STT-models/discussions), or chat with us on [Gitter](https://gitter.im/coqui-ai/).

## Intended use

Speech-to-Text for the [German Language](https://en.wikipedia.org/wiki/German_language) on 16kHz, mono-channel audio.

## Performance Factors

Factors relevant to Speech-to-Text performance include but are not limited to speaker demographics, recording quality, and background noise. Read more about STT performance factors [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data).

## Metrics

STT models are usually evaluated in terms of their transcription accuracy, deployment Real-Time Factor, and model size on disk.

#### Transcription Accuracy

No exact statistics on transcription accuracy, however, Word Error Rate was in the range of 10% to 20% on Mozilla and Tuda-De test set. Relevant discussion [here](https://github.com/AASHISHAG/deepspeech-german/issues/39#issuecomment-812829812).

#### Real-Time Factor

Real-Time Factor (RTF) is defined as `proccesing-time / length-of-audio`. The exact real-time factor of an STT model will depend on the hardware setup, so you may experience a different RTF.

Recorded average RTF on laptop CPU: `.69`

#### Model Size

`model.pbmm`: 181M
`model.tflite`: 46M

### Approaches to uncertainty and variability

Confidence scores and multiple paths from the decoding beam can be used to measure model uncertainty and provide multiple, variable transcripts for any processed audio.

## Training data

This German STT model was bootstrapped from a pre-trained English model, and fine-tuned to German via the following datasets: Common Voice 5.1 (750 hours) + SWC (248 hours) + MAILABS (233 hours) + Tuda-De (184 hours) + Voxforge (57 hours).

## Evaluation data

This German STT model was evaluated on the following datasets: Common Voice 5.1 and Tuda-De.

## Ethical considerations

Deploying a Speech-to-Text model into any production setting has ethical implications. You should consider these implications before use.

### Demographic Bias

You should assume every machine learning model has demographic bias unless proven otherwise. For STT models, it is often the case that transcription accuracy is better for men than it is for women. If you are using this model in production, you should acknowledge this as a potential issue.

### Surveillance

Speech-to-Text may be mis-used to invade the privacy of others by recording and mining information from private conversations. This kind of individual privacy is protected by law in may countries. You should not assume consent to record and analyze private speech.

## Caveats and recommendations

Machine learning models (like this STT model) perform best on data that is similar to the data on which they were trained. Read about what to expect from an STT model with regard to your data [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data). 

In most applications, it is recommended that you [train your own language model](https://stt.readthedocs.io/en/latest/LANGUAGE_MODEL.html) to improve transcription accuracy on your speech data.
