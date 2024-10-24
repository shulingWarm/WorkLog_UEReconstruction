# 目标
- 在显存足够的服务器上想办法降低train_lora过程的显存消耗
- 成功降低显存消耗后，再回到目前的电脑上实验用少量图片生成重建结果。

# 工作过程
- [DONE] 在新的服务器上配置GaussianObject的环境
	- 状态:
		- [DONE] 配置train_lora.py需要用到的库
		- [DONE] 运行train_lora.py的前置脚本
	- 结果:
		- 目前已经可以在新服务器上正常测试train_lora.
- [DONE] 寻找服务器上运行train_lora时，是在哪个时刻达到了7G的显存占用
	- 目标: 只要找到了这个显存过载的场景，就可以确定在什么时刻执行offload操作。 
	- 结果: 是在完成第一次推理后，开始进行backward，backward的过程中发生了内存溢出。
- [DOING] 子任务1 手动将grad内存删除。