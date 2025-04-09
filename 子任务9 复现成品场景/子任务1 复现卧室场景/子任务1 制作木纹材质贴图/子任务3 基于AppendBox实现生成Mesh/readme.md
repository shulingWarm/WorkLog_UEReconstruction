# 目标
- 基于AppendBox里面解耦出来的代码，实现基于横截面的Mesh生成效果。

# 工作过程
- [DONE] 实现横截面的闭合效果。
- [DONE] 实现横截面的连接效果。
- [DONE] 测试基于横截面的Mesh生成以及贴图效果。
	- 结果: 测试发现新的方法生成的Mesh仍然不能正常显示贴图。
- [DONE] 研究AppendBox中的UV和Normal。
	- 背景: 发现AppendBox的逻辑中，不只有三角形有UV和normal，每个节点也有UV和Normal。
	- 结果: 每个节点的UV和normal需要描述它们所属的节点id，以及它们在进行贴图时的平面坐标。
- [DONE] 基于新的UV和Normal的理解，重新实现横截面生成Mesh的逻辑。
	- 状态:
		- [DONE] 实现闭合横截面时的UV和Normal赋值逻辑。
		- [DONE] 实现链接横截面时，每个侧面的法向量的计算。
		- [DONE] 实现链接横截面的逻辑。
	- 结果: 完成了新UV和Normal赋值的实现，编译通过。
- [TO-DO] 解决运行AppendBox时的空指针报错。