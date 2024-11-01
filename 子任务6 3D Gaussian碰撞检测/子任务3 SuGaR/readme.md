# 目标
- 测试SuGaR生成3D Gaussian对应的Mesh.
- 子任务结束的标志是把SuGaR里面的3D Gaussian转Mesh的功能解耦出来，并且在Linux上运行测试通过。

# 工作记录
- [DONE] 寻找SuGaR里面用于将3D Gaussian转换成Mesh的函数入口。 
	- 结果: 这个入口位于SuGaR/sugar_extractors/coarse_mesh.py
- [DONE] Import这个coarse_mesh里面的函数，确实相关的库齐备从而可以正常完成import阶段
	- 结果: import过程不再报错，用到的python库都安装好了。
- [DOING] 寻找Mesh输出对应的直接前导输入。
	- 背景: 按说下一步该准备输入数据了，但这个Extract_mesh里面还包含一些对mesh的优化，可能并非所有的输入都需要给定。
	- Stage:
		- [DONE] SuGar这个module里面有一个points_属性，它是最终输出模型的主要前导变量。
		- [DONE] 确认points_对应的前导变量。
	- 结果:
		最终的Mesh来源就是Gaussian Splatting生成的标准结果，一个ply文件和一个包含图片的文件夹，另外有一个cameras.json。