# 目标
- 选用之前在虚幻引擎里面用过的房子场景来实验Relightable3DGaussian的效果。
- 之前的手机测试场景本身质量不好，难以充分体现Relightable3DGaussian的效果。

# 工作过程
- [DONE] 把之前房子的colmap工程转换成pinhole模型。
- [DONE] 试图用Relightable3DGaussian加载房子的稀疏重建结果，遇到显存不足的问题。
- [DOING] 切割房子的稀疏点云，只保留其中30张图片以及对应的剩余点云。