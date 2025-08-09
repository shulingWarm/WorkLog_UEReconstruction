# 目标
- 允许模型在输入句子的指定位置插入think token并且根据句子前后的期望输出token解算需要插入的embedding 向量。

# 工作过程
- [TO-DO] 封装分离的think token，让embedding和lm_head里面分别使用思考embedding和语言embedding。目标是往里面思考添加几个思考embedding它能正常推理完成即可。