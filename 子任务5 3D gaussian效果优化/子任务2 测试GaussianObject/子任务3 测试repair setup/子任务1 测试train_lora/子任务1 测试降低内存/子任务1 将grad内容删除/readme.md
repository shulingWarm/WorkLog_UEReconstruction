# 目标
- 现在的目标是想在内存溢出的位置把所有的grad信息手动删除掉，从而就可以观察这些grad内容会占用多少内存了。

# 工作过程
- [DOING] 研究给定一个Tensor，怎样获取这个Tensor所在的计算图涉及到的所有Tensor以及其对应的grad
	- Stage:
		- [DONE] 定位到获取tensor前导tensor对应的C++入口。
		- [DONE] 定位到C++实现中用于获取tensor前导tensor的C++函数。
		- [DONE] 研究用于获取tensor前导tensor的C++实现，观察底层数据结构。
			- 结果: 它的底层数据是一个Edge,每个Edge两端是Node
		- [DONE] 子任务1 用torch的C++接口写一个backward过程，然后获取tensor的前导edge.
		- [DOING] 通过一个tensor的grad_fn以及前导信息，获取它的前导tensor
			- 背景: 虽然已经可以获取tensor的edge，但tensor连接的Node并没有直接转换成Tensor的接口。因此需要额外寻找将Node转换成Tensor的方法，这需要研究Tensor对应的前导函数。