# Model card for Swahili STT v8.0

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
- Model language: Swahili / kiswahili / `sw`
- Model date: March 8, 2022
- Model type: `Speech-to-Text`
- Model version: `v8.0`
- Compatible with 🐸 STT version: `v1.3.0`
- License: Apache 2.0
- Citation details: `@techreport{swahili-stt, author = {Coqui}, title = {Swahili STT v8.0}, institution = {Coqui}, address = {\url{https://coqui.ai/models}} year = {2022}, month = {March}, number = {STT-SW-8.0} }`
- Where to send questions or comments about the model: You can leave an issue on [`STT` issues](https://github.com/coqui-ai/STT/issues), open a new discussion on [`STT` discussions](https://github.com/coqui-ai/STT/discussions), or chat with us on [Gitter](https://gitter.im/coqui-ai/).

## Intended use

Speech-to-Text for the [Swahili Language](https://en.wikipedia.org/wiki/Swahili_language) on 16kHz, mono-channel audio.

## Performance Factors

Factors relevant to Speech-to-Text performance include but are not limited to speaker demographics, recording quality, and background noise. Read more about STT performance factors [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data).

## Metrics

STT models are usually evaluated in terms of their transcription accuracy, deployment Real-Time Factor, and model size on disk.

#### Transcription Accuracy

Using the language model with settings `lm_alpha=0.898202045251655` and `lm_beta=2.2684674938753755` (found via `lm_optimizer.py`):

- Swahili Common Voice 8.0 Test: WER: 15.8\%, CER: 6.6\%

#### Model Size

For STT, you always must deploy an acoustic model, and it is often the case you also will want to deploy an application-specific language model.

|Model type|Vocabulary|Filename|Size|
----------------|-----|----------------|-----|
|Acoustic model | open | `model.tflite` | 45M|
|Language model | large  | `large-vocabulary.scorer` |321M|

### Approaches to uncertainty and variability

Confidence scores and multiple paths from the decoding beam can be used to measure model uncertainty and provide multiple, variable transcripts for any processed audio.

## Training data

This model was trained on the following corpora: Common Voice 8.0 Swahili.

## Evaluation data

The validation ("dev") sets came from Common Voice 8.0.

## Ethical considerations

Deploying a Speech-to-Text model into any production setting has ethical implications. You should consider these implications before use.

### Demographic Bias

You should assume every machine learning model has demographic bias unless proven otherwise. For STT models, it is often the case that transcription accuracy is better for men than it is for women. If you are using this model in production, you should acknowledge this as a potential issue.

### Surveillance

Speech-to-Text may be mis-used to invade the privacy of others by recording and mining information from private conversations. This kind of individual privacy is protected by law in may countries. You should not assume consent to record and analyze private speech.

## Caveats and recommendations

Machine learning models (like this STT model) perform best on data that is similar to the data on which they were trained. Read about what to expect from an STT model with regard to your data [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data). 

In most applications, it is recommended that you [train your own language model](https://stt.readthedocs.io/en/latest/LANGUAGE_MODEL.html) to improve transcription accuracy on your speech data.
