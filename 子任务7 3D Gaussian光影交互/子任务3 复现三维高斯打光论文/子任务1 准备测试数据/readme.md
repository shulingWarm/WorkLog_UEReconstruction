# 目标
- 现在需要测试RelightableGaussian的效果，因此需要准备一个用于测试的colmap场景。

# 工作过程
- [DONE] 研究RelightableGaussian加载数据的代码，发现允许读取colmap格式的工程。
- [DONE] 测试用手机拍的场景是否满足相机模型要求。
	- 背景: 目前使用的房子的场景使用的相机模型是SIMPLE_RADIAN，RelightableGaussian无法读取。
	- 状态:
		- [DONE] 重新对手机拍摄的场景用colmap做重建。
		- [DONE] 测试用手机拍摄的colmap工程能不能被加载到RelightbaleGaussian里面。
	- 结果: 用手机重建的时候指定相机模型为PINHOLE,在Relightable里面就可以正常加载了。
- [DONE] 用colmap工程完成后续的scene信息加载。
	- [DONE] 发现colmap_project里面找不到train_cameras是发生发生在调用random.shuffle之后
	- [DONE] 发现在调用cameraList_from_camInfos这个函数之前，train_cameras一直都是可以访问的。
	- [DONE] 测试自己能不能自行遍历这个list，结果发现是可以自行遍历train_cameras的
	- [DONE] 解决colmap_project里面没有train_cameras属性的问题。
		- 解决方法: 报错是因为self里面没有找到train_cameras这个属性，把self属性初始化一下就可以。
- [DOING] 准备优化器参数
	- 背景: 为了初始化三维高斯的优化状态，需要使用优化器参数。