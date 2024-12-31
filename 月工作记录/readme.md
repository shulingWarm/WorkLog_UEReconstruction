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

# 10月
- [DONE] 使用对colmap友好的数据集做重建并得到导入到虚幻引擎中。
	- 视频演示: https://www.bilibili.com/video/BV191y8YfEVR
- [DONE] 将外部Mesh导入到虚幻引擎中并实现碰撞效果。
	- 背景: 为了后续实现3D Gaussian的碰撞效果，打算将Mesh导入到游戏中并透明化，从而作为3D Gaussian的碰撞边界。
- [DOING] 解耦SuGaR中将3D Gaussian转换为Mesh的功能，用于将3D Gaussian转换成Mesh
	- 背景: SuGaR相对来说比较受认可，并且其中包含将3D Gaussian转换成Mesh的模块。
- [DOING] 优化GaussianObject中train_lora.py的内存峰值。
	- 背景: GaussianObject是输入4张图片并得到3D Gaussian重建结果的算法，但训练过程中发现显存不够。这种显存不够的情况很可能会频繁遇到，因此打算以这个项目为例开发一种将torch里面的梯度内存offload到CPU上的方法，这确保各种算法至少是可以在PC上跑起来的。

# 11月
- [DONE] 实现三维高斯在虚幻引擎中的碰撞效果。
	- 视频演示: https://www.bilibili.com/video/BV1eRScYfEDP
- [DOING] 给三维高斯实现光影交互效果，让三维高斯的表面颜色随着环境光照的变化而变化。
	- [DONE] 调研论文后选用Relightable3DGaussian作为参考
	- [DOING] 根据Relightable3DGaussian提供的源码复现论文中的效果。

# 12月
- [DONE] 给三维高斯实现光影交互效果，让三维高斯的表面颜色随着环境光照的变化而变化。
	- 结果: 最后并没有利用论文里面的方法，而是发现目前在虚幻引擎里面的渲染逻辑本来就是支持光影交互的。
	视频演示: https://www.bilibili.com/video/BV16i6DYQEhc/
- [TO-DO] 实现在虚幻引擎里面做三维重建的交互逻辑，开始把目前的工作做得像个产品。