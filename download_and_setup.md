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
* [Installing from sources](https://www.tensorflow.org/versions/r0.10/get_started/os_setup.html#installing-from-sources): 建立pip wheel並用pip安裝TensorFlow。

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
$ sudo easy_install --upgrade six

```

接著選擇正確的二進位檔安裝:

```
# Ubuntu/Linux 64-bit, CPU only, Python 2.7
$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.9.0-cp27-none-linux_x86_64.whl

# Ubuntu/Linux 64-bit, GPU enabled, Python 2.7 
# Requires CUDA toolkit 7.5 and CuDNN v4. For other versions, see "Install from sources" below.
$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.9.0-cp27-none-linux_x86_64.whl

# Mac OS X, CPU only, Python 2.7:
$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/mac/tensorflow-0.9.0-py2-none-any.whl

# Ubuntu/Linux 64-bit, CPU only, Python 3.4
$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.9.0-cp34-cp34m-linux_x86_64.whl

# Ubuntu/Linux 64-bit, GPU enabled, Python 3.4 
# Requires CUDA toolkit 7.5 and CuDNN v4. For other versions, see "Install from sources" below.
$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.9.0-cp34-cp34m-linux_x86_64.whl

# Ubuntu/Linux 64-bit, CPU only, Python 3.5
$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.9.0-cp35-cp35m-linux_x86_64.whl

# Ubuntu/Linux 64-bit, GPU enabled, Python 3.5 
# Requires CUDA toolkit 7.5 and CuDNN v4. For other versions, see "Install from sources" below.
$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.9.0-cp35-cp35m-linux_x86_64.whl

# Mac OS X, CPU only, Python 3.4 or 3.5:
$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/mac/tensorflow-0.9.0-py3-none-any.whl

```

安裝TensorFlow:

```
# Python 2
$ sudo pip install --upgrade $TF_BINARY_URL

# Python 3
$ sudo pip3 install --upgrade $TF_BINARY_URL

```
**注意**: 如果你想從<0.7.1的版本升級，先解安裝舊版本的TensorFlow並用`pip uninstall` 確保你之後可以完整地安裝。

現在你可以 [測試你的安裝](testinstallation.md)

## Virtualenv 安裝

[Virtualenv](http://docs.python-guide.org/en/latest/dev/virtualenvs/)是一個可以保持位於不同位置的Python專案的依存性(dependencies)的工具。 利用Virtualenv安裝TensorFlow並不會覆蓋本來存在Python packages版本。

[Virtualenv](http://docs.python-guide.org/en/latest/dev/virtualenvs/)的安裝流程
* 安裝pip 及 Virtualenv
* 建立Virtualenv環境
* 啟用Virtualenv環境並在環境中安裝TensorFlow
* 當你每次想使用TensorFlow，先啟動Virtualenv環境

安裝pip 及 Virtualenv:

```
# Ubuntu/Linux 64-bit
$ sudo apt-get install python-pip python-dev python-virtualenv

# Mac OS X
$ sudo easy_install pip
$ sudo pip install --upgrade virtualenv

```
於目錄` ~/tensorflow`下建立Virtualenv環境:

```
$ virtualenv --system-site-packages ~/tensorflow

```
啟用Virtualenv環境並在環境中安裝TensorFlow

```
$ source ~/tensorflow/bin/activate  # If using bash
$ source ~/tensorflow/bin/activate.csh  # If using csh
(tensorflow)$  # Your prompt should change

```

同樣的，如同Pip安裝的步驟選擇正確的二進位檔安裝:

```

# Ubuntu/Linux 64-bit, CPU only, Python 2.7
(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.9.0-cp27-none-linux_x86_64.whl

# Ubuntu/Linux 64-bit, GPU enabled, Python 2.7 
# Requires CUDA toolkit 7.5 and CuDNN v4. For other versions, see "Install from sources" below.
(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.9.0-cp27-none-linux_x86_64.whl

# Mac OS X, CPU only, Python 2.7:
(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/mac/tensorflow-0.9.0-py2-none-any.whl

# Ubuntu/Linux 64-bit, CPU only, Python 3.4
(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.9.0-cp34-cp34m-linux_x86_64.whl

# Ubuntu/Linux 64-bit, GPU enabled, Python 3.4 
# Requires CUDA toolkit 7.5 and CuDNN v4. For other versions, see "Install from sources" below.
(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.9.0-cp34-cp34m-linux_x86_64.whl

# Ubuntu/Linux 64-bit, CPU only, Python 3.5
(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.9.0-cp35-cp35m-linux_x86_64.whl

# Ubuntu/Linux 64-bit, GPU enabled, Python 3.5 
# Requires CUDA toolkit 7.5 and CuDNN v4. For other versions, see "Install from sources" below.
(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.9.0-cp35-cp35m-linux_x86_64.whl

# Mac OS X, CPU only, Python 3.4 or 3.5:
(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/mac/tensorflow-0.9.0-py3-none-any.whl

```

最後安裝TensorFlow:

```

# Python 2
(tensorflow)$ pip install --upgrade $TF_BINARY_URL

# Python 3
(tensorflow)$ pip3 install --upgrade $TF_BINARY_URL

```

Virtualenv環境啟動後，現在你可以 [測試安裝](testinstallation.md)

當你使用完畢，關閉環境:

```
(tensorflow)$ deactivate

$  # Your prompt should change back

```

若要稍後繼續使用TensorFlow，你需要再次啟動Virtualenv環境:

```
$ source ~/tensorflow/bin/activate  # If using bash.
$ source ~/tensorflow/bin/activate.csh  # If using csh.
(tensorflow)$  # Your prompt should change.
# Run Python programs that use TensorFlow.
...
# When you are done using TensorFlow, deactivate the environment.
(tensorflow)$ deactivate

```

##Anaconda環境安裝
Anaconda是一個囊括許多科學數值計算package的Python版本。Anaconda使用了一個名為「conda」的package管理系統，類似Virtualenv，Anaconda也擁有自己的環境管理系統([environment system](http://conda.pydata.org/docs/using/envs.html))。

Virtualenv下的conda環境可以針對不同Python專案提供各自的版本需求。在Anaconda環境下安裝TensorFlow不會覆蓋TensorFlow需要使用到的Python package版本。

* 安裝Anaconda。
* 創建一個conda環境
* 啟動conda環境並在環境中安裝TensorFlow
* 安裝後，每次你想使用TensorFlow時都需要先啟動這個conda環境

安裝Anaconda

請依照[Anaconda download site](https://www.continuum.io/downloads)的指示

創建一個名為**TensorFlow**的conda環境:

```
# Python 2.7
$ conda create -n tensorflow python=2.7

# Python 3.4
$ conda create -n tensorflow python=3.4

# Python 3.5
$ conda create -n tensorflow python=3.5

```

啟動這個環境並用pip安裝TensorFlow，利用`--ignore-installed`參數避免`easy_install`錯誤。

```
$ source activate tensorflow
(tensorflow)$  # Your prompt should change

```

同樣的，如同Pip安裝的步驟選擇正確的二進位檔安裝:

```

# Ubuntu/Linux 64-bit, CPU only, Python 2.7
(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.9.0-cp27-none-linux_x86_64.whl

# Ubuntu/Linux 64-bit, GPU enabled, Python 2.7 
# Requires CUDA toolkit 7.5 and CuDNN v4. For other versions, see "Install from sources" below.
(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.9.0-cp27-none-linux_x86_64.whl

# Mac OS X, CPU only, Python 2.7:
(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/mac/tensorflow-0.9.0-py2-none-any.whl

# Ubuntu/Linux 64-bit, CPU only, Python 3.4
(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.9.0-cp34-cp34m-linux_x86_64.whl

# Ubuntu/Linux 64-bit, GPU enabled, Python 3.4 
# Requires CUDA toolkit 7.5 and CuDNN v4. For other versions, see "Install from sources" below.
(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.9.0-cp34-cp34m-linux_x86_64.whl

# Ubuntu/Linux 64-bit, CPU only, Python 3.5
(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.9.0-cp35-cp35m-linux_x86_64.whl

# Ubuntu/Linux 64-bit, GPU enabled, Python 3.5 
# Requires CUDA toolkit 7.5 and CuDNN v4. For other versions, see "Install from sources" below.
(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.9.0-cp35-cp35m-linux_x86_64.whl

# Mac OS X, CPU only, Python 3.4 or 3.5:
(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/mac/tensorflow-0.9.0-py3-none-any.whl

```

最後安裝TensorFlow:

```

# Python 2
(tensorflow)$ pip install --upgrade $TF_BINARY_URL

# Python 3
(tensorflow)$ pip3 install --upgrade $TF_BINARY_URL

```

conda環境啟動後，你可以 [測試安裝](testinstallation.md)

當你使用完畢，關閉環境:

```
(tensorflow)$ source deactivate

$  # Your prompt should change back

```

若要再次使用TensorFlow時，重新啟動conda環境:

```
$ source activate tensorflow
(tensorflow)$  # Your prompt should change.
# Run Python programs that use TensorFlow.
...
# When you are done using TensorFlow, deactivate the environment.
(tensorflow)$ source deactivate

```

## Docker安裝

[Docker](http://docker.com/)是一個在你的電腦建立SCS(Self-Contained Systems) Linux OS的系統。當你透過Docker安裝並運行TensorFlow，他完全獨立於你電腦裡安裝的所有package。

我們提供四個Docker映像:

* **gcr.io/tensorflow/tensorflow**: TensorFlow CPU binary image
* **gcr.io/tensorflow/tensorflow:latest-devel**: CPU Binary image plus source code
* **gcr.io/tensorflow/tensorflow:latest-gpu**: TensorFlow GPU binary image
* **gcr.io/tensorflow/tensorflow:latest-devel-gpu**: GPU Binary image plus source code

對於最新版本(e.g., 0.9.0-gpu).我們加上了*latset* tag

Docker安裝的流程如下:
* 在你的電腦安裝Docker
* 創建一個[Docker group](http://docs.docker.com/engine/installation/ubuntulinux/#create-a-docker-group)，之後不需要`sudo就能啟動`
* 啟動包含TensorFlow映像的Docker容器，第一次啟動時映像會自動下載

關於安裝Docker請參考[installing Docker](http://docs.docker.com/engine/installation/)

安裝好Docker之後，啟動Docker容器及TensorFlow的二進位檔映像:
```
$ docker run -it -p 8888:8888 gcr.io/tensorflow/tensorflow
```

`-p 8888:8888`的參數是用於傳回Docker容器的內部port給host，確保Jupyter notebook連接。

port的格式是 **hostPort:containerPort**。你可以用任何有效的port number作為host port但container Port的部分必須是`8888`。

NVidia GPU支援最新的NVidia驅動安裝與[nvidia-docker](https://github.com/NVIDIA/nvidia-docker):
```
$ nvidia-docker run -it -p 8888:8888 gcr.io/tensorflow/tensorflow:latest-gpu

```

更多細節可見[TensorFlow docker readme](https://www.google.com/url?q=https://github.com/tensorflow/tensorflow/tree/master/tensorflow/tools/docker&usg=AFQjCNFvS7IAkd_CPrZ3DK7tpMmBKmRrXg)

你現在可以利用Docker容器[測試安裝](testinstallation.md)。
