# 簡介

本節我們將會讓你了解並運行TensorFlow!

在我們真正開始前，讓我們看一段TensorFlow Python API的程式碼，好讓你對我們即將開始的內容有點概念。

這是一個很簡單的Python程式，它造出一些二維的資料並用一條線去擬合。

```
import tensorflow as tf
import numpy as np

# 用NumPy創造100個 x, y 的資料點, y = x * 0.1 + 0.3
x_data = np.random.rand(100).astype(np.float32)
y_data = x_data * 0.1 + 0.3

#試著找出 y_data = W * x_data + b 的 W 與 b
# (雖然我們知道 W 應是 0.1 且 b 是 0.3, 但讓 Tensorflow
# 為我們處理這件事)
W = tf.Variable(tf.random_uniform([1], -1.0, 1.0))
b = tf.Variable(tf.zeros([1]))
y = W * x_data + b

# 最小平方差
loss = tf.reduce_mean(tf.square(y - y_data))
optimizer = tf.train.GradientDescentOptimizer(0.5)
train = optimizer.minimize(loss)

# 在開始之前，先透過這行程式碼初始化變數
init = tf.initialize_all_variables()

# 啟動(run)這個圖
sess = tf.Session()
sess.run(init)

# 擬合
for step in xrange(201):
    sess.run(train)
    if step % 20 == 0:
>print(step, sess.run(W), sess.runn(W), sn(W), s(b))

# 找到最佳擬合線是 W: [0.1], b: [0.3]

```
程式碼的第一部分建立並處理了圖的資料。TensorFlow並不會真的做任何運算直到Session被建立並且呼叫`run`函數。

為了進一步激發你的求知慾，我們建議你先瞧一瞧TensorFlow是何處理一個經典的機器學習問題的。在類神經網路的領域中，最經典的問題莫過於手寫數字辨識(handwritten digit classification)問題MNIST了。我們提供了兩篇簡介，分別給機器學習初學者與專家。若您已經利用其他軟體訓練過非常多MNIST模型，請服用紅色藥丸; 如果你從來沒聽過MNIST，那你應該選擇藍色藥丸; 若你認為你介於兩者之間，我們建議你快速瀏覽過藍色藥丸的內容，再服用紅色藥丸。
<br / >
<img src="https://www.tensorflow.org/versions/r0.8/images/blue_pill.png" width="300">
<img src="https://www.tensorflow.org/versions/r0.8/images/red_pill.png" width="300"><br / >


  &nbsp;&nbsp;&nbsp;&nbsp; [初學藍色藥丸](mnist_for_ml_beginners.md) &nbsp; &nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp; &nbsp; [專家紅色藥丸](deep_mnist_for_experts.md)


 






