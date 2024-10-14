# 目标
- 按照github里面提供的命令运行train_lora

# 工作流程
- [DONE] 解决下载模型后找不到./models/v1-5-pruned.ckpt
	- 背景: 在运行train_lora时，虽然运行了download的过程，但加载模型的时候仍然找不到文件。
	- 解决方案: 手动把这个脚本上的内容下载下来就可以: /media/zzh/data/privateSpace/workSpace/504GaussianObject/GaussianObject/models/download_hf_models.py
- [DOING] 子任务1 换大显存服务器测试降低内存
	- 目的: 想办法优化代码实现，降低训练过程中的内存消耗。
- [TO-DO] 解决加载模型后找不到点云的问题。
	- 背景: 解决上述找不到checkpoint的问题后，进一步出现了找不到输入点云的问题.
- [TO-DO] 完整调用train_lora的流程。