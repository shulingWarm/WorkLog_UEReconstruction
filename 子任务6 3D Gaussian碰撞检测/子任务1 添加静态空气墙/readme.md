# 目标
- 由于后续需要给3D Gaussian添加碰撞检测，需要动态生成mesh，所以需要研究怎样给3D Gaussian添加mesh.
- 由于之前并没有添加过mesh，所以需要先从最简单的空气墙开始，学习怎样在虚幻引擎里面使用mesh.
- 可以正常使用mesh之后，就可以进一步设计怎样给3D Gaussian动态应用碰撞mesh了。

# 工作记录
- [DONE] 向3D Gaussian里面添加静态Mesh

# 结果
- 静态空气墙只需要导入静态的mesh
- 将静态的mesh的材质设置为透明即可
- 静态的mesh通常需要外部导入，可能是通过blender之类的东西制作的。