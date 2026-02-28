# 1月
- [DOING] 加速Qwen-Image-Edit。
	- [DONE] 验证发现flash-attention使用的已经是最大的形状的mma指令。
	- [DONE] 基于Nsight-Compute的profile结果发现原有的实现使用了过多寄存器导致kernel的occupancy过低。
	- [DONE] 写demo验证了使用过多寄存器会导致kernel的Flops/s下降。
	- [DOING] 手搓寄存器使用率较低的flash-attention.
		- [DONE] 实现将key矩阵从全局内存加载到寄存器再加载到共享内存。
		- [DONE] 实现将query, key从共享内存加载到寄存器并满足PTX指令的要求。
		- [DONE] 实现增量式的softmax，维护output结果，最大分数以及指数和。
		- [DONE] 实现将value从全局内存加载到共享内存。
		- [DONE] 实现将value从共享内存加载到寄存器。
		- [DOING] 验证Q\*K^T的计算结果是否与CPU上的计算结果一致。

# 2月
- [DOING] 加速Qwen-Image-Edit。
	- [DOING] 手搓寄存器使用率较低的flash-attention.
		- [DONE] 验证Q\*K^T的计算结果是否与CPU上的计算结果一致。
		- [DOING] 验证softmax的计算结果是否与CPU上的结果一致。
- [DOING] 部署map-anything用于提高3DGS生成的质量。
	- [DONE] 在服务器上测试map-anything的生成质量，理论上可以不作BA直接使用。
	- [DONE] 在服务器上部署sam3模型，用于识别地面像素从而置正地面点。
	- [DOING] 由于map-anything会对输入图片进行裁剪，两个图片的像素点需要重新对齐。