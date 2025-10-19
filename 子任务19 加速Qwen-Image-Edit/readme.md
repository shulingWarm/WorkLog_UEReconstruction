# 目标
- 加速基于nunchaku推理的Qwen-Image-Edit。

# 工作过程
- [DONE] 从源码编译nunchaku。
	- 跳过pip，直接用python setup.py build_ext可以正常编译。
- [DONE] 测试nunchaku的主要时间瓶颈。
	- 89%的时间用于transformer block，全局50%的时间用于attention.
- [DONE] 将nunchaku的attention实现换成flash attention.
	- 将torch native attention换成flash attention后没有性能提升。
- [TO-DO] 对nunchaku调用的flash attention做breakdown.