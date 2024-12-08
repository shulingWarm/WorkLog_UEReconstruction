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

# 2024/9/29
- [DONE] 实现控制3D gaussian旋转、缩放和平移相关的逻辑
	- 背景: 目前的重建结果在场景中放置的位置是没有规律的，所以需要允许玩家摆放自己的重建结果。
	- 视频演示: https://www.bilibili.com/video/BV16asfepEaq
- [DOING] 测试GaussianCube提升重建质量的效果
	- 背景: 目前的3D Gaussian重建效果差差得太多，需要跟进一下新的算法来提升一下重建质量。

# 2024/10/6
- [GIVE-UP] 测试GaussianCube提升重建质量的效果
	- 放弃原因: GaussianCube的github引导与论文中的描述难以对应，后续如果发现其他的3D Gaussian优化方案都是这样的话再来仔细研究它的文档。
- [DOING] 测试GaussianObject提升重建结果质量的效果。
	- 背景: GaussianObject可以用4张图片来生成重建结果。
	- [DONE] 完成GaussianObject的环境配置。
	- [DOING] 准备测试GaussianObject所需的输入数据。

# 2024/10/13
- [GIVE-UP] 测试GaussianObject提升重建结果质量的效果。
	- 放弃原因: 运行到train_lora时，显存不足，无法继续测试。
- [DOING] 借助服务器降低train_lora的内存消耗
	- 目的: 借助服务器，先把train_lora跑起来，找到内存消耗点，想办法实现内存动态offload到cpu上
- [DOING] 采用带先验位姿的数据集，生成高质量的重建结果。
	- 目的: 为了做出来的视频有一定的观赏效果，需要自己先拿出来质量足够的重建结果，后续再考虑如何降低使用门槛。

# 2024/10/20
- [DONE] 采用带先验位姿的数据集，用传统方法生成3D Gaussian场景。
	- 视频演示: https://www.bilibili.com/video/BV191y8YfEVR
- [DOING] 借助服务器研究怎样降低train_lora的内存消耗。
	- Stage:
		- [DONE] 在服务器上配置train_lora.py所需的环境。
		- [DONE] 在服务器上测试train_lora，发现在服务器上需要占用14G显存。
		- [DOING] 研究降低train_lora内存的方法。
- [DOING] 给3D Gaussian添加碰撞检测

# 2024/10/27
- [DOING] 借助服务器研究怎样降低train_lora的内存消耗。
	- Stage:
		- [DOING] 尝试释放掉train_lora过程中的梯度内存，观察内存变化。
		- [TO-DO] 研究降低train_lora内存的方法。
- [DOING] 给3D Gaussian添加碰撞检测效果
	- [DONE] 在UE运行时从外部导入Mesh
	- [DONE] 验证从外部导入的Mesh可以正常产生碰撞效果。
	- [TO-DO] 实现根据3D Gaussian生成碰撞Mesh的算法。

# 2024/11/3
- [DOING] 借助服务器研究怎样降低train_lora的内存消耗。
	- Stage:
		- [DOING] 通过源码编译pytorch添加打印信息，寻找获取一个Tensor的前导Tensor的方法。
		- [TO-DO] 尝试释放掉train_lora过程中的梯度内存，观察内存变化。
- [DOING] 从3D Gaussian结果中导出可用于进行碰撞判定的Mesh.
	- [DONE] 测试SuGaR算法，成功将3D Gaussian转换为Mesh，但发现其中外围存在大量无用的3D Gaussian.
	- [TO-DO] 通过实现三维点的观察角度约束，过滤掉外围无效的三维点。
- [TO-DO] 将得到的Mesh添加到虚幻引擎中，用于给3D Gaussian模型附加碰撞效果。

# 2024/11/10
- [DOING] 借助服务器研究怎样降低train_lora的内存消耗。
- [DOING] 从3D Gaussian结果中导出可用于进行碰撞判定的Mesh.
	- [DONE] 测试SuGaR算法，成功将3D Gaussian转换为Mesh，但发现其中外围存在大量无用的3D Gaussian.
	- [DOING] 在colmap重建结束阶段，执行更严格的过滤操作，过滤掉与房子无关的外围点。

# 2024/11/17
- [DONE] 从3D Gaussian结果中导出可用于进行碰撞判定的Mesh.
	- [DONE] 直接用角度约束过滤掉无用的外围点。
	- [DONE] 直接调用colmap生成简单的Mesh
	- [DONE] 解决了OpenSplat自带一个偏移量的问题，确保将Colmap生成的Mesh和3D Gaussian对齐。
- [TO-DO] 将生成的Mesh透明化之后导入到虚幻引擎中，用于进行碰撞判定。

# 2024/11/24
- [DONE] 将生成的Mesh透明化之后导入到虚幻引擎中，用于进行碰撞判定。
	- 视频演示: https://www.bilibili.com/video/BV1eRScYfEDP
- [DONE] 调研适用于给三维高斯做光影交互的方法。
	- 结果: 最终选定采用这篇论文中的方法: https://nju-3dv.github.io/projects/Relightable3DGaussian/
- [DOING] 配置Relightable三维高斯工程所需的运行环境。

# 2024/12/1
- [DONE] 配置Relightable三维高斯工程所需的运行环境。
- [DONE] 准备Relightable三维高斯工程所需的输入数据。
	- [DONE] 由于Relightable工程对于Colmap工程的相机模型有要求，重新选择相机模型进行了一次稀疏重建。
- [DOING] 尝试在Relightable三维高斯工程中读取自己制作的Colmap输入数据。
	- [DOING] 解决找不到train_cameras这个attribute的问题。 

# 2024/12/8
- [DONE] 调用Relightable3DGaussian里面的train过程成功生成带法向量信息的三维高斯。
- [DOING] 测试Relightable3DGaussian里面的重新打光的效果。
- [TO-DO] 将Relightable3DGaussian给三维高斯重新打光的逻辑迁移到虚幻引擎中。