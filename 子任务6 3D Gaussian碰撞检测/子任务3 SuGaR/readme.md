# 目标
- 测试SuGaR生成3D Gaussian对应的Mesh.
- 子任务结束的标志是把SuGaR里面的3D Gaussian转Mesh的功能解耦出来，并且在Linux上运行测试通过。

# 工作记录
- [DONE] 寻找SuGaR里面用于将3D Gaussian转换成Mesh的函数入口。 
	- 结果: 这个入口位于SuGaR/sugar_extractors/coarse_mesh.py
- [TO-DO] Import这个coarse_mesh里面的函数，确实相关的库齐备从而可以正常完成import阶段