---
permalink: /review/
title: "After Action Review"
author_profile: true
redirect_from:
  - /review.html
---

# Daily Review

## Kaggle 
1. 不要使用自己完全不理解的算法，不要让ai写自己看不懂的程序（指santa ）
2. 包的版本很重要，所有参数都需要注意（指所有pytorch之类的）
3. 管线的概念
4. 数据的格式！ 了解到整体把握, e.g.[spacecraft]中，具体的数据处理方法（缺失值）,pipeline搭建,joblib
5. 善用github搜索前人经验（如[monet]，找到别人的cyclegan with pytorch,自己再去理解）


## lora
1. 使用别的模型/vibecoding前，先了解好对象，做好背调：比如模型会话输入格式(别ai说alpaca就alpaca）【当时花了很多时间在测试是否能读取json格式，以怎样形式读取，ai又能否拆解，实际上不要问大模型，他们出幻觉就完蛋了，自己去查可靠的资料和前人的轮子】
2. 看看有没有前人的例子（qwen模型有很多开源教程）；
3. 看看每个库的版本


## HacKawayi
1. 风格的统一
2. workspace, codespace
3. 版本dockerfile很重要
4. localstorage存登录信息


## baseball：
1. 处理好工具，理解好所用工具的作用
2. 保持耐心
3. 现实数据往往很差劲

## 概率论
1. 专心阅读
2. 合理使用ai，但不要完全依赖，完全信任

## 论文
1. 参数
2. 专有名词


## 20260204
1. 去了解yolo，语义分割
2. 我做一个baseball模型最后需要能解出一点东西才能有用处（即因果推断）
3. 为达到这个可以看点文章

4. 大的创新只有：transofor，resenet，别的人，小的创新耳耳？
5. 我能做的创新： 别人没想到能把这套方法用在这个问题上，我用了；我迁移的过程中发现有些不好的地方，我因地制宜修改了；我组合其他模型一起使用；看看自己读过的论文能不能用上
6. 读论文：知道这个论文做了什么，有个怎样的结论，遇到了怎样的问题，怎么解决的
7. 怎样的优点，怎样的缺点？
8. 后人怎么引用这篇论文的，我能不能去复现？我能不能去使用/改进

## 20260205
1. 科目一考过，证明精力要适当分配，本就不用太过担心，花太多时间；同时心态还是有点急躁（考试时第一遍83分有很多傻子错
2. 不要太纠结，time is money，现在火车票已经没了。这次能转莆田，下次不一定了
3. 又重新搞了一下概率论，还是要有耐心和专注度
4. 回顾了一下在线算法，关于log的放缩其实还没有那么【下意识】，关于英语文档也许再熟悉一下；
5. 把论文最后收尾读完了，明天有空再最后看一看那些提到的论文，局限，
6. 随机算法要去学

## 20260206
1. 环境配置陷阱：GeoPandas 的依赖地狱

* **错误现象**：尝试安装 `geopandas` 时，Conda 的 `solving environment` 无限卡顿，无法完成环境配置。
* **解决方案**：果断放弃 `geopandas` 和 GIS 库。转而利用 `edge_index`（图拓扑）和 NumPy/Pandas 纯数学计算来提取特征（如通过出入度判断节点性质）。
* **经验教训**：**如无必要，勿增实体。** 在深度学习任务中，如果能用简单的矩阵运算或图结构代替复杂的 GIS 操作，优先选择前者，以保证环境的轻量化和可复现性。

2. PyG 数据集持久化与安全加载 (PyTorch 2.6+ 特性)

* **错误现象**：
  -  `FileNotFoundError`：Dataset 初始化报错，因为 `process()` 方法只处理了数据却忘记调用 `torch.save()`。
  -  `pickle.UnpicklingError`：修复保存后，加载时报错，因为 PyTorch 2.6+ 默认开启 `weights_only=True`，拒绝加载自定义的 HeteroData 对象。


* **解决方案**：
  -  在 `process()` 末尾显式添加 `torch.save((self.data, self.slices), ...)`。
  -  在 `torch.load()` 中显式设置 `weights_only=False`。


* **经验教训**：**闭环思维**。写数据处理管线时，时刻检查“输入-处理-输出-加载”的完整性；同时关注深度学习框架的新版本 Breaking Changes（如安全策略变更）。

3. 异构图卷积的自环问题 (Topology Constraint)

* **错误现象**：`ValueError: add_self_loops attribute set to True...`。GATv2Conv 试图在异构边（如 `manhole -> cell`）上添加自环。
* **解决方案**：在 `model.py` 构建卷积层时，针对跨类型的边（Bipartite edges）显式设置 `add_self_loops=False`。
* **经验教训**：**物理意义优先**。在图神经网络中，自环意味着“自己指向自己”。对于不同类型的节点交互（如下水道流向地面），物理上不存在“自己流向自己”的概念，代码必须尊重物理拓扑。

4. 循环神经网络 (GRU) 的维度匹配

* **错误现象**：`RuntimeError: mat1 and mat2 shapes cannot be multiplied`。
* **解决方案**：意识到 GRU 的门控机制是将“当前输入 ”和“上一时刻隐状态 ”拼接作为输入。因此，卷积层的输入维度应该是 `2 * hidden_dim` 而不是 `hidden_dim`。
* **经验教训**：**张量演算需谨慎**。在实现自定义的 RNN/GRU 单元时，必须手推一遍每一层的输入输出维度，特别是涉及 `torch.cat` 操作的地方。

5. 自回归训练的梯度流截断 (Autoregressive Detach)

* **错误现象**：`RuntimeError: Trying to backward through the graph a second time`。
* **解决方案**：在 `train.py` 的时间步循环中，将传递给下一时刻的隐状态 `h_dict` 进行 `.detach()` 操作。
* **经验教训**：**理解计算图**。在处理长序列（BPTT）时，必须手动切断历史梯度的传播，否则计算图会无限累积，既耗尽显存又导致逻辑错误。

6. 数据集划分与路径硬编码 (Train vs Test)

* **错误现象**：`FileNotFoundError`。在推理阶段，代码试图在 `.../train/` 目录下寻找测试集文件（如 `event_17`），导致失败。
* **解决方案**：重构 `UrbanFloodDataset`，增加 `split` 参数（'train'/'test'），使其能根据模式动态生成 `raw_dir` 路径。
* **经验教训**：**代码模块化与参数化**。永远不要在 Dataset 类中硬编码路径。始终假设你的模型需要运行在不同的数据子集上。

7. 大规模推理的内存溢出 (OOM / Killed)

* **错误现象**：`Killed`。在推理包含 29 个 Event 的测试集时，尝试将所有结果保存在一个巨大的 List 中，导致内存撑爆。
* **解决方案**：实施**流式写入 (Stream Writing)**。每跑完一个 Event，立即将结果写入 CSV 并清空内存 (`gc.collect`)，不再在 RAM 中囤积数据。
* **经验教训**：**工程思维**。在处理大数据（尤其是时空序列）时，必须假设内存是有限的。批处理和流式处理是解决大规模数据推理的唯一正解。
---
