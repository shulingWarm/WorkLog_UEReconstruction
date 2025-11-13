# 目标
- 为了后续方便优化cute::copy执行输出复制的地方，现在追溯一下最后一句cute::copy的数据来源。
- 确认数据来源后，就可以考虑用内联汇编复制或者把复制操作嵌入到计算过程中。

# 工作过程
- [DONE] 确认sO和tOsO这两个Tensor的数据关系。
	- [DONE] 确认sO的shape是128x128
	- [DONE] 根据文档确定((2,3),(1,4))和(6,4)这两种shape的表达方法是等价的。
	- [DONE] 确认tOsO与sO的位置关系。
	- tOsO是sO的一行
- [DONE] 基于TiledCopy写一个示例。
	- 目的: 因为cute::copy调用的是TiledCopy，为了充分理解这个过程，写一个TiledCopy的示例。
	- [DONE] 确认TiledCopy的TV_layout每个参数的意义，用于确定第t个线程的第v个数据的offset.
	- [DONE] 发现TiledCopy里面提供了获取MN_layout的接口。
	- [DONE] 通过改变原始的TiledCopy模板类，观察MN_layout和TV_layout的变化。
		- 确定了MN和TV两个layout与TiledCopy里面参数的计算关系。
	- [DONE] 测试用TV_layout只指定部分Tensor执行复制，结果执行cute::copy时仍然复制了完整的tensor.
	- [DONE] TiledCopy声明里面最后一个二元元组表示的可能是对tensor分出来的切片数量，传入不同的tensor会分出来不同的切片大小，需要进一步确认。
	- [DONE] 测试用TiledCopy执行单独线程切片的复制。
		- 复制128\*128的Tensor，确认了每个模板参数对于复制效果的影响。
- [GIVE-UP] 画Flash-Attention在Tensor级别的pipeline.
	- [DONE] 解析Query和Key的shape变换。
	- [DONE] 理解shared_memory排列时引入的Swizzle机制。
		- 通过行列标号的异或操作获取新的偏移量从而把bank id散列开。
	- [DONE] 分析了tQgQ和原始的指针位置的对应关系。
	- [DONE] 实现了检测bit交换映射的函数用于分析sQ和原始指针偏移量的关系。
	- [DONE] 分析sQ和原始指针偏移量的对应关系。
	- [DONE] 分析带swizzle的逻辑id和指针偏移量的对应关系。
		- 沿着行方向分成多个块，在块在行号和列号异或得到新的行号。
	- [DONE] 分析tQsQ和原始指针的位置关系。
	- [DOING] 用类似于Python的伪代码表示Q\*K^T过程中的数据流动。
	- [TO-DO] 画Kernel里面Q\*K^T过程的数据流图。

# 放弃原因
- 画flash-attention的数据流动与优化flash-attention性能的基本动机并不一致。