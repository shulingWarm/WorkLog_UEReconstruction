# 目标
- PyTorch在反向求导的时候，可以记录下之前保存的内容，但一直不知道这个被保存的Tensor具体应该怎样被找到。
- 所以需要调查PyTorch的源码，找到这个Tensor,这样后续才能有办法释放这个Tensor.

# 工作记录
- [DIONG] 确认softmax算子在进行反向推理时得到的记录输出信息以及得到的求导结果被保存在哪了。
	- [DONE] 通过源码编译加打印信息，目前已经确定PyTorch里面的softmax会把推理时的输出信息保存下来。
	- [DOING] 追溯SoftMax的backward函数中得到的梯度信息和记录输出是从哪传入的。 