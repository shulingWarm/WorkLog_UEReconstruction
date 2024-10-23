# 目标
- 由于3D Gaussian模型是在运行时动态生成的，相应地，它的碰撞边界也应该动态生成。
- 所以需要研究怎样在运行时生成由外部数据动态决定的mesh.

# 工作过程
- [DOING] 尝试使用UDynamicMeshComponent生成动态mesh
	- 背景: UDynamicMeshComponent是UE里面自带的一个组件功能，用它或许可以直接动态生成Mesh
	- Status:
		- [DOING] 在蓝图里面构造一个新的DynamicMeshComponent的实例。
		- [TO-DO] 观察UDynamicMeshComponent提供的蓝图接口，随便调用其中一个函数观察效果。