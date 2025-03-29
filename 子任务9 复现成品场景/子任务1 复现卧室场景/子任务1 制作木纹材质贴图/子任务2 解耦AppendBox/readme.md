# 目标
- 解耦 AGeneratedDynamicMeshActor 类中 AppendBox的方法
- 暴露出类中修改Mesh的地方，方便以后做扩展。

# 工作过程
- [DONE] 由于 FGeometryScriptPrimitiveOptions 无法正常构造，直接去除代码中用到 FGeometryScriptPrimitiveOptions 的地方。
- [DONE] 将最外层的数据结构解耦之后，动态生成Mesh的代码可以正常工作。
- [DOING] 打印原始代码每次调用SetUV和SetNormal时指定的数据，观察规律。
- [TO-DO] 将解耦出来的生成Mesh的代码改成自己之前的横截面逻辑。