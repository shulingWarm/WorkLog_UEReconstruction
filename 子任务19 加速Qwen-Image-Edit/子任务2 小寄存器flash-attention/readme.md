# 目标
- 重新使用寄存器使用较小的flash-attention.

# 工作过程
- [DONE] 准备用于测试flash-attention的输入数据。
- [DONE] 准备执行flash-attention计算过程的寄存器。
- [DONE] 准备把query复制到共享内存过程中，先把全局内存的query复制到寄存器中。
- [DONE] 开辟了用于准备KV数据的共享内存以及双重缓冲机制。
- [DONE] 将query的加载量改成warp_num\*mma_n_size\*
	- 改成mma_n_size是为了减少共享内存的使用量。
	- 根据warp_num来加载是为了让每个warp可以并行执行mma计算。
	- 删除双缓冲机制，靠SM自行调度来隐藏延迟。
- [DOING] 阶段性验证query的寄存器加载效果。
- [TO-DO] 计算qkt之前将数据从共享内存加载到寄存器中用于准备mma计算。
	- [DONE] 根据m16n8k16的计算布局要求，将query从共享内存加载到寄存器。
- [TO-DO] 修改一次加载K一次加载V的双缓冲机制。
	- 由于flash-attention需要完整算完一整列的Q\*K^T，所以需要分别完整地加载K和V。
	- [DONE] 修改依次加载KV的数据结构。
	- [TO-DO] 实现在每个计算qkt结束后加载V数据。
