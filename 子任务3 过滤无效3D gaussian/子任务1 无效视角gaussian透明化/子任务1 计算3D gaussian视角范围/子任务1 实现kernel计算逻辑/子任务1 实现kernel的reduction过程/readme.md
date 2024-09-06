# 背景
- kernel最后需要把每个warp管理的线程角度合并成一个范围
- 合并过程中需要使用到__shfl_xor_sync

# 工作流程
- 【DONE】 把每个线程维度的范围对应的中间角度变换到[0, 2PI)
- 【DONE】 用__shfl_xor_sync 访问warp中其他线程中的角度范围
- 【DONE】 完成同一个warp中32个角度范围的合并。
	- 参考代码: https://github.com/shulingWarm/OpenSplat/commit/4db6ffa09606bfbcca9f0f50247fa3df408727cd
- 【DONE】 在kernel中将归约后的角度保存到output指针中
- 【DONE】 在主pipeline中调用这个kernel，查看是否会有运行时错误。
	- 结果: 调用pipeline的过程中并没有遇到运行时报错。

# 结果
- kernel开发好时对应的commit: https://github.com/shulingWarm/OpenSplat/commit/233098b8cfa3c787a2849a086891bd6ace76d1ef
- 调用kenrel后运行时没有报错，但目前无法保证结果的正确性。