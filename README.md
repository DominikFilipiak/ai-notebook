[![Build Status](https://travis-ci.org/0xdfdfdf/ai-notebook.svg?branch=master)](https://travis-ci.org/0xdfdfdf/ai-notebook)
![Docker pulls](https://img.shields.io/docker/pulls/0xdfdfdf/ai-notebook.svg)
![Docker stars](https://img.shields.io/docker/stars/0xdfdfdf/ai-notebook.svg)
[![Metadata](https://images.microbadger.com/badges/image/0xdfdfdf/ai-notebook.svg)](https://microbadger.com/images/0xdfdfdf/ai-notebook)

<p align="center">
   <img height="60" src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/Python-logo-notext.svg/1024px-Python-logo-notext.svg.png" />
   <img height="60" src="https://samskalicky.files.wordpress.com/2018/08/cudnn-logo.png" />
  <img height="60" src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/38/Jupyter_logo.svg/1200px-Jupyter_logo.svg.png" />
  <img height="60" src="https://devblogs.nvidia.com/wp-content/uploads/2017/04/pytorch-logo-dark.png" />
  <img height="60" src="https://miro.medium.com/max/7752/1*zmMOdVZ_j9vwMcpdD8Uceg.png" />
</p>

# Python AI notebook stack
------------
Python 3 + Jupyter Notebook (with themes) + TensorFlow + PyTorch + TensorBoard + CUDA/CuDNN

Excellent for AI research on GPU(s) in Python. The Dockerfile is heavily based on [TensorFlow dockerfiles](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/tools/dockerfiles).

## Prerequisites
Requires Docker (>=19.03), NVIDIA driver and nvidia-docker (see how to install it [here](https://github.com/NVIDIA/nvidia-docker)). Tested on Debian 10, should work on Ubuntu, CentOS and RHEL as well.

## Usage
Use the following command to run the notebook:
```bash
docker-compose up 
```
If you want to make your adjustments (like I do with the KGTN repo):
```bash
docker-compose -f docker-compose.yml -f docker-compose-KGTN.yml up 
```
Now navigate to http://127.0.0.1:18888.
The default password is: *Cybermyszki7*

The following code will fire up tensorboard:
```bash
docker exec -it [container_name] tensorboard --logdir=/tf/logs --bind_all
```
Now you can navigate to http://127.0.0.1:16006 to access tensorboard.

## Additional information
You can change the default password.
In Python (```pip install ipython``` if needed) do the following:
```python
from IPython.lib import passwd
passwd()
> Enter password:
> Verify password:
> 'sha1:xxxxxxx:xxxxxxxxxxxxxxx'
```
Now you have to copy the SHA hash to the Dockerfile and built it on your computer (might take 15 minutes or so).
```
docker build -t 0xdfdfdf/ai-notebook .
```
