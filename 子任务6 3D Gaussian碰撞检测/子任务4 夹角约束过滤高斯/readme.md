# 目标
- 用点的观察角度数量来确定无效的3D Gaussian。
- 由于目前的三维高斯结果生成的Mesh外围有很多无效的3D Gaussian，用这个结果来判定遮挡是不行的。

# 工作记录
- [DONE] 在colmap源码寻找每个三维点的有效观察视角
	- 结果: 已经在colmap源码中找到reconstruction，和OpenMVG的SfM_Data的内容基本一致。
- [DONE] 在Colmap里面写入point3D.bin的时候，同时写入一个ply形式的点云。
- [DONE] 重新运行Colmap的重建数据，然后观察未稠密化的点云的效果。
	- 结果: 得到了colmap的ply格式的稀疏点云的结果，可以发现稀疏点云中就存在大量的在房子外围的点。
- [DOING] 在colmap的点云数据中锁定这些外围点。
	- 状态:
		- [DONE] 研究发现colmap中不能像载入sfm_data.bin那样载入所有的数据。
		- [DONE] 在colmap稀疏点云计算完成后，实现了遍历所有三维点坐标并打印的功能。
		- [TO-DO] 在colmap刚刚完成稀疏点云计算时，遍历所有稀疏点云，锁定其中异常位置点。
- [TO-DO] 针对colmap中锁定到的外围点，观察它们的重投影误差以及投影角度差。