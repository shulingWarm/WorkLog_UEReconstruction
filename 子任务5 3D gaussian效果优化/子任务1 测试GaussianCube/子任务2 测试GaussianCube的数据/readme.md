# 目标
- 准备用于测试GaussianCube的数据。
- 最终效果需要让GaussianCube跑起来

# 工作记录
- [DONE] 验证它的输入数据是不是colmap形式的
	- 结果: 不是，它输入的似乎是一种有特殊格式要求的3D Gaussian重建结果
- [DONE] 解决 FORCE_MEM_EFFICIENT_ATTN= 0 @UNET:QKVATTENTION 这个报错
	- 背景: 用GaussianCube官方提供的数据集测试时，遇到了这个报错。
	- 结果: 这并不是报错，这是一个正常的读取环境变量的过程。
- [GIVE-UP] 测试GaussianCube官方提供的数据集
	- 背景: 
		- 虽然这样测试不能算是自己的测试数据，但至少可以先把程序跑通。
		- 后续会再重新构建自己的测试数据。
	- 放弃原因: GaussianCube的github readmd存在严重的误导性，还是需要靠自己的判断来确定这个程序应该怎样使用。
- [GIVE-UP] 准备constrained fitting的测试数据
	- 背景: 
		- 根据GaussianCube的论文，它一共分为4个部分，其中第一部分是Constrained fitting
		- Constrained fitting是将原本的3D gaussian整理成固定Gaussian个数的3D Gaussian.
	- 放弃原因: GaussianCube的论文与github中的代码难以对应，不宜在这方面继续浪费时间。