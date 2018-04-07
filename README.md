# Deep Learning Server Environment Setup
This file contains detailed configuration on how to setup environment on the Deep Learning server.

**IP Address**

128.173.54.27

**Directories**

All required packages are installed under /opt/, which includes

- /opt/anaconda/
  -/opt/anaconda/anaconda2/: Anaconda python 2.7 
  -/opt/anaconda/anaconda3/: Anaconda python 3.6
  
- /opt/code/: current segmentation code on git.cs.vt.edu

- /opt/wordembedding/: pre-trained GloVe and word2vec word embedding file

- /opt/stanfordnlp/: full Stanford NLP package

- /opt/cudnn/: cudnn6.0 and cudnn 7.1 files


**Python and CUDA Setup**

Currently, both CUDA-8.0 and CUDA-9.0 are installed in /usr/local/. 
PyTorch (0.3.1) and Tensorflow (r1.7) in Python 2.7 are built upon CUDA-9.0 (cudnn 7.1), 
while in Python 3.6, they are built upon CUDA-8.0 (cudnn 6.0). 
Also as requested by Yaser, I installed Tensorflow r1.4 in Python 3.6.

In order to enable these packages, you'll need to setup some environment variables in ~/.bashrc.
By default, I've activated Python 3.6 and CUDA-8.0. To use Python 2.7 and CUDA-9.0, run the following
commands in your terminal after you login:

``` bash
echo 'export PATH=/usr/local/cuda-9.0/bin:$PATH' » ~/.bashrc
echo 'export LD_LIBRARY_PATH=/usr/local/cuda-9.0/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc
echo 'export PATH=/opt/anaconda/anaconda2/bin:$PATH'
```
Also you'll need to setup CORENLP variable for python version of Stanford NLP:

``` bash
echo 'export CORENLP_HOME=/opt/stanfordnlp/stanford-corenlp-full-2018-02-27/'
```
