动驾驶比赛

 此目录为自动驾驶比赛示例代码。

提供了以下功能：

1. limo 的完整 gazebo 仿真支持库
2. limo移动底盘包

> 仓库地址：https://github.com/jiayh-sustech/Self-Driving-Race

## 0. 工作目录

如下方式组织工作空间.

## 1. 环境配置

`limo`使用 `ROS-melodic` + `Gazebo9` 作为仿真环境。

在selfDriving_ws工作目录下，正常编译与运行：

```
$ catkin_make
$ source devel/setup.bash
```

`limo_description`包主要为 `limo` 仿真模型，`display_models.launch` 为车辆在 `Rviz`中的展示：

```
$ roslaunch limo_description display_models.launch# 在 Rviz 中查看
```

可以得到如下界面：

![Image](https://mmbiz.qpic.cn/mmbiz_png/iaGiawqW0Pic7KLN0860dW3JueA9O8xjrUdwVW6oyEK9g1Pnfia0ObA2kYAiaV0gxb67pY8IibjiavbXNgOyTdnpv2u9w/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

`limo_gazebo_sim`包为 `limo` 车型在 `gazebo`中的仿真，`limo_xxx_.launch`为车型在不同模式下于 `gazebo` 中仿真展示

```
$ roslaunch limo_gazebo_sim limo_ackerman.launch # 在 gazebo 中使用 阿卡曼 模式运动
```

可以看到 Gazebo 中出现了我们的小车

![Image](https://mmbiz.qpic.cn/mmbiz_png/iaGiawqW0Pic7KLN0860dW3JueA9O8xjrUdZ6WMwvp5eurXF6lDYRibL1b8iapcH2dDndSOpnQ5adJE2ibict37Bxl8JA/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

并且 `Rviz`中出现了 传感器 信息

![Image](https://mmbiz.qpic.cn/mmbiz_png/iaGiawqW0Pic7KLN0860dW3JueA9O8xjrUdHedmuYicSibqhglaQDgszianZOsFGbPrJ9bSrKnIV5JujGr1pO1HXicPyQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

这时，我们新开启一个终端运行：

```
$ rosrun teleop_twist_keyboard teleop_twist_keyboard.py 
```

则可以使用键盘控制 limo 进行移动

注意

使用其他地图前需要补全 gazebo 的 models，不然会一直黑屏。
