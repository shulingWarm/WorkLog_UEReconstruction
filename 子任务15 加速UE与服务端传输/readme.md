# 目标
- 加速UE与Linux服务端的传输速度(目前传输时服务器的传输速度只有1.5MB/s)。

# 工作过程
- [DONE] 将每次传输的数据量改成64KB后，UE端收到的贴图变得不完整。
- [GIVE-UP] 研究怎样将数据包传输过程变得安全。
	- UE端贴图不完整的问题无法稳定复现，等后续再解决。
- [DOING] 将UE向服务端发送图片的实现改为使用LongArray消息。
	- [DONE] 实现从UE向服务端发送LongArray的逻辑(以前UE端只有接收LongArray的实现)
	- [DONE] 解决request和data_back这两个message循环引用的问题。
	- [DONE] 实现使用LongArray情况下的EndMessage接收图片，让接收端打包图片。
	- [TO-DO] 将发送图片的逻辑实现为一个图片通信函数，直接在图片通信函数里面发送LongArray并执行结束操作。
	- [TO-DO] 实现UE发送图片时使用的结束时回调函数。