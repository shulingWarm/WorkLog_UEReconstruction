# 目标
- 现在需要手动创建用于碰撞检测的mesh，所以需要想办法在运行时创建mesh.
- 创建mesh关键的类是DynamicMeshComponenet，而它里面的一个新建Mesh的函数是SetDynamicMesh
- 这个任务就是想办法调用一下DynamicMeshComponet里面的SetDynamicMesh

# 工作过程
- [DONE] 在C++代码里面创建FDynamicMesh3
	- 背景: 由于SetDynamicMesh的输入是FDynamicMesh3，所以需要先想办法创建一个FDynamicMesh的实例。
	- 结果: 这是可以直接在代码里面添加的。
- [DOING] 生成一个UDynamicMesh然后往里面添加FDynamicMesh3
	- 背景: FDynamicMesh3是真正承载数据的实体，而UDynamicMesh是Object子类，是可以被蓝图操作的类。