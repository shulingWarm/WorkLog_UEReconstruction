# 目标
- 在虚幻引擎里面实现指定重建图片，重建结果放置等逻辑。
- 在这里做好之后，输出的重建结果质量可能不太好，但一定要像一个产品一样能实现完整的操作流程。

# 工作流程
- [DONE] 实现三维重建控制台，走近时弹出三维重建的交互对话框。
	- 状态:
		- [DONE] 子任务1 靠近操作台时显示按E交互。
		- [DONE] 在三维重建界面添加了基本的黑色背景框。
		- [DONE] 实现了可以把鼠标指针显示出来的Controller.
		- [DONE] 实现当显示三维重建界面时允许鼠标操作。
		- [DONE] 当显示三维重建时禁时对角色的移动控制。
		- [DONE] 实现三维重建界面的框架(按钮，文字等)。
	- 结果: 目前在走近时按E可以正常显示三维重建界面。
- [DONE] 实现了三维重建界面里的退出按钮。
- [DONE] 查看旧的reconstruction工程里面加载文件路径的方式。
- [DONE] 实现三维重建选择图片根目录的按钮。
- [DONE] 实现显示用户选择的图片目录的文本，把它显示在重建界面里面。
- [DONE] 添加用于执行重建操作的按钮。
	- 结果: 目前添加进去的代码是启动重建功能，并不包括回传重建结果的功能。
- [DONE] 在蓝图中调用C++实现的重建接口。
	- 结果: 由蓝图调用C++接口后，可以在文件生成的文件夹里面看到点云。
- [DONE] 实现加载ply文件的功能。
	- 背景: 这算是ply文件里面的一个附加功能。
	- 状态:
		- [DONE] 在代码里面执行ply的加载过程后并不会报错。
		- [DONE] 实现一个数据结构用于保存重建结果并且在游戏里面传输。
			- 最终这个数据结构被确定为Texture的列表。
			- UE里面不方便定义在蓝图之间传递的struct.
		- [DONE] 移植旧工程里面的把点高斯场景转换成Texture.
	- 结果: 最终效果是传进来一个构造好的Component然后把数据存储到Component里面。
- [DONE] 在三维重建操作台上显示重建好的项目。
	- 状态:
		- [DONE] 制作带图标和重建文本名的小Widget.
		- [DONE] 在操作台上添加带滚动条的列表来显示所有的重建结果。
	- 结果: 加载点云后会在三维重建操作台上显示一个新的Widget.
- [DONE] 给操作台上的重建结果绑定点击事件。
- [DONE] 实现玩家的背包系统。
	- 状态:
		- [DONE] 当玩家按下暂停按钮后，触发按下暂停按钮的事件，将逻辑实现在全局响应事件里面。
		- [DONE] 实现玩家背包系统的基本背景。
		- [DONE] 当玩家按下暂停按键后，实质地显示玩家的背包系统。
		- [DONE] 实现玩家再次按下暂停键后，关闭背包系统。
		- [DONE] 当玩家点击重建操作台的重建结果时，会把它放进背包。
	- 结果: 目前已经实现了打开背包内容以及显示背包内容的列表。
- [DONE] 实现用于渲染三维高斯的粒子系统。
	- 状态: 
		- [DONE] 将旧工程里面的三维高斯粒子系统复制到新工程中。
		- [DONE] 实现三维高斯的粒子系统的初始化函数，用加载好的点云信息初始化粒子系统。
		- [DONE] 添加sample大小和sample步长的数据读取并添加到粒子系统中。
		- [DONE] 把粒子系统用到的纹理移植到新的工程里面。
	- 结果: 目前已经可以基于粒子系统做正常的三维高斯渲染。
- [DONE] 当玩家点击背包里面的重建结果时把它加入到场景中。
	- 结果: 当玩家点击背包里的重建结果时，重建结果会显示在场景中。
- [DONE] 当背包里的重建结果显示在场景中时，把它显示在当前相机视角的正前方。
- [DONE] 当玩家移动时，让重建结果始终显示在视角正前方。
- [DONE] 当玩家点击鼠标左键时把场景固定在当前的位置。
	- 结果: 当玩家点击鼠标的时候，断开角色蓝图里面实时更新移动的判断。
- [DONE] 实现将已经放在场景中的物体重新拿起的逻辑。
	- 状态:
		- [DONE] 实现一个可抓起的物体抓起和放下的逻辑。
		- [DONE] 让重建好的Actor实现抓起放下的接口(用于判断什么时候触发抓起交互)。
		- [DONE] 实现通用的按E交互的界面，以及玩家按下E时的回调接口。
		- [DONE] 实现在重建结果有人靠近的时候以及重建结果被放下时，显示按E交互的界面。
		- [DONE] 当显示按E交互的界面时，玩家按下E时执行将重建结果抓起的逻辑。
	结果: 目前可以做到将重建结果反复放下和拿起。
- [DONE] 实现重建结果缩放的功能。
	- 状态:
		- [DONE] 定义抽象的背包物体接口，将来会用于提供物体名称以及使用逻辑。
		- [DONE] 定义背包物体的基本UI，包括图标和文本。
		- [DONE] 令背包物体的基本UI实现注册背包物体接口的功能。
		- [DONE] 开辟一个全局Actor专门用于保存动态生成的Actor.
		- [DONE] 让用于缩放功能的工具实质性地显示在背包里面。
		- [DONE] 单独定义背包UI的初始化函数，构造函数似乎不只会被调用一次。
		- [DONE] 解决每次重新打开背包时缩放工具都会在背包里面添加一个新的的问题。
		- [DONE] 子任务2 实现重建缩放的点击效果。
	- 结果: 当抓起重建结果时，可以通过控制滚轮键来对重建结果进行缩放。
- [DONE] 子任务3 实现重建结果旋转的功能。

# 结果
- 目前实现了在操作台里面加载重建结果以及调用重建。
- 实现了从背包里面拿出重建结果将它放入场景中
- 实现了旋转和缩放工具，用于对场景中的重建结果调整旋转，缩放和位置。