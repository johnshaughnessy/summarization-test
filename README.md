# Summarization Test

- [ ] Configure a python environment with hugging face transformers
- [ ] Loading a text summarization model
- [ ] Bundle the app with `PyInstaller`


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
pyinstaller --onefile summarize.py
```


