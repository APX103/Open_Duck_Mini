# 组装指南

> 在组装你的`Duck`之前，你需要先 [配置你的舵机](./configure_motors.md)

## 需求：

你需要：
- 一把焊锡铁、基础电子工具和技能
- X个M3螺丝 (TODO：添加确切数量) (我买了4mm，6mm和10mm长的M3螺丝各一袋，100个。也没必要数着螺丝买捏)
- 一些电线 (我买的是 28 awg 的超软硅胶线)
- Loctite Threadlocker blue 243 (就是螺丝防滑胶)

> 上面这些工具是需要自备的，而且不在BOM表里。这很重要。

> 通用说明：每次将东西拧入电机时，你都需要使用一点Loctite螺纹锁固胶。这可以防止由于机器人运行时的振动导致螺丝松动。虽然这会增加一点组装时间，但你会庆幸自己花时间做了这件事；)

> 在任何时候，你可以参考这里的CAD：https://cad.onshape.com/documents/64074dfcfa379b37d8a47762/w/3650ab4221e215a4f65eb7fe/e/0505c262d882183a25049d05

## 步骤：

### 组装躯干

将轴承放入`trunk_bottom`中，并在这些孔中插入M3内螺纹套筒。这也是一个好时机，在这部分底部插入4个M3内螺纹套筒，以便稍后安装身体部件。

<img src="https://github.com/user-attachments/assets/9ed8591a-7c96-4410-8d7e-9b7d88c6bd1f" alt="1" width="500px" >

然后组装`trunk_bottom`和`trunk_top`，并通过这些孔用2个`M3x10`螺丝将它们拧在一起。

<img src="https://github.com/user-attachments/assets/ae36b396-a34a-4691-8e62-fd916cd1f76c" alt="1" width="500px" >

像这样安装中间电机，并用随电机提供的塑料螺丝将其拧紧。

<img src="https://github.com/user-attachments/assets/d4a6ba6c-852f-440e-afb7-3b9ca66ad3dc" alt="1" width="500px" >

像这样插入`roll_motor_bottom`。

<img src="https://github.com/user-attachments/assets/31c031b7-58b8-4c4c-a3fa-1f14a310c2f2" alt="1" width="500px" >


### 组装脚部

两只脚是一样的。 (**但其实在安装舵机方向的时候有说法，这个留到你装好左脚之后看，必看**)

首先，将`foot_bottom_tpu`与`foot_bottom_pla`组装在一起。在这些孔中插入M3内螺纹套筒：

<img src="https://github.com/user-attachments/assets/6749a5ba-cea9-4b0a-ac32-f32e130fd057" alt="1" width="500px" >

然后用两个`M3x6`螺丝将两部分拧在一起。

然后，在`foot_top`的这些孔中插入M3内螺纹套筒：

<img src="https://github.com/user-attachments/assets/1a77f2f8-56ea-43d2-91c7-78130456c45b" alt="1" width="500px" >

像这样组装所有部件。确保电机驱动侧位于`foot_top`部件的一侧：

<table>
  <tr>
    <td> <img src="https://github.com/user-attachments/assets/197cd9b7-05a6-46ed-9af5-d2def37970c8" alt="1" width="500px" > </td>
    <td> <img src="https://github.com/user-attachments/assets/f532fbcc-100b-4715-96a8-66697e4fda26" alt="1" width="500px" > </td>
   </tr> 
</table>

### 组装小腿

在`leg_spacer`的这些孔中插入M3内螺纹套筒（两侧都要插入，总共插入4个M3内螺纹套筒）：

<img src="https://github.com/user-attachments/assets/41eb01a2-d6f9-43b1-a83e-d14785907425" alt="1" width="500px" >

然后，首先将电机电缆插入脚部电机，并使其穿过`right_sheet`如下图所示：

<img src="https://github.com/user-attachments/assets/a1432505-6b6c-4765-aea6-0a7a0b8b220b" alt="1" width="500px" >

然后按照下图进行组装：

<img src="https://github.com/user-attachments/assets/54615217-fec9-46dd-8b40-e21a4f527b55" alt="1" width="500px" >

### 组装大腿

大腿基本上是同样的操作，只是`hip_pitch`电机以这种方式安装（对零位很重要）。

<img src="https://github.com/user-attachments/assets/951157a4-26dc-41bb-b97f-18dbbb0c1cd3" alt="1" width="500px" >

### 组装髋部

安装`left_roll_to_pitch`或`right_roll_to_pitch`，这里部件是对称的，所以要使用正确的那个。

<img src="https://github.com/user-attachments/assets/368a85ad-1c58-4db2-bdd0-812334b6c784" alt="1" width="500px" >

将`roll_motor_top`安装到`hip_yaw`伺服电机上（从底部拧螺丝）。暂时不要将伺服电机安装到躯干上。

<img src="https://github.com/user-attachments/assets/768f1664-030c-4432-9071-c52d79d3ef6b" alt="1" width="500px" >

然后像这样安装`hip_roll`。

<img src="https://github.com/user-attachments/assets/e1287f67-320c-42cf-a5dc-84f4c64abb17" alt="1" width="500px" >

然后像这样插入子组件。

<img src="https://github.com/user-attachments/assets/dba458ae-e9cb-4e16-a82e-cbe74d2350fa" alt="1" width="500px" >

尽可能地拧紧所有能拧紧的部分（使用随伺服电机提供的塑料螺丝）。

现在你可以像这样安装腿：

<img src="https://github.com/user-attachments/assets/a7169791-9f0a-4827-aea7-00ab1d0f6212" alt="1" width="500px" >

另一条腿也做同样的操作 :)

你的鸭子现在应该看起来像这样：

<img src="https://github.com/user-attachments/assets/4921b29b-b38b-423d-9da1-1c8f84689e84" alt="1" width="500px" >

### 组装颈部

你知道该怎么做。

<img src="https://github.com/user-attachments/assets/f96fe44f-a7bc-423e-a925-4aef3e7bf568" alt="1" width="500px" >

### 组装头部

> TODO 更新此内容以包含新的头部功能

作为参考，现在的头部内部看起来像这样：

![image](https://github.com/user-attachments/assets/91284081-a563-4c02-bb3d-194b3afbc25c)


首先像这样安装`head_pitch_to_yaw`。

<img src="https://github.com/user-attachments/assets/a4dba395-eb0d-4150-8980-8e14f1173d02" alt="1" width="500px" >

然后独立安装`head_yaw_to_roll`和`head_roll_mount`到`head_roll dof`。

<img src="https://github.com/user-attachments/assets/4648cd6c-391e-41e4-9617-4ecebfa9215b" alt="1" width="500px" >

（你现在也可以插入`head_bot_plate`和`body_middle_top`，以避免以后拆卸头部）

然后：

<img src="https://github.com/user-attachments/assets/03f3bdae-06c3-4c37-b68f-14587edd6123" alt="1" width="500px" >

然后：

<img src="https://github.com/user-attachments/assets/04a219d8-bbaf-4910-b5d3-7ca67bce466c" alt="1" width="500px" >

你的鸭子现在应该看起来像这样：

<img src="https://github.com/user-attachments/assets/71545d40-f0f5-411d-a8d5-1cd676a74e75" alt="1" width="500px" >

### 安装舵机驱动板

TODO 拍张照片

### 安装IMU

像这样安装：

> 实际上，最好以正确的自然方向安装IMU，这与下面的图片相比会在X轴上翻转。
> TODO 拍张照片并更好地解释

<table>
  <tr>
    <td> <img src="https://github.com/user-attachments/assets/8772996d-5906-48fa-8cbe-6b6823982375" alt="1" width="500px" ></td>
    <td> <img src="https://github.com/user-attachments/assets/172f44c7-c7c6-47f8-894a-14024abd24f4" alt="2" width="500px" ></td>
   </tr> 
</table>

## 电子部分

以下是整体电子原理图供参考：

<table>
  <tr>
    <td> <img src="open_duck_mini_v2_wiring_diagram.png" alt="1" width="500px" ></td>
    <td> <img src="wiring.png" alt="2" width="500px" ></td>
   </tr> 
</table>

### 电池组

> 为了安全起见，请确保在将电池放入电池座之前，所有电池单元已充电至相同的电压。

<table>
  <tr>
    <td> <img src="https://github.com/user-attachments/assets/371db809-7cb3-47e1-b277-7fc2bdf21025" alt="1" width="500px" ></td>
    <td> <img src="https://github.com/user-attachments/assets/3acfa4e6-ecf7-41f6-a965-35a3040f52fb" alt="2" width="500px" ></td>
   </tr> 
</table>


### 头部

首先，在所有这些孔中插入M3内螺纹套筒：

![image](https://github.com/user-attachments/assets/ef4cd513-6b8d-41fa-9cc3-149fc8333d3e)


然后插入轴承，安装耳部电机和Raspberry Pi Zero 2W。

然后像这样将颈部与头部组装在一起：

![image](https://github.com/user-attachments/assets/96fd5347-bff7-47e9-a7bd-fde17ab1bcd2)


## 身体

首先将`body_middle_bottom`拧紧：

![Capture d’écran du 2025-02-09 12-10-00](https://github.com/user-attachments/assets/081d8840-8e88-4938-9d9a-4d97614e6261)

然后在`body_middle_bottom`和`body_middle_top`的所有孔中插入M3内螺纹套筒，我们将在其上安装电池组和`body_front`。

然后安装`body_middle_top`、`body_front`和电池组：

<table>
  <tr>
    <td> <img src="https://github.com/user-attachments/assets/679a9cd2-89ca-41e8-9d03-f93fc040068b" alt="1" width="500px" ></td>
    <td> <img src="https://github.com/user-attachments/assets/ca292c48-1c72-4649-b7d1-4d3c9eac62ac" alt="2" width="500px" ></td>
   </tr> 
</table>

就这样完成了 :) 

<table>
  <tr>
    <td> <img src="https://github.com/user-attachments/assets/312ec747-8eb4-4145-92eb-c1c3ddba80da" alt="1" width="500px" ></td>
    <td> <img src="https://github.com/user-attachments/assets/864d9dd7-3daf-4e63-913c-2e99157e4aaf" alt="2" width="500px" ></td>
   </tr> 
</table>


> 现在你的鸭子已经完全组装好了，你可以在这里设置Raspberry Pi和运行时软件：[这里](https://github.com/apirrone/Open_Duck_Mini_Runtime)
