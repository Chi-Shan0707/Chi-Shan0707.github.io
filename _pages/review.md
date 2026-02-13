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

8. **自回归崩溃与数值爆炸 (The NaN Disaster)**

* **错误现象**：Submission contains null values。虽然模型训练正常，但在生成提交文件时，前 10 步数据正常，第 11 步开始突然变成 NaN 或 Infinity，导致 5000 万行数据中有 4800 万行无效。

* **核心概念 (新学到的知识)**：
  - Ground Truth (地面真值/标准答案)：真实世界观测到的数据（如真实水位）。
  - Teacher Forcing (教师强制)：一种训练策略。就像"爸爸扶车把"，在训练时不管模型上一步预测得偏离多远，下一步输入时强行把它纠正回 Ground Truth，让模型基于正确的数据继续算。

* **根本原因**：
  - 过度依赖 (Exposure Bias)：模型在训练时享受了 Teacher Forcing 的"呵护"，没学会在犯错后自我调整。
  - 推理崩溃：在推理（Inference）阶段，没有 Ground Truth 可用，模型必须吃自己上一步生成的预测值。一旦产生一点微小的误差，这个误差会在几十个时间步内指数级放大（1.01 的 100 次方），最终导致数值溢出（梯度爆炸）。
  - 数据未归一化：输入数据的绝对值差异过大（0 到 500），加速了这种爆炸。

* **解决方案**：
  - 急救 (Inference time)：在推理循环中加入数值截断 (Clamping)。使用 torch.clamp(val, 0, 200) 和 nan_to_num，给模型装上强制护栏，无论它算出的数字多离谱，都强行压回合理区间。
  - 长效 (Training time)：需要在训练代码中引入数据标准化 (Z-Score)，并逐步减少 Teacher Forcing 的比例。

* **经验教训**：温室里的花朵经不起风雨。训练 loss 低不代表推理效果好。如果你的模型是自回归的（Autoregressive），一定要警惕"训练推理不一致"的问题，并在推理端做好异常值防御。

# 20260207

1. 数学要静下心来学<br>
2. 算法奇妙，学习了一些mc++好用的东西
3. 经验与教训 (Lessons Learned)
  > C++ 性能哲学：<br>能 emplace 就不 push：emplace_back 省去了一次临时对象的构造和析构，在大循环中收益显著。<br>
 定长用 std::array：对于如字符集大小 (26 或 256) 这种固定维度的数组，std::array 比 std::vector 更轻量，且比 C 风格数组更安全（支持迭代器和边界检查）。<br>
4. UrbanFlood 问题很多啊，对于数据要预处理，太大总归是不好的；对于代码理解还不够深刻，对于到底在预测什么，依赖什么都不是很清楚,必须要搞明白，要控制住<br>
5. c++这啥的，路径不要有乱七八糟字符<br>

# 20260208
1. 数据类型
2. json，jsonl, split
3. LoRA原理
4. MLP
5. 
```markdown
这是一个非常棒的复盘请求。今天的调试过程充满了“硬核”的工程挑战，你基本上踩遍了**自定义算法 + 4-bit 量化 + RL 训练**这一复杂组合下的所有经典坑位。

以下是对今日错误的深度复盘，我将其分为**框架机制**、**算法实现**、**训练动力学**三个层面，帮你理清脉络。

---

### 第一阶段：框架与环境的“博弈” (The Framework Battles)

这部分错误主要源于 Hugging Face `Trainer` 与你“手动魔改”模型之间的冲突。

#### 1. 4-bit 模型的“非法训练”误判

* **现象**：报错 `ValueError: You cannot perform fine-tuning on purely quantized models...`。
* **原因**：
* **背景**：你加载了 4-bit 模型 (`load_in_4bit=True`)。
* **机制**：HF Trainer 为了防止用户错误地尝试更新冻结的量化权重，会检查 `model.is_loaded_in_4bit`。如果为真，且模型不是官方的 `PeftModel`（即没有 `peft_config`），它就判定为非法操作并报错。
* **冲突点**：你的 `TinyLoRA` 是手写的，不是通过 `get_peft_model` 生成的，所以 Trainer 认为你在裸跑量化模型。


* **解决方案（Hack）**：
* 手动设置 `model._hf_peft_config_loaded = True`。这是一张“伪造的通行证”，骗过 Trainer 的安检，让它以为这是一个标准的 PEFT 模型。



#### 2. “隐形”的量化层

* **现象**：`apply_tiny_lora` 运行了，但替换数量为 `0`。
* **原因**：
* **代码逻辑**：你最初写的是 `if isinstance(child, nn.Linear)`。
* **事实**：量化后的模型，线性层已经变成了 `bitsandbytes.nn.Linear4bit`。它们虽然功能像 Linear，但在 Python 类型系统中不是 `nn.Linear` 的子类（或者判定失效）。


* **教训**：在处理量化模型时，永远不要假设层是标准的 `nn.Linear`。必须显式检查 `bnb.nn.Linear4bit`。

---

### 第二阶段：算法实现的“细节魔鬼” (The Implementation Details)

这部分错误主要发生在手写 TinyLoRA 核心逻辑时。

#### 3. `einsum` 的维度迷宫

* **现象**：`RuntimeError: einsum(): output subscript r appears more than once in the output`。
* **代码**：`torch.einsum('u, urr -> rr', v, self.P)`。
* **原因**：
* 你希望输出一个  的矩阵。
* 但在 Einstein Summation 约定中，输出下标 `rr` 表示取对角线（或者在此语境下是非法/歧义的），不允许在输出端重复使用下标来代表两个不同的维度。


* **修正**：改为 `'u, uij -> ij'`。使用不同的字母（i, j）明确表示输出矩阵的行和列是独立的维度。

#### 4. “薛定谔”的可训练参数 (Global V)

* **现象**：`trainable params: 0` 或者参数被意外冻结。
* **原因**：
* **引用陷阱**：`global_v` 被共享给了 200 多个层。当你遍历 `model.named_parameters()` 并根据名字冻结参数时，同一个对象（`global_v`）会被遍历多次。
* **覆盖效应**：第一次遇到它（作为 `tiny_lora_params`）时设为了 `True`，但第二次遇到它（作为某层的 `v`）时，因为名字不匹配逻辑，又被设回了 `False`。


* **修正**：
1. 建立 `TinyLoRAGlobalParams` 容器，给它一个正式的“户口”。
2. 不再依赖名字匹配，而是先 `model.requires_grad_(False)` 全冻，再通过对象引用 `global_params.global_v.requires_grad = True` 精准解冻。



---

### 第三阶段：RL 训练的“冷启动” (The Cold Start)

这部分不是代码错误，而是强化学习的特性导致的现象。

#### 5. 0 分的静默 (Zero Reward & Loss)

* **现象**：`loss: 0.0`, `reward: 0.0`, `grad_norm: 0.0`。
* **恐慌点**：你以为代码坏了，或者模型输出了全错的东西。
* **真相**：
* 这是 GRPO 的正常机制。GRPO 依赖**组内优势 (Group Advantage)**。
* 如果是 **[0, 0, 0, 0]**（全错）：没有优势，没有梯度，模型不更新。
* 如果是 **[0, 1, 0, 0]**（有一个对）：产生优势，产生梯度，开始更新。


* **突破**：在 Step 1，模型终于蒙对了一次，Reward 变成了 `0.25`，Loss 和梯度瞬间出现，训练正式开始。

#### 6. 10347 Tokens 的误解

* **现象**：看到日志里 `num_tokens: 10347`，以为显存炸了或者窗口溢出。
* **真相**：这是 **Total Tokens**（Batch Size × Group Size × Sequence Length）。对于 `accumulation=8`，`group=4` 的设置，这个数字非常正常（平均每条 300 多 token）。

---

### 总结：你的“避坑指南”

如果下次再做类似的任务，这份清单价值千金：

1. **欺骗 Trainer**：只要是非官方 PEFT 的量化微调，起手就加 `_hf_peft_config_loaded = True`。
2. **类型检查**：替换层时，必查 `bnb.nn.Linear4bit`。
3. **参数冻结**：涉及参数共享（Shared Parameters）时，**绝对不要**在循环里用 `name` 判定 `requires_grad`。**先全冻，再点对点解冻对象**。
4. **Einsum**：输出维度的下标字母永远不要重复。
5. **RL 心态**：看到 `Reward=0` 不要慌，只要 `Length` 在变短，说明模型在挣扎；只要出现一次非 0 分数，训练就是活的。

今天你不仅跑通了代码，还深入理解了 PyTorch 计算图、Trainer 机制和 RL 动力学，这是一次质量极高的 Debug！
```


# 20260211
（9 10  11）

1. 不要想太远的数学，从简单的，眼下的来，先去搞懂下学期的数学模型所需要的
2. 今日完成仓库的迁移就明显迅速了很多。 首先要搞明白文件格式。 训练可以再考虑如何提速。 最近思考了服务器的问题， 门道还是多。
3. 今日dyh问了java的问题， 嗯， 类型，实例，方法这些概念是相通的，可以多去思考
4. 教表妹python， 乐， 基础语法我也不会
5. 核电， 两家。 利润高？。 单日1000万。 但是很多时候是 不被批准发电： 电太多了
6. 在线学习：考虑财富增量； 琴声不等式，凸函数， 伯努利不等式， 是全知的expert problems
7. 静下心来 


# 20260212

## 之前为什么修不好

| 次数 | 我做了什么 | 为什么无效 |
|------|-----------|-----------|
| 第1次 | 在 forward 中对 delta 做 `.to(W_base.dtype)` | **只转了 delta，没转 x**。`x` 是 bfloat16（模型以 `torch_dtype=bfloat16` 加载），`W_base` 从 `dequantize_4bit` 返回 float32，`F.linear(x, W_base)` 直接炸 |
| 第2次 | 在 `model.generate()` 前对 inputs 做 `.to(float32)` | **完全无效**。tokenizer 输出只有 `input_ids`（int64）和 `attention_mask`（int64），没有 float 张量可转。真正引发错误的是模型内部激活值的 dtype |

## 这次的根本修复

问题核心：`x`（激活值，bfloat16）和 `W_base`（反量化权重，float32）dtype 不一致。

修复策略：在 `TinyLoRALinear.forward()` 中，以 `W_base` 的 dtype 为唯一基准（`compute_dtype`），**所有参与 matmul 的张量（x、U、S、Vh、P、global_v、delta）全部显式转为同一 dtype**，最后再转回原始 dtype 输出。


# 20260213

1. 今日下午搞了agent，发现自己对于agent相关知识，如ollama，langchain不是很熟悉，之后可以更加多了解一点
2. agent对于我这样的人布置也尚有难度，manus有必要？
3. qwen那么大的模型也会写有大bug的程序（）
4. 和魏教授细聊，继续保持兴趣，但是要加强数理基础，然后多找他聊天，然后稍微精简一下注意力
5. 学习了在线算法，但晚上心有点燥动，关于电引入的思想能掌握，但是计算还没细算
6. 该多陪陪外公，我有罪。
7. 看数分吧

---
