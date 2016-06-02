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