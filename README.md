# Summarization Test

- [x] Configure a python environment with hugging face transformers
- [x] Loading a text summarization model
- [x] Bundle the app with `PyInstaller`

## Result of test

PyInstaller seems to be able to bundle pytorch and HF transformers into an executable just fine on Linux. I tested both CPU and CUDA variants of pytorch and they both worked.

For GPU acceleration, the system needs CUDA / NVIDIA deps installed separately, so maybe that could be handled by a bash script on Linux and an equivalent script or "installer" program on Windows / Mac.

Overall I think this is a positive proof-of-concept, which means if I want to use HF stack in memory cache we can probably just do that. 

I will need to test the same on Windows and Mac, and I will also need to figure out how to get whatever dependencies (e.g. CUDA) installed on the target system during the install process.

## Link dump

- https://huggingface.co/facebook/bart-large-cnn
- https://paperswithcode.com/sota/summarization-on-cnn-dailymail
- https://github.com/facebookresearch/fairseq/tree/main/examples/bart
- https://arxiv.org/abs/1910.13461
- https://pytorch.org/docs/stable/hub.html
- https://huggingface.co/transformers/main_classes/pipelines.html
- https://pyinstaller.org/en/stable/

## Setup

``` sh
python3.11 -m venv venv
source ./venv/bin/activate
``` 

Install transformers:

``` sh
pip install transformers
``` 

Install pytorch for build target. Options include:

- `Linux` + `CUDA 11.8`
- `Linux` + `CUDA 12.1`
- `Linux` + `ROCm 5.7`
- `Linux` + `CPU`
- `Mac` + `CPU`
- `Windows` + `CUDA 11.8`
- `Windows` + `CUDA 12.1`
- `Windows` + `CPU`

e.g. for `Linux` + `CUDA 12.1`

``` sh
pip3 install torch torchvision torchaudio
```

or for `Linux` + `CPU`
``` sh
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
```

Run the script:

``` sh
python summarize.py
```

Install `PyInstaller`

``` sh
pip install pyinstaller
```

Invoke `PyInstaller` to bundle the app:

``` sh
pyinstaller --onefile summarize.py --clean
```


