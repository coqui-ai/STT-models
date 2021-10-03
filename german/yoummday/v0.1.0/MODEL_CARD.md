# Model card for German STT
<p align="center">
  <img src="https://media-exp1.licdn.com/dms/image/C4E0BAQG-E3_G_O5Cbg/company-logo_200_200/0/1623842868103?e=2159024400&v=beta&t=g7WEG5VjqQbkl_e8SEyK7CnXcH_YwlWvMaN4bUXZNU0" title="Yoummday GmbH">
  <h4>Yoummday (The world’s first online marketplace for contact centers) puts its German speech model in your hands.</h4>
</p>

Jump to section:

- [Model details](#model-details)
- [Intended use](#intended-use)
- [Training data](#training-data)
- [Evaluation data](#evaluation-data)
- [Ethical considerations and disclaimer](#ethical-considerations-and-disclaimer)
- [About Yoummday](#about-yoummday)

## Model details

- Organization developing the model: trained by [Yoummday GmbH](https://www.yoummday.com/en/).
- Model date: December 10, 2021
- Model type: `Speech-to-Text`
- Model version: `v0.1.0`
- Compatible with 🐸 STT version: `v0.9.3`
- Size:
  - `model.pbmm` -> 181M
  - `kenlm.scorer` -> 411M
- License: [Attribution-NonCommercial 4.0 International (CC BY-NC 4.0) ](https://creativecommons.org/licenses/by-nc/4.0/)

## Intended use

The model is trained to work with Yoummday's telephone audio-data, hence the **8kHz** constraint. However, the model can be used in any Speech-To-Text (STT) application for the [German Language](https://en.wikipedia.org/wiki/German_language) on **8kHz, mono-channel audios**.

## Training data

The following datasets were used during the training process:

- Common Voice
- Voxforge
- Librivox
- Forscher
- Tatoeba
- Tuda
- Zamia
- YouTube data.
- Yoummday's data.

## Ethical considerations and disclaimer
- Deploying a STT model has various ethical implications. Therefore, you should consider those implications alongside the privacy rules in your region before use.
- Yoummday does not assume any liability nor responsibility for any misuse of the provided STT model.
- Yoummday reserves the right to take legal actions against any misuse that might in any way negatively affect it.


## About Yoummday
- Yoummday‘s concept is based on the sharing economy‘s principles. Among an innovative software solution, the marketplace is matching clients and freelancing call center agents whom we call talents. Through the concept, our platform provides a solution to work as a freelancing talent globally. Moreover, the provided technology enables the possibility for the talents to work from home.
- *More about Yoummday can be found [here](https://www.yoummday.com/en/company).*



<p align="center">
  <img src="https://media-exp1.licdn.com/dms/image/C4E1BAQHvtIDcqTuJqQ/company-background_10000/0/1623917729993?e=2159024400&v=beta&t=lAwwvU8DLVjEfDpE5FWMakLQzdiFrHRr_AJp9AoCYQo" title="Yoummday GmbH">
</p>
