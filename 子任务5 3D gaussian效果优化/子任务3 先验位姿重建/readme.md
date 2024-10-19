# 目标
- 进行带先验位姿的重建，获得高质量的重建结果后，用来做后续效果，碰撞检测、三维物体分割等。

# 工作记录
- [SUSPEND] 寻找colmap里面指定先验pose的接口
	- 放弃原因: 查找后发现colmap并没有直接支持输入gps prior的接口，还需要借助外部工具
- [SUSPEND] 子任务1 在OpenMVG里面测试prior位姿的重建效果。
	- 目标: 直接拿带位姿信息的数据集去测试重建效果，稀疏重建后调用OpenSplat来做3D Gaussian渲染。
	- 放弃原因: 由于之前下载的数据集是专为colmap准备的，重建质量尚可，所以就不再进行优化了。
- [DONE] 测试直接用colmap运行south-building数据集
	- 背景: 
		- 由于south-building本来就是用于测试colmap的数据集，它里面自带database数据
		- 对于自带database的数据，它里面有可能本身就有相机位姿，因此可以直接用这个东西重建一下看看效果。
	- 结果:
		- 用OpenSplat进行30000次迭代后可以正常得到房子的渲染效果。
- [TO-DO] 录视频记录当前的房子重建的效果。
