# 目标
- 通过三维重建控制台，选择图片然后后端调用VGGT之后再调用3DGS，最后将3DGS的结果回传到UE。

# 工作过程
- [DONE] 在服务器上部署VGGT。
- [DONE] 在服务器上部署OpenSplat。
- [DONE] 部署VGGT配套的BA模型。
- [DONE] 实验发现VGGT在重建大场景时对显存要求过高，无法广泛使用。
- [DOING] 部署VGGT-Long，一个支持大场景重建的项目。