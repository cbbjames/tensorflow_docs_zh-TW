# 下載與安裝

[英文原文](https://www.tensorflow.org/versions/r0.8/get_started/os_setup.html#download-and-setup)

你可以從我們提供的安裝包或是直接由Github下載來安裝TensorFlow

## 系統需求
TensorFlow Python API 支援 Python 2.7 and Python 3.3+

GPU (僅限Linux) 搭載Cuda Toolkit 7.5 及 cuDNN v4 最佳。其他版本(Cuda toolkit >= 7.0 and cuDNN 6.5(v2), 7.0(v3), v5)僅限直接由原始碼安裝。細節請參照[Cuda installation](https://www.tensorflow.org/versions/r0.8/get_started/os_setup.html#optional-install-cuda-gpus-on-linux)。

##總攬

我們支援以下方式來安裝TensorFlow:

* [Pip install](https://www.tensorflow.org/versions/r0.8/get_started/os_setup.html#pip-installation): 在本機安裝TensorFlow，可能會升級某些Python的Package，影響您電腦裡目前的Python程式。
* [Virtualenv install](https://www.tensorflow.org/versions/r0.8/get_started/os_setup.html#virtualenv-installation): 僅安裝在自目錄下，不會影響您電腦裡任何的其他Python程式。
* [Anaconda install](https://www.tensorflow.org/versions/r0.8/get_started/os_setup.html#anaconda-installation): 在 Anaconda Python 環境下安裝，不會影響您電腦裡任何的其他Python程式。
* [Docker install](https://www.tensorflow.org/versions/r0.8/get_started/os_setup.html#docker-installation): 安裝在Docker的容器下，獨立於您電腦的任何程式。

若您熟悉Pip, Virtualenv, Anaconda, 或 Docker，您可以針對你的需求來安裝。  
pip 與 Docker 的映象檔名在上述對應的連結中。  
若有安裝困難，請見[常見問題](https://www.tensorflow.org/versions/r0.8/get_started/os_setup.html#common-problems)。

## Pip安裝

Pip是一個package管理系統，可用來管理與安裝以Python寫的軟體package。

Pip安裝過程可能會安裝或升級的package清單:  [REQUIRED_PACKAGES section of setup.py](https://github.com/tensorflow/tensorflow/blob/master/tensorflow/tools/pip_package/setup.py)

安裝 pip (or pip3 for python3) :

```
# Ubuntu/Linux 64-bit
$ sudo apt-get install python-pip python-dev

# Mac OS X
$ sudo easy_install pip

```

安裝TensorFlow:

```
# Ubuntu/Linux 64-bit, CPU only:
$ sudo pip install --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.8.0-cp27-none-linux_x86_64.whl

# Ubuntu/Linux 64-bit, GPU enabled. Requires CUDA toolkit 7.5 and CuDNN v4.  For
# other versions, see "Install from sources" below.
$ sudo pip install --upgrade https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.8.0-cp27-none-linux_x86_64.whl

# Mac OS X, CPU only:
$ sudo easy_install --upgrade six
$ sudo pip install --upgrade https://storage.googleapis.com/tensorflow/mac/tensorflow-0.8.0-py2-none-any.whl

```

Python3:

```
# Ubuntu/Linux 64-bit, CPU only:
$ sudo pip3 install --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.8.0-cp34-cp34m-linux_x86_64.whl

# Ubuntu/Linux 64-bit, GPU enabled. Requires CUDA toolkit 7.5 and CuDNN v4.  For
# other versions, see "Install from sources" below.
$ sudo pip3 install --upgrade https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.8.0-cp34-cp34m-linux_x86_64.whl

# Mac OS X, CPU only:
$ sudo easy_install --upgrade six
$ sudo pip3 install --upgrade https://storage.googleapis.com/tensorflow/mac/tensorflow-0.8.0-py3-none-any.whl

```
**注意**: 如果你想從<0.7.1的版本升級，先解安裝舊版本的TensorFlow並用`pip uninstall` 確保你之後可以完整地安裝。

現在你可以[測試你的安裝](testinstallation.md)

## Virtualenv 安裝




