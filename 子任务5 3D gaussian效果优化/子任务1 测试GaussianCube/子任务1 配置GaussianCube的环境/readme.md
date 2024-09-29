# 目标
- 配置GaussianCube所需的运行环境

# 工作过程
- [DONE] 手动安装diff-gaussian-rasterization
	- 说明: 需要clone下来手动调用python3 setup.py, 而不能用pip安装
- [DOING] 解决submodule init时的错误: libcublas.so.11: undefined symbol: cublasLtGetStatusString
	- Status: 这本质上是它的依赖库diff-gaussian-rasterization需要手动安装导致的报错