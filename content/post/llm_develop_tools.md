---
title: LLM Develop Tools
description: llama-index, langchain, semantic-kernel and etc.
date: 2023-05-31
categories:
  - "LLM"
tags:
  - "LLM"
  - "llama-index"
  - "langchain"
  - "semantic-kernel"
menu:
  main:
    name: Article
    weight: 4
---

## Motivation

如何开发以下需求？

+ **业务 （Models、Prompt）**
  * 多模型（gpt-3.5, gpt-4, chatglm-6b, chatglm-6b-ft）
  * 多业务（运营push、个性化push、weibo地域、商业评论、新闻评论……）
  * 不同业务 X 不同模型 = 不同prompt
  * 敏感词风控
  * 输出标准化json格式

+ **网页 （Memory）**
  * 多轮对话
  * 控制记忆上限（按轮数、按token[全量, 摘要……]）

+ **外部数据 （Indexes）**
  * 汽车博文生成，需要参考车型各类参数（pdf，md, txt……）

+ **任务拆分 （Chain）**
  * 汽车博文3段式生成 
    1. 根据brief =》开头
    2. 根据brief、开头 =》 中间
    3. 根据开头、中间 =》结尾

+ **日志（Callbacks）**
  * 过程日志统计、token统计……

+ **……**


## 工具

目前开源工具包括以下几种：llama_index、langchain、semantic-kernel等。

<!--more-->

|    tool      | starred         |
|:-----------:| :------------:|
| [langchain](https://github.com/hwchase17/langchain) | 43.6k |
| [LlamaIndex(GPTIndex）](https://github.com/jerryjliu/llama_index) | 16.3k |
| [semantic-kernel](https://github.com/microsoft/semantic-kernel) | 9.6k |

+ langChain是一个用于开发LLM应用程序的`框架`，使LLM开发变得规范快捷，类似于 java的Spring Boot、php的Laravel、python的Django ……

+ LlamaIndex（GPTIndex）是LLM应用程序的`数据框架`。

  + GptIndex为什么改名为LlamaIndex？

    > Funny that we had just rebranded our tool from GPT Index to LlamaIndex about a week ago `to avoid potential trademark issues with OpenAI`, and turns out Meta has similar ideas around LLM+llama puns :). Must mean the name is good though! Also very excited to try plugging in the LLaMa model into LlamaIndex, will report the results. https://news.ycombinator.com/item?id=34928386

    ![GptIndex-renamed-LlamaIndex](/img/WechatIMG1439.png)

+ semantic-kernel（SK）是一个轻量级的SDK，能够将人工智能大型语言模型（LLM）与传统编程语言集成。

## 区别

[Q: Llamaindex vs langchain, which one should be used?](https://community.openai.com/t/llamaindex-vs-langchain-which-one-should-be-used/163139
)

|    WEB      | LLM         |
|:-----------:| :------------:|
| Spring Boot | langchain |
| ElasticSearch-Lucene、MyBatis-Mysql| LlamaIndex（GptIndex）-Faiss|

> 取决于你的最终目标，如果它主要是一个智能搜索工具，llamaindex是很棒的，如果你想构建一个能够创建插件的chatgpt克隆，那就完全不同了。Langchain允许您利用ChatGPT的多个实例，为它们提供内存，甚至多个llamaindex实例。你可以用langchain做的事情是构建代理，它可以做不止一件事，一个例子是执行python代码，同时搜索谷歌。基本上llmaindex是一种智能存储机制，而Langchain是一种将多种工具结合在一起的工具。

[Q: Differences between semantic-kernel and langchain? #936](https://github.com/microsoft/semantic-kernel/issues/936)

|    Deep Learning      | LLM         |
|:-----------:| :------------:|
| tensorflow、pytorch、paddlepaddle | langchain、semantic-kernel|


> `@santanaeds` As far as I know, semantic-kernel do support .Net, which langchain doesn't, that's all.


开源Demo

|    application     | starred         |
|:-----------:| :------------:|
|[langchain-ChatGLM](https://github.com/imClumsyPanda/langchain-ChatGLM) | 7.5k |
|[DevSecOpsKB-LlamaIndex-LangChain-OpenAI](https://github.com/wenqiglantz/DevSecOpsKB-LlamaIndex-LangChain-OpenAI) | 3 |
|[本地知识库 QA Bot](https://www.heywhale.com/mw/project/643977aa446c45f4592a1e59) | - |


**Note:** starred数据截至2023-05-31 **取个好名字很重要 (￣┰￣\*)**


## langchain

LangChain 是一个用于开发由语言模型驱动的应用程序的框架。

主要功能
+ 调用语言模型
+ 将不同数据源接入到语言模型的交互中
+ 允许语言模型与运行环境交互
![langchain_overview](/img/WX20230601-170727@2x.png)

LangChain 中提供的模块
* Models: 支持的模型类型和集成。
* Prompt: 提示词管理、优化和序列化。
* Memory: 内存是指在链/代理调用之间持续存在的状态
* Indexes: 当语言模型与特定于应用程序的数据相结合时，会变得更加强大-此模块包含用于加载、查询和更新外部数据的接口和集成。
* Chain: 链是结构化的调用序列 (对LLM或其他实用程序)。
* Agents: 代理是一个链，其中LLM在给定高级指令和一组工具的情况下，反复决定操作，执行操作并观察结果，直到高级指令完成。
* Callbacks: 回调允许您记录和流式传输任何链的中间步骤，从而轻松观察、调试和评估应用程序的内部。

![langchain_components](/img/WX20230601-170411@2x.png)

各组件功能、demo https://python.langchain.com/en/latest/getting_started/getting_started.html

> [LangChain for LLM Application Development](https://learn.deeplearning.ai/langchain/lesson/1/introduction) `@DeepLearning Ai`



## 应用 

### langchain-ChatGLM

[langchain-ChatGLM](https://github.com/imClumsyPanda/langchain-ChatGLM/tree/master/content/samples)：一种利用 ChatGLM-6B + langchain 实现的基于本地知识的 ChatGLM 应用。


langchain-ChatGLM实现原理如下图所示，过程包括加载文件 -> 读取文本 -> 文本分割 -> 文本向量化 -> 问句向量化 -> 在文本向量中匹配出与问句向量最相似的top k个 -> 匹配出的文本作为上下文和问题一起添加到prompt中 -> 提交给LLM生成回答。

![langchain+chatglm](https://github.com/imClumsyPanda/langchain-ChatGLM/blob/master/img/langchain+chatglm.png?raw=true)

从文档处理角度来看，实现流程如下：

![langchain+chatglm2](https://github.com/imClumsyPanda/langchain-ChatGLM/blob/master/img/langchain+chatglm2.png?raw=true)

项目特点
* 依托 ChatGLM 等开源模型实现，可离线部署
* 基于 langchain 实现，可快速实现接入多种数据源
* 在分句、文档读取等方面，针对中文使用场景优化
* 支持pdf、txt、md、docx等文件类型接入，具备命令行demo、webui 和 vue 前端

项目结构
* models: llm的接口类与实现类，针对开源模型提供流式输出支持loader: 文档加载器的实现类。
* textsplitter: 文本切分的实现类。
* chains: 工作链路实现，如 chains/local doc ga 实现了基于本地文档的问答实现
* content:用于存储上传的原始文件。
* vector store: 用于存储向量库文件，即本地知识库本体
* configs: 配置文件存储。


### langchain-ChatGLM QA Bot

[ChatGLM-6B 结合 langchain 实现本地知识库 QA Bot](https://www.heywhale.com/mw/project/643977aa446c45f4592a1e59)


### LangChain-LlamaIndex

[Building Your Own DevSecOps Knowledge Base with OpenAI, LangChain, and LlamaIndex](https://betterprogramming.pub/building-your-own-devsecops-knowledge-base-with-openai-langchain-and-llamaindex-b28cda15abb7)


![stage 1](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*7-3ejsbENu_qMF77PAzHCw.png)

![stage 2](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*eWgA_U9RAFtm7IS0EmDecQ.png)
