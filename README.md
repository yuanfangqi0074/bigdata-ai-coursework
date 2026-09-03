# Big Data & AI Coursework

大数据与人工智能课程作业仓库。

## 仓库结构

| 目录 | 内容 |
|---|---|
| `01-大数据基础/` | Hadoop / HDFS / MapReduce / Spark 相关作业 |
| `02-机器学习/` | 特征工程、经典机器学习算法实现与调优 |
| `03-深度学习/` | 神经网络、CNN / RNN / Transformer 相关作业 |
| `04-综合项目/` | 期末综合项目 |
| `notebooks/` | Jupyter 实验记录 |
| `docs/` | 实验报告（含报告模板） |

## 环境准备

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## 命名约定

- 作业目录：`01-大数据基础/hw1-wordcount/`
- 报告文件：`docs/hw1-实验报告.md`
- 数据文件：小体积样本入仓库，大数据集放 `data/` 并在 `.gitignore` 中排除

## 常用命令备忘

```bash
git status              # 看当前改动
git add .               # 暂存全部改动
git commit -m "说明"     # 提交
git push                # 推送到 GitHub
git pull                # 拉取远端更新
```
