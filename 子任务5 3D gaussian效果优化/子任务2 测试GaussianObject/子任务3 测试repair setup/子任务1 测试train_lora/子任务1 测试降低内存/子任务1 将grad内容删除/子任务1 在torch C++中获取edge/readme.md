# 目标
- 为了研究PyTorch里面管理梯度内存的方法，新建一个工程，执行一次backward的过程。
- 执行完backward的过程后，利用torch里面的C++接口，访问某个torch tensor的edge信息。

# 工作过程
- [DONE] 在C++的torch工程里面进行最简单的torch运算，并且记录梯度信息。
- [DONE] 对于某个tensor,获取这个tensor的edge信息。

# 结果
- 目前可以在torch的C++代码里面获取一个tensor的edge。