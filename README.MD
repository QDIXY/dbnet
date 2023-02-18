# 深度学习课程设计--第八组

## 数据集预处理
将下载的数据集导入并解压在./datasets文件夹下，并用data_ycl.py进行数据集划分与归纳。
数据集经过data_ycl.py运行并将训练集和验证集的图片和标签以./datasets/image_train/T1.AK_XX8hXXbnu_Z1_042512.jpg.jpg	./datasets/txt_train/T1.AK_XX8hXXbnu_Z1_042512.jpg.txt的格式分别存入train.txt和test.txt中。

## 环境配置
```bash
conda create -n dbnet python=3.6
conda activate dbnet
conda install ipython pip
pip install -r requirement.txt
conda install pytorch torchvision cudatoolkit=10.1 -c pytorch

```
## 模型训练参数修改
在config/icdar2015_resnet18_FPN_DBhead_polyLR.yaml配置文件中修改参数（优化器、迭代次数......)

## 模型训练
运行指令
```bash
python tools/train.py --config_file "config/icdar2015_resnet18_FPN_DBhead_polyLR.yaml"
```

## 模型评估
运行指令
```bash
CUDA_VISIBLE_DEVICES=0 python3 tools/eval.py --model_path 'output/DBNet_resnet18_FPN_DBHead/checkpoint/model_latest.pth'(模型可改为model_best.pth)
```

## 模型预测
运行指令
```
python  'tools/predict.py'  --model_path  'output/DBNet_resnet18_FPN_DBHead/checkpoint/model_latest.pth'  --input_folder  'datasets/icpr_mtwi_task2/image_test' --output_folder  'output/DBNet_resnet18_FPN_DBHead/result'

```


 