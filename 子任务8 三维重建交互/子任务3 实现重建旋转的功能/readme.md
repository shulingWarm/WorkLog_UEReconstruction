# 目标
- 在背包里面实现一个工具，用于对当前正在抓起的重建结果做旋转操作。

# 工作过程
- [DONE] 定义旋转工具的背包UI，并且可以在背包里面默认显示这个旋转工具的item。
- [DOING] 实现背包里面的旋转工具的点击回调。
	- 状态:
		- [DONE] 调查访问普通的Actor Componet以及Scene Component都不能往场景里面添加Mesh信息。
		- [DONE] 调查发现需要使用Child Actor作为显示Mesh的组件添加进子Actor里面。
		- [TO-DO] 查看能否在运行时给一个Actor添加Child Actor.