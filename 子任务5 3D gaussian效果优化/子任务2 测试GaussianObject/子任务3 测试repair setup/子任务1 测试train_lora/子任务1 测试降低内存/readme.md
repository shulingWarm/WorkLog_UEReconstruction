# 目标
- 在显存足够的服务器上想办法降低train_lora过程的显存消耗
- 成功降低显存消耗后，再回到目前的电脑上实验用少量图片生成重建结果。

# 工作过程
- [DOING] 在新的服务器上配置GaussianObject的环境
	- 状态:
		- [DONE] 配置train_lora.py需要用到的库
		- [TO-DO] 运行train_lora.py的前置脚本