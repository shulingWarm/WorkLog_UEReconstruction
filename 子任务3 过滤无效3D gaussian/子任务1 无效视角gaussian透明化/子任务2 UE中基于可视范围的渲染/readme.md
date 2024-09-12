# 背景
- 现在已经计算出了每个3D gaussian的视角范围
- 但UE中渲染3D gaussian仍然是全视角渲染的
- 为了达到基于可视视角的渲染效果，需要修改UE中的渲染逻辑。

# 工作记录
- 【DONE】 修改OpenSplat中的视角范围计算，将输入坐标改为(x,-z,-y)
	- 目的: 这是为了和UE里面的3D gaussian渲染预处理保持一致，UE里面会先对每个3D gaussian坐标做这样的变换
	- Commit: https://github.com/shulingWarm/OpenSplat/commit/bf71c36bd969467f9aa5c27f5df3c5a0c7b5c204
- 【DONE】 找到玩家视角在Actor坐标系下的坐标
	- 目的: 由于3D gaussian的坐标系是粒子系统的actor下面的坐标系，因此需要另外计算actor下面的相机坐标。
- 【DONE】 根据相机光心在Actor坐标系下的坐标，计算它到3D gaussian的角度。
- 【DONE】 子任务1 将gaussian的角度范围导入到HLSL中
- 【DONE】 在HLSL中判断x,y的观察角度是否符合原定的角度范围
	- 结果: 目前在代码中添加了判断，如果观察角度超出了原有的观察范围，就直接将size设置为零然后退出

# 结果
- 已经完成UE中HLSL的代码修改
- 目前无法验证代码修改的正确性
- 等计算kernel的角度范围被重新实现后，即可开始效果测试。
