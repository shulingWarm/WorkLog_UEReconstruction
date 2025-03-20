# 目标
- 分析这段代码的实现: Pass->Views.Add(View->Handle);
- 分析Pass-Views的消费者。

# 工作过程
- [DONE] 找到Pass的类定义。
- [DONE] 调研发现Pass-Views不会直接调用到Texture的渲染过程。

# 结果
Pass->Views.Add与底层的渲染过程不直接相关。

