# Model card for Hindi STT v0.8.99

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

- Person or organization developing model: Trained and released by [Bülent Özden](https://www.linkedin.com/in/bülent-özden-53869019/) a member of [Common Voice Türkçe](https://twitter.com/CVTurkce) for the [3D Voice Chess](https://github.com/HarikalarKutusu/3d-voice-chess) project by [Harikalar Kutusu](https://github.com/HarikalarKutusu).
- Model language: Hindi / हिन्दी / `hi`
- Model date: March 13, 2022
- Model type: `Speech-to-Text`
- Model version: `v0.8.99`
- Compatible with 🐸 STT version: `v1.0.0`
- License: CC-BY-SA 4.0
- Citation details: `@misc{hindi-stt, author = {Bülent Özden}, title = {Hindi STT v0.8.99}, institution = {Harikalar Kutusu}, address = {\url{https://coqui.ai/models}} year = {2022}, month = {March}, number = {STT-HI-0.8.99} }`
- Where to send questions or comments about the model: You can leave an issue on [`STT` issues](https://github.com/coqui-ai/STT/issues), open a new discussion on [`STT` discussions](https://github.com/coqui-ai/STT/discussions), or chat with us on [Gitter](https://gitter.im/coqui-ai/).

## Intended use

Speech-to-Text for the [Hindi Language](https://en.wikipedia.org/wiki/Hindi) on 16kHz, mono-channel audio.

## Performance Factors

Factors relevant to Speech-to-Text performance include but are not limited to speaker demographics, recording quality, and background noise. Read more about STT performance factors [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data).

## Metrics

STT models are usually evaluated in terms of their transcription accuracy, deployment Real-Time Factor, and model size on disk.

#### Transcription Accuracy

This model only includes acoustic model, as it is developed for the special purpose low-vocabulary application. The following is the results from the Acoustic Model training.

|Test Corpus|WER|CER|
|-----------|---|---|
|Common Voice|82.2\%|34.6\%|

#### Model Size

`model.tflite`: 46M

### Approaches to uncertainty and variability

Confidence scores and multiple paths from the decoding beam can be used to measure model uncertainty and provide multiple, variable transcripts for any processed audio.

## Training data

This model was trained on the following corpora: [Common Voice](https://commonvoice.mozilla.org/en/datasets) Corpus 8.0 for Hindi. Custom train/dev/test splits are created by [Common Voice Corpora Creator](https://github.com/common-voice/CorporaCreator) with --duplicate-sentence-count 99 parameter, which allowed us to use the whole dataset. The dataset contains approximately ~11 hours of voice data (276 distinct voices, 65% male, 4% female).

Note: Our model numbering for Common Voice only data reflect Common Voice corpus version and Corpora Creator duplicate-sentence-count (dsc) setting (e.g. "v0.corpus.dsc").

## Evaluation data

The validation ("dev") and test ("test") sets also came from CV as specified above.

## Ethical considerations

Deploying a Speech-to-Text model into any production setting has ethical implications. You should consider these implications before use.

### Demographic Bias

You should assume every machine learning model has demographic bias unless proven otherwise. For STT models, it is often the case that transcription accuracy is better for men than it is for women. If you are using this model in production, you should acknowledge this as a potential issue.

### Surveillance

Speech-to-Text may be mis-used to invade the privacy of others by recording and mining information from private conversations. This kind of individual privacy is protected by law in may countries. You should not assume consent to record and analyze private speech.

## Caveats and recommendations

Machine learning models (like this STT model) perform best on data that is similar to the data on which they were trained. Read about what to expect from an STT model with regard to your data [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data). 

In most applications, it is recommended that you [train your own language model](https://stt.readthedocs.io/en/latest/LANGUAGE_MODEL.html) to improve transcription accuracy on your speech data.
