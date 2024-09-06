# 背景
- 为了不在场景中看到过大的无效3D gaussian,采用一种视角约束的方法
- 记录3D gaussian在训练过程中都从哪些视角观察过，记录下来这些视角从而形成一个视角范围
- 在UE中观察3D gaussian时，当从一个无效视角观察3D gaussian时，直接不显示它。

# 工作记录
- 【DONE】 子任务1: 计算每个3D gaussian的视角范围
- 【TO-DO】 在UE里面实现基于gaussian可见视角范围的渲染。
	- 目的: 由于每个3D gaussian有它自己的渲染视角范围，需要对UE的粒子系统渲染有针对性的修改。
- 【TO-DO】 在OpenSplat中，将3D gaussian的视角范围回传给UE