# 目标
- 实现3D Gaussian的光影交互，把3D Gaussian从外发光的逻辑修改成反射光的逻辑。
- 最终要求的效果是，UE里面光源位置的变化会引发3D Gaussian模型高光位置的变化。

# 工作过程
- [DOING] 调研光线追踪的基本实现。
	- 背景: 目的是说清楚光线追踪是怎样实现的，不用真的去手写实现出来，但需要知道如果要手写实现应该怎样做。
- [TO-DO] 解构3D Gaussian光线追踪的论文: https://gaussiantracer.github.io/