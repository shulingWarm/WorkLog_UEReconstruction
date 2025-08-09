# 目标
- 人为控制训练流程，在词表里面添加新的token。
- 当需要让模型学习新的概念时，将新的token作为训练参数，在句子里面添加思考token来让模型适应思考过程。

# 工作过程
- [DONE] 只使用一个句子做训练，确认带思考token的情况下，loss仍然可以逐步下降并收敛。
- [DONE] 为了验证训练思考token的效果，将原版模型先扩展词表再保存下来。
- [DONE] 令模型训练思考token时改成由think_token的字符串生成think_token的id。
- [DONE] 对插入后的think token训练后保存示例checkpoint。
- [DONE] 确认发现只训练部分词表的方式下，swift无法保存下来有效的checkpoint，保存下来的文件是空的。
- [DONE] 给swift添加保存checkpoint的钩子。
	- [DONE] 定位到了swift里面保存checkpoint的位置。
	- [DONE] 定义了checkpoint保存的回调格式。
	- [DONE] 在swift里面对应的位置添加注册回调。
- [DONE] 实现针对embedding部分训练的定制化checkpoint保存方案。
- [DONE] 确认这种只训练部分embedding的模式下，保存下来的checkpoint是什么。
	- 保存下来的是对应的训练部分的tensor的pr文件。
- [DONE] 加载训练部分的embedding用于模型推理。
	- 用加载checkpoint后的模型推理，发现没有训练效果，仍然和训练之前的推理内容相同。
- [DONE] 将think_token添加到换行符之后重新训练，添加到\<think\>与换行符之间没有意义。
	- 用这种方式训练得到的模型，会在推理时报错。
- [DONE] 解决在换行符后添加think_token报错。
	- 将推理使用的数据类型换成bf16就可以了。
- [DONE] 验证发现添加的think_token会干扰到其他正常对话内容，导致以前的知识遗忘。
- [DONE] 改成让think_token均匀分布在训练句子里面，效果仍然是会出现知识遗忘。
- [DONE] 验证训练的时候有没有对非think_token位置的logits形成约束。
	- 验证发现训练的时候对于非think_token的位置没有形成约束，并没有抑制其他id。
- [DONE] 实现约束函数，在不该出现think_token的位置抑制think_token的出现。
- [DONE] 给swift添加自定义约束函数的接口，调用抑制think_token的loss函数。
- [DONE] 使用抑制token训练得到的checkpoint仍然无法得到正常的推理效果。
- [DONE] 改用更长的训练时间，测试训练效果。
	- 用更长时间的训练是可以达到训练效果的，训练之后think_token基本不会干扰正常推理。
- [DONE] 为了后续在模型推理过程中添加打印信息，成功在transformers里面注册一个等价模型，可以将模型代码解耦到transformer外面。
- [DONE] 添加一个推理测试接口，打印输入一句话之后下次预测的内容，以及期望token的预测概率。
	- [DONE] 在自定义模型里面强制logits_keep_num变成零，这样会打印所有的预测概率。
	- [DONE] 制作预测概率的格式化输出接口，打印概率最高的10个的概率和每个位置的解码，以及期望输出的概率。
	- 从打印结果中可以看到有的token的推理置信很高，这种情况通常是正确的推理，对于置信较低的推理通常是错误的。

# 结果
- 添加思考token并训练后可以得到预期的推理效果，但仍然会有不该出现think token的地方出现think token。