# 目标
- 由于3D Gaussian模型是在运行时动态生成的，相应地，它的碰撞边界也应该动态生成。
- 所以需要研究怎样在运行时生成由外部数据动态决定的mesh.

# 工作过程
- [DONE] 尝试使用UDynamicMeshComponent生成动态mesh
	- 背景: UDynamicMeshComponent是UE里面自带的一个组件功能，用它或许可以直接动态生成Mesh
	- Status:
		- [DONE] 在蓝图里面构造一个新的DynamicMeshComponent的实例。
			- 结果: 目前暂且认为，DynamicMeshComponent会在蓝图里面自动创建。
		- [DONE] 子任务1 调用DynamicMeshComponent里面的SetDynamicMesh
	- 结果: 用UDynamicMesh生成的Mesh再添加到DynamicMeshComponent之后，可以正常显示出来Mesh.
- [DONE] 给运行时动态生成的Mesh添加碰撞效果。
	- 结果: 使用SetComplexAsSimpleCollision即可。
- [DONE] 拿一个实际的Mesh数据测试导入效果。
	- 结果: 在运行时可以正常导入Mesh，导入的Mesh可以按照实际情况来判断碰撞。

# 结果
- 目前已经可以从外部数据运行时导入Mesh
- 从外部导入的Mesh可以正常实现碰撞效果。