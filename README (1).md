# 数据说明

## 数据来源

本项目使用的数据集由东京大学 FieldPhenomics Lab 提供，需要向原作者申请获取。

**申请方式：** 访问原始仓库填写表格
https://github.com/UTokyo-FieldPhenomics-Lab/P2PNet-Soy

## 数据结构

下载后请按以下结构放置数据：

```
data/
├── Soybean_seed_counting/       # 训练与验证数据（~400MB）
│   ├── images_a/                # A面拍摄的裁剪图像块（.png）
│   ├── images_b/                # B面拍摄的裁剪图像块（.png）
│   ├── labels_a/                # A面对应的点标注文件（.txt）
│   ├── labels_b/                # B面对应的点标注文件（.txt）
│   ├── soybean_seed_counting_a.txt   # A面数据集索引
│   └── soybean_seed_counting_b.txt   # B面数据集索引
└── Test_data/                   # 独立测试数据（~200MB）
```

## 文件命名规则

图像与标注文件采用相同命名，例如：

```
D12E-D13E_DSC04509_a_1_D13E_a_1.png   ← 图像
D12E-D13E_DSC04509_a_1_D13E_a_1.txt   ← 对应标注
```

命名含义：`{品系编号}_{原始图像名}_{面}_{裁剪序号}_{其他信息}.扩展名`

## 标注格式

每个 `.txt` 标注文件中，每行代表一个大豆种子的点坐标：

```
x1 y1
x2 y2
...
```

## 注意事项

- 数据集较大（总计约 600MB），请勿上传至 GitHub
- 本仓库已在 `.gitignore` 中排除 `data/` 目录下的图像与标注文件
- 小组成员可通过百度网盘共享数据（链接由组长分发）
