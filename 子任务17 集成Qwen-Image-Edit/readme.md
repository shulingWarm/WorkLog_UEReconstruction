# 目标
- 在UE中集成QwenImageEdit。
- 每次由图生3D完成之后，添加文本框内容，允许用户先编辑图片然后再重新生成3D模型。

# 工作过程
- [DONE] 下载QwenImageEdit的原始模型。
- [DONE] 测试模型的基本推理效果。
	- 使用模型的基本推理效果显存不够，无法加载模型。
- [DOING] 使用modelscope的低显存推理模式来推理。
	- [DONE] 继续下载通过python下载失败的文件。
	- [DONE] 解决modelscope从本地加载模型的加载代码的问题。
		- modelscope加载本地模型应该指定safetensor的绝对路径。
	- [DONE] 解决加载text_encoder时的报错, text_config传入时变成了字典。
	- [TO-DO] 验证是否强行将text_config改字典导致了modelscope不认state_dict。
	- [TO-DO] 如果仍然无法正常推理就使用modelscope的API。