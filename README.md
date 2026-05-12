# P2PNet-Soy 大豆种子定位与计数复现

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-1.10+-red.svg)](https://pytorch.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 项目简介

本项目复现论文：

> Zhao J, Kaga A, Hirafuji M, Ninomiya S, Guo W. **Improved Field-Based Soybean Seed Counting and Localization with Feature Level Considered**. *Plant Phenomics*. 2022. https://doi.org/10.34133/plantphenomics.0026

原始代码仓库：https://github.com/UTokyo-FieldPhenomics-Lab/P2PNet-Soy

### 方法概述

P2PNet-Soy 是一种基于点注释的大豆种子定位与计数方法，在原始 P2PNet 基础上进行了以下改进：

- **无监督聚类后处理**：合并过密预测点，减少重复计数
- **多尺度特征融合**：融合低层与高层特征，提升定位精度
- **空洞卷积**：提取尺度不变特征，适应大豆籽粒大小变化
- **注意力机制**：通道与空间注意力，有效分离前景与背景

复现结果：MAE 从原始 P2PNet 的 **105.55** 降低至 **12.94**。

---

## 小组信息

| 成员 | 学号 | GitHub |
|------|------|--------|
| 董帅 | 2025303120177 | [@dongshuai9331](https://github.com/dongshuai9331) |
| 任鹏 | 2025303120002 | [@renpeng-rp916](https://github.com/renpeng-rp916) |
| 张若宇 | 2025303120097 | [@zry0309](https://github.com/zry0309) |
| 陈旭 | 2025303110080 | [@cx20263333333](https://github.com/cx20263333333) |
| 彭钦昊 | 2025303110058 | [@Qinova02](https://github.com/Qinova02) |

---

## 目录结构

```
P2PNet-Soy-reproduction/
├── README.md                    # 项目说明
├── requirements.txt             # Python依赖
├── environment.yml              # Conda环境配置
├── data/
│   └── README.md                # 数据获取说明
├── notebooks/
│   ├── 01_data_exploration.ipynb     # 数据探索与可视化
│   ├── 02_model_inference.ipynb      # 模型推理与预测
│   └── 03_results_analysis.ipynb    # 结果分析与报告
├── src/
│   ├── models/                  # 模型结构代码（来自原仓库）
│   ├── utils/
│   │   ├── data_loader.py       # 数据加载工具
│   │   └── visualization.py    # 可视化工具
│   └── evaluate.py              # 评估指标计算
└── outputs/
    ├── figures/                 # 输出图表
    └── results/                 # 预测结果
```

---

## 快速开始

### 1. 克隆仓库

```bash
git clone https://github.com/D2RS-2026spring/P2PNet-Soy-reproduction.git
cd P2PNet-Soy-reproduction
```

### 2. 配置环境

```bash
# 使用 conda（推荐）
conda env create -f environment.yml
conda activate p2pnet-soy

# 或使用 pip
pip install -r requirements.txt
```

### 3. 准备数据

数据集需向原作者申请，详见 [data/README.md](data/README.md)。

获取数据后，按如下结构放置：

```
data/
├── Soybean_seed_counting/
│   ├── images_a/
│   ├── images_b/
│   ├── labels_a/
│   ├── labels_b/
│   ├── soybean_seed_counting_a.txt
│   └── soybean_seed_counting_b.txt
└── Test_data/
```

### 4. 运行 Notebook

按顺序运行 `notebooks/` 中的三个 Notebook：

```bash
jupyter notebook notebooks/01_data_exploration.ipynb
```

---

## 复现结果

| 指标 | 原文结果 | 复现结果 |
|------|---------|---------|
| MAE  | 12.94   | -       |
| RMSE | -       | -       |
| R²   | -       | -       |

> 复现完成后将更新此表格。

---

## 参考文献

```bibtex
@Article{zhao_P2PNet-Soy_2022,
  AUTHOR  = {Zhao, Jiangsan and Kaga, Akito and Hirafuji, Masayuki 
             and Ninomiya, Seishi and Guo, Wei},
  TITLE   = {Improved infield soybean seed counting and localization 
             with feature level considered},
  JOURNAL = {Plant Phenomics},
  YEAR    = {2022},
  DOI     = {10.34133/plantphenomics.0026}
}
```
