# 目标
- 人为控制训练流程，在词表里面添加新的token。
- 当需要让模型学习新的概念时，将新的token作为训练参数，在句子里面添加思考token来让模型适应思考过程。

# 工作过程
- [DONE] 只使用一个句子做训练，确认带思考token的情况下，loss仍然可以逐步下降并收敛。
- [DONE] 为了验证训练思考token的效果，将原版模型先扩展词表再保存下来。
- [DONE] 令模型训练思考token时改成由think_token的字符串生成think_token的id。
- [DONE] 对插入后的think token训练后保存示例checkpoint。
- [DONE] 确认发现只训练部分词表的方式下，swift无法保存下来有效的checkpoint，保存下来的文件是空的。
- [DOING] 给swift添加保存checkpoint的钩子。
- [TO-DO] 确认这种只训练部分embedding的模式下，保存下来的checkpoint是什么。