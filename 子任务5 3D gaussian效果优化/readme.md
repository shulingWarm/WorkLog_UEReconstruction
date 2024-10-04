# 目标
- 目前已经把三维重建相关的功能整合进了虚幻引擎，但重建结果的视觉效果还是比较差的，有很严重的模糊和伪影。
- 需要找一下目前成熟的算法，看一下简单应用上这些算法之后能不能得到更好的效果。

# 工作记录
- [GIVE-UP] 子任务1 测试GaussianCube
	- 背景: 这是一个可以文本生成3D模型也可以用少量图片生成3D Gaussian的算法
	- 放弃原因: GaussianCube的论文与代码无法对应，继续调研成本太大，所以应该调研其他算法。
- [DOING] 测试GaussianObject的效果
	- 背景: GaussianObject是华为的工作，使用4张输入图像来生成3D Gaussian.
- [TO-DO] 测试GaussianRoom
	- 背景: 这是一个还没开源的算法，等GaussianCube试用完了，如果GaussianCube效果不行再考虑这个。
