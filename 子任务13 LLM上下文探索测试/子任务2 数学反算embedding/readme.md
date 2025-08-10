# 目标
- 允许模型在输入句子的指定位置插入think token并且根据句子前后的期望输出token解算需要插入的embedding 向量。

# 工作过程
- [DOING] 封装分离的think token，让embedding和lm_head里面分别使用思考embedding和语言embedding。目标是往里面思考添加几个思考embedding它能正常推理完成即可。
	- [DONE] 封装lm_head，给lm_head添加用于思考的head，将两个lm_head推理后的结果合并。
	- [DONE] 实现专用的ThinkModel用于分离Qwen3CausalLM的实现，方便后续做修改。
	- [DOING] 实现embedding的分离效果，分为思考embedding和原始的embedding。
	- [DOING] 将分离后的embedding添加到Qwen3Model里面。

# 放弃原因
- 仅仅lm_head可以根据匹配输入反算，embedding无法反算。
- 后续可以考虑用反馈环路计算KV-cache。