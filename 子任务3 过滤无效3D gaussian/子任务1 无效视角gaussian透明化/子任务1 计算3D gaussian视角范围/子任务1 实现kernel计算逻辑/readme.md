# 目标
- 在这个子任务中实现kernel的具体计算逻辑

# 工作流程
- 【DONE】 实现kernel中的block计算任务划分，并统计每个3D gaussian的视角范围。
	- 参考commit: d04a9d6fc819f11c0b7e84b6368c8c10f787dad0
- 【TO-DO】 实现Kernel最终的Reduce过程
	- 背景: 由于Kernel中一个3D gaussian的视角范围是由一个Warp来计算的，warp完成计算后，需要将warp中的计算结果整合成一个具体的角度范围
- 【TO-DO】 对每个gaussian的view范围选取有效区间。
	- 背景: 一个角度范围会将360度的角度范围划分成两个区域，需要在最后一步确定到底被选取的是哪个区域。
- 【TO-DO】 调用测试Kernel执行后的计算结果是否符合预期。
	- 背景: 预期应该将3D gaussian的视角范围划分在一个比较小的视角范围内，至少它不应该都是零。