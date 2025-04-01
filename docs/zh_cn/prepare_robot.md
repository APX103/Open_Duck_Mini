# 在MuJoCo中仿真机器人的准备

## 如果你在OnShape中设计了你的机器人

### 确保根据onshape-to-robot的约束设计你的机器人
https://onshape-to-robot.readthedocs.io/en/latest/design.html


生成的urdf文件将包含名为`closing_<...>_1`和`closing_<...>_2`的框架，你可以在mjcf文件中使用它们来闭合循环。

### 从OnShape获取机器人urdf

运行以下命令：

```bash
$ onshape-to-robot robots/bd1/
```

#### （可选）如果你有闭合循环，请按照onshape-to-robot文档中的说明进行处理，然后：

在`robot.urdf`中添加：
```xml
<robot name="...">
    <mujoco>
        <compiler fusestatic="false"/>
    </mujoco>
	...
</robot>
```

# 将URDF转换为MJCF（MuJoCo）

## 获取MuJoCo二进制文件

从以下地址下载MuJoCo二进制文件：https://github.com/google-deepmind/mujoco/releases

解压并运行：

```bash
$ ./compile robot.urdf robot.xml
```

## 在robot.xml中添加执行器：
示例：
```xml
	<actuator>
		<position name="left_hip_yaw"    joint="left_hip_yaw"    inheritrange="1"/>
		<position name="left_hip_roll"   joint="left_hip_roll"   inheritrange="1"/>
		<position name="left_hip_pitch"  joint="left_hip_pitch"  inheritrange="1"/>
		<position name="left_knee"       joint="left_knee"       inheritrange="1"/>
		<position name="left_ankle"      joint="left_ankle"      inheritrange="1"/>
		<position name="right_hip_roll"  joint="right_hip_roll"  inheritrange="1"/>
		<position name="right_hip_yaw"   joint="right_hip_yaw"   inheritrange="1"/>
		<position name="right_hip_pitch" joint="right_hip_pitch" inheritrange="1"/>
		<position name="right_knee"      joint="right_knee"      inheritrange="1"/>
		<position name="right_ankle"     joint="right_ankle"     inheritrange="1"/>
		<position name="head_pitch1"     joint="head_pitch1"     inheritrange="1"/>
		<position name="head_pitch2"     joint="head_pitch2"     inheritrange="1"/>
		<position name="head_yaw"        joint="head_yaw"        inheritrange="1"/>
	</actuator>
```

## 添加自由关节

将主体封装在一个自由关节中：
```xml
<worldbody>
	<body>
		<freejoint />
		...
		...
	</body>
</worldbody>
```

## （可选）约束闭合循环

在mjcf文件中添加以下内容：
```xml
<equality>
    <connect body1="closing_<...>_1" body2="closing_<...>_2" anchor="x y z" />
</equality>
```

x, y, z 的值可以在 .urdf 文件中找到：

```xml
<joint name="closing_<...>_1_frame" type="fixed">
	<origin xyz="x y z" rpy="r p y" />
	...
</joint>
```

## 设置碰撞组、阻尼和摩擦
/!\ 删除关节中的actuatorfricrange
将其放入<mujoco>标签内：
```xml
<mujoco>
  <default>
    <geom contype="1" conaffinity="1" solref=".004 1" />
    <joint damping="0.09" frictionloss="0.1"/>
    <position kp="10" forcerange="-5.0 5.0"/>
  </default>
	...
	...
</mujoco>
```

还需要添加：
- change frames to sites


## 可视化

```bash
$ python3 -m mujoco.viewer --mjcf=<path>/scene.xml
```

或者

```bash
$ <path_to_mujoco_bin>/bin/simulate <path>/scene.xml
```