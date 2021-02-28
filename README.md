# knlp

这是一个工具包，主要实现对中文的NLP基础操作，在实现过程中，调研了网络上很多已经开源的工具包，对他们致以深深的感谢。

在coding过程中，参考学习了很多参考pkg中的编码方式，也有直接调用。如果作者感觉到被冒犯，请随时私信联系。

本pkg的主体架构参考了snownlp和textblob，因为这种实现方式对于调用方来说最方便。


pkg中提供了inference这个方法，主要是调用各种能力进行inference，seg这样的类是实现对应的功能。最后seq_upgrade，这样的pkg中有训练使用的代码，可以用来自己进行训练

最后，这个pkg还提供了很多现成的对各种nlp任务的评估方法以及相应的评估数据集（或者地址），可以供各位NLPer进行学习使用。

和现有的NLP工具包的不同点在于，本pkg提供深度学习相关的功能，并且面向中文开发，且功能很基础，适合于based on这个进行二次改造。

# 安装方式
```
pip install knlp
```

# 参考并致谢
- snownlp
- jieba
- textblob
- https://www.letiantian.me/2014-06-10-pagerank/

# 评估结果
离线评估

c榜单评估结果


# 开发方案
因为这不是一个有强时间节点的工作，所以我并不适合将具体的时间节点写在这里，但是其他的方案我还是应该简单设计一下。

首先，明确一下这个工程的目标，是一个即自私又无私的项目：
1. 这个项目要能可以集成现在已经有的一些能力，并很方便的调用他们，所以在api的设计上，工程的设计上一定要友好一些，且需要从用户使用的角度来考虑。
2. 另一方面，我可以借此机会把基础的算法数据结构自己都实现一次，这是一个挺长久的工作。

## 开发节点
### 第一阶段：完成基础的工程架构，通过开源能力将基础的能力具备，且可以pip安装使用
第一个阶段，就不对自己实现具体的算法做要求，主要是调用开源的能力实现，这里考究的是工程架构，以及一些基础的工作。同时我也要把各个模块的评估在这里写好，这样才能评估各个模块的具体的性能如何。

- [ ] test模块
- [ ] 各个能力的调用入口类knlp
- [ ] 序列标注
    - [ ] 分词
        - [ ] jieba
        - [ ] snownlp
        - [ ] 分词的评估
    - [ ] NER
        - [ ] jieba
        - [ ] snownlp
        - [ ] 分词的评估
- [ ] 信息提取
- [ ] 输入归一化
- [ ] 情感识别


### 第二阶段：需要自己实现各个模块的非深度学习部分，这里考究的是自己对基础的算法与数据结构在NLP上的应用能力。（要求，理论写不清楚，就不准打勾）


### 第三阶段：需要自己实现各个模块的深度学习部分，之所以放在这里是因为这个的迭代是一个长期工作，会有很多新的模型出来，随便follow一下就会有一次更新，不如直接放在最后

上传的指令：
```bash
python setup.py sdist bdist_wheel
pip install certifi --upgrade
twine upload dist/*
```