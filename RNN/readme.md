# RNN--循环神经网络
## 文本理解和文本生成问题
* 文本数据特点是：强调文字序列中前后元素之间的相互影响；属于变长数据
  <br>因此对于文本处理的模型，需要能捕捉和利用数据的顺序并能处理变长数据
* 传统的前馈神经网络假定“输入输出是定长的”、“所有输入节点之间是独立的”，因此不适用于NLP
* CNN的卷积只是输入序列中很少几个相邻元素的函数，同样不能表达文本中的语序关系
* 在RNN中，每一个输出元素的生成都基于同一个网络，这样就可以简单的输出变长结果。输出序列中的每个元素都是其之前位置的输出元素所组成的函数，这就保持了序列元素的顺序依赖关系
## 标准RNN模型
* RNN是专门用于处理**序列数据**的深度学习模型
* RNN网络是在传统神经网络的基础上加入了“记忆”部分。序列(x1,x2,..,xm)被看做一系列随时间步长(time step)递进的事件序列。其中，时间步长指序列中的位置。</br>
RNN在对当前时刻状态的计算还依赖于前一步（前一个位置）的计算结果。

用公式来表示，RNN的前向传播可以表示为：
<br>
![image](https://github.com/anonymous236/tensorflow/raw/master/RNN/CodeCogsEqn.gif)