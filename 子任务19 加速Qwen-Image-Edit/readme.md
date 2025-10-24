# 目标
- 加速基于nunchaku推理的Qwen-Image-Edit。

# 工作过程
- [DONE] 从源码编译nunchaku。
	- 跳过pip，直接用python setup.py build_ext可以正常编译。
- [DONE] 测试nunchaku的主要时间瓶颈。
	- 89%的时间用于transformer block，全局50%的时间用于attention.
- [DONE] 将nunchaku的attention实现换成flash attention.
	- 将torch native attention换成flash attention后没有性能提升。
- [DONE] 为了定位flash-attention的具体实现，源码编译flash attention.
- [DONE] 在flash-attention源码里面定位实际执行的kernel。
- [DONE] 解耦flash-attention里面的关键kernel.
	- [DONE] 令解耦的flash-attention链接pytorch.
	- [DONE] 参考原本的flash-attention的头文件，在解耦的flash-attention中引用。
	- [DONE] 引用flash attention的核函数，仅带头文件编译完成。
	- [DONE] 解决带实际调用核函数时编译检查报错的问题。
- [DONE] Dump调用Qwen-Image-Edit时产生的实际attention输入数据，用于测试解耦kernel。
- [DONE] 根据运行Qwen-Image-Edit记录的attention数据数据，在解耦kernel里面执行测试。