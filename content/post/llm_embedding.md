---
title: LLM Embedding
description: LLM Embedding.
date: 2023-06-07
categories:
  - "LLM"
tags:
  - "LLM"
  - "Embedding"
---

# LLM Embedding


# ChatGLM

+ [ChatGLM获取Embedding向量](https://juejin.cn/post/7229676998749241405)
  
    ```python
    inputs = tokenizer([text], return_tensors="pt").to(device)
    resp = model.transformer(**inputs, output_hidden_states=True)
    y = resp.last_hidden_state
    y_mean = torch.mean(y, dim=0, keepdim=True)
    y_mean = y_mean.cpu().detach().numpy()
    print(y_mean.shape)

    > [1, 4096]
    ```