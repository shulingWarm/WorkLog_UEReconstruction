# 目标
- 现在的目标是想在内存溢出的位置把所有的grad信息手动删除掉，从而就可以观察这些grad内容会占用多少内存了。

# 工作过程
- [DOING] 研究给定一个Tensor，怎样获取这个Tensor所在的计算图涉及到的所有Tensor以及其对应的grad
	- Stage:
		- [DONE] 定位到获取tensor前导tensor对应的C++入口。
		- [DONE] 定位到C++实现中用于获取tensor前导tensor的C++函数。
		- [DOING] 研究用于获取tensor前导tensor的C++实现，观察底层数据结构。