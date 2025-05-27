# 目标
- 通过UE集成libzmq的方式，让UE和python之间可以方便地传输大量数据，并且可以通过接口一次性传输。

# 工作过程
- [DONE] 在windows上源码编译libzmq。
- [TO-DO] 实现一个链接zmq的小工程，用于封装libzmq里面的通信接口。