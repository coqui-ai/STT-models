# Model card for Ukrainian STT

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

- Person or organization developing model: Originally trained by [Yurii Paniv](https://github.com/robinhad) and released under the [voice-recognition-ua](https://github.com/robinhad/voice-recognition-ua) project.
- Model date: Accessed from [Github](https://github.com/robinhad/voice-recognition-ua/releases/tag/v0.4) on March 31, 2021
- Model type: `Speech-to-Text`
- Model version: `0.4`
- Code: [voice-recognition-ua](https://github.com/robinhad/voice-recognition-ua)
- License: CC BY-NC 4.0
- Citation details: `@misc{ukrainian-stt-paniv,
author = {Paniv,Yurii},
title = {Ukrainian STT},
publisher = {voice-recognition-ua},
journal = {Github},
howpublished = {\url{https://github.com/robinhad/voice-recognition-ua/releases/tag/v0.4}},
commit={1252a9e9337ceeff52fe9772dc8802f4337ccff3}
}`
- Where to send questions or comments about the model: You can leave an issue on [`STT-model` issues](https://github.com/coqui-ai/STT-models/issues), open a new discussion on [`STT-model` discussions](https://github.com/coqui-ai/STT-models/discussions), or chat with us on [Gitter](https://gitter.im/coqui-ai/).

## Intended use

Speech-to-Text for the [Ukranian Language](https://en.wikipedia.org/wiki/Ukrainian_language) on 16kHz, mono-channel audio.

## Performance Factors

Factors relevant to Speech-to-Text performance include but are not limited to speaker demographics, recording quality, and background noise. Read more about STT performance factors [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data).

## Metrics

STT models are usually evaluated in terms of their transcription accuracy, deployment Real-Time Factor, and model size on disk.

#### Transcription Accuracy

The following Word Error Rates (WER) are reported on [Github](https://github.com/robinhad/voice-recognition-ua/releases/tag/v0.4).

|Test Corpus|WER|CER|
|-----------|---|---|
|Common Voice|57.2\%|16.3\%|
	
#### Real-Time Factor

Real-Time Factor (RTF) is defined as `proccesing-time / length-of-audio`. The exact real-time factor of an STT model will depend on the hardware setup, so you may experience a different RTF.

Recorded average RTF on laptop CPU: `.76`

#### Model Size

`model.pbmm`: 181M
`model.tflite`: 46M

### Approaches to uncertainty and variability

Confidence scores and multiple paths from the decoding beam can be used to measure model uncertainty and provide multiple, variable transcripts for any processed audio.

## Training data

This model is trained on a total of 1,230 hours from the Ukrainian Dataset at Academic torrents and Common Voice Ukrainian 6.1.

## Evaluation data

This model was tested on Common Voice Ukrainian 6.1.

## Ethical considerations

Deploying a Speech-to-Text model into any production setting has ethical implications. You should consider these implications before use.

### Demographic Bias

You should assume every machine learning model has demographic bias unless proven otherwise. For STT models, it is often the case that transcription accuracy is better for men than it is for women. If you are using this model in production, you should acknowledge this as a potential issue.

### Surveillence

Speech-to-Text may be mis-used to invade the privacy of others by recording and mining information from private conversations. This kind of individual privacy is protected by law in may countries. You should not assume consent to record and analyze private speech.

## Caveats and recommendations

Machine learning models (like this STT model) perform best on data that is similar to the data on which they were trained. Read about what to expect from an STT model with regard to your data [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data). 

In most applications, it is recommended that you [train your own language model](https://stt.readthedocs.io/en/latest/LANGUAGE_MODEL.html) to improve transcription accuracy on your speech data.
