# 1月
- [DOING] 实现在虚幻引擎里面做三维重建的交互逻辑，开始把目前的工作做得像个产品。
	- 状态: 
		- [DONE] 实现了基本的三维重建操作台，玩家可以走近操作台加载重建结果以及调用重建。
		- [DONE] 实现了基本的背包系统，玩家可以在背包里面查看重建好的结果以及用于操作重建结果的工具。
		- [DOING] 实现对重建结果的缩放工具。

# 2月
- [DONE] 实现在虚幻引擎里面做三维重建的交互逻辑。
	- 结果: 实现了重建结果的操作工具，包括缩放工具和旋转工具。
- [DONE] 复刻成品场景里面的材质，了解后续GEN AI会用到的操作。
	- 结果: 实现了墙体的材质和树叶摆动的材质。
- [TO-DO] 在虚幻引擎里面复现自己的卧室。
- [TO-DO] 复现可编辑的3D高斯的论文。

# 3月
- [DOING] 在虚幻引擎里复现自己的卧室
	- 状态:
		- [DONE] 实现横截面+线动态构造三维模型的逻辑。
		- [DOING] 解耦UE里面自带的动态生成Box Mesh的代码。
		- [TO-DO] 基于UE解耦出来的生成Box Mesh的代码，实现横截面+线的生成逻辑。
		- [TO-DO] 解决动态生成的Mesh无法显示纹理贴图的BUG。
# 4月
- [DOING] 在虚幻引擎里面复现自己的卧室场景。
	- 状态:
		- [DONE] 解耦UE里面自带的动态生成Box Mesh的代码。
		- [DONE] 基于UE解耦出来的生成Box Mesh的代码，实现横截面+线的生成逻辑。
		- [DONE] 解决动态生成的Mesh无法显示纹理贴图的问题。
		- [DONE] 实现了木纹贴图的生成。
		- [DONE] 实现了圆角矩形横截面的生成。
		- [DONE] 实现了圆角矩形的木纹桌面。
		- [DOING] 制作桌子的弧形支持杆。
		- [TO-DO] 将桌子的弧形支持杆与木纹桌板拼接成桌子。
- [TO-DO] 配置服务器，用于后续深度学习相关开发。
	- 背景: 目前的电脑只有8G显存，需要升级一下设备方便后续集成更多的应用场景。
- [TO-DO] 在虚幻引擎里面集成一个3DGS的生成模型。
- [TO-DO] 微调3DGS的生成模型，优化它在虚幻引擎中的显示效果。

# 5月
- [GIVE-UP] 在虚幻引擎里面复现卧室场景。
	- 放弃原因: 
		- 任务开发违背了增量式开发的原理。
		- 由于新的服务器已经配置完成，后续要转向深度学习模型相关的开发了。
- [DOING] 在虚幻引擎中配置混元3D，用于图生3D。
	- 状态:
		- [DONE] 在服务器上配置混元3D进行推理，效果良好。
		- [DOING] 建立UE与Linux上服务端程序的通信。

# 6月
- [DOING] 在虚幻引擎中部署混元3D，用于图生3D。
	- [DONE] 建立python server和UE之间的消息通信机制。
	- [DONE] 实现两端之间的图片传输，mesh的vertex和face传输。
	- [DONE] 在server上部署Hunyuan3D 2.1的纹理生成模型。
	- [DOING] 在server生成mesh的pipeline里面集成生成纹理的pipeline。
	- [TO-DO] 测试通过UE向server发起请求执行完整文生图的过程。

# 7月
- [DONE] 在虚幻引擎中部署混元3D，用于图生3D。
	- 完成了server端与UE的通信框架。
	- UE端收到3D模型后可以正常显示mesh与贴图。
- [DOING] 为了后续提出对话式的3D生成模型，预研究基于词表训练的LLM模型。
	- [DOING] 搭建词表训练的Demo，通过扩展模型词表来让模型记住更多信息。

# 8月
- [GIVE-UP] 为了后续提出对话式的3D生成模型，预研究基于词表训练的LLM模型。
	- LLM无法仅通过词表就理解知识内容，仅仅是可以干预推理过程，但简单增加词表无法让模型直接理解对话内容。
- [DOING] 在UE中集成vggt+3D gaussian的三维重建pipeline，当用户输入一组图片时调用服务器上的vggt pipeline执行三维重建。

# 9月
- [DONE] 在UE上部署vggt+3D gaussian的三维重建pipeline。
- [DONE] 修复了UE上对3DGS结果的放置操作。
	- 演示视频: https://www.bilibili.com/video/BV1Rrp3zYEtE
- [DONE] 在服务器上部署Qwen-Image-Edit。
- [DOING] 在UE上实现调用Qwen-Image-Edit的接口。

# 10月
- [DONE] 给UE的旋转工具添加了切换视角的功能，当旋转某个物体时，自动切换到以这个物体为中心的视角。
- [DONE] 在UE上实现调用Qwen-Image-Edit的接口。
	- 演示视频: https://www.bilibili.com/video/BV1PBWqzxE7v
- [DOING] 加速Qwen-Image-Edit。
	- [DONE] 确认flash-attention占整个推理过程的40%，可以认为是优先优化目标。
	- [DONE] 从flash-attention中解耦出核心的核函数，方便快速编译验证修改效果。
	- [DOING] 理解flash-attention的实现逻辑。
	- [TO-DO] 设计flash-attention的加速方案。

# 11月
- [DOING] 加速Qwen-Image-Edit。
	- [DONE] 理解flash-attention的实现逻辑。
	- [DONE] 理解flash-attention中用到的cute::copy涉及到的Tensor和Layout等概念。
	- [DONE] 实现基本的mma指令测试，并按照文档中提到的layout分配不同线程取的数据块。
	- [DOING] 测试不同大小的mma指令的性能差异。

# 12月
- [DOING] 加速Qwen-Image-Edit。
	- [DONE] 验证发现flash-attention使用的已经是最大的形状的mma指令。
	- [DONE] 基于Nsight-Compute的profile结果发现原有的实现使用了过多寄存器导致kernel的occupancy过低。
	- [DONE] 写demo验证了使用过多寄存器会导致kernel的Flops/s下降。
	- [DOING] 手搓寄存器使用率较低的flash-attention.
		- [DONE] 设计只使用较少寄存器的flash-attention的分配方案。
		- [DONE] 实现将query从全局内存加载到寄存器再加载到共享内存，并重排至适合mma指令的layout.
		- [TO-DO] 实现将key矩阵从全局内存加载到寄存器再加载到共享内存。