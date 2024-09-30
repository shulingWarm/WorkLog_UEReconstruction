# 8月
- 【DONE】 在UE中调用三维重建，直接将三维重建静态放置到场景中。
	- 目的: 后续会在UE里面实现与三维重建结果更复杂的交互，这里仅仅是一个初步实现版本。
	- 演示效果: https://www.zhihu.com/zvideo/1811054681465708545
- 【DOING】 过滤3D重建结果中的无效3D gaussian.
	- 目的: 对于室内的重建结果场景，将结果放到游戏中并从“室外”观察它时，看到的3D gaussian是无意义的，很影响视觉观感，因此需要寻找方法将它去除。 

# 9月
- [DONE] 渲染时过滤掉当前视角下的无效Gaussian
	- 视频演示: https://www.bilibili.com/video/BV1bpskesE4R
- [DONE] 添加按键交互，允许玩家旋转、缩放3D Gaussian场景
	- 视频演示: https://www.bilibili.com/video/BV16asfepEaq
- [DOING] 使用GaussianCube优化重建结果质量