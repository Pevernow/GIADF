# Genshin Impact Auto Domain Fighter(GIADF)
## introduce
This project combines target detection, target tracking models, and some traditional cv algorithms.
Automatically refresh the original mysterious environment, no manual operation is required in the whole process.

The target detection part constructs a monster target detection data set, uses a semi-supervised method to learn (label 5%), and labels pseudo-labels for the entire data set.
The original author's data set was closed 10 months ago, which means that this project only supports Daozuma, and does not support Sumeru and Fontaine Domain for the time being (it may be updated later).

This fork removes useless functions, and replaces the default team to increase damage. (The automatic general attack of skirmishers is very far away, and the range damage)
Packaged weights, resolved and simplified dependencies, improved usage instructions.

The biggest problem at present is not being able to avoid damage. There is no way, it is limited by the project structure.
The ability to resist interruption can only be improved by brushing the shield, otherwise the combat strategy will be affected.

There are plans to port to mmengine2.0 for higher accuracy and efficiency (charging)
Thanks to the original author [SchrödingerのRainbow Cat (7eu7d7)](https://space.bilibili.com/8205465)

### Notice
Genshin Impact requires **1920x1080** resolution to run, other resolutions are not supported. It can be run in windowed mode.

# Pull
```bash
git clone https://github.com/Pevernow/GIADF.git
```
## Install
First install the basic dependencies
##### Does not include Pytorch, please install the appropriate version by yourself
```bash
pip install -r requirements.txt
```

The project has its own weight and can be run directly
## Combat strategy configuration
The default team is 1 Skirmisher, 2 Xingqiu, 3 Noelle, 4 Barbara (please team up in order)
The combat strategy configuration file is in the folder ```control/script/```, there are currently two examples.
Multiple combat strategies can be configured in each file, and a certain cooling time is set for each strategy.
The program will run the strategy that cools down first according to the priority from top to bottom.

If the policy adds
```yaml
type: break
```
field, this strategy has the highest priority, and it will be executed first as long as it is cooled down, and other running strategies can be interrupted.

Supported commands
```
switch 4 #Switch to role 4
delay i #wait for i seconds
key e #Tap the keyboard key e
key down e #Press the keyboard key e and hold
key up e #lift up the keyboard key e
mouse l i #Press the left button for i seconds
mouse r i #Press the right button for i seconds
```

## Tutorial
Start the command line in administrator mode and run the program:
```bash
python auto_domain_fighter.py --cfg control/script/hutao_shatang.yaml
```
Can be replaced with your own team battle strategy file.

Start Genshin Impact, select and enter the domain you want to attack, click anywhere to hide the domain pop-up window, and then press the T key. After a few minutes, you will automatically enter the award receiving interface (the pathfinding has some defects and may cause problems , please wait patiently for one minute or manually go to claim the prize).
Is it very similar to the automatic copybook of the Hoki:Star Rail? Click to start, click t, wait a few minutes, and get a reward.
## 介绍
本项目融合了目标检测，目标跟踪模型，以及一些传统cv算法。
全自动刷原神秘境，全程无需人工操作。

目标检测部分通过构建怪物目标检测数据集，用半监督方法学习(标注5%)，为整个数据集标注伪标签。
原作者数据集截止10个月前，这意味着本项目仅支持到稻妻，暂不支持须弥和枫丹秘境（后续可能会更新）。

本fork去掉了没啥用的功能，并更换默认配队以提升伤害。（散兵自动普攻锁定挺远的，而且范围伤）
打包了权重，解决并简化了依赖问题，改进了使用说明。

目前最大的问题是不会躲伤害，这没办法，受项目架构限制了。
只能通过刷盾提升抗打断能力，不然战斗策略会受影响。

有计划移植到mmengine2.0以获得更高的精确度和效率（代办）
感谢原作者[薛定谔の彩虹猫(7eu7d7)](https://space.bilibili.com/8205465)

### 注意
原神需要以 **1920x1080** 的分辨率运行，不支持其他分辨率。可以窗口化运行。

# 拉取
```bash
git clone https://github.com/Pevernow/GIADF.git
```
## 安装
首先安装基本依赖
##### 不包括Pytorch,请自行安装合适的版本
```bash
pip install -r requirements.txt
```

项目已自带权重，可以直接运行
## 战斗策略配置
默认配队是1散兵2行秋3诺艾尔4芭芭拉（请按顺序配队）
刷本战斗策略配置文件在```control/script/```文件夹内，目前有两个例子。
每个文件内可以配置多条战斗策略，每个策略设置一定冷却时间。
程序会按从上到下的优先级，运行最先冷却完的策略。

如果策略内添加了
```yaml
type: break
```
字段，则这一策略具有最高优先级，只要冷却好就优先执行，可以打断其他正在运行的策略。

支持的指令
```
switch 4 #切换到4号位角色
delay i #等待i秒
key e #敲击键盘按键e
key down e #按下键盘按键e不放
key up e #抬起键盘按键e
mouse l i #按下左键i秒
mouse r i #按下右键i秒
```

## 使用教程
以管理员模式启动命令行，运行程序:
```bash
python auto_domain_fighter.py --cfg control/script/hutao_shatang.yaml
```
可替换成你自己的队伍战斗策略文件。

启动原神，选择并进入你想刷的秘境，单击任意处隐藏秘境弹窗，然后按下t键，等几分钟打完之后，会自动进入领奖界面（寻路有点缺陷可能会日墙，请耐心等待一分钟或手动前往领奖）。
是不是很像星穹铁道的自动刷本？点一下开始，按一下t，等几分钟，领个奖励。
