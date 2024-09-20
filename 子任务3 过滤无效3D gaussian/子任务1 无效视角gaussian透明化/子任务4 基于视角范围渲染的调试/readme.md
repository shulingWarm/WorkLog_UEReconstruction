# 目标
- 目前3D gaussian的视角范围渲染的初步代码工作已经完成了，但还没有做过测试工作
- 在此任务中会进行基于视角范围渲染效果的测试，如果效果不符合预期会进行相应的debug.

# 工作过程
- 【DONE】 测试UE中的渲染效果
	- 结果: 基于视角范围的渲染完全没有效果，与实现该功能之前的渲染效果完全一致。
- 【DONE】 修复OpenSplat中移位操作溢出的问题。
	- 背景: 代码中的(1<<idBit)需要改成(1LLU<<idBit)，不然计算的时候会溢出
	- Commit: https://github.com/shulingWarm/OpenSplat/commit/b75b177e9d09e3527a43e9c13c08bd86c6162855
- 【DONE】 寻找UE视觉范围渲染没有效果的原因
	- 结论: 
		- OpenSplat中导出的光心坐标是错误的，从计算结果中导致的光心坐标与gaussian的相对位置不符合预期。
		- OpenSplat在约束优化的过程中很可能已经对光心做了变换，应该直接使用OpenSplat中的光心坐标
- 【DOING】 导出OpenSplat里面的光心坐标，需要从它最终的InputData里面导出。
	- 【DONE】 开发函数，用于从OpenSplat的外参信息中导出光心坐标并保存到float\* 中
	- 【DOING】 在重建主流程中调用导出光心坐标的函数
	- 【TO-DO】 将新的dump光心坐标结果保存到ply文件中，观察目前是否符合预期。