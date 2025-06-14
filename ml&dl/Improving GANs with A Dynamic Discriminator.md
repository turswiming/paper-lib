似乎没什么用...，我们没办法动态调整模型的

论文总结：《Improving GANs with A Dynamic Discriminator》
核心思想
该论文提出了一种名为 DynamicD 的动态判别器训练策略，旨在通过 动态调整判别器（Discriminator）的容量（capacity） 来改善生成对抗网络（GAN）的训练效果。其核心观点是：

GAN训练过程中，生成器（Generator）不断演化，导致判别器面临的“真实 vs. 生成”二分类任务随时间变化（time-varying）。

固定容量的判别器无法适应这种动态任务，可能导致 过拟合（数据不足时）或 欠拟合（数据充足时）。

DynamicD通过 在线调整判别器的层宽度（如增加或减少滤波器数量），匹配任务难度的变化，从而提升生成质量。

关键方法
两种容量调整方案：

增加容量（适用于数据充足场景）：逐步扩展判别器的层宽度（如添加新滤波器），以应对生成器能力提升带来的更复杂任务。

减少容量（适用于数据有限场景）：随机丢弃部分滤波器，防止判别器过拟合训练数据。

实现细节：

调整基于线性系数（如扩展系数α或收缩系数β），无需额外计算成本或损失函数。

低层（如浅层卷积）不参与容量减少，以避免训练不稳定。

实验结果
数据充足场景（如FFHQ-140K、LSUN）：增加容量策略显著降低FID（如FFHQ从3.75→3.53）。

数据有限场景（如FFHQ-0.1K）：减少容量策略大幅提升性能（FID从179.21→50.37）。

兼容性：DynamicD可与数据增强（ADA）、正则化（zCR）、预训练等方法结合，进一步优化性能。

泛化性：在2D图像（人脸、场景）和3D感知生成（StyleNeRF）任务中均有效。

创新点
动态容量调整：首次系统研究判别器容量与任务动态变化的匹配问题。

高效性：无需额外计算开销，仅通过调整网络结构实现性能提升。

数据自适应：针对不同数据规模（充足/有限）设计相反策略，解决过拟合与欠拟合问题。

局限性
仅调整层宽度，未探索深度或其他结构变化的影响。

实验基于CNN判别器，未验证Transformer架构的适用性。

缺乏理论分析（如收敛性证明）。

意义与启示
为GAN训练提供新维度：判别器容量的动态调整可作为通用优化手段。

启发后续研究：结合AutoML自动调整容量，或扩展到其他生成模型（如扩散模型）。

[paper](https://arxiv.org/abs/2209.09897)
