# 目标
- 改写OpenSplat里面之前实现过的用于计算每个3D gaussian有效观察角度范围的kernel
- 每个gaussian的观察角度由float表示的角度大小范围改为用bit表示的角度选中范围

# 工作过程
- 【DONE】 用角度recorder的形式实现对每个角度值的记录。
	- Commit: https://github.com/shulingWarm/OpenSplat/commit/a8fb2e395f200670b45ee16ab48bb3c1d471a2d9
- 【DONE】 根据角度recorder的操作实现角度的归约操作
	- Commit: https://github.com/shulingWarm/OpenSplat/commit/375dc3819fc303f4cba38624e1af5639e42d6696
- 【DONE】 根据角度的bit移位形式，将它最终转换为float的角度大小范围的形式
	- 背景: 由于目前的kernel的角度范围计算改成了bit位记录的形式，但HLSL里面用和还是float的类型，因此需要在kernel结束的时候进行转换。
	- Commit: https://github.com/shulingWarm/OpenSplat/commit/13c20678f17939bf8f462e8958850bea87b2597f

# 结果
- OpenSplat完成视角范围的计算后，会把它转换成float形式的视角范围并保存在二进制文件中.