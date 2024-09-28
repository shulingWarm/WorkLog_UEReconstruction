# 目标
- 在UE里面开发一套交互逻辑，可以让用户对输入进来的3D gaussian场景做放置、平移或缩放。

# 工作记录
- 【DONE】 实现3D gaussian跟随actor的放置改变渲染角度
	- 目标: 初步只需要实现按下按钮就让它跟着转就行。
	- 结果: 粒子系统是会自动跟随它所在的actor进行旋转的。
- 【DONE】 实现3D gaussian根据actor的scale设置渲染scale
	- 结果: 目前在3D gaussian场景跟随旋转变化的时候，可以保证渲染角度也是跟随处理的。
	- Commit: https://github.com/shulingWarm/UEReconstruction/commit/107c1b722a9d173aca7e806aa99799b02f5032d3
- 【DONE】 实现3D gaussian的另外两个旋转轴的操作
	- 结果: 另外两个旋转轴的实现与Z轴是一样的，现在可以用按键控制三个方向的旋转。
- 【DONE】 实现由玩家控制3D gaussian场景的缩放。
	- 状态: 添加了一些按键用于控制3D gaussian结果的缩放。
	- 视频: https://www.bilibili.com/video/BV16asfepEaq

# 结果
- 目前已经支持用按键交互让3D gaussian的重建结果旋转或者缩放。
- 视频效果: https://www.bilibili.com/video/BV16asfepEaq
- 关于将3D gaussian拿起再放下，基本是一个UI系统的逻辑，现在先不急着做这个。