# 目标
- 进行带先验位姿的重建，获得高质量的重建结果后，用来做后续效果，碰撞检测、三维物体分割等。

# 工作记录
- [SUSPEND] 寻找colmap里面指定先验pose的接口
	- 放弃原因: 查找后发现colmap并没有直接支持输入gps prior的接口，还需要借助外部工具
- [DOING] 测试直接用colmap运行south-building数据集
	- 背景: 
		- 由于south-building本来就是用于测试colmap的数据集，它里面自带database数据
		- 对于自带database的数据，它里面有可能本身就有相机位姿，因此可以直接用这个东西重建一下看看效果。
- [DOING] 子任务1 在OpenMVG里面测试prior位姿的重建效果。
	- 目标: 直接拿带位姿信息的数据集去测试重建效果，稀疏重建后调用OpenSplat来做3D Gaussian渲染。