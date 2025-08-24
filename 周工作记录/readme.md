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

# 2025/2/23
- [DONE] 实现旋转重建结果的旋转交互。
	- 结果: 打开重建结果时会显示旋转轴，拖动旋转轴时会跟随鼠标旋转。
- [DOING] 复现成品场景中的关键要素，主要关注材质、光照和粒子系统相关的配置。

# 2025/3/2
- [DONE] 复现成品场景中的关键要素。
	- 结果: 成品场景里面主要是简单的mesh搭配材质，并没有复杂的设定。
- [DOING] 复现当前居住的卧室场景。
	- 工作过程:
		- [DOING] 定义最基本的使用的截面和长度生成mesh的逻辑。
		- [TO-DO] 由生成简单几何体的方法生成桌子。

# 2025/3/9
- [DOING] 复现当前的卧室场景。
	- 工作过程:
		- [DONE] 定义截面和基于线描述的mesh生成逻辑。
		- [DONE] 实现连接横截面的功能。
		- [DONE] 实现闭合两端横截面的逻辑。
		- [DONE] 测试效果发现可以在游戏中显示矩形盒子。
		- [DOING] 实现运行时生成木纹贴图，用于后续生成木纹材质。

# 2025/3/16
- [DOING] 解决纹理贴图附加到Mesh时只显示纯色的问题。
	- [DOING] 研究材质贴图的代码实现。
- [TO-DO] 复现当前的卧室场景。
	- [TO-DO] 实时生成木纹贴图。

# 2025/3/23
- [DOING] 解决纹理贴图附加到Mesh时只显示纯色的问题。
	- [DONE] 研究发现UE源码中的底层渲染代码与上层逻辑之前存在复杂的抽象层。
	- [TO-DO] 直接比较代码中动态Mesh和静态Mesh设置材质时的代码实现区别。
- [TO-DO] 复现当前的卧室场景。
	- [TO-DO] 实时生成木纹贴图。

# 2025/3/30
- [DOING] 解决纹理贴图附加到Mesh时只显示纯色的问题。
	- [DONE] 通过使用GeneratedMeshActor这个插件解决了Mesh只显示纯色贴图的问题。
	- [DOING] 暴露出GeneratedMeshActor控件中对Mesh形状的设置，把它弄成可自定义的component。

# 2025/4/6
- [DOING] 解决纹理贴图附加到Mesh时只显示纯色的问题。
	- [DONE] 暴露出GeneratedMeshActor控件中对Mesh形状的设置，把它弄成可自定义的component。
	- [DONE] 使用解耦后的GeneratedMeshActor实现基于横截面的生成Mesh的逻辑。
	- [DOING] 解决基于GeneratedMeshActor生成的mesh仍然无法正常显示贴图的问题。

# 2025/4/13
- [DONE] 解决纹理贴图附加到Mesh上只显示纯色的问题。
	- [DONE] 基于GeneratedMeshActor实现了UV所属节点的管理。
- [TO-DO] 实现运行时生成木纹贴图。
	- [TO-DO] 实现类似于PS里面云彩生成的效果。

# 2025/4/20
- [DONE] 实现运行时生成木纹贴图。
	- [DONE] 实现PS里面的云彩效果。
	- [DONE] 实现添加杂色效果。
	- [DONE] 实现动感模糊效果。
- [DOING] 为了生成圆角桌板，生成圆角矩形的桌子。
	- [DONE] 利用DeepSeek生成圆角矩形的横截面。
	- [DOING] 解耦基于横截面生成Mesh的class。

# 2025/4/27
- [DONE] 生成了带有木纹的圆角桌板。
- [DOING] 生成桌子的金属支撑杆
	- [DOING] 生成圆形横截面。
	- [TO-DO] 沿着弧线方向生成金属支持杆的Mesh。

# 2025/5/18
- [DONE] 完成4090D主机的组装，后续可以开始深度学习模型相关的工作。
- [DONE] 在主机上部署GaussianCube发现效果并不好。
- [TO-DO] 测试Hunyuan3D在本地部署后的3D生成效果。

# 2025/5/25
- [DONE] Hunyuan 3D在本地部署后图生3D效果良好，可以用于在UE上部署。
- [DONE] 测试Windows上的UE与Linux上服务端的网络通信。
- [DONE] 实现UE在运行时加载图片。
- [DOING] 测试Hunyuan直接从数据流中读取图片而不是从文件中。
- [TO-DO] 测试hunyuan通过UE发来的图片生成mesh的效果。

# 2025/6/1
- [DOING] 测试Hunyuan直接从数据流中读取图片。
	- [DONE] 测试基本的UE和Linux服务端之间的通信。
	- [DOING] 解决UE到Linux之间不能一次性发送图片的问题。

# 2025/6/8
- [DOING] 测试Hunyuan直接从数据流中读取图片。
	- [DOING] 搭建UE和python服务端之间的消息通信机制。
	- [TO-DO] 解决UE到Linux之间不能一次性发送图片的问题。

# 2025/6/15
- [DONE] Hunyuan3D直接从数据流中读取图片。
- [DONE] Hunyuan3D收到UE发来的图片后开始做Mesh生成。
- [TO-DO] Hunyuan3D完成Mesh生成后，将Mesh回传给UE。

# 2025/6/22
- [DOING] Hunyuan3D完成Mesh生成后，将Mesh回传给UE。
	- [DONE] 将Mesh的每个节点回传给UE。
	- [DOING] 将Mesh的每个face回传给UE。
	- [TO-DO] UE收到Mesh信息后，拼成实际的Mesh并投放到场景中。

# 2025/6/29
- [DOING] 部署Hunyuan3D 2.1来解决原始贴图过慢的问题.
	- [DONE] 验证Hunyuan3D 2.1的效果。
	- [TO-DO] 从Hunyuan3D 2.1的Mesh生成结果里面取出Mesh数据结构。
- [TO-DO] Hunyuan3D完成Mesh后，将Mesh回传给UE。
	- [DONE] 将Mesh的每个face回传给UE。
	- [TO-DO] 将贴图信息回传给UE。

# 2025/7/6
- [DONE] 部署Hunyuan3D 2.1解决生成贴图过慢的问题。
	- [DONE] 验证发现Hunyuan3D 2.1生成的mesh是直接的numpy数组形式。
	- [DONE] 基于Numpy数组封装mesh。
- [DONE] 解决因python多线程导致的推理线程过慢的问题，python里面没有真正的多线程。
- [DONE] 实现通用的长数组传输框架。
- [DOING] 基于通用的长数组传输框架回传uv和纹理信息。

# 2025/7/13
- [DONE] 基于通用的长数组传输框架回传uv和纹理信息。
- [DOING] 将UE收到的3D模型注册到场景中，显示出来。

# 2025/7/20
- [DONE] 将UE收到的3D模型注册到场景中，显示出来。
- [DOING] 为期一个月，探索LLM实现长期记忆的能力。
- [TO-DO] 研究多模态生成模型的多轮对话生成的能力。
- [TO-DO] 研究3D生成模型的多轮对话生成。
- [TO-DO] 研究3D生成模型的长期记忆能力，以此解决训练数据不足的问题。

# 2025/7/27
- [DOING] 每当大模型遇到新的概念时，在词表添加新的token，然后训练token的embedding。
	- [DONE] 制作对embedding和linear的封装，允许linear和embedding分别对某些列做训练。
	- [DOING] 在框架即将开始训练的时候替换linear和embedding。

# 2025/8/3
- [DOING] 每当大模型遇到新的概念时，在词表添加新的token，然后训练token的embedding。
	- [DONE] 替换模型里面的embedding和linear, 确保只训练部分单词。
	- [DONE] 实现为embedding和linear部分训练适配的保存checkpoint的方式。
	- [DONE] 测试使用部分训练的embedding和linear做推理。
	- [DOING] 解决使用部分训练的embedding和linear推理时的报错。

# 2025/8/10
- [DOING] 每当大模型遇到新的概念时，在词表添加新的token，然后训练token的embedding。
	- [DONE] 测试后确认静态添加新的token可以用于记忆新的信息，但对于其他非训练句子仍存在干扰。
	- [DOING] 设计不对其他非训练问题产生干扰的训练方法。
		- [DOING] 使用反算模式而不是训练模式，直接根据期望输出的token反算embedding应该具有的向量数据。
		- [TO-DO] 检查对于输入句子预测不准确的地方，在对于的地方插入反处出来的引导token。

# 2025/8/17
- [GIVE-UP] 每当大模型遇到新的概念时，在词表添加新的token，然后训练token的embedding。
	- 放弃原因: 测试发现新添加的token只能适应特定的推理内容，无法泛化，需要调研之后才能确定如何设计训练。
- [DOING] 给UE添加调用Hunyuan3D生成三维模型的界面，并且收到重建结果后自动显示在场景中。
	- [DONE] 在三维重建控制台添加用于操作图生3D的界面。
	- [DOING] 实现收到3D生成结果后，将3D模型显示在UE场景中。

# 2025/8/24
- [DONE] 给UE添加调用Hunyuan3D生成的界面。
	- 操作生成3D后会将3D生成的结果显示在游戏中。
- [DONE] 加速LongArrayPackage的传输速度。
	- 增加每包的字节数。
	- 偶尔会出现数据不完整的情况。
- [DOING] 将图片传输的方式改成使用LongArray传输。