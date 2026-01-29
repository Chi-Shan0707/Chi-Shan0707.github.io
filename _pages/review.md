---
permalink: /review/
title: "After Action Review"
author_profile: true
redirect_from:
  - /review.html
---

# Daily Review

Kaggle 比赛
不要使用自己完全不理解的算法，不要让ai写自己看不懂的程序（指santa ）
包的版本很重要，所有参数都需要注意
<br>
（
tweet

| 方面 | 修复前 | 修复后 |
|------|--------|--------|
| 版本支持 | transformers 4.30 | 4.57.6+ |
| 错误处理 | 某些地方缺失 | 全覆盖（8 patterns） |
| 参数文档 | 简单一行注释 | 详细效果说明 + 范围 |
| 数据验证 | 无 | 完整审计日志 |
| 类型标准化 | tuple/ModelOutput 混合 | 强制 ModelOutput |
| 设备检查 | 无 | 动态同步 |
| 序列化支持 | 局部类（无法保存） | 全局类（可序列化） |
| 调试能力 | 有限 | 详细的 [DEBUG] 输出 |
）


管线的概念，数据的格式！ 

了解到整体把握


[spacecraft]中，具体的数据处理方法（缺失值）
pipeline搭建
joblib



调参lora
vibecoding前，先了解好对象：比如模型会话输入格式，看看有没有前人的例子；看看每个库的版本；尤其是数据输入格式（别ai说alpaca就alpaca）




baseball：
处理好工具，理解好所用工具的作用


---
