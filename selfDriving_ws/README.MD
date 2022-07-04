自动驾驶比赛

 此目录为自动驾驶比赛示例代码。

提供了以下功能：

1. limo 的完整 gazebo 仿真支持库
2. limo移动底盘包

> 仓库地址：https://github.com/jiayh-sustech/Self-Driving-Race

## 0. 工作目录

如下方式组织工作空间.

## 1. 环境配置

`<span>limo</span>` 使用 `<span>ROS-melodic</span>` + `<span>Gazebo9</span>` 作为仿真环境，如果您已经拥有此环境请跳过此节

这里推荐使用 docker 作为开发环境，具体请移步我的ROS 开发环境(https://anthonysun256.github.io/my_ros_env/) 和 Docker 配合VSC 开发最佳实践(https://anthonysun256.github.io/docker-with-vsc_best-practice/)

如果启用 `<span>GPU</span>` 可以查看在Docker中使用Nvidia 显卡(https://anthonysun256.github.io/docker_with_nvidia/)

此处我们使用的 Dockerfile 文件如下：

devcontainer.json 内容如下：

2. 初始化仿真环境

首先更新 `<span>apt</span>` 和 `<span>rosdep database</span>` 保持最新

```
$ sudo apt update
$ rosdep update
```

然后安装仿真依赖库：

```
$ sudo apt-get -y install --no-install-recommends \
ros-melodic-ros-control \
ros-melodic-ros-controllers \
ros-melodic-gazebo-ros \
ros-melodic-gazebo-ros-control \
ros-melodic-joint-state-publisher-gui \
ros-melodic-teleop-twist-keyboard
```

下一步初始化工作空间并安装依赖：

```
$ cd limo/src
$ catkin_init_workspace
$ cd ..
$ rosdep install --from-paths src --ignore-src -r -y
```

即可正常编译与运行：

```
$ catkin_make
$ source devel/setup.bash
```

`<span>limo_description</span>` 包主要为 `<span>limo</span>` 仿真模型，`<span>display_models.launch</span>` 为车辆在 `<span>Rviz</span>` 中的展示：

```
$ roslaunch limo_description display_models.launch# 在 Rviz 中查看
```

可以得到如下界面：

![Image](https://mmbiz.qpic.cn/mmbiz_png/iaGiawqW0Pic7KLN0860dW3JueA9O8xjrUdwVW6oyEK9g1Pnfia0ObA2kYAiaV0gxb67pY8IibjiavbXNgOyTdnpv2u9w/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

`<span>limo_gazebo_sim</span>` 包为 `<span>limo</span>` 车型在 `<span>gazebo</span>` 中的仿真，`<span>limo_xxx_.launch</span>` 为车型在不同模式下于 `<span>gazebo</span>` 中仿真展示

```
$ roslaunch limo_gazebo_sim limo_ackerman.launch # 在 gazebo 中使用 阿卡曼 模式运动
```

可以看到 Gazebo 中出现了我们的小车

![Image](https://mmbiz.qpic.cn/mmbiz_png/iaGiawqW0Pic7KLN0860dW3JueA9O8xjrUdZ6WMwvp5eurXF6lDYRibL1b8iapcH2dDndSOpnQ5adJE2ibict37Bxl8JA/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

并且 `<span>Rviz</span>` 中出现了 传感器 信息

![Image](https://mmbiz.qpic.cn/mmbiz_png/iaGiawqW0Pic7KLN0860dW3JueA9O8xjrUdHedmuYicSibqhglaQDgszianZOsFGbPrJ9bSrKnIV5JujGr1pO1HXicPyQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

这时，我们新开启一个终端运行：

```
$ rosrun teleop_twist_keyboard teleop_twist_keyboard.py 
```

则可以使用键盘控制 limo 进行移动

注意

使用其他地图前需要补全 gazebo 的 models，不然会一直黑屏。
