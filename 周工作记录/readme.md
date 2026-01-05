# 2026/1/4
- [DOING] 加速Qwen-Image-Edit
	- [DOING] 手搓寄存器开销较小的flash-attention.
		- [DONE] 解决query验证共享内存写入结果时出现段错误。
		- [DONE] 验证query的共享内存layout符合预期。
		- [DONE] 开发key矩阵从全局内存复制到共享内存。
		- [DOING] 解决key矩阵的共享内存内容不符合预期的问题。