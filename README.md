

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

![push output](https://github.com/Ava7i/How-to-install-git-LFS-on-Linux-22.4/blob/main/Img/lfs.png)

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
4. Then type

```python
$chmod 755 install.sh
$sudo ./install.sh
```

5. Then install

```python
$git lfs install
```

![push output](https://github.com/Ava7i/How-to-install-git-LFS-on-Linux-22.4/blob/main/Img/Screenshot%20from%202022-11-09%2016-20-19.png)
 ## SUCCESS!!
## How can you use git LFS in your repo
1. Go to settings on your repository
2. Then click the button 
 
 
 ![push output](https://github.com/Ava7i/How-to-install-git-LFS-on-Linux-22.4/blob/main/Img/Screenshot%20from%202022-11-09%2016-29-32.png)

3. ActivateD git LFS IN YOUR REPO.

# OR YOU CAN USE git LFS by VS code

 ![push output](https://github.com/Ava7i/How-to-install-git-LFS-on-Linux-22.4/blob/main/Img/Screenshot%20from%202022-11-09%2016-46-02.png)
 
 
 
 ## ANOTHER WAY:
1. select the file types you'd like Git LFS to manage (Suppose the file extension is .py)
 
```python
git lfs track "*.py"
```

2. select the file types you'd like Git LFS to manage (Suppose the file extension is .py)
 
```python
git add .gitattributes
vi .gitattributes


```

3. Now just push and commit your repo
```python
git add ubattery_dep.py
git commit -am "Add isotopic composition after depletion"
git push origin master

```

