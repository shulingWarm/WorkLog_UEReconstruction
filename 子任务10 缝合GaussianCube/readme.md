# 目标
- 将GaussianCube在服务器上跑通。
- 在UE里面添加接口用于访问GaussianCube。

# 工作过程
- [DONE] 在服务器上配置GaussianCube。
	- 过程
		- [DONE] 解决mpi4py无法安装的问题。
		- [DONE] 初步运行GaussianCube，确认没有因import问题导致运行失败。
		- [DONE] 下载GaussianCube所需的模型文件。
		- [DONE] 完成了GaussianCube的Demo测试。
- [DONE] 测试发现GaussianCube的效果并不好，大部分提示词下的3D生成效果都无法做到真实感。

# 放弃原因
- 由于GaussianCube效果不符合预期，改为寻找其他模型。