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
- [DOING] 在核函数里面打印渲染图片的变量，寻找out_color为空的原因
	- 背景: 目前发现render过程在CUDA里面实现的，需要从核函数里面寻找out_color为空的原因。
	- 状态:
		- [DONE] 打印信息发现进入kernel之前的num_rendered是零，导致根本没有有效输入。
		- [DONE] 寻找num_rendered是零的原因。
			- num_rendered的前导是由tile_touched是零决定的。
		- [DOING] 研究preprocessCUDA的内容寻找tile_touched是零的原因。