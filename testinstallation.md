# 測試安裝

## (Linux選項) 開啟GPU支援

如果你先前安裝了GPU版本的TensorFlow，你必須同時安裝Cuda Toolkit 7.5 及 cuDNN v4。請見Cuda安裝。

你必須設置 LD_LIBRARY_PATH 及 CUDA_HOME環境變數。 請在`~/.bash_profile` 下加上以下指令，以確保你的CUDA安裝在`/usr/local/cuda`:

```
export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/cuda/lib64"
export CUDA_HOME=/usr/local/cuda
```

## 由命列列啟動TensorFlow

若有任何錯誤發生，請見[常見問題]()。

打開終端機並輸入以下:

```
$ python
...
>>> import tensorflow as tf
>>> hello = tf.constant('Hello, TensorFlow!')
>>> sess = tf.Session()
>>> print(sess.run(hello))
Hello, TensorFlow!
>>> a = tf.constant(10)
>>> b = tf.constant(32)
>>> print(sess.run(a + b))
42
>>>

```

## 啟動TensorFlow演示模型(demo model)

所有的TensorFlow package包括演示模型(demo models)都安裝在Python library。精確的安裝位置根據你的系統不同，但通常是以下之一:

```
/usr/local/lib/python2.7/dist-packages/tensorflow
/usr/local/lib/python2.7/site-packages/tensorflow

```
你可以利用以下的指令找到所在資料夾(注意: 使用你用來安裝TensorFlow的Python版本，例如如果你是用 Python3 安裝，輸入`python3`而不是`Python`。)

```
$ python -c 'import os; import inspect; import tensorflow; print(os.path.dirname(inspect.getfile(tensorflow)))'

```
