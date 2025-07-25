# 目标
- 当用户对于LLM模型反馈的结果不满意时，可以用语言指出LLM回答不好的地方，模型根据玩家的反馈直接进行在线训练。
- 因为这里面涉及到超长的上下文，所以模型里面需要一些结构把这些内容都记忆下来。

# 工作过程
- [DONE] 开发一个LLMTrainer用于封装LLM的训练过程。
- [DONE] 准备用于训练的复杂提示词。
- [DONE] 训练LLM在简单提示词的情况下，输出和完整提示词质量一样的输出。
	- [DONE] 配置MS Swift，这是qwen3推荐的训练框架。
	- [DONE] 准备用于训练的数据集格式。
	- [DONE] 用lora训练qwen3-8b。
	- [DONE] 验证lora的训练效果，可以确认lora训练后它已经掌握了训练数据里面的信息。
- [DONE] 研究目前最新的LLM模型的结构，看看在什么地方适合添加这种记忆模块。
	- 最终确认，在扩展词表里面添加记忆模块，在词表里面添加一些新的token，这些token不是输出token而是中间的思考token。
- [DOING] 搭建中间的思考token的接口，把不确定怎样实现的部分声明为抽象接口。
	- [DONE] 实现了扩展model词表和embedding的函数。
	- [DONE] 研究MS Swift里面的lora训练代码，观察什么地方指定了只训练Lora层。
	- [DONE] 封装将Embedding层拆分成部分可训练的计算层。
	- [DONE] 封装将Linear层拆分成部分可训练的计算层。
	- [DONE] 验证Swift可以直接添加新的训练模式，默认情况下是一种无训练参数的训练。
	- [DONE] 在embedding的扩展函数里面同时扩展tokenizer和embedding, linear.
	- [TO-DO] 在Swift的训练之前调用外部传入的参数预处理回调函数。