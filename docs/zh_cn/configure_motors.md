# 舵机配置

> 原文是使用[Runtime](https://github.com/apirrone/Open_Duck_Mini_Runtime)来配置的。但既然是中文教程，自然会有些属于中国人的福利
>
> 重点说前面。我们选的舵机是 7.4v 的，别用12v电源供电。用8v的。

## 使用Runtime库的工具配置

克隆（git clone）[Runtime](https://github.com/apirrone/Open_Duck_Mini_Runtime) 库，切换到 `v2` 分支，切换到你的python环境（最好还是不要污染了其他python环境，有条件的朋友可以用venv或conda），执行 `pip install -e .` 安装

您可以根据需要将其安装在自己的PC上，也可以安装在 Raspberry Pi 上进行配置。

舵机将会被安装到舵机控制板上设置，舵机控制板本身需要供电(2s)。可以考虑先将鸭子的后盖组装好（带电池），用后盖供电。

``` shell
# 这是给装在PC上的朋友写的。如果是装树莓派，按照 Open_Duck_Mini_Runtime 的 README.md 中安装runtime的方式安装即可
conda create -n open_duck_mini_runtime
conda activate open_duck_mini_runtime
git clone https://github.com/apirrone/Open_Duck_Mini_Runtime
cd Open_Duck_Mini_Runtime
pip install -e .
```

将舵机控制板连上你的树莓派或PC。

将每个舵机单个安装到舵机控制板上，并执行以下命令:

```bash
python configure_motor.py --id <id>
```

其中，<id> 是该舵机应该指定的id，对应不同位置的舵机的id按照如下字典配置即可：

```python
{
    "left_hip_yaw": 20,
    "left_hip_roll": 21,
    "left_hip_pitch": 22,
    "left_knee": 23,
    "left_ankle": 24,
    "neck_pitch": 30,
    "head_pitch": 31,
    "head_yaw": 32,
    "head_roll": 33,
    "right_hip_yaw": 10,
    "right_hip_roll": 11,
    "right_hip_pitch": 12,
    "right_knee": 13,
    "right_ankle": 14,
}
```

> 这里设置的id最好是设置得和上文中一样。
> 
> 如果有修改，在运行算法时就需要修改Runtime中的硬件接口（HWI）相关的代码映射。比较麻烦，对新手来说也不方便debug，所以还是按照建议设置id为妙。

## 使用FD修改

需要将舵机控制板连接到你的 Windows PC，并上电（电池或者其他2s的电源）
