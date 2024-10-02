# 目标
- 准备用于测试GaussianCube的数据。
- 最终效果需要让GaussianCube跑起来

# 工作记录
- [DONE] 验证它的输入数据是不是colmap形式的
	- 结果: 不是，它输入的似乎是一种有特殊格式要求的3D Gaussian重建结果
- [DOING] 解决 FORCE_MEM_EFFICIENT_ATTN= 0 @UNET:QKVATTENTION 这个报错
	- 背景: 用GaussianCube官方提供的数据集测试时，遇到了这个报错。
- [DOING] 测试GaussianCube官方提供的数据集
	- 背景: 
		- 虽然这样测试不能算是自己的测试数据，但至少可以先把程序跑通。
		- 后续会再重新构建自己的测试数据。
	- 状态:
		- 初次用官方提供的数据集测试时，遇到了报错: FORCE_MEM_EFFICIENT_ATTN= 0 @UNET:QKVATTENTION