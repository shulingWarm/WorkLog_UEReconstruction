# 目标
- 为了在运行时生成木纹材质，需要先在运行时生成木纹贴图。

# 工作过程
- [DONE] 为了验证木纹贴图的生成效果，先在UE里面添加一个允许运行时指定纹理的空材质。
- [DONE] 在新建了动态Mesh之后，新建一个可配置纹理的材质，然后手动配置纹理。
- [DONE] 在运行时新建Material并修改Material参数。
- [DOING] 解决Material指定的图片在Mesh上只采样到了颜色而不能体现图片的问题。
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
		- [TO-DO] 研究shader数据中UV参数的来源。
- [TO-DO] 使用C++实现类似于PS里面的云彩效果。
- [TO-DO] 使用C++实现PS里面添加杂色效果。
- [TO-DO] 使用C++实现PS里面的动感模糊效果。
- [TO-DO] 使用C++实现PS里面旋转扭曲的效果。