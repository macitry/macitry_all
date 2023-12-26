# 教程
## PC端训练环境配置
1.anaconda 创建环境--此处创建python版本为3.9

2.安装pytorch以及cuda 命令如下

```c
pip install torch==1.10.2+cu102 torchvision==0.11.3+cu102 torchaudio==0.10.2 --extra-index-url https://download.pytorch.org/whl/cu102
```

3.使用cd命令到 yolov5_lite安装路径下
注意查看该路径下是否存在requirements.txt文件，该文件是此项目所需的依赖包清单

4.运行以下命令

```c
pip install -r requirements.txt
```

5.运行出现以下错误，请输入以下指令，更改numpy版本

AttributeError: module ‘numpy‘ has no attribute ‘int‘.

```c
pip uninstall numpy
pip install numpy==1.23.4 -i https://pypi.tuna.tsinghua.edu.cn/simple/
```

6.安装onnx模型转换包

```c
pip install onnx
```

7.运行权重文件转换命令

```c
python export.py --weights best_lite_wight.pt
```
