# 目标
- 为了后续方便优化cute::copy执行输出复制的地方，现在追溯一下最后一句cute::copy的数据来源。
- 确认数据来源后，就可以考虑用内联汇编复制或者把复制操作嵌入到计算过程中。

# 工作过程
- [DOING] 确认sO和tOsO这两个Tensor的数据关系。
	- [DONE] 确认sO的shape是128x128
	- [TO-DO] 确认tOsO与sO的位置关系。