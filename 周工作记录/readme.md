# 2026/1/4
- [DOING] 加速Qwen-Image-Edit
	- [DOING] 手搓寄存器开销较小的flash-attention.
		- [DONE] 解决query验证共享内存写入结果时出现段错误。
		- [DONE] 验证query的共享内存layout符合预期。
		- [DONE] 开发key矩阵从全局内存复制到共享内存。
		- [DOING] 解决key矩阵的共享内存内容不符合预期的问题。

# 2026/1/11
- [DOING] 加速Qwen-Image-Edit.
	- [DOING] 手搓寄存器开销较小的flash-attention.
		- [DONE] 解决key矩阵共享内存内容不符合预期的问题。
		- [DONE] 根据mma指令的layout需要，改成按照十字划分来加载key矩阵。
		- [DOING] 根据mma指令的需要，重新加载query矩阵。

# 2026/1/25
- [DOING] 加速Qwen-Image-Edit.
	- [DOING] 手搓寄存器开销较小的flash-attention.
		- [DONE] 根据mma指令的需要，重新加载query矩阵。
		- [DONE] 完成softmax部分的分数最大值和指数和。
		- [TO-DO] 把softmax的输出结果直接存储到寄存器里面用于attn_score×V

# 2026/2/1
- [DOING] 加速Qwen-Image-Edit.
	- [DOING] 手搓寄存器开销较小的flash-attention.
		- [DONE] 把softmax的输出结果直接存储到寄存器里面用于attn_score×V
		- [DONE] 把value从全局内存加载到共享内存。
		- [DOING] 验证Q\*K^T的计算结果。

# 2026/2/8
- [DOING] 加速Qwen-Image-Edit.
	- [DOING] 手搓寄存器开销较小的flash-attention.
		- [DOING] 验证Q\*K^T的计算结果。
			- [DONE] 实现CPU版本的Q\*K^T的结果。
			- [DOING] 重排GPU上的结果，和标准的output排布对齐。
- [DOING] 部署Map-Anything用于提高3DGS的重建质量。