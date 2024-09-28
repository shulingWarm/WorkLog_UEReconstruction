# 背景
- 虽然目前已经计算出了每个gaussian的角度范围，但是HLSL中无法访问到这个数据
- 需要将保存在二进制文件中的角度范围信息导入到HLSL脚本中。

# 工作记录
- 【DONE】 在C++导入点云的时候，一并导入视角范围的信息
	- 参考commit: https://github.com/shulingWarm/UEReconstruction/commit/0d183c9d3c1a76855e21a7caa027f3e1507924f7
- 【DONE】 在蓝图里面初始化Niagara系统的时候，把view range的texture传入Niagara
- 【DONE】 把Niagara里面的view range texture传入到HLSL中

# 结果
- 目前已经将ViewRange信息以Texture采样颜色的形式传入到了HLSL脚本中
- 参考commit: https://github.com/shulingWarm/UEReconstruction/commit/b88e95bcd1bbf2bf4927eafc6bb9c4d79602e223