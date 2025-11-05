# Paddel_detection_manual

**文档版本**: v0.1  
**最后更新**: 2025-10-31  
**维护者**: Willie Chen 

**修訂歷史**
| 版本 | 日期 | 作者 | 修订内容 |
| V0.1 | 2025-10-11 | Willie Chen | 建立 |
| V0.2 | 2025-10-31 | Willie Chen | 更新PaddleDetection部署流程 |

## 目錄
-[目錄](#目錄)
-[簡介](#1.簡介)
-[安裝與部屬](#2安裝與部屬)



## 1.簡介

### 軟件目的
視覺檢測

### 主要功能
- 模型訓練
參考 ![PaddelDetection](https://github.com/PaddlePaddle/PaddleDetection) github



## 2.安裝與部屬
參考 ![PaddelDetection](https://github.com/PaddlePaddle/PaddleDetection) github

1. 安裝 Conda
如果尚未安裝 Conda，請先下載安裝：
-[Miniconda](https://www.anaconda.com/)

安裝時務必勾選：
✅ Add Anaconda to my PATH environment variable
✅ Register Anaconda as my default Python 3.x

2. 建立 Conda 環境
```
# 開啟命令提示字元

# 建立新的 conda 環境 (使用 Python 3.8，與 PaddlePaddle 兼容性好)
conda create -n paddledet python=3.8

# 啟動環境
conda activate paddledet
```

3. 安裝 PaddlePaddle
```
# 安裝GPU版本 PaddlePaddle
pip install paddlepaddle-gpu--2.6.2 -f https://www.paddlepaddle.org.cn/whl/whindows/mkl/avx/stable.html
```
更多CUDA版本或环境快速安装，请参考[PaddlePaddle快速安装文档](https://www.paddlepaddle.org.cn/install/quick)
更多安装方式例如conda或源码编译安装方法，请参考[PaddlePaddle安装文档](https://www.paddlepaddle.org.cn/documentation/docs/zh/install/index_cn.html)

请确保您的PaddlePaddle安装成功并且版本不低于需求版本。使用以下命令进行验证。
```
# 在您的Python解释器中确认PaddlePaddle安装成功
>>> import paddle
>>> paddle.utils.run_check()

# 确认PaddlePaddle版本
python -c "import paddle; print(paddle.__version__)"
```

4. 安裝 VS Code 與必要擴充功能
下載並安裝 [VS Code](https://code.visualstudio.com/)
如果有偏好的ODE可以忽略
请确保您的VS code安装成功
```
```

```
# 安裝GPU版本 PaddlePaddle
pip install paddlepaddle-gpu--2.5.0.post114 -f https://www.paddlepaddle.org.cn/whl/whindows/mkl/avx/stable.html
```


```
# 克隆PaddleDetection倉庫
cd <path/to/clone/PaddleDetection>
git clone https://github.com/PaddlePaddle/PaddleDetection.git

# 安裝其他依賴
cd PaddleDetection
pip install -r requirements.txt -i https://mirrors.aliyun.com/pypi/simple/

# 編譯安裝paddledet
python setup.py install
```




## 3.使用說明 (主要部分)

### 數據導入

圖片獲取
缺陷標籤標注


### 模型選擇與配置

缺陷檢測可使用優先使用 ppyoloe_plus_crn_l_60e_objects365



### 

1. 模型訓練

windows训练命令
```
python tools/train.py -c configs/ppyoloe/objects365/ppyoloe_plus_crn_l_60e_objects365.yml --eval --use_vdl=true --vdl_log_dir=vdl_dir/current -o use_gpu=true
```


模型導出命令
```
python tools/export_model.py -c configs/ppyoloe/objects365/ppyoloe_plus_crn_l_60e_objects365.yml --output_dir=./inference_model \ -o weights=output\best_model\model.pdparams
```

预测命令
```
python deploy/python/infer.py --model_dir=output/inference_model/ppyoloe_plus_crn_l_60e_objects365 --image_dir=dataset/voc/images --device=GPU
```

日志可视化

```
visualdl --logdir (dir path)
```



## 5.配置说明




## 6.常见问题与故障排除

Q： pip 下載速度過慢 

A：改其他鏡像位置
清華 
```
-i https://pypi.tuna.tsinghua.edu.cn/simple  

# 清华大学
pip <your_installing_file> -i https://pypi.tuna.tsinghua.edu.cn/simple

# 阿里云
pip <your_installing_file> -i https://mirrors.aliyun.com/pypi/simple/

# 豆瓣
pip <your_installing_file> -i https://pypi.douban.com/simple/
```



## 7.获取帮助

遇到問題 從![PaddelDetection](https://github.com/PaddlePaddle/PaddleDetection) github 找尋

如果需要幫助請聯繫




