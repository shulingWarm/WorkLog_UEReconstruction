# 目标
- 配置GaussianCube所需的运行环境

# 工作过程
- [DONE] 手动安装diff-gaussian-rasterization
	- 说明: 需要clone下来手动调用python3 setup.py, 而不能用pip安装
- [DONE] 解决submodule init时的错误: libcublas.so.11: undefined symbol: cublasLtGetStatusString
	- Status: 这本质上是它的依赖库diff-gaussian-rasterization需要手动安装导致的报错
	- 结果: 目前已经手动安装了目标库。
- [DONE] 按照环境配置的要求，手动安装所有库。
	- 结果: 目前已经手动安装了所有库，但并没有保证版本完全一致，至少现在import阶段不会报错了。

# 结果
- 已经安装GaussianCube所需的所有依赖库，目前已经可以import过程中不报错了。