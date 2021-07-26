# Model card for English yesno STT

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

- Person or organization developing model: Maintained by [Coqui](https://coqui.ai/).
- Model language: English / English / `en`
- Model date: July 26, 2021
- Model type: `Speech-to-Text` / `constrained vocabulary` / `yesno`
- Model version: `v0.0.1`
- Compatible with 🐸 STT version: `v0.9.3`
- License: Apache 2.0
- Citation details: `@techreport{english-yesno-stt, author = {Coqui}, title = {English yesno STT v0.0.1}, institution = {Coqui}, address = {\url{https://github.com/coqui-ai/STT-models}} year = {2021}, month = {July}, number = {STT-EN-YESNO-0.0.1} }`
- Where to send questions or comments about the model: You can leave an issue on [`STT-model` issues](https://github.com/coqui-ai/STT-models/issues), open a new discussion on [`STT-model` discussions](https://github.com/coqui-ai/STT-models/discussions), or chat with us on [Gitter](https://gitter.im/coqui-ai/).

## Intended use

Speech-to-Text `yesno` model for the [English Language](https://en.wikipedia.org/wiki/English_language) on 16kHz, mono-channel audio. This model has been trained to only recognize the two words "yes" and "no" in English.

## Performance Factors

Factors relevant to Speech-to-Text performance include but are not limited to speaker demographics, recording quality, and background noise. Read more about STT performance factors [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data).

## Metrics

STT models are usually evaluated in terms of their transcription accuracy, deployment Real-Time Factor, and model size on disk.

#### Transcription Accuracy

The model was trained and evaluted on the Common Voice Target Segments Corpus, specifically, only on "yes" and "no" audio clips.

|Test Corpus|Word Error Rate|
|-------|----------|
|Common Voice 6.1 (Target Segments Corpus "yes" and "no") | 1.6\% |

#### Model Size

`yesno.pbmm`: 319K
`yesno.scorer`: 1.7K

### Approaches to uncertainty and variability

Confidence scores and multiple paths from the decoding beam can be used to measure model uncertainty and provide multiple, variable transcripts for any processed audio.

## Training data

The model was trained and evaluted on the Common Voice Target Segments Corpus, specifically, only on "yes" and "no" audio clips.

## Evaluation data

The model was trained and evaluted on the Common Voice Target Segments Corpus, specifically, only on "yes" and "no" audio clips.

## Ethical considerations

Deploying a Speech-to-Text model into any production setting has ethical implications. You should consider these implications before use.

### Demographic Bias

You should assume every machine learning model has demographic bias unless proven otherwise. For STT models, it is often the case that transcription accuracy is better for men than it is for women. If you are using this model in production, you should acknowledge this as a potential issue.

### Surveillance

Speech-to-Text may be mis-used to invade the privacy of others by recording and mining information from private conversations. This kind of individual privacy is protected by law in may countries. You should not assume consent to record and analyze private speech.

## Caveats and recommendations

Machine learning models (like this STT model) perform best on data that is similar to the data on which they were trained. Read about what to expect from an STT model with regard to your data [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data). 

In most applications, it is recommended that you [train your own language model](https://stt.readthedocs.io/en/latest/LANGUAGE_MODEL.html) to improve transcription accuracy on your speech data.
