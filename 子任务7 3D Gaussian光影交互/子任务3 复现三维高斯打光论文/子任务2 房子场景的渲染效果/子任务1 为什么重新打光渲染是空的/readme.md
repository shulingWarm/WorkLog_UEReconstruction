# 目标
- 目前发现即使选用了正确的渲染视角，得到的重新打光的效果仍然是空的。
- 此任务结束的标志是让渲染结果里面有内容。

# 工作流程
- [DONE] 找到重新打光效果里面对输出帧做渲染的代码位置。
	- 结果: 输出帧的位置在gui.py里面，调用render_fn的时候会传入渲染视角。
- [DONE] 找到render_fn里面真正执行点投影的过程。
- [DONE] 在gui.py里面dump出了投影矩阵。
- [DONE] 在重新打光的程序里面打印投影矩阵。
- [DONE] 发现在Relight程序里面使用的是w2c,而训练过程中的渲染用的是w2c.
	- 把正确的w2c传入Relight程序里面后仍然不能得到有效的渲染结果。
- [DONE] 在核函数里面打印渲染图片的变量，寻找out_color为空的原因
	- 背景: 目前发现render过程在CUDA里面实现的，需要从核函数里面寻找out_color为空的原因。
	- 状态:
		- [DONE] 打印信息发现进入kernel之前的num_rendered是零，导致根本没有有效输入。
		- [DONE] 寻找num_rendered是零的原因。
			- num_rendered的前导是由tile_touched是零决定的。
		- [DONE] 研究preprocessCUDA的内容寻找tile_touched是零的原因。
			- 在preprocessCUDA里面，in_frustum这个判断位置就直接返回了。
		- [DONE] 分析为什么preprocess过程中所有的点都不在视锥坐标系里面。
			- 在preprocess里面所有的所有投影点都不在成像平面前面。
		- [DONE] 目前发现投影矩阵的排列是[R^T;T^T]，并不是横向排列。
		- [DONE] 研究为什么preprocess的核函数中，为什么所有投影点都投影在了相机后面。
			- 结果: 把输入视角的旋转矩阵手动取了负数之后就能投影出正常的结果了。
	- 结果: 把输入视角的旋转矩阵手动取一下负数，就可以得到有效的渲染图片。

# 结果
- 目前已经可以做到输出图片里面有内容，但并没有重新打光的效果，墙的颜色仍然与原图类似。