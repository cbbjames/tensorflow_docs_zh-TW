# 由原始碼安裝

利用pip從原始碼安裝你需要建立pip wheel，請參考前述pip安裝章節來安裝pip。

從Clone TensorFlow的repository:

```
$ git clone https://github.com/tensorflow/tensorflow

```

注意這些指令會安裝最新版本的TensorFlow master branch。若你想安裝某個特定的branch(例如某個release branch)，在`git clone`指令加上`-b <branchname>`與`--recurse-submodules`來抓取r0.8或更早的TensorFlow protobuf library。

## Linux的安裝

### 安裝Bazel

參考[這裡](http://bazel.io/docs/install.html)的指示來安裝bazel。接著由[installer for your system](https://github.com/bazelbuild/bazel/releases)下載最新的穩定版bazel版本並由以下運行安裝:

```
$ chmod +x PATH_TO_INSTALL.SH
$ ./PATH_TO_INSTALL.SH --user

```
記得將`PATH_TO_INSTALL.SH`換成你下載installer的位置。

最後根據指示將*bazel*放進你的binary path。





