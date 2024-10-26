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
- [DOING] 给运行时动态生成的Mesh添加碰撞效果。
- [TO-DO] 根据3D Gaussian的实际情况生成动态Mesh并且添加到Actor里面。