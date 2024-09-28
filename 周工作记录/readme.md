# 2024/9/1
- 【DONE】 在UE中调用三维重建，直接将三维重建静态放置到场景中。
	- 目的: 后续会在UE里面实现与三维重建结果更复杂的交互，这里仅仅是一个初步实现版本。
	- 演示效果: https://www.zhihu.com/zvideo/1811054681465708545
- 【DONE】 在UE里面添加一个按钮，允许用户选择图片所在的路径，然后调用目标的三维重建。
- 【DOING】 过滤3D重建结果中的无效3D gaussian.
	- 目的: 对于室内的重建结果场景，将结果放到游戏中并从“室外”观察它时，看到的3D gaussian是无意义的，很影响视觉观感，因此需要寻找方法将它去除。 
	- 【DONE】 在重建流程的最后调用3D gaussian视角范围的计算步骤
	- 【DONE】 实现gaussian view视角的核心CUDA核函数的角度计算部分
	- 【TO-DO】 处理最终角度范围的有效区间选择
		- 目的: 角度范围将360度划分为两半，需要特别处理哪一半才是有效区间

# 2024/9/8
- 【DOING】 在DirectX的HLSL中实现3D gaussian的渲染。
	- 目的: 由于UE中的3D gaussian渲染是用HLSL实现的，但目前对于HLSL还不熟悉，因此做一个原生的HLSL项目来积累经验。
- 【TO-DO】 过滤3D重建结果中的无效3D gaussian.
	- 目的: 对于室内的重建结果场景，将结果放到游戏中并从“室外”观察它时，看到的3D gaussian是无意义的，很影响视觉观感，因此需要寻找方法将它去除。 
	- 【DONE】 Gaussian视角范围的计算kernel
		- Commit: https://github.com/shulingWarm/OpenSplat/commit/233098b8cfa3c787a2849a086891bd6ace76d1ef
	- 【TO-DO】 修改UE中的渲染逻辑，适配每个gaussian的可见范围

# 2024/9/15
- 【GIVE-UP】 在DirectX的HLSL中实现3D gaussian的渲染。
	- 原因: HLSL虽然是Windows推出的渲染代码，但文档和教程并不友善，而且语法和C类似，因此可以基于对C语法的认知直接进行UE中HLSL的开发。
- 【DOING】 过滤3D重建结果中的无效3D gaussian.
	- 【DONE】 Gaussian视角范围的计算kernel
	- 【DONE】 修改UE中的渲染逻辑，适配每个gaussian的可见范围
		- Commit: https://github.com/shulingWarm/UEReconstruction/commit/6f75b63238f03ea60eaf56ae4b51731032a5e0d9
		- 结果: 在HLSL中实现了对观察视角的计算以及判断它是否在合法的观察范围内
	- 【DOING】 基于视角范围的渲染效果调试。
		- 目的: 目前基于视角范围的渲染仅仅是完成了代码工作，还未进行测试。

# 2024/9/22
- 【DONE】 过滤3D重建结果中的无效3D gaussian.
	- 结果: 通过限制渲染视角范围，禁止3D gaussian从无效的视角做渲染
	- 视频演示: https://www.bilibili.com/video/BV1bpskesE4R
- 【TO-DO】 实现控制3D gaussian旋转、缩放和平移相关的逻辑
	- 背景: 目前的重建结果在场景中放置的位置是没有规律的，所以需要允许玩家摆放自己的重建结果。