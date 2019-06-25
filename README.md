# **judicial_competition**
------------------------------

## **语言**
-----------
Python 3.6<br>
[![](https://img.shields.io/badge/Python-3.6-blue.svg)](https://www.python.org/)<br>


## **依赖库**
----------
numpy<br>
jieba<br>
pandas<br>
tensorflow<br>
Keras<br>
scikit-learn<br>

## **模块简介**
这个模块主要包含三大块：
1. 数据预处理 [data_utils](/data_utils)
2. 预测 [precditor](/python_sample/predictor)


## **数据预处理**
--------------------
数据预处理的功能主要包含在`data_utils`中，包括数据预处理各类功能函数集合[data_processing.py](/data_utils/data_processing.py)和对数据进行实际预处理的数据准备模块[data_preparation.py](/data_utils/data_preparation.py)。<br>

* __*基本流程*__：
1. 分别对train、test和valid数据进行分词并清洗；
2. 输入分好词的结果，使用keras的数据预处理工具把词语列表转化为词典，取频率最高的前40000个词语（数值可自定义）。事实证明词典大小对结果影响也是相当大的。
3. 根据词典，利用`texts_to_sequences`功能把词语列表转为序列（数字）列表，不在词典中的词语去掉；
4. 序列的长度固定为400（也可自定义，对后续的结果也是有一定的影响），利用`pad_sequences`对序列进行截断（长度大于400）或补全（长度少于400的补0）。

* __*数据预处理要点*__：
1. 对文本进行分词进行分词，只保留长度大于1的词语（即去除单个字的）；
2. 部分案情陈述中都有的涉案金额，但金额数量比较零散，不同意，容易导致在分词后建立词典时被筛掉，所以需要对涉案金额进行化整处理；
即预先订好固定的金额区间，如“50, 100, 200, 500, 800, 1000, 2000, 5000”，然后把处于对应区间的金额转化为固定的金额数值；
3. 去掉部分停用词，查阅了部分案情陈述后发现，大部分的案情陈述都涉及相同或类似的词语，如“某某，某某乡，某某县，被告人，上午，下午”等。
这类词语词频相当高，需要把他们去掉，以免影响对数据进行干扰。


## **模型**
--------------------
在这个项目的时候，对RNN和LSTM还不是很了解，所以主要使用了CNN和TextCNN去做，而且对比起RNN，CNN在时间成本上更有优势。<br>

__*CNN模型结构*：__<br>
![](/pics/cnn_filter3.png)

__*TextCNN模型结构*：__<br>
![](/pics/textcnn_filter345.png)




