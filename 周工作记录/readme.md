# 2025/1/5
- [DONE] 实现在运行时修改环境光照的亮度体现三维高斯的表面颜色随亮度变化。
	- 演示视频: https://www.bilibili.com/video/BV16i6DYQEhc
- [DOING] 实现三维重建的交互界面。
	- 状态:
		- [DONE] 实现走近操作台时显示按E交互的提示。
		- [DONE] 实现在操作台附近按E时显示三维重建的界面。
		- [DOING] 实现三维重建界面的具体内容。 

# 2025/1/12
- [DONE] 实现三维重建的交互界面。
	- 结果: 点击了界面上的按钮后可以调用重建接口。
- [DONE] 将C++的重建接口移植到新工程。
- [DOING] 实现加载ply文件的程序并在游戏里保存成三维高斯描述结构。

# 2025/1/19
- [DONE] 实现加载ply文件并在游戏里保存成三维高斯的描述。
- [DONE] 当点击重建操作台上的图标时，把重建结果保存到玩家的背包里面。
- [DOING] 点击背包里的重建结果时把它显示在场景里。

# 2025/1/26
- [DONE] 点击背包的重建结果时显示在场景里。
- [DONE] 实现重建结果的拿起和放下的逻辑，重建结果拿起时会不断跟随视角。
- [DOING] 实现对场景中的重建结果的缩放效果。

# 2025/2/9
- [DONE] 实现场景中重建结果的缩放效果。
	- 结果: 当进入和重建结果的交互状态时，可以使用鼠标滚轮调整重建结果的大小。
- [DOING] 实现重建结果的旋转交互。
	- 状态:
		- [DONE] 实现当进入重建结果交互状态并打开旋转工具时，显示旋转轴。
		- [DONE] 实现了鼠标悬停在旋转轴上时，对应的旋转轴高亮。
		- [TO-DO] 实现当鼠标按住旋转轴拖动时，沿着对应轴旋转。

# 2025/2/16
- [DOING] 实现旋转重建结果的旋转交互。
	- 状态:
		- [DOING] 当鼠标点击旋转轴拖动时，让旋转轴跟随鼠标移动。