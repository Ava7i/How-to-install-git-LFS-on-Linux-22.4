
#STEP 0. MAKE SURE YOU HAVE GITHUB CLIENT INSTALLED
# How to install git LFS on Linux 22.4

| Version Info | [![Python](https://img.shields.io/badge/python-v3.9.0-green)](https://www.python.org/downloads/release/python-390/) [![Platform](https://img.shields.io/badge/Platforms-Ubuntu%2020.04.4%20LTS%2C%20win--64-orange)](https://releases.ubuntu.com/20.04/) [![anaconda]
|--------------|----------------|

This repository guides you to install git LFS on your pc
## Usage
Before installing git LFS you need to know what is git LFS and why should we install git LFS on our pc. 
Okay for understanting need of git LFS, let's assume the story oin below-


Suppose you create a project that contains large files or data.But you want to upload it on git. Unfortunately you cannot upload the large files on github. While you try to uploading the file on git it will show a error. 100MB is the maximum file size for git and github. A warning message is displayed for files larger than 50MB, yet they can still be pushed through.I upload a project that contains a huge dataset with 34k text. But I could not upload the file on git. It shows error which is depict in below image-

![push output](https://github.com/Ava7i/How-to-install-git-LFS-on-Linux-22.4/blob/main/Img/Screenshot%20from%202022-11-09%2012-39-45.png)
To solve this problem we need git LFS. By using git LFS we can easily upload the large files.

## What is git LFS
An addition to Git, Git LFS is an open-source project. The objective is to work with huge files and binary files into your repository more effectively.
When large files are modified, your repository's history will expand;Fetching and pulling will take longer for large files;
Other than, say, for a plain text file, where only the differences to the file are preserved, an update of a binary file will be viewed by Git as a complete file change. Your Git repository will expand in size if you often modify binary files. Git commands will start to run more slowly after a while due to your repository's expanding size.

![push output](https://github.com/Ava7i/How-to-install-git-LFS-on-Linux-22.4/blob/main/Img/Screenshot%20from%202022-11-09%2012-39-45.png)(https://github.com/Ava7i/How-to-install-git-LFS-on-Linux-22.4/blob/main/Img/lfs.png)

## Installing / Getting started

1. Clone the repo and navigate to the directory

```python
git clone https://github.com/yeahiasarker/gpt-dialogue.git
cd gpt-dialogue
```

2. Install the required library packages named `requirements.txt` using below command

```python
pip install -r requirements.txt
```

## Usage
1. We have to first download/load the dataset using [`downloader.py`](https://github.com/yeahiasarker/gpt-dialogue/blob/main/downloader.py) by running this command in terminal:

```python
python downloader.py 
```


2. Then, Here's how to create a Mingpt model.
```python
from mingpt.model import GPT, GPTConfig
mconf = GPTConfig(train_dataset.vocab_size, train_dataset.block_size,
                  n_layer=8, n_head=8, n_embd=128) #128
model = GPT(mconf)
```
3. After that, initialize a trainer instance by using:

```python
from mingpt.trainer import Trainer, TrainerConfig

tconf = TrainerConfig(max_epochs=1, batch_size=128, learning_rate=6e-4,
                      lr_decay=True, warmup_tokens=128*20, final_tokens=2*len(train_dataset)*block_size,#   ckpt_path='mingpt_persona_v1.pt',
                      num_workers=8)
trainer = Trainer(model, train_dataset, None, tconf)
trainer.train()
```
4. Testing a text input by using:

```python
from mingpt.utils import sample

context = "i love to" #sample input 
x = torch.tensor([train_dataset.stoi[s] for s in context], dtype=torch.long)[None,...].to(trainer.device)
y = sample(model, x, 500, temperature=1.0, sample=True, top_k=10)[0]
completion = '='.join([train_dataset.itos[int(i)] for i in y])
print(completion)
```
>here is the output
```
i love to dance.', ' i am single. i enjoy nature. my favorite food is salad. my mother was a teacher.', ' i like to drust. i like to eat meat. i like to eat. i want to feel pretty.', ' my favorite band is nightfish. i work from home. i have a cat as a pet. i love reading. i love comics.', ' i enjoy home cooked meals. my favorite music genre is pop. my favorite color is blue. my favorite tv show is game of thrones. my favorite music genre is pop.', ' i love country. i enjoy reading. i love dogs. i am a ru
```
See [`QA_minGPT.ipynb`](https://github.com/yeahiasarker/gpt-dialogue/blob/main/examples/QA_mingpt.ipynb) for a more specific illustration.



## Database Info:
For training/testing the model we use [ParlAI](https://github.com/facebookresearch/ParlAI/blob/main/README.md) dialogue models, from open-domain chitchat, to task-oriented dialogue, to visual question answering dataset. 

Here is list of dataset: [parlAI_dataset_info](https://docs.google.com/spreadsheets/d/1Sw5Wjs5aGXF-rvzc49gFjLgnGvmsJgZiPNIMK2rf01I/edit?usp=sharing)




Below are the list of dataset I have tested so far. 

| #   | Dataset Name                                                              | Dataset Link                                                        | Data Format | Status  |
| --- | ------------------------------------------------------------------------- | ------------------------------------------------------------------- | ----------- | ------- |
| 1   | [PERSONA-CHAT](https://www.kaggle.com/datasets/atharvjairath/personachat) | [kaggle](https://www.kaggle.com/datasets/atharvjairath/personachat) | csv         | &check; | 
| 2  | [DailyDialog](http://yanran.li/files/ijcnlp_dailydialog.zip) | [link](http://yanran.li/files/ijcnlp_dailydialog.zip) | txt        | &check; |
| 3  | [QuAC](https://s3.amazonaws.com/my89public/quac/train_v0.2.json) | [link](https://s3.amazonaws.com/my89public/quac/train_v0.2.json) | json        | &check; |
| 4  | [MS MARCO](https://github.com/microsoft/msmarco/blob/master/Datasets.md) | [link](https://msmarco.blob.core.windows.net/msmarcoranking/msmarco-docs-lookup.tsv.gz) | tsv        | &check; |

<!-- |checked|unchecked|crossed|
|---|---|---|
|&check;|_|&cross;|
|&#x2611;|&#x2610;|&#x2612;| -->

## Docker Initialization

1. Docker build and tag

```docker
docker build -t factor_analysis .
```
2. Docker tag as per the docker hub repository name

```
docker tag mingpt shohanursobuj/mingpt
```
Alright, now we have to build a docker image and also tagged it as per our docker hub repository name.

3. Docker login
```
docker login
```
Once you issue the docker login command it will ask for your docker hub username and password.

```
Login with your Docker ID
Username : shohanursobuj
Password: ******
```

Supply your username and password. After the successful authentication, you will see a message Login Succeeded

4. docker push

```
docker push shohanursobuj/mingpt:latest
```
And here are the successful logs

```
latest: digest: sha256:e7dfba40a27d2ccf6fd86c9717288a58c885c615baa7a239723bddf63b0781b6 size: 2849
```

And here is the container running:

![push output](https://github.com/yeahiasarker/gpt-dialogue/blob/main/img/doc_01.png)


5. Viewing builds
```
docker run shohanursobuj/mingpt:latest
```

![build output](https://github.com/yeahiasarker/gpt-dialogue/blob/main/img/dock_02.png)

6. Docker build from github repository

```
docker run -p 3000:3000 -e github='https://github.com/yeahiasarker/gpt-dialogue.git' -it shohanursobuj/mingpt
```
### Prerequisites
- Ubuntu 20.04.4 LTS
- Anaconda 4.12.0
