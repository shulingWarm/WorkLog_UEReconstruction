# 目标
- 现在需要测试RelightableGaussian的效果，因此需要准备一个用于测试的colmap场景。

# 工作过程
- [DONE] 研究RelightableGaussian加载数据的代码，发现允许读取colmap格式的工程。
- [DOING] 测试用手机拍的场景是否满足相机模型要求。
	- 背景: 目前使用的房子的场景使用的相机模型是SIMPLE_RADIAN，RelightableGaussian无法读取。
	- 状态:
		- [DONE] 重新对手机拍摄的场景用colmap做重建。
		- [TO-DO] 测试用手机拍摄的colmap工程能不能被加载到RelightbaleGaussian里面。