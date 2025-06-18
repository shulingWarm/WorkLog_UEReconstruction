# 目标
- 在Server上实现收到图片后异步生成Mesh。
- 当异步生成Mesh完成后返回给请求者。

# 工作过程
- [DONE] 实现由已经加载好的图片生成Mesh，而不是pipeline默认那个传入图片路径的形式。
- [DONE] 定义由Server调用生成Mesh的消息，需要实现为异步生成的形式。
- [DONE] 在C++端实现请求server生成Mesh的消息。
- [DONE] 测试从发起请求到开始生成Mesh的pipeline能否正常执行。
- [DONE] 确认mesh里面节点的uv是否存在。
	- 结果: 不存在，需要手动创建uv。
- [DOING] 实现mesh生成完成后的回传过程。
	- [DONE] 创建发送mesh的数据头。
	- [DONE] C++接收数据头。
	- [DONE] C++定义抽象的Mesh接口，用于做mesh动态读写。
	- [DONE] Python实现Mesh的动态接口，用于做mesh的动态读写。
	- [DONE] 实现指定的vertex序列的请求消息。
	- [DONE] C++收到回传消息后，请求下一行的消息。
	- [TO-DO] 服务端检查是否已经发送了所有的节点，如果已经发送了所有节点，向客户端发送通知。