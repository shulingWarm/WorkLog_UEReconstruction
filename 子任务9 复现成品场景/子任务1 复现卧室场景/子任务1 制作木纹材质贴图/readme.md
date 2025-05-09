# 目标
- 为了在运行时生成木纹材质，需要先在运行时生成木纹贴图。

# 工作过程
- [DONE] 为了验证木纹贴图的生成效果，先在UE里面添加一个允许运行时指定纹理的空材质。
- [DONE] 在新建了动态Mesh之后，新建一个可配置纹理的材质，然后手动配置纹理。
- [DONE] 在运行时新建Material并修改Material参数。
- [DONE] 解决Material指定的图片在Mesh上只采样到了颜色而不能体现图片的问题。
	- 工作状态:
		- [DONE] 研究发现UDynamicMesh没有直接设置Material的接口。
		- [DONE] 找到了设置Override材质中涉及到的对材质属性的获取。
		- [DONE] 研究材质的GetRelevance_Concurrent的具体实现。
		- [DONE] 研究发现材质底层的更新主要发生在渲染线程，核心数据结构是FUniformExpressionCache。
		- [DONE] 确认Material的核心数据结构是UniformBuffer。
		- [DONE] UniformBuffer执行渲染过程的位置是Function(UniformBuffer);。
		- [DONE] 分析Function(UniformBuffer)的逻辑，发现UniformBuffer是一个树形结构，每一层根据Buffer的数据类型单独处理。
		- [DONE] 分析EnumerateTextures传入的回调函数，更进一步查看对Texture的处理逻辑，核心可能在于给Pass添加了View。
		- [DONE] 子任务1 深入研究: Pass->Views.Add(View->Handle);
		- [DONE] 在UE的shader代码中寻找与Texture渲染UV相关的代码。
			- 在shader中找到了UV确实被使用了，但UV仅仅是一个纹理的采样坐标，关键要看采样坐标是怎样被传递进shader函数的。
		- [DONE] 研究发现FShader确实是由Shaders里面的代码构造得到的。
		- [DONE] 研究静态Mesh和动态Mesh设置材质时的区别，为什么动态Mesh设置材质之后纹理无法正常显示。
			- 动态Mesh和静态Mesh设置材质的流程完全不同，甚至静态Mesh和动态Mesh都没有一个公共的父类。
		- [DONE] 测试用AGeneratedDynamicMeshActor在运行时生成Mesh。
			- AGeneratedDynamicMeshActor 可以正常用于在运行时生成Mesh。
		- [DONE] 测试使用AGeneratedDynamicMeshActor叠加自定义的代码来动态生成Mesh。
			- 用 AGeneratedDynamicMeshActor 叠加自定义Mesh生成逻辑得到的Mesh无法正常显示材质。
		- [DONE] 子任务2 解耦 AGeneratedDynamicMeshActor 里面原生的AppendBox过程，直到暴露出修改Mesh内容的接口。
		- [DONE] 子任务3 基于AppendBox的实接口，重新实现基于横截面生成Mesh的逻辑。
	- 结果: 目前可以基于AppendBox的接口生成能正常显示贴图的正方体。
- [DONE] 把正方体显示的贴图改成动态指定的贴图。
- [DONE] 将之前实现过的Texture的生成、获取数据、解锁等接口整合进一个独立模块方便复用。
- [DONE] 动态生成空白贴图。
	- 结果: 可以在生成的场景中看到纯白色的贴图。
- [DONE] 使用C++实现类似于PS里面的云彩效果。
- [DONE] 使用C++实现PS里面添加杂色效果。
- [DONE] 使用C++实现PS里面的动感模糊效果。
	- 状态:
		- [DONE] 研究发现动感模糊是用模糊方向每个像素点两边采样取平均得到的。
		- [DONE] 实现了每个像素遍历的基本逻辑。
		- [DONE] 实现对特定像素的采样逻辑。
	- 结果: 动感模糊之后，基本可以实现木纹的外观，但表面光泽差很多。

# 结果
- 在云彩+杂色+动感模糊的情况下，基本可以看到木纹的外观效果。