# Model card for Bengali STT

Jump to section:

- [Model details](#model-details)
- [Intended use](#intended-use)
- [Performance Factors](#performance-factors)
- [Metrics](#metrics)
- [Training data](#training-data)
- [Training parameters](#training-parameters)
- [Evaluation data](#evaluation-data)
- [Ethical considerations](#ethical-considerations)
- [Caveats and recommendations](#caveats-and-recommendations)

## Model details

- Person and organization developing model: [Alp Öktem](https://alpoktem.github.io/) @[Clear Global/Translators without Borders](https://clearglobal.org/).
- Model language: Bengali / বাংলা / `bn` / `ben`
- Model date: June 9, 2021
- Model type: `Speech-to-Text`
- Model version: `v0.1.0`
- Compatible with 🐸 STT version: `v0.10.0a6`
- License: Custom
- Citation details: `@techreport{bengali-stt, author = {\"Oktem, Alp}, title = {Bengali STT 0.1}, institution = {Translators without Borders}, address = {\url{https://github.com/coqui-ai/STT-models}} year = {2021}, month = {June}, number = {STT-BN-0.1} }`
- Official page: [https://gamayun.translatorswb.org/data/](https://gamayun.translatorswb.org/download/bengali-asr-model/)
- Where to send questions or comments about the model: You can leave an issue on [`STT-model` issues](https://github.com/coqui-ai/STT-models/issues), open a new discussion on [`STT-model` discussions](https://github.com/coqui-ai/STT-models/discussions), or chat with us on [Gitter](https://gitter.im/coqui-ai/).

## Intended use

Speech-to-Text for the [Bengali Language](https://en.wikipedia.org/wiki/Bengali_language) on 16kHz, mono-channel audio.

## Performance Factors

Factors relevant to Speech-to-Text performance include but are not limited to speaker demographics, recording quality, and background noise. Read more about STT performance factors [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data).

## Metrics

STT models are usually evaluated in terms of their transcription accuracy, deployment Real-Time Factor, and model size on disk.

#### Transcription Accuracy

The following Word Error Rates and Character Error Rates are reported on [Large Bengali ASR training data set](https://www.openslr.org/53/). 

|Test Corpus|WER|CER|
|-----------|---|---|
|Large Bengali ASR training data set|30.6\%|11.0\%|

#### Real-Time Factor

Real-Time Factor (RTF) is defined as `processing-time / length-of-audio`. The exact real-time factor of an STT model will depend on the hardware setup, so you may experience a different RTF.

Recorded average RTF on laptop CPU: ` `

#### Model Size

`bn-model.pbmm`: 189.3M
`general-bn.scorer`: 71.9M

### Approaches to uncertainty and variability

Confidence scores and multiple paths from the decoding beam can be used to measure model uncertainty and provide multiple, variable transcripts for any processed audio.

## Training data

Acoustic model was trained on top of English STT model using the [Large Bengali ASR training data set](https://www.openslr.org/53/). It was converted to 16kHz WAV before training. 

Train size: 203067 samples, 199.99 hours
Dev size: 10690 samples, 10.55 hours

Language model was trained on OSCAR and Bengali portions of English-Bengali parallel corpora available from [OPUS](https://opus.nlpl.eu/). 

Lines: 782827 
Tokens: 13953256

## Training parameters

|Parameter|Value|
|---------|-----|
|Epochs|200|
|Drop source layers|2|
|Learning rate|0.001|
|Dropout rate|0.2|
|augment frequency_mask|[p=0.8,n=2:4,size=2:4]|
|augment time_mask|[p=0.8,n=2:4,size=10:50,domain=spectrogram] |
|Train/test/dev batch size|32|

## Evaluation data

The Model was evaluated on a 2000 sample subset (1.84 hours) of [Large Bengali ASR training data set](https://www.openslr.org/53/). Testing set filenames and transcriptions are included with the model.

## Ethical considerations

Deploying a Speech-to-Text model into any production setting has ethical implications. You should consider these implications before use.

### Demographic Bias

You should assume every machine learning model has demographic bias unless proven otherwise. For STT models, it is often the case that transcription accuracy is better for men than it is for women. If you are using this model in production, you should acknowledge this as a potential issue.

### Surveillance

Speech-to-Text may be mis-used to invade the privacy of others by recording and mining information from private conversations. This kind of individual privacy is protected by law in may countries. You should not assume consent to record and analyze private speech.

## Caveats and recommendations

Machine learning models (like this STT model) perform best on data that is similar to the data on which they were trained. Read about what to expect from an STT model with regard to your data [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data). 

In most applications, it is recommended that you [train your own language model](https://stt.readthedocs.io/en/latest/LANGUAGE_MODEL.html) to improve transcription accuracy on your speech data.
