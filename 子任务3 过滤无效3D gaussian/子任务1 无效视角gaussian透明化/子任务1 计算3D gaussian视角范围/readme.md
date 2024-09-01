# 目标
- 计算每个3D gaussian的视角范围
- 这是对3D gaussian splatting计算结果的一个后处理

# 工作记录
- 【DONE】 在OpenSplat中添加一个library，在library中声明一个GPU kernel
	- 目的: 后面会在这个kernel里面实现计算gaussian视角范围相关的逻辑
- 【DOING】 子任务1 实现kernel的具体计算逻辑