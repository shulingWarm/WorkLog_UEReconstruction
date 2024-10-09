# 目标
- 测试GaussianObject中的论文效果

# 工作流程
- [DONE] 子任务1 配置GaussianObject所需的环境
- [DONE] 下载mip360数据集
	- 背景: GaussianObject官方建议的测试数据是mip360里面的kitchen,为了和论文保持一致这里采用相同的数据集。
	- 结果: 已经在这个链接中下载到mip360的数据集: https://drive.google.com/drive/folders/1DUOxFybdsSYJHI5p79O_QH87TIODiJ8h
- [DONE] 测试GaussianObject中的visual_hull.py脚本。
	- [DONE] 调用官方提供的数据集，完整地运行了visual_hull.py
	- [DONE] 由于运行完成后并没有看到生成结果，需要寻找原因。
		- 点云保存在数据集所在的文件夹里了。
- [DONE] 子任务2 测试粗糙3D高斯
- [DOING] 子任务3 测试repair setup