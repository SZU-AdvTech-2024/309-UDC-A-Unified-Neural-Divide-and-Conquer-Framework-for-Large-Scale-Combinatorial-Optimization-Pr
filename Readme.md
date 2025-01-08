# Readme


### 设置和依赖项

每个 CO 问题的代码默认保留训练预训练模型时的参数和用于测试的参数。请参阅我们的论文以了解训练设置和测试设置。

大部分参数已在每个 CO 问题的 test/train.py 文件中指明。对于征服阶段数 r，请在每个问题的 Tester.py 中的验证函数下修改此设置。

我们环境中的显著依赖项：

* python = 3.9

* torch-geometric = 2.4.0

* torch = 1.12.1

* networkx = 2.6.3

* numpy = 1.22.4

### 数据和模型

UDC 使用强化学习进行训练，并在 UDC/ATSProblemDef.py 和 UDC/OPProblemDef.py 等十个文件中演示了随机数据生成方法。

请从 Google Drive https://drive.google.com/file/d/1lVWBPvxhHDd-ZLJNCorGJugi_Smrx8uh/view?usp=sharing 下载测试集和预训练模型。

### 复现

下载预训练模型和测试集以复现文章中报告的结果。

**由于代码在 GNN 计算中使用 $O(N^2)$ 空间复杂度实现来并行运行。对于 7000 节点以上的测试问题，您需要考虑将距离矩阵、热图（甚至一些耗费空间的 GNN 操作，通常不需要）放在 CPU 上。**

随机性：如果在一次运行中运行两个测试集或使用不同的批处理大小，则会出现随机性。

**对于随机生成的实例，报告的结果来自单个 NVIDIA RTX 3090 GPU 上的最大批处理大小（例如，CVRP500 的批处理大小为 6，$\alpha=50$）。我们在一次运行中也只测试一个测试集。**
