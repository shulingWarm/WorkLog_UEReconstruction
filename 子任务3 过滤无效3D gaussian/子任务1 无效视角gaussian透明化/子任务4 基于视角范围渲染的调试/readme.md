# 目标
- 目前3D gaussian的视角范围渲染的初步代码工作已经完成了，但还没有做过测试工作
- 在此任务中会进行基于视角范围渲染效果的测试，如果效果不符合预期会进行相应的debug.

# 工作过程
- 【DONE】 测试UE中的渲染效果
	- 结果: 基于视角范围的渲染完全没有效果，与实现该功能之前的渲染效果完全一致。
- 【DONE】 修复OpenSplat中移位操作溢出的问题。
	- 背景: 代码中的(1<<idBit)需要改成(1LLU<<idBit)，不然计算的时候会溢出
	- Commit: https://github.com/shulingWarm/OpenSplat/commit/b75b177e9d09e3527a43e9c13c08bd86c6162855
- 【DOING】 寻找UE视觉范围渲染没有效果的原因
	- 状态:
		- 最关键的原因之一是SampleTexture的时候没有传入正确的UV
			- 这导致每个gaussian的角度范围被传到HLSL里面的都是零
		- 传入正确的texture采样后，每个gaussian都拥有了各自的合法观察范围
		- 整体的渲染效果仍然不满足预期，gaussian拖尾虽然从背面看不到了，但还是可以从侧面看到