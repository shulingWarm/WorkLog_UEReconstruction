# 目标
- 在Server上实现收到图片后异步生成Mesh。
- 当异步生成Mesh完成后返回给请求者。

# 工作过程
- [DONE] 实现由已经加载好的图片生成Mesh，而不是pipeline默认那个传入图片路径的形式。
- [DONE] 定义由Server调用生成Mesh的消息，需要实现为异步生成的形式。
- [DONE] 在C++端实现请求server生成Mesh的消息。
- [DONE] 测试从发起请求到开始生成Mesh的pipeline能否正常执行。
- [TO-DO] 实现mesh生成完成后的回传过程。