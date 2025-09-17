# 目标
- 在UE中集成QwenImageEdit。
- 每次由图生3D完成之后，添加文本框内容，允许用户先编辑图片然后再重新生成3D模型。

# 工作过程
- [DONE] 下载QwenImageEdit的原始模型。
- [DONE] 测试模型的基本推理效果。
	- 使用模型的基本推理效果显存不够，无法加载模型。
- [DOING] 使用modelscope的低显存推理模式来推理。