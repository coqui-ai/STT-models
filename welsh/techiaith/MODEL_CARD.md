# Model card for Welsh STT

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

- Person or organization developing model: Originally trained by [Dewi Bryn Jones](https://github.com/DewiBrynJones) and released by the [Techiaith Language Technologies Unit](https://github.com/techiaith)
- Model date: Accessed from [Github](https://github.com/techiaith/docker-deepspeech-cy/releases/tag/21.03) on March 31, 2021
- Model type: `Speech-to-Text`
- Model version: `21.03`
- Code: [docker-deepspeech-cy](https://github.com/techiaith/docker-deepspeech-cy)
- License: MIT
- Citation details: `@misc{welsh-stt-dewibrynjones,
author = {Dewi Bryn Jones},
title = {Docker DeepSpeech Cymraeg},
publisher = {Techiaith},
journal = {docker-deepspeech-cy},
howpublished = {\url{https://github.com/techiaith/docker-deepspeech-cy/releases/tag/21.03}}
}`
- Where to send questions or comments about the model: You can leave an issue on [`STT-model` issues](https://github.com/coqui-ai/STT-models/issues), open a new discussion on [`STT-model` discussions](https://github.com/coqui-ai/STT-models/discussions), or chat with us on [Gitter](https://gitter.im/coqui-ai/).

## Intended use

Speech-to-Text for the [Welsh Language](https://en.wikipedia.org/wiki/Welsh_language) on 16kHz, mono-channel audio.

## Performance Factors

Factors relevant to Speech-to-Text performance include but are not limited to speaker demographics, recording quality, and background noise. Read more about STT performance factors [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data).

## Metrics

STT models are usually evaluated in terms of their transcription accuracy, deployment Real-Time Factor, and model size on disk.

#### Transcription Accuracy

Word Error Rates and Character Error Rates were not reported for this model

#### Real-Time Factor

Real-Time Factor (RTF) is defined as `proccesing-time / length-of-audio`. The exact real-time factor of an STT model will depend on the hardware setup, so you may experience a different RTF.

Recorded average RTF on laptop CPU: `.76`

#### Model Size

`model.pbmm`: 181M
`model.tflite`: 46M

### Approaches to uncertainty and variability

Confidence scores and multiple paths from the decoding beam can be used to measure model uncertainty and provide multiple, variable transcripts for any processed audio.

## Training data

These models were trained with the Welsh dataset from the [Common Voice Corpus 6.1](https://commonvoice.mozilla.org/datasets) in addition to a small dataset of validated recordings donated by the first users of Bangor University's Language Technology Unit's online automatic transcription website service: [Trawsgrifiwr Ar-lein](https://trawsgrifiwr.techiaith.cymru). [Detailed release notes here](https://github.com/techiaith/docker-deepspeech-cy/releases/tag/21.03).

## Evaluation data

With a language model, the Welsh STT model had a Word Error Rate of 11\%. [Detailed release notes here](https://github.com/techiaith/docker-deepspeech-cy/releases/tag/21.03).

## Ethical considerations

Deploying a Speech-to-Text model into any production setting has ethical implications. You should consider these implications before use.

### Demographic Bias

You should assume every machine learning model has demographic bias unless proven otherwise. For STT models, it is often the case that transcription accuracy is better for men than it is for women. If you are using this model in production, you should acknowledge this as a potential issue.

### Surveillence

Speech-to-Text may be mis-used to invade the privacy of others by recording and mining information from private conversations. This kind of individual privacy is protected by law in may countries. You should not assume consent to record and analyze private speech.

## Caveats and recommendations

Machine learning models (like this STT model) perform best on data that is similar to the data on which they were trained. Read about what to expect from an STT model with regard to your data [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data). 

In most applications, it is recommended that you [train your own language model](https://stt.readthedocs.io/en/latest/LANGUAGE_MODEL.html) to improve transcription accuracy on your speech data.
