# 目标
- 在这个论文里面配置三维高斯重新打光的论文，找一个能跑起来的示例复现论文里面的效果。
- 不要求使用论文里面的数据集，受限于GPU显存的大小，找一个能承载的运算量即可。

# 工作过程
- [DONE] 配置论文工程所需的环境，确保train.py在import阶段不报错就可以。
	- [DONE] 修改了RelightableGaussian里面的bvh,确保cuda代码能编译通过。
	- 结果: 目前可以确保train.py在import阶段不报错。
- [DONE] 子任务1 准备用于打光的测试数据，确保进入训练迭代之前不会报错。
- [DOING] 子任务2 测试房子场景在Relightable3DGaussian下的渲染效果。