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
		- 验证发现HLSL的坐标系计算错误，目前已经将坐标系改成CameraOrigin - AcotrPosiion
		- 改成正确的坐标系后，3D gaussian完全无法显示，全部被过滤掉了。
		- 目前怀疑是viewRange的角度没有被正常传入到HLSL里面
		- 下一步做一个实验：读取view range的时候把读取到的数据写死，看一下能不能得到正常的结果。