# 目标
- 重新使用寄存器使用较小的flash-attention.

# 工作过程
- [DONE] 准备用于测试flash-attention的输入数据。
- [DONE] 准备执行flash-attention计算过程的寄存器。
- [DONE] 准备把query复制到共享内存过程中，先把全局内存的query复制到寄存器中。
- [DONE] 开辟了用于准备KV数据的共享内存以及双重缓冲机制。
- [DOING] 实现KV数据的双缓冲加载。