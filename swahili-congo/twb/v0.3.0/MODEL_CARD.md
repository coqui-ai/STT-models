# Model card for Swahili (Congo) STT

Jump to section:

- [Model details](#model-details)
- [Intended use](#intended-use)
- [Performance Factors](#performance-factors)
- [Metrics](#metrics)
- [Training data](#training-data)
- [Training parameters](#training-parameters)
- [Language models](#language-models)
- [Evaluation data](#evaluation-data)
- [Ethical considerations](#ethical-considerations)
- [Caveats and recommendations](#caveats-and-recommendations)

## Model details

- Person and organization developing model: [Alp Öktem](https://alpoktem.github.io/) @[Clear Global/Translators without Borders](https://clearglobal.org/).
- Model language: Swahili (Congo) / `swc` / `sw-cd`
- Model date: August 26, 2021
- Model type: `Speech-to-Text`
- Model version: `v0.3.0`
- Compatible with 🐸 STT version: `v0.10.0a13`
- License: Custom (`LICENSE.txt`)
- Citation details: `@techreport{swc-stt, author = {\"Oktem, Alp}, title = {SWC STT 0.3}, institution = {Translators without Borders}, address = {\url{https://github.com/coqui-ai/STT-models}} year = {2021}, month = {June}, number = {STT-SWC-0.3} }`
- Official page: [https://gamayun.translatorswb.org/data/](https://gamayun.translatorswb.org/data/swc-stt-model)
- Where to send questions or comments about the model: Directly to [Alp Öktem](mailto:alp.oktem@clearglobal.org) or you can leave an issue on [`STT-model` issues](https://github.com/coqui-ai/STT-models/issues), open a new discussion on [`STT-model` discussions](https://github.com/coqui-ai/STT-models/discussions), or chat with us on [Gitter](https://gitter.im/coqui-ai/).

## Intended use

Speech-to-Text for the Congolese dialect of [Swahili Language](https://en.wikipedia.org/wiki/Swahili_language) on 16kHz, mono-channel audio.

## Performance Factors

Factors relevant to Speech-to-Text performance include but are not limited to speaker demographics, recording quality, and background noise. Read more about STT performance factors [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data).

## Metrics

STT models are usually evaluated in terms of their transcription accuracy, deployment Real-Time Factor, and model size on disk.

#### Transcription Accuracy

The following Word Error Rates and Character Error Rates are reported on [Congolese Swahili Commands dataset](https://gamayun.translatorswb.org/data/). 

|Test Corpus|Scorer|WER|CER|
|-----------|---|---|---|
|TICO-19 devset|swc-general|18.31\%|6.15\%|
|Congolese Swahili Commands|swc-commands|21.08\%|20.82\%|

#### Real-Time Factor

Real-Time Factor (RTF) is defined as `processing-time / length-of-audio`. The exact real-time factor of an STT model will depend on the hardware setup, so you may experience a different RTF.

Recorded average RTF on laptop CPU: ` `

#### Model Size

`swc-stt-0.3.pbmm`: 188.9 Mb
`swc-stt-0.3.tflite`:47.3 Mb
`swc-general.scorer`: 158.6 Mb
`swc-commands.scorer`: 2.9 Kb

### Approaches to uncertainty and variability

Confidence scores and multiple paths from the decoding beam can be used to measure model uncertainty and provide multiple, variable transcripts for any processed audio.

## Training data

Acoustic model was trained on top of English STT model using portions of [Congolese Swahili audio mini-kit](https://gamayun.translatorswb.org/download/congolese-swahili-audio-mini-kit/) and [TICO-19 Congolese Swahili testing set](https://gamayun.translatorswb.org/download/congolese-swahili-tico-19-audio-test-set/). It was converted to 16kHz WAV before training. 

Total train size: 8.93 (mini-kit) + 3.27 (TICO-19 testset) = 12.2 hours
Dev size: 0.49 hours (mini-kit)
Test size: 1.71 hours (TICO-19 devset) 

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

## Language models

Model is packaged with two language models (scorers):
- *General purpose language model* (`swc-general.scorer`) is trained on a 37.7M word mixed Swahili text corpus
- *Commands language model* (`swc-commands.scorer`) is trained on 12 commands (numbers from 1 to 10 and yes/no) which are listed in `vocab-commands.txt`.

## Evaluation data

The Model was evaluated on two different sets: 
- [Congolese Swahili audio commands corpus](https://gamayun.translatorswb.org/download/swc-audio-commands/): 185 sample subset (1.8 minutes) consisting of 5 speakers uttering numbers 1 to 10 and yes/no in Congolese Swahili. For this evaluation, the `swc-commands` language model was used.
- [Congolese Swahili TICO-19 audio development set](https://gamayun.translatorswb.org/download/swc-tico-19-audio-devset/): 536 sample subset (1.71 hours) consisting of TICO-19 domain sentences spoken by a male and female speaker (listed in `swc-tico-test.csv`). For this evaluation, the `swc-general` language model was used.

## Ethical considerations

Deploying a Speech-to-Text model into any production setting has ethical implications. You should consider these implications before use.

### Demographic Bias

You should assume every machine learning model has demographic bias unless proven otherwise. For STT models, it is often the case that transcription accuracy is better for men than it is for women. If you are using this model in production, you should acknowledge this as a potential issue.

### Surveillance

Speech-to-Text may be mis-used to invade the privacy of others by recording and mining information from private conversations. This kind of individual privacy is protected by law in may countries. You should not assume consent to record and analyze private speech.

## Caveats and recommendations

Machine learning models (like this STT model) perform best on data that is similar to the data on which they were trained. Read about what to expect from an STT model with regard to your data [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data). 

In most applications, it is recommended that you [train your own language model](https://stt.readthedocs.io/en/latest/LANGUAGE_MODEL.html) to improve transcription accuracy on your speech data.
