# 目标
- 由于colmap并没有友好的支持prior pose,所以这里改用OpenMVG
- 现在的首要目标是把3D Gaussian里面的游戏效果做出来，只要Linux上能做出来效果，缝合根本不是问题。

# 工作流程
- [DONE] 编译OpenMVG
- [TO-DO] 准备输入pose所需的sfm_data.json
- [TO-DO] 运行OpenMVG重建的主流程