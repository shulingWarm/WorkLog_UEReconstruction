# 目标
- 通过UE集成libzmq的方式，让UE和python之间可以方便地传输大量数据，并且可以通过接口一次性传输。

# 工作过程
- [DONE] 在windows上源码编译libzmq。
- [GIVE-UP] 实现一个链接zmq的小工程，用于封装libzmq里面的通信接口。
	- 状态:
		- [DONE] 解决无法找到zmq.hpp的问题。
		- [DONE] 链接静态库而不是动态库解决编译时的链接错误。
		- [TO-DO] 封装基本的建立通信连接的接口。
	- 放弃原因: 在windows上链接libzmq过于麻烦，虽然一定能解决，但不必再花时间了。
- [DOING] 基于C++和python里面基本的socket功能，封装一个支持大数据通信的类。
	- 状态:
		- [DONE] C++和Python封装基本的通信接口，只暴露发送和接收接口。
		- [DONE] C++封装实现事件机制，每次发送一个事件Tag，接收段根据Tag处理后续接收逻辑。
		- [TO-DO] Python端实现和C++对等的事件通信机制。