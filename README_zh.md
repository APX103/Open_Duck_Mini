# Open Duck Mini v2

> 机翻 + 手工优化，有问题可以提issue.

> 中文翻译的仓库在合入到主仓库前，代码本身不会更新(一个月看一下吧，如果文档改动大，会修改文档的~)

<table>
  <tr>
    <td> <img src="https://github.com/user-attachments/assets/1cec3e46-de46-4abb-9c9e-20f936f15121" alt="1" width="300px" ></td>
    <td> <img src="https://github.com/user-attachments/assets/d2588204-32db-47c1-9ac5-2d2f71dbb98a" alt="2" width="300px" ></td>
    <td> <img src="https://github.com/user-attachments/assets/94fbd245-655e-4465-a727-950a89ff02c2" alt="3" width="300px" ></td>
   </tr> 
</table>

我们正在制作迪士尼BDX机器人的迷你版本。伸展腿部时，它的高度约为42厘米。
完整的BOM成本应低于400美元！

这个仓库是一个中心枢纽，集中了与该项目相关的所有资源。这是一个工作中的仓库，因此有很多未记录的脚本 :) 我们会在某个时候尝试清理一下。

# 模拟到现实（sim2real）的状态

步态正在变得更好！

https://github.com/user-attachments/assets/5ea58549-78dc-4448-8f86-d3e0499df830

https://github.com/user-attachments/assets/a0afcd38-15d8-40c6-8171-a619107406b8


# 更新

> 2025年3月15日更新：加入我们的Discord服务器以获取帮助或向我们展示你的小鸭 :) https://discord.gg/UtJZsgfQGe

> 2025年2月7日更新：在模拟到现实方面取得了巨大进展，参见上方视频 :)

> 2025年2月24日更新：正在努力研究模拟到现实！

> 2025年2月7日更新：我们正在编写文档，但设计和BOM不应发生剧烈变化。仍然缺少“表情”功能，但可以在构建机器人后添加！

> 2025年1月22日更新：机械设计基本完成（修复了一些错误）。当前版本不包括我们希望在最终机器人中包含的所有“表情”功能（眼睛的LED、摄像头、扬声器和麦克风）。我们现在正致力于通过强化学习使其行走！

# CAD

https://cad.onshape.com/documents/64074dfcfa379b37d8a47762/w/3650ab4221e215a4f65eb7fe/e/0505c262d882183a25049d05

参见[此文档](docs/zh_cn/prepare_robot.md)，了解如何从Onshape设计转换为MuJoCo中的模拟机器人。

> 用现成的朋友可以先跳过，有兴趣可以看下

# 强化学习相关内容

> 译者推荐的

我们正在切换到Mujoco Playground，参见此[仓库](https://github.com/apirrone/Open_Duck_Playground)

https://github.com/user-attachments/assets/293ed5f2-bd24-472e-b44d-c2e4153b8cba

> 译者没跑过

我们仍在使用[AWD](https://github.com/rimim/AWD) 

https://github.com/user-attachments/assets/07059dbe-2ebb-4718-afe7-16ce80691073

## 模仿学习的参考动作生成 

https://github.com/user-attachments/assets/4cb52e17-99a5-47a8-b841-4141596b7afb

参见[此仓库](https://github.com/apirrone/Open_Duck_reference_motion_generator)

> 中文文档在[这里](https://github.com/APX103/Open_Duck_reference_motion_generator)看


## 执行器(Actuator)鉴定(识别？identification)

> 译者注：这里直译有点问题。这个步骤其实是提取我们使用的舵机的各种参数，以更好的在物理仿真中建模，减小sim2real的gap

> 而且该库作者在这里面提了[分支](https://github.com/Rhoban/bam/tree/feetech_sts3215)

> 这个译者没跑过。如果以后会用别的舵机做别的项目的哥们可以看看，我就没翻译中文文档了

我们使用了Rhoban的[BAM](https://github.com/Rhoban/bam)

# 物料清单（BOM）

> 作者在法国，他用的google doc，里面全是aliexpress和亚马逊。我这里做了一个[中国的BOM](https://rua57i3q5t.feishu.cn/sheets/POwpsrCL6hCNG1tDJ4YcbQgOnIv?from=from_copylink)（全TB链接）。不一定用我推荐的，不是最好的，不是最便宜的，有空的朋友可以自己选型一下。只是我用的而已。

https://docs.google.com/spreadsheets/d/1gq4iWWHEJVgAA_eemkTEsshXqrYlFxXAPwO515KpCJc/edit?usp=sharing


# 构建指南

## 打印指南

> 译者注：这里面，在这个版本，暂时没有**眼眶**的stl模型，换句话说，眼睛的亚克力板可能没有那么好装上

参见[打印指南](docs/zh_cn/print_guide.md)。

## 组装指南

参见[组装指南（未完成）](docs/zh_cn/assembly_guide.md)。

# 嵌入式运行时

该仓库包含在板载计算机（Raspberry pi zero 2w）上运行policy的代码：https://github.com/apirrone/Open_Duck_Mini_Runtime

> 中文文档在[这里](https://github.com/APX103/Open_Duck_Mini_Runtime)看

# 训练你自己的策略

当我们获得一个非常稳定且稳健的 walk policy 并能转移到真实机器人时，我们会在这里提供（如果你想尝试，也可以在Discord上请求检查点）。

如果你想训练自己的 policy，并为让小鸭更好地行走做出贡献，请参见[此文档](docs/zh_cn/sim2real.md)
