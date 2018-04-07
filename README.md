# Deep Learning Server Environment Setup
This file contains detailed configuration on how to setup environment on the Deep Learning server.

**Get Access**

```bash
ssh username@128.173.54.27
```

**Repositories**

All required packages and shared files are under /opt/, which includes:

- /opt/anaconda/

  -/opt/anaconda/anaconda2/: Anaconda python 2.7 
  
  -/opt/anaconda/anaconda3/: Anaconda python 3.6
  
- /opt/code/: Segmentation code on git.cs.vt.edu

- /opt/wordembedding/: Pre-trained GloVe and word2vec embeddings

- /opt/stanfordnlp/: Stanford NLP full package

- /opt/cudnn/: cudnn6.0 and cudnn 7.1 source files


**Python and CUDA Setup**

- CUDA-8.0 (cudnn 6.0) and CUDA-9.0 (cudnn 7.1) have been installed under /usr/local/. 

- PyTorch (0.3.1) and Tensorflow (r1.7) under Python 2.7 built upon CUDA-9.0 (cudnn 7.1).

- PyTorch (0.3.1) and Tensorflow (r1.4) under Python 3.6 built upon CUDA-8.0 (cudnn 6.0).

  - If I remember correctly, Yaser wants Tensorflow r1.4 with CUDA-8.0 (cudnn 6.0)?

In order to enable these packages, you can setup environment variables in ~/.bashrc.

By default, I've activated Python 3.6 in /etc/profile, which will be executed for every user. 

To specificly use these packages, please run the following commands in your terminal:

``` bash
# enable cuda-9.0
echo 'export PATH=/usr/local/cuda-9.0/bin:$PATH' » ~/.bashrc
echo 'export LD_LIBRARY_PATH=/usr/local/cuda-9.0/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc

# enbale python 2.7
echo 'export PATH=/opt/anaconda/anaconda2/bin:$PATH' >> ~/.bashrc

# enable cuda-8.0
echo 'export PATH=/usr/local/cuda-8.0/bin:$PATH' » ~/.bashrc
echo 'export LD_LIBRARY_PATH=/usr/local/cuda-9.0/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc

# enbale python 3.6
echo 'export PATH=/opt/anaconda/anaconda3/bin:$PATH' >> ~/.bashrc
```

You may comment out ones that you don't want to use in ~/.bashrc in the future.

Also you'll need to setup CORENLP variable for python version of Stanford NLP:

``` bash
# Python Stanford NLP environment variable CORENLP
echo 'export CORENLP_HOME=/opt/stanfordnlp/stanford-corenlp-full-2018-02-27/' >> ~/.bashrc
```

Enjoy!
