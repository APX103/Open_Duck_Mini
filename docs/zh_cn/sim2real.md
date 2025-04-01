> 尚未最终确定

# 训练可迁移到真实机器人上的策略（sim2real）

我们希望训练能够很好地迁移到真实机器人上的策略。这就是所谓的 sim2real 问题。这是一个很难的问题，尤其是对我们来说，因为我们使用的是难以建模且性能并不十分强大的廉价伺服电机。

下面，我将大致解释我们为实现这一目标所经历的步骤，但你不必重新做所有的事情，因为我们提供了每个过程的结果。

## 创建机器人的精确模型 (URDF/MJCF)

### 机器人结构

在 [Onhape 文档](https://cad.onshape.com/documents/64074dfcfa379b37d8a47762/w/3650ab4221e215a4f65eb7fe/e/0505c262d882183a25049d05) 中，我们指定了每个部分的材料。为了更精确，由于我们打印时使用填充物，我们用切片机的（相当准确的）估算值覆盖了部件的质量。

我们使用 [onshape-to-robot](https://github.com/Rhoban/onshape-to-robot) 导出 URDF/MJCF 描述。对于 MJX，我们需要创建一个轻量级模型，参见我们的 [config.json](https://github.com/apirrone/Open_Duck_Playground/blob/main/playground/open_duck_mini_v2/xmls/config.json)。

这为我们提供了一个 MJCF（Mujoco 格式）[机器人的描述](https://github.com/apirrone/Open_Duck_Playground/blob/main/playground/open_duck_mini_v2/xmls/open_duck_mini_v2.xml)，它描述了整个机器人的质量和惯性矩。

### 电机

拥有精确模型的另一个非常重要的部分是建模电机的行为。我们使用 [BAM](https://github.com/Rhoban/bam/) 来完成这一任务。你不需要自己进行识别过程，我们已经提供了结果 [在这里](https://github.com/Rhoban/bam/tree/main/params/feetech_sts3215_7_4V)。

模拟器精确地模拟电机行为至关重要，因为我们将训练一个策略（神经网络），根据传感器输入（电机位置/速度、IMU 和脚部传感器）输出电机位置。如果电机在仿真中的行为与现实世界不同，策略将无法正常工作，或者最坏的情况是产生混乱的动作。

`BAM` 允许我们将主要识别参数导出为 Mujoco 单位（使用 `bam.to_mujoco`）。这些值是我们设置在 MJCF 模型中用于执行器和关节属性的值。

- 阻尼 (damping)
- 比例增益 (kp)
- 摩擦损失 (frictionloss)
- 电枢 (armature)
- 力范围 (forcerange)

## 训练策略

我们使用基于自己的 [mujoco playground](https://github.com/google-deepmind/mujoco_playground) 框架，[Open Duck Playground](https://github.com/apirrone/Open_Duck_Playground)

在 [joystick](https://github.com/apirrone/Open_Duck_Playground/blob/main/playground/open_duck_mini_v2/joystick.py) 环境中，你可以尝试启用/禁用不同的奖励，编写自己的奖励，调整权重、噪声、随机化等。

我们通过实现迪士尼在其 [BDX 论文](https://github.com/apirrone/Open_Duck_Playground/blob/main/playground/open_duck_mini_v2/joystick.py) 中描述的模仿奖励获得了良好的结果。

要使用此奖励，我们需要参考运动。我们创建了 [这个仓库](https://github.com/apirrone/Open_Duck_reference_motion_generator) 使用参数化行走引擎生成此类运动。按照那里的说明，你可以生成一个包含参考运动的 `polynomial_coefficients.pkl` 文件。在 playground 仓库的 `data/` 目录下已经有这样一个文件。

一旦你的策略训练完成，你可以尝试使用 runtime 仓库中的 [这个脚本](https://github.com/apirrone/Open_Duck_Mini_Runtime/blob/v2/scripts/v2_rl_walk_mujoco.py) 在真实机器人上运行它。在运行之前，请确保你已完成 [检查清单](https://github.com/apirrone/Open_Duck_Mini_Runtime/blob/v2/checklist.md) 中的所有步骤。
