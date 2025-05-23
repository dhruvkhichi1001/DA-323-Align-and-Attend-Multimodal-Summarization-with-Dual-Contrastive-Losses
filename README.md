# Align and Attend: Multimodal Summarization with Dual Contrastive Losses (CVPR2023)
### [Paper](https://arxiv.org/abs/2303.07284)
My repository of the paper "**Align and Attend: Multimodal Summarization with Dual Contrastive Losses**".

<p align="center">
<img src="figs/teaser.png" alt="teaser" width="80%">
</p>


## Model Overview
<p align="center">
<img src="figs/model.png" alt="model" width="80%">
</p>


## Requirements
You can install the conda environment by running:
```bash
conda create -n a2summ python=3.8.13
conda activate a2summ
pip install torch==1.12.0+cu113 torchvision==0.13.0+cu113 --extra-index-url https://download.pytorch.org/whl/cu113
pip install tensorboard
pip install rouge-score==0.1.2
pip install scipy ortools h5py pyyaml
```

## Dataset
I have evaluated the Aspect-Aware Summarization (A2Summ) on two multimodal summarization multimodal output datasets ([CNN, Daily_Mail](https://aclanthology.org/2021.naacl-main.473.pdf)) and two standard video summarization datasets ([SumMe](https://gyglim.github.io/me/papers/GygliECCV14_vsum.pdf), [TVSum](https://www.cv-foundation.org/openaccess/content_cvpr_2015/papers/Song_TVSum_Summarizing_Web_2015_CVPR_paper.pdf)).
I also collected a large-scale multimodal summarization dataset BLiSS which consists of livestream videos and transcripts with annotated summary.
Before running the code, please download the pre-processed datasets from [google drive link](https://drive.google.com/drive/folders/1rqXEIelRzq4mb7NaBk3GXxh7jlfP_Snm?usp=share_link).
Unzip it under the `data/` folder and make sure the data structure is as below.

   ```
    ├── data
        └── BLiSS
            ├── annotation
            ├── feature
        └── CNN
            ├── annotation
            ├── feature
        └── Daily_Mail
            ├── annotation
            ├── feature
        └── SumMe
            ├── caption
            ├── feature
            ├── splits.yml
        └── TVSum
            ├── caption
            ├── feature
            ├── splits.yml

   ```
### BLiSS Dataset
For the BLiSS dataset, due to the copyright issue, I have only provide the extracted video/thumbnail features instead of the original videos/thunmbnails. 

## Running

### Training
I have trained the model on a single GTX-1080ti GPU. To train the model on different dataset, please execute the following command.
```bash
python train.py --dataset ${dataset}
```

### Testing
First, download the [checkpoints](https://drive.google.com/file/d/1LuXWjW3BcAXCOals4o2UUVYMx-FYnJ3T/view?usp=sharing) into "saved_model" directory and pass it as the checkpoint flag. 

```bash
python train.py --dataset ${dataset} \
    --test --checkpoint saved_model/${dataset}
```


## Acknowledgement
I have referenced the repos below for the code
- [DSNet](https://github.com/li-plus/DSNet)
- [UMT](https://github.com/TencentARC/UMT)

