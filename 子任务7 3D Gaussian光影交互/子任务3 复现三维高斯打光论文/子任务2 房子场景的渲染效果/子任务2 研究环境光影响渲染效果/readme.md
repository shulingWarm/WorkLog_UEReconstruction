# 目标
- 现在需要复现Relightable3DGaussian里面重新打光的效果。
- 所以需要研究代码里面是怎样通过env_map影响实际的渲染图片的。

# 工作记录
- [DONE] 研究发现读取进来的env_map本质上是hdr格式的图片。
- [DOING] 研究env_map如何影响渲染结果。