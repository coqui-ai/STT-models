# Model card for French STT

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

- Person or organization developing model: Originally trained and released by the [commonvoice-fr](https://github.com/common-voice/commonvoice-fr) project, revived by [Waser Technologies](https://github.com/wasertech/commonvoice-fr/tree/v0.9.0-fr-0.1)
- Model date: Accessed from [Github](https://github.com/wasertech/commonvoice-fr/releases/tag/v0.9.0-fr-0.1) on Jun 10, 2022
- Model type: `Speech-to-Text`
- Model version: `v0.9`
- Compatible with 🐸 STT version: `v1.4.0`
- Code: [commonvoice-fr](https://github.com/wasertech/commonvoice-fr/tree/v0.9.0-fr-0.1)
- License: MPL 2.0
- Citation details: `@misc{commonvoice-fr,
author = {commonvoice-fr Contributors},
title = {Common Voice Fr STT Model},
publisher = {Github},
journal = {GitHub repository},
howpublished = {\url{https://github.com/wasertech/commonvoice-fr/releases/tag/v0.9.0-fr-0.1}},
commit = {0a2d028b124691bbee656f43aa02251169dce69b}
}`
- Where to send questions or comments about the model: You can leave an issue on [`STT-model` issues](https://github.com/coqui-ai/STT-models/issues), open a new discussion on [`STT-model` discussions](https://github.com/coqui-ai/STT-models/discussions), or chat with us on [Gitter](https://gitter.im/coqui-ai/).

## Intended use

Speech-to-Text for the [French Language](https://en.wikipedia.org/wiki/French_language) on 16kHz, mono-channel audio.

## Performance Factors

Factors relevant to Speech-to-Text performance include but are not limited to speaker demographics, recording quality, and background noise. Read more about STT performance factors [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data).

## Metrics

STT models are usually evaluated in terms of their transcription accuracy, deployment Real-Time Factor, and model size on disk.

#### Transcription Accuracy

The following Word Error Rates (WER) are reported on [Github](https://github.com/wasertech/commonvoice-fr/releases/tag/v0.9.0-fr-0.1).

|Test Corpus|WER|CER|
|-----------|---|---|
|African_Accented_French_test.csv|47.7\%|6.6\%|
|Att-HACK|12.9\%|7.1\%|
|M-AILABS|9.9\%|3.3\%|
|trainingspeech|10.9\%|4.1\%|
|Common Voice|31.5\%|15.2\%|
|LinguaLibre|67.6\%|21.6\%|
|MLS|22.6\%|9.7\%|

#### Real-Time Factor

Real-Time Factor (RTF) is defined as `processing-time / length-of-audio`. The exact real-time factor of an STT model will depend on the hardware setup, so you may experience a different RTF.

Recorded average RTF on laptop CPU: `~0.3`

#### Model Size

`model.tflite`: 46M
`kenlm.scorer`: 689M

### Approaches to uncertainty and variability

Confidence scores and multiple paths from the decoding beam can be used to measure model uncertainty and provide multiple, variable transcripts for any processed audio.

## Training data

This French STT model was trained on the following corpora:

1. Lingua Libre (~40h)
2. Common Voice FR (v8) (~850h, by allowing up to 32 duplicates)
3. Training Speech (~180h)
4. African Accented French (~15h)
5. M-AILABS French (~315h)
6. Multilingual LibriSpeech (~1,100h)
7. Att-HACK (~75h)

Total : ~2,573h 
(~1,925h by default)

## Evaluation data

The model was tested on the following corpora.

1. Lingua Libre
2. Common Voice FR (v9)
3. Training Speech
4. African Accented French
5. M-AILABS French
6. Multilingual LibriSpeech
7. Att-HACK

Data was augmented with the following parameters.

```
Parsed augmentations: [
    Reverb(p=0.1, delay=ValueRange(start=50.0, end=50.0, r=30.0), decay=ValueRange(start=10.0, end=2.0, r=1.0)),
    Resample(p=0.1, rate=ValueRange(start=12000, end=8000, r=4000)),
    Codec(p=0.1, bitrate=ValueRange(start=48000, end=16000, r=0)),
    Volume(p=0.1, dbfs=ValueRange(start=-10.0, end=-40.0, r=0.0)),
    Pitch(p=0.1, pitch=ValueRange(start=1.0, end=1.0, r=0.2)),
    Tempo(p=0.1, factor=ValueRange(start=1.0, end=1.0, r=0.5), max_time=-1.0), 
    FrequencyMask(p=0.1, n=ValueRange(start=1, end=3, r=0), size=ValueRange(start=1, end=5, r=0)), 
    TimeMask(p=0.1, domain='signal', n=ValueRange(start=3, end=10, r=2), size=ValueRange(start=50.0, end=100.0, r=40.0)),
    Dropout(p=0.1, domain='spectrogram', rate=ValueRange(start=0.05, end=0.05, r=0.0)),
    Add(p=0.1, domain='signal', stddev=ValueRange(start=0.0, end=0.0, r=0.5)),
    Multiply(p=0.1, domain='features', stddev=ValueRange(start=0.0, end=0.0, r=0.5))
]
```

## Ethical considerations

Deploying a Speech-to-Text model into any production setting has ethical implications. You should consider these implications before use.

### Demographic Bias

You should assume every machine learning model has demographic bias unless proven otherwise. For STT models, it is often the case that transcription accuracy is better for men than it is for women. If you are using this model in production, you should acknowledge this as a potential issue.

### Surveillance

Speech-to-Text may be mis-used to invade the privacy of others by recording and mining information from private conversations. This kind of individual privacy is protected by law in may countries. You should not assume consent to record and analyze private speech.

## Caveats and recommendations

Machine learning models (like this STT model) perform best on data that is similar to the data on which they were trained. Read about what to expect from an STT model with regard to your data [here](https://stt.readthedocs.io/en/latest/DEPLOYMENT.html#how-will-a-model-perform-on-my-data). 

In most applications, it is recommended that you [train your own language model](https://stt.readthedocs.io/en/latest/LANGUAGE_MODEL.html) to improve transcription accuracy on your speech data.
