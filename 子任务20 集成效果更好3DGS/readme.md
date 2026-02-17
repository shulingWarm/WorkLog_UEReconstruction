# 目标
- 集成效果更好的3D Gaussian Splatting算法，优化虚幻引擎里面生成的3DGS的效果。

- [GIVE-UP] 验证Learning Unified Representation of 3D Gaussian Splatting的重建效果。
	- [DONE] 配置工程的依赖包，运行训练脚本不会报找不到包的错误。
	- 没有明确的项目复现guide，放弃。
- [DOING] 部署MapAnything，用于提升3DGS的效果。
	- [DONE] 准备map anything的主模型。
	- [DONE] 下载主模型需要的dinov2模型。
	- [DOOE] 准备主模型要求的代版本的numpy，实现两种版本的numpy并存。
	- [DONE] 测试map anything的运行效果。
	- [DONE] 用map anything生成了colmap形式的点云。
	- [DOING] 寻找语义分割模型，用于寻找地面点来把map anything生成的点云置正。
		- [DONE] 确认使用sam3模型。
		- [DONE] 配置sam3的运行环境。
		- [DOING] 运行sam3的demo。
	- [TO-DO] 测试基于map anything生成的colmap点云再转换成3DGS的效果。