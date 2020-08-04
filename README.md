# atomdemo

pocketsphinx_continuous -inmic yes

CMU Sphinx介绍



CMU Sphinx(简称Sphinx)是美国卡内基梅隆大学开发的一系列语音识别系统的总称，也是一个领先的语音识别工具包，具有用于构建语音应用程序的各种工具，CMU Sphinx包含许多用于不同任务和应用程序的开发包。主要包括：

• Pocketsphinx — lightweight recognizer library written in C（C语言开发的轻量级语音识别引擎）

• Sphinxtrain — acoustic model training tools （声学模型训练工具）

• Sphinxbase — support library required by Pocketsphinx andSphinxtrain（Pocketsphinx和Sphinxtrain的基础类库）

• Sphinx4 — adjustable, modifiable recognizer written in Java (Java语言开发的可调节、可修改的语音识别引擎)





CMU Sphinx包含的模型



CMU Sphinx中的模型包括声学模型（acoustic model）、语言模型（language model）、发音字典（phonetic dictionary）。

**（1）声学模型主要用于计算语音特征和每个发音模板之间的似然度**，目的是为每个声学单元建立一套模型参数，通过不断地学习和改进得到概率最大的一组HMM模型参数。CMU Sphinx的声学模型包含每个句子的声学特性，存在与上下文相关的模型，其包含属性（每个音素的最可能的特征向量）和依赖于上下文的（从具有上下文的语音建立的）属性。

**（2）语言模型定义了哪些单词可以遵循以前识别的单词**，并通过剥离不可能的单词来帮助限制匹配过程。最常用的语言模型是N-gram语言模型，它包含单词序列的统计数据和有限状态语言模型，通过有限状态自动化（有时具有权重）来定义语音序列。

**（3）发音字典包含了从单词(words)到音素(phones)之间的映射**，作用是用来连接声学模型和语言模型。发音字典包含系统所能处理的单词的集合，并标明了其发音。通过发音字典得到声学模型的建模单元和语言模型建模单元间的映射关系，从而把声学模型和语言模型连接起来，组成一个搜索的状态空间用于解码器进行解码工作。





CMU Sphinx中文模型



CMU Sphinx的中文模型主要有如下3个包：

> **声学模型**：zh_broadcastnews_16k_ptm256_8000.tar.bz2
> **语言模型**：zh_broadcastnews_64000_utf8.DMP
> **拼音字典**：zh_broadcastnews_utf8.dic

zh_broadcastnews_ptm256_8000目录结构

├── feat.params //HMM模型的特征参数

├── mdef //模型定义文件（为每个即将进行训练的HMM的每一状态定义一个独特的数字标识）

├── means //混合高斯模型的均值

├── mixture_weights //混合权重

├── noisedict //噪声也就是非语音字典

├── sendump //用来从声学模型中获取mixture_weights文件的？

├── transition_matrices //HMM模型的状态转移矩阵

└── variances //混合高斯模型的方差



授人以渔

CMU Sphinx中包含了许多简单易懂的案例（Demo），对语音识别感兴趣的童鞋不妨一试。

- CMU Sphinx主页：[https://cmusphinx.github.io/](https://link.zhihu.com/?target=https%3A//cmusphinx.github.io/)
- 教学网址：[https://cmusphinx.github.io/wiki/tutorial/](https://link.zhihu.com/?target=https%3A//cmusphinx.github.io/wiki/tutorial/)
- 模型下载地址：[https://sourceforge.net/projects/cmusphinx/files/Acoustic%20and%20Language%20Models/]