# 训练相关基本操作
## 环境
+ python
+ torch
+ 其他
```
pip install -r requirements.txt -i  https://pypi.tuna.tsinghua.edu.cn/simple

```
+ 注意torch不能1.12.0，torchvision不能0.13.0,requirements里面有注明
+ numpy在1.24以上没有int，改为inf，所以要么用1.23，要么手动改inf
## 数据集
+ 数据格式，与yolov5相同
```
├── images
│   ├── train
│   └── val
└── labels
    ├── train
    └── val

```
## 命令行执行
### 训练必用train.py
+ --weights 默认yolo7.pt迁移学习，自动下载，输入false则默认加载--cfg中的配置文件
+ --cfg 默认在cfg/training文件夹下找yaml文件，修改yaml文件实现多种模型子模块的增删改查
+ --data 数据集加载，默认data文件夹下找yaml文件
+ --hyp 超参，默认data文件夹下找yaml
+ --epochs 训练代数
+ --batch-size 视显存大小而定
+ --img-size 训练尺度
+ --resume 断点重训
+ --device gpu数量
+ --workers 0肯定可以，其他数值请自行尝试
### 辅助检测分支train_aux.py
+ 用于大输入尺度
+ 提高检测精度和召回率

### 验证必用test.py
+ --weights 想要验证的权重文件地址
+ --data 数据集加载，默认data文件夹下找yaml文件
+ --batch-size 视验证目标而定
+ --img-size 测试尺度
+ --conf-thres 置信度阈值，影响较大
+ --iou-thres iou阈值
+ --task 主要用val、test、speed
+ --device gpu数量


### 推理必用detect.py
+ --weights 想要推理的权重文件地址
+ --source 想要推理的目录，可以是图片、视频、文件夹、屏幕、摄像头
+ --img-size 推理尺度
+ --conf-thres 置信度阈值，影响较大
+ --iou-thres iou阈值
+ --device gpu数量
+ --nosave 不保存

### 导出必用export.py
+ --weights 想要导出的权重地址
+ --img-size 导出尺度
+ --batch-size 导出尺度
+ --dynamic 动态导出
+ --end2end 端到端导出
+ --conf-thres 置信度阈值，影响较大
+ --iou-thres iou阈值
+ --device gpu数量
+ --simplify 调用onnx-simplify进行简化


# 代码基础介绍
## cfg 模型yaml
### baseline基准模型
### deploy部署模型
### training训练模型
## data数据 yaml
## deploy triton推理支持
## models
### common.py主要子模块
### yolo.py主要调用类
## utils 主要工具
