# Model card for Yoloxóchitl Mixtec STT

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

- Person or organization developing model: Originally trained by [Joe Meyer](https://www.linkedin.com/in/joe-meyer-25753951/).
- Model language: Yoloxóchitl Mixtec / / `xty`
- Model date: April 17, 2022
- Model type: `Speech-to-Text`
- Model version: `v0.1.0`
- Compatible with 🐸 STT version: `v1.0.0`
- License: CC BY-NC-SA 3.0 
- Citation details: `@techreport{xty-stt, author = {Meyer,Joe}, title = {Yoloxóchitl Mixtec STT 0.1}, institution = {Coqui}, address = {\url{https://github.com/coqui-ai/STT-models}} year = {2022}, month = {April}, number = {STT-SLR89-XTY-0.1} }`
- Where to send questions or comments about the model: You can leave an issue on [`STT-model` issues](https://github.com/coqui-ai/STT-models/issues), open a new discussion on [`STT-model` discussions](https://github.com/coqui-ai/STT-models/discussions), or chat with us on [Gitter](https://gitter.im/coqui-ai/).

## Intended use

Speech-to-Text for the [Yoloxóchitl Mixtec Language](https://en.wikipedia.org/wiki/Yolox%C3%B3chitl_Mixtec) on 16kHz, mono-channel audio.

## Performance Factors

Factors relevant to Speech-to-Text performance include but are not limited to speaker demographics, recording quality, and background noise. Read more about STT performance factors [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data).

## Metrics

STT models are usually evaluated in terms of their transcription accuracy, deployment Real-Time Factor, and model size on disk.

#### Transcription Accuracy

The following Word Error Rates and Character Error Rates are reported for a modified data set from OpenSLR [SLR89](https://www.openslr.org/89/). The official `validated.tsv` had rows removed which had errors processing, and the data was re-processed by [Cmmon Voice Utils](https://github.com/ftyers/commonvoice-utils) to convert to 16kHz mono-channel PCM .wav files.

|Test Corpus|WER|CER|
|-----------|---|---|
|OpenSLR|48.85\%|18.04\%|

#### Real-Time Factor

Real-Time Factor (RTF) is defined as `processing-time / length-of-audio`. The exact real-time factor of an STT model will depend on the hardware setup, so you may experience a different RTF.

Recorded average RTF on laptop CPU: ``

#### Model Size

`model.pbmm`: M
`model.tflite`: M

### Approaches to uncertainty and variability

Confidence scores and multiple paths from the decoding beam can be used to measure model uncertainty and provide multiple, variable transcripts for any processed audio.

## Training data

This model was trained on a modified data set from OpenSLR [SLR89](https://www.openslr.org/89/). The official `validated.tsv` had rows removed which had errors processing, and the data was re-processed by [Cmmon Voice Utils](https://github.com/ftyers/commonvoice-utils) to convert to 16kHz mono-channel PCM .wav files.

## Evaluation data

This model was evaluated on a modified data set from OpenSLR [SLR89](https://www.openslr.org/89/). The official `validated.tsv` had rows removed which had errors processing, and the data was re-processed by [Cmmon Voice Utils](https://github.com/ftyers/commonvoice-utils) to convert to 16kHz mono-channel PCM .wav files.

## Ethical considerations

Deploying a Speech-to-Text model into any production setting has ethical implications. You should consider these implications before use.

### Demographic Bias

You should assume every machine learning model has demographic bias unless proven otherwise. For STT models, it is often the case that transcription accuracy is better for men than it is for women. If you are using this model in production, you should acknowledge this as a potential issue.

### Surveillance

Speech-to-Text may be mis-used to invade the privacy of others by recording and mining information from private conversations. This kind of individual privacy is protected by law in may countries. You should not assume consent to record and analyze private speech.

## Caveats and recommendations

Machine learning models (like this STT model) perform best on data that is similar to the data on which they were trained. Read about what to expect from an STT model with regard to your data [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data). 

In most applications, it is recommended that you [train your own language model](https://stt.readthedocs.io/en/latest/LANGUAGE_MODEL.html) to improve transcription accuracy on your speech data.
