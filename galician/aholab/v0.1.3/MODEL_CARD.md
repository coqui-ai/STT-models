# Model Card for Galician STT

Jump to section:

- [Model details](#model-details)
- [Intended use](#intended-use)
- [Performance Factors](#performance-factors)
- [Metrics](#metrics)
- [Training data](#training-data)
- [Evaluation data](#evaluation-data)
- [Ethical considerations](#ethical-considerations)
- [Caveats and recommendations](#caveats-and-recommendations)

## Model Details

- Person or organization developing model: trained by Xabier de Zuazo and the [Aholab](https://aholab.ehu.eus/aholab/) group, inspired by [Francis Tyers](https://scholar.google.fr/citations?user=o5HSM6cAAAAJ)'s work on the following paper: [[arXiv:2105.04674] What shall we do with an hour of data? Speech recognition for the un- and under-served languages of Common Voice](https://arxiv.org/abs/2105.04674).
- Model language: Galician / Galego / `gl`
- Model date: January 5, 2023
- Model type: `Speech-to-Text`
- Model version: `v0.1.3`
- Compatible with 🐸 STT version: `v0.9.3`
- Code: [commonvoice-docker xzuazo's fork](https://gitlab.com/xzuazo/commonvoice-docker)
- License: AGPL
- Citation details: `@techreport{galician-stt, author = {de Zuazo,Xabier}, title = {Galician STT 0.1.3}, institution = {Aholab}, address = {\url{https://aholab.ehu.eus/}} year = {2023}, month = {January}, number = {STT-CV12.0-GL-0.1.3} }`
- Where to send questions or comments about the model: You can leave an issue on [`STT-model` issues](https://github.com/coqui-ai/STT-models/issues), open a new discussion on [`STT-model` discussions](https://github.com/coqui-ai/STT-models/discussions), or chat with us on [Gitter](https://gitter.im/coqui-ai/).

## Intended Use

Speech-to-Text for the [Galician Language](https://en.wikipedia.org/wiki/Galician_language) on 16kHz, mono-channel audio.

## Performance Factors

Factors relevant to Speech-to-Text performance include but are not limited to speaker demographics, recording quality, and background noise. Read more about STT performance factors [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data).

## Metrics

STT models are usually evaluated in terms of their transcription accuracy, deployment Real-Time Factor, and model size on disk.

#### Transcription Accuracy

The following Word Error Rates and Character Error Rates are reported on Common Voice test split:

|Test Corpus|WER|CER|
|-----------|---|---|
|Common Voice|16.4\%|6.8\%|

#### Model Size

`model.pbmm`: 181M
`model.tflite`: 46M
`kenlm.scorer`: 527M

### Approaches to Uncertainty and Variability

Confidence scores and multiple paths from the decoding beam can be used to measure model uncertainty and provide multiple, variable transcripts for any processed audio.

## Training Data

This model was trained on Common Voice 12.0 train.

## Evaluation Data

The Model was evaluated on Common Voice 12.0 test.

## Ethical Considerations

Deploying a Speech-to-Text model into any production setting has ethical implications. You should consider these implications before use.

### Demographic Bias

You should assume every machine learning model has demographic bias unless proven otherwise. For STT models, it is often the case that transcription accuracy is better for men than it is for women. If you are using this model in production, you should acknowledge this as a potential issue.

### Surveillance

Speech-to-Text may be mis-used to invade the privacy of others by recording and mining information from private conversations. This kind of individual privacy is protected by law in may countries. You should not assume consent to record and analyze private speech.

## Caveats and Recommendations

Machine learning models (like this STT model) perform best on data that is similar to the data on which they were trained. Read about what to expect from an STT model with regard to your data [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data).

In most applications, it is recommended that you [train your own language model](https://stt.readthedocs.io/en/latest/LANGUAGE_MODEL.html) to improve transcription accuracy on your speech data.
