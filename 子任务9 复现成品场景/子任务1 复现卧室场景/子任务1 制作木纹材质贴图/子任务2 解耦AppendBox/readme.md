# 目标
- 解耦 AGeneratedDynamicMeshActor 类中 AppendBox的方法
- 暴露出类中修改Mesh的地方，方便以后做扩展。

# 工作过程
- [DOING] 由于 FGeometryScriptPrimitiveOptions 无法正常构造，直接去除代码中用到 FGeometryScriptPrimitiveOptions 的地方。