# 目标
- PyTorch在反向求导的时候，可以记录下之前保存的内容，但一直不知道这个被保存的Tensor具体应该怎样被找到。
- 所以需要调查PyTorch的源码，找到这个Tensor,这样后续才能有办法释放这个Tensor.

# 工作记录
- [TO-DO] 寻找在pyTorch里面用到的ctx.saved_tensor的具体来源。