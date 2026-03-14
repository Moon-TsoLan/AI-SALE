# AI-SALE: 基于AI的商品属性与销售关联系统

## 项目概述

本项目旨在开发一个基于人工智能的商品属性与销售关联分析系统，通过深度学习技术提取商品属性特征，并建立与销售数据的关联模型。

## 技术栈

根据规则R1的技术栈约束：

- **BERT相关**：使用 bert-base-chinese 作为预训练模型
- **CNN相关**：使用 ResNet 预训练模型（ResNet50/ResNet101）
- **深度学习框架**：PyTorch（BERT部分），TensorFlow/Keras（CNN部分）
- **机器学习**：Scikit-learn 实现回归分析和决策树
- **可解释性**：SHAP 和 LIME 库
- **可视化**：Matplotlib（静态）、Seaborn（统计）、Plotly（交互式）

## 项目结构

```
AI-SALE/
│
├── data/                           # 数据目录
│   ├── raw/                        # 原始数据
│   ├── processed/                  # 清洗后的数据
│   └── features/                   # 提取的特征
│
├── models/                         # 模型目录
│   ├── bert/                       # BERT相关模型
│   ├── cnn/                        # CNN相关模型
│   ├── ml/                         # 机器学习模型
│   └── checkpoints/                # 模型检查点
│
├── notebooks/                      # Jupyter notebooks
├── src/                            # 源代码目录
├── utils/                          # 工具目录
├── tests/                          # 测试目录
└── outputs/                        # 输出目录
```

## 快速开始

### 1. 环境配置

```bash
# 安装依赖
pip install -r requirements.txt

# 或者使用conda
conda create -n ai-sale python=3.9
conda activate ai-sale
pip install -r requirements.txt
```

### 2. 数据准备

将原始数据放置在 `data/raw/` 目录下：
- `products.csv` - 商品属性数据
- `images/` - 商品图片
- `sales.csv` - 销售数据

### 3. 运行流程

按照以下顺序执行notebooks：

1. `01_data_exploration.ipynb` - 数据探索
2. `02_data_preprocessing.ipynb` - 数据清洗
3. `03_bert_training.ipynb` - BERT特征提取
4. `04_cnn_training.ipynb` - CNN特征提取
5. `05_feature_mapping.ipynb` - 特征映射
6. `06_association_model.ipynb` - 关联模型
7. `07_model_explanation.ipynb` - 模型解释
8. `08_visualization.ipynb` - 可视化

## 开发规范

### 代码质量（规则R2）
- 所有代码必须包含类型提示（type hints）
- 关键函数必须添加文档字符串（docstrings）
- 使用相对路径而非绝对路径
- 数据处理代码必须包含异常处理

### 数据处理（规则R4）
- 数据清洗必须处理：缺失值、异常值、重复数据、数据格式统一
- 文本预处理：分词、去除停用词、统一编码（UTF-8）
- 图像预处理：统一尺寸、归一化

### 模型开发（规则R5）
- BERT模型采用 Fine-tuning 方式
- CNN模型冻结预训练层的前N层，微调后续层
- 回归模型必须进行特征标准化
- 决策树模型必须设置超参数防止过拟合

## 输出结果

项目将生成以下输出：
- 特征分布图和重要性排序图
- 销量预测 vs 实际销量散点图
- SHAP 摘要图和 LIME 局部解释图
- 商品属性-销售关联热力图
- 模型性能对比报告

## 许可证

本项目仅供学术研究使用。