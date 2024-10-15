# 目标
- 进行带先验位姿的重建，获得高质量的重建结果后，用来做后续效果，碰撞检测、三维物体分割等。

# 工作记录
- [DOING] 寻找colmap里面指定先验pose的接口
	- 状态:
		- 目前已经定位到的函数: ReadDatabaseCameraLocations 位于 model.cc