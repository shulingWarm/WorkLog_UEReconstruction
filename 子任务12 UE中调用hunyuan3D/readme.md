# 目标
- 在UE中调用hunyuan3D生成Mesh。
- 在UE中实现方便用户使用的UI。

# 工作过程
- [DONE] 建立UE与服务端程序之间的TCP通信。
	- 状态:
		- [DONE] 在UE中实现客户端。
		- [DONE] 在Linux中用python实现服务端。
		- [DONE] 测试通过UE客户端和Linux中的服务端可能收发数据。
- [DONE] 从UE向Linux发送图片。
- [DONE] 在Linux端凭空生成适用于hunyuan的图片。
- [DONE] 在Linux端接收UE发送来的图片并保存到Linux本地确认传输正常。
	- 状态:
		- [DONE] 测试发现UE端可以正常发出去，但python端对解码有要求。
		- [DONE] 研究python端对于非字符串类型的数据格式。
	- 结果: Linux端可以接收并保存图片，但双端之间无法一次性传输大量数据，只能传小图片。
- [DONE] 子任务1 实现双端之间用于传输大量数据的buffer。
- [DOING] 子任务2 实现服务端收到图片后，基于图片调用hunyuan3D生成Mesh。