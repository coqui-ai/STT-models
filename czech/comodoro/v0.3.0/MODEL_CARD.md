# Model card for Czech STT

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

- Person or organization developing model: Trained by [Vojtěch Drábek](https://www.draabek.cz).
- Model language: Czech / čeština / `cs`
- Model date: May 31, 2022
- Model type: `Speech-to-Text`
- Model version: `v0.3.0`
- Compatible with 🐸 STT version: `v0.9.3`
- License: CC-BY-NC 4.0
- Citation details: `@misc{czech-stt, author = {Drábek, Vojtěch}, title = {Czech STT 0.3}, publisher = {comodoro}, journal = {deepspeech-cs}, howpublished =  {\url{https://github.com/comodoro/deepspeech-cs}} }`
- Where to send questions or comments about the model: You can leave an issue on [the model release page](https://github.com/comodoro/deepspeech-cs) or [`STT-model` issues](https://github.com/coqui-ai/STT-models/issues), open a new discussion on [`STT-model` discussions](https://github.com/coqui-ai/STT-models/discussions), or chat with us on [Gitter](https://gitter.im/coqui-ai/) or Matrix channel coqui-ai/STT.

## Intended use

Speech-to-Text for the [Czech Language](https://en.wikipedia.org/wiki/Czech_language) on 16kHz, mono-channel audio.

## Performance Factors

Factors relevant to Speech-to-Text performance include but are not limited to speaker demographics, recording quality, and background noise. Read more about STT performance factors [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data).

## Metrics

STT models are usually evaluated in terms of their transcription accuracy, deployment, Real-Time Factor, and model size on disk.

#### Transcription Accuracy

More information reported on [Github](https://github.com/comodoro/deepspeech-cs/).

|Test Corpus|WER|CER|
|-----------|---|---|
|Acoustic model|
|Czech Common voice 6.1|40.6%|10.7%|
|Vystadial 2016|50.6%|19.6%|
|Parliament Plenary Hearings|21.3%|5.3%|
|ParCzech 3.0|21%|6.2%|
||
|With the attached scorer|
|Czech Common voice 6.1|15.3%|6.8%|
|Vystadial 2016|35.7%|20.1%|
|Parliament Plenary Hearings|9.7%|3.7%|
|ParCzech 3.0|10.1%|4.5%|

#### Real-Time Factor

Real-Time Factor (RTF) is defined as `processing-time / length-of-audio`. The exact real-time factor of an STT model will depend on the hardware setup, so you may experience a different RTF.

Recorded average RTF on laptop CPU: `0.73`

#### Model Size

`model.pbmm`: 181M
`model.tflite`: 46M
`scorer`: 461M

### Approaches to uncertainty and variability

Confidence scores and multiple paths from the decoding beam can be used to measure model uncertainty and provide multiple, variable transcripts for any processed audio.

## Training data

This model was trained on the following corpora:

1. Vystadial 2016 – Czech data
2. OVM – Otázky Václava Moravce
3. Czech Parliament Meetings
4. Large Corpus of Czech Parliament Plenary Hearings
5. Common Voice Czech
6. Some private recordings and parts of audioboooks

## Evaluation data

The model was evaluated on Common Voice Czech, Large Corpus of Czech Parliament Plenary Hearings, Vystadial 2016 – Czech data and ParCzech 3.0 test sets.

## Ethical considerations

Deploying a Speech-to-Text model into any production setting has ethical implications. You should consider these implications before use.

### Demographic Bias

You should assume every machine learning model has demographic bias unless proven otherwise. For STT models, it is often the case that transcription accuracy is better for men than it is for women. If you are using this model in production, you should acknowledge this as a potential issue.

### Surveillance

Speech-to-Text may be mis-used to invade the privacy of others by recording and mining information from private conversations. This kind of individual privacy is protected by law in many countries. You should not assume consent to record and analyze private speech.

## Caveats and recommendations

Machine learning models (like this STT model) perform best on data that is similar to the data on which they were trained. Read about what to expect from an STT model with regard to your data [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data). 

In most applications, it is recommended that you [train your own language model](https://stt.readthedocs.io/en/latest/LANGUAGE_MODEL.html) to improve transcription accuracy on your speech data.