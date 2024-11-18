# 目标
- 目前已经有了一个观赏效果足够的3D Gaussian场景被放到了虚幻引擎里面。
- 但这个场景目前还无法产生交互，尤其是没有碰撞相关的实现。

# 工作记录
- [DONE] 子任务1 在虚幻引擎场景中添加空气墙
- [DONE] 子任务2 在运行时添加动态mesh
- [DONE] 子任务3 测试使用SuGaR生成3D Gaussian对应的Mesh
- [DONE] 子任务4 用夹角约束的方式去除无用的3D Gaussian.
- [DONE] 子任务5 把稀疏点云直接转换为Mesh。
- [DOING] 将用于碰撞判定的Mesh和3D Gaussian一同导入到虚幻引擎中。
	- 状态:
		- [DONE] 将UE里面读取mesh的方式改成读取ply文件。
		- [DOING] 将UE里面读取的Mesh和3D Gaussian的坐标系对齐。
			- 背景: UE里面刚刚将3D Gaussian读取进来的时候，也会涉及到坐标变换。 