# 背景
- 为了不在场景中看到过大的无效3D gaussian,采用一种视角约束的方法
- 记录3D gaussian在训练过程中都从哪些视角观察过，记录下来这些视角从而形成一个视角范围
- 在UE中观察3D gaussian时，当从一个无效视角观察3D gaussian时，直接不显示它。

# 工作记录
- 【DOING】 子任务1: 计算每个3D gaussian的视角范围
- 【TO-DO】 在OpenSplat中，将3D gaussian的视角范围回传给UE
- 【TO-DO】 修改UE里面对于3D gaussian的渲染逻辑，确保视角范围外的3D gaussian不做显示