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

$$ a_t = b + Wh_{t-1} + Ux_t $$
<br>
$$ ppx =  \int_x \int_y P(x) P_{true}(y|x) \log P(y|x) dx dy$$
<br>
在这里，**参数共享**起到重要作用。从公式看出，参数矩阵U、W、V并没有变化，而是使用同一组参数。参数共享的意义在于`在一段文本中，部分重要的信息可能出现在序列的任何位置，甚至同时出现在多个位置上。`也正是由于参数共享的作用，RNN可以处理任意长度的序列。
# LSTM--长短期记忆网络
* LSTM(Long Short Term Memory Networks)可以解决**长期依赖问题**，它是RNN的改进。
* LSTM的改进就是多出了三个门控制器：输入门、输出门、遗忘门。三个门控制器的结构都相同，主要由sigmoid函数和点积操作构成。门控制器描述了信息能够通过的比例。
* 从网络结构设计角度来说，LSTM对标准RNN的改进主要体现在`通过门控制器增加了对不同时刻记忆的权重控制，以及加入跨层连接、削减梯度消失问题的影响。`
* 如果一件事情非常重要，输入门就按重要程度将短期记忆合并进长期记忆，或者通过遗忘门忘记部分长期记忆，按比例替换为现在的新记忆。