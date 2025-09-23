# 目标
- 在UE中集成QwenImageEdit。
- 每次由图生3D完成之后，添加文本框内容，允许用户先编辑图片然后再重新生成3D模型。

# 工作过程
- [DONE] 下载QwenImageEdit的原始模型。
- [DONE] 测试模型的基本推理效果。
	- 使用模型的基本推理效果显存不够，无法加载模型。
- [DONE] 使用modelscope的低显存推理模式来推理。
	- [DONE] 继续下载通过python下载失败的文件。
	- [DONE] 解决modelscope从本地加载模型的加载代码的问题。
		- modelscope加载本地模型应该指定safetensor的绝对路径。
	- [DONE] 解决加载text_encoder时的报错, text_config传入时变成了字典。
	- [DONE] 如果仍然无法正常推理就使用modelscope的API。
		- 使用modelscope的API可以正常推理，但无法使用本地图片，而且响应速度过慢了。
	- [DONE] 使用nunchaku的量化后的模型。
		- [DONE] 解决默认加载方式中CPU内存不够的问题。
	- 用nunchaku加载的是transformer的INT4量化版本，效果可以接受。
- [DONE] 制作UE中调用3D模型编辑的UI。
	- [DONE] 制作了用于生成控件的通用接口。
	- [DONE] 把按E交互的界面做成了通用widget。
	- [DONE] 通过horizontal stack控制了Gen 3D UI的占位。
	- [DONE] 在Gen 3D UI里面添加关闭页面的功能。
	- [DONE] 在Gen 3D UI里面添加调用3D生成的功能。
	- [DONE] 在Gen3DUI里面测试调用过程，符合预期。
- [DOING] 把3D生成的结果作为图标放到背包里而不是直接生成在场景中。
	- [DONE] 定义3DMesh的描述结构。
	- [DOING] 定义用于存储3DMesh的背包物体类型，用于传递3D Mesh。
- [TO-DO] 先调用图片编辑，再调用图生3D来间接实现3D模型编辑。