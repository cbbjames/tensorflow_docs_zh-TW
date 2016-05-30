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

# 啟動(*'run'*)這個圖
sess = tf.Session()
sess.run(init)

# 擬合
for step in xrange(201):
    sess.run(train)
    if step % 20 == 0:
        print(step, sess.run(W), sess.run(b))

# 找到最佳擬合線是 W: [0.1], b: [0.3]


















```



