# 目标
- 用点的观察角度数量来确定无效的3D Gaussian。
- 由于目前的三维高斯结果生成的Mesh外围有很多无效的3D Gaussian，用这个结果来判定遮挡是不行的。

# 工作记录
- [DONE] 在colmap源码寻找每个三维点的有效观察视角
	- 结果: 已经在colmap源码中找到reconstruction，和OpenMVG的SfM_Data的内容基本一致。
- [DONE] 在Colmap里面写入point3D.bin的时候，同时写入一个ply形式的点云。
- [TO-DO] 重新运行Colmap的重建数据，然后观察未稠密化的点云的效果。