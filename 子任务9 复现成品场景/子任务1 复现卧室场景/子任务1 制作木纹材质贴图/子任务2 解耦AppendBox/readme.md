# 目标
- 解耦 AGeneratedDynamicMeshActor 类中 AppendBox的方法
- 暴露出类中修改Mesh的地方，方便以后做扩展。

# 工作过程
- [DONE] 由于 FGeometryScriptPrimitiveOptions 无法正常构造，直接去除代码中用到 FGeometryScriptPrimitiveOptions 的地方。
- [DONE] 将最外层的数据结构解耦之后，动态生成Mesh的代码可以正常工作。
- [DONE] 打印原始代码每次调用SetUV和SetNormal时指定的数据，观察规律。
- [DONE] 观察打印SetUV的规律发现由于Frame.PointAt的调用，8个点中相邻的两个点坐标是相同的。
- [DONE] 画图分析代码中UV和Normal设置的规律发现UV描述的是每个Mesh面的绘制顺序，它的id是递增的，并不是和vertex对应。
- [DOING] 将解耦出来的生成Mesh的代码改成自己之前的横截面逻辑。
	- 状态:
		- [DOING] 闭合横截面时，为每个点分配UV的id.