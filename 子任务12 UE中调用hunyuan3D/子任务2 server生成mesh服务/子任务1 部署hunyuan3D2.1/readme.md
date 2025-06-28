# 目标
- 由于Hunyuan3D2的贴图生成过程太慢，在此特地部署Hunyuan3D2.1。

# 工作过程
- [DONE] 配置Hunyuan3D2.1的依赖库，例如bpy库采用手动clone的形式。
- [DONE] 下载Hunyuan3D paint的模型。
- [DONE] 解决Hunyuan2.1里面默认的cutsom pipeline路径写错的问题。
- [DONE] 测试Hunyuan2.1的texture生成效果。
	- 结果: Hunyuan3D 2.1明显比Hunyuan3D 2快，可在1分钟内完成贴图生成。
- [TO-DO] 调查怎样获取Hunyuan3D 2.1生成的mesh数据，目前它是直接保存文件，无法获取中间数据。