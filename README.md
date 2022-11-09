

# How to install git LFS on Linux 22.4

| Version Info | [![Python](https://img.shields.io/badge/python-v3.9.0-green)](https://www.python.org/downloads/release/python-390/) [![Platform](https://img.shields.io/badge/Platforms-Ubuntu%2022.04.4%20LTS%2C%20win--64-orange)](https://releases.ubuntu.com/22.04/)
|--------------|----------------|

This repository guides you to install git LFS on your pc
## Usage
Before installing git LFS you need to know what is git LFS and why should we install git LFS on our pc. 
Okay for understanting need of git LFS, let's assume the story oin below-


Suppose you create a project that contains large files or data.But you want to upload it on git. Unfortunately you cannot upload the large files on github. While you try to uploading the file on git it will show a error. 100MB is the maximum file size for git and github. A warning message is displayed for files larger than 50MB, yet they can still be pushed through.I upload a project that contains a huge dataset with 34k text. But I could not upload the file on git. It shows error which is depict in below image-

![push output](https://github.com/Ava7i/How-to-install-git-LFS-on-Linux-22.4/blob/main/Img/Screenshot%20from%202022-11-09%2012-39-45.png)
To solve this problem we need git LFS. By using git LFS we can easily upload the large files.

## What is git LFS 🚀
An addition to Git, Git LFS is an open-source project. The objective is to work with huge files and binary files into your repository more effectively.
When large files are modified, your repository's history will expand;Fetching and pulling will take longer for large files;
Other than, say, for a plain text file, where only the differences to the file are preserved, an update of a binary file will be viewed by Git as a complete file change. Your Git repository will expand in size if you often modify binary files. Git commands will start to run more slowly after a while due to your repository's expanding size.

![push output](https://github.com/Ava7i/How-to-install-git-LFS-on-Linux-22.4/blob/main/Img/lfs.gif)

##  Getting started 💡

1. Download the file for linux. Here is the link(https://git-lfs.github.com/) or you can check this link for more information(https://github.com/git-lfs/git-lfs/releases)



![push output](https://github.com/Ava7i/How-to-install-git-LFS-on-Linux-22.4/blob/main/Img/Screenshot%20from%202022-11-09%2015-29-01.png)



2. Then check the version of your git
```python
$git --version

```
If you don't have git on your pc you have to install the git first.


3. Then unzip the downloaded file using below command

```python
$cd ~/Downloads
$tar -xf git-lfs-linux-amd64-v2.9.0.tar.gz
```
3. Then type

```python
$chmod 755 install.sh
$sudo ./install.sh
```

4. Then install

```python
$git lfs install
```

![push output](https://github.com/Ava7i/How-to-install-git-LFS-on-Linux-22.4/blob/main/Img/Screenshot%20from%202022-11-09%2016-20-19.png)

## How can you use git LFS in your repo
1. Go to settings on your repository
2. Then click the button ![push output](https://github.com/Ava7i/How-to-install-git-LFS-on-Linux-22.4/blob/main/Img/Screenshot%20from%202022-11-09%2016-29-32.png)

4. ActivateD git LFS IN YOUR REPO.

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




