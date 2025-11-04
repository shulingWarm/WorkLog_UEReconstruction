# 目标
- 为了后续方便优化cute::copy执行输出复制的地方，现在追溯一下最后一句cute::copy的数据来源。
- 确认数据来源后，就可以考虑用内联汇编复制或者把复制操作嵌入到计算过程中。

# 工作过程
- [DONE] 确认sO和tOsO这两个Tensor的数据关系。
	- [DONE] 确认sO的shape是128x128
	- [DONE] 根据文档确定((2,3),(1,4))和(6,4)这两种shape的表达方法是等价的。
	- [DONE] 确认tOsO与sO的位置关系。
	- tOsO是sO的一行
- [DOING] 基于TiledCopy写一个示例。
	- 目的: 因为cute::copy调用的是TiledCopy，为了充分理解这个过程，写一个TiledCopy的示例。
	- [DONE] 确认TiledCopy的TV_layout每个参数的意义，用于确定第t个线程的第v个数据的offset.
	- [DONE] 发现TiledCopy里面提供了获取MN_layout的接口。
	- [TO-DO] 通过改变原始的TiledCopy模板类，观察MN_layout和TV_layout的变化。
	- [TO-DO] 开发一个Tensor复制Kernel用于验证对于TiledCopy的理解。