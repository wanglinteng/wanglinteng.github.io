---
title: Tools
description: Common tools.
date: 2023-06-07
authorbox: false
sidebar: false
pager: false
menu:
  main:
    name: Tools
    weight: 4
---

# Common tools


## shell

+ kill through name
    ```shell
    ps  aux | grep "xxx.py"|grep -v grep|awk '{print $2}'|xargs kill -9
    ```

## python

+ pip tsinghua source 
    ``` shell
    pip install -i https://pypi.tuna.tsinghua.edu.cn/simple numpy
    ```

## git 

+ clone LLM
    ```shell
    git lfs install
    git lfs clone <repo_URL>

    # breakpoint continuation
    git lfs fetch --all --resume <repo_URL>

    # clone without large files
    git lfs clone --skip-smudge <repo_URL>
    ```

## regex

+ https://regex101.com/


## ping

+ https://17ce.com/
+ https://7c.cc/