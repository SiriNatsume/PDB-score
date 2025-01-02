<div align="center">
     <img alt="img.jpg" height="200" src="avatar.png" width="200"/>
</div>
<h1 align="center">PDB-score</h1>


## 功能
实现了对大量蛋白模型预测值和实际值的 GDT 方法打分，并计算坐标对齐后的 RMSD，可用于评估预测模型。


## 安装
```
pip install PDB-score
```


## 使用
```aiignore
psc [-h] -c /path/to/control -t /path/to/treatment -o /path/to/output [-T THREAT] [-B BATCH]
```
- `-c` 实验值 PDB 文件存放目录。
- `-t` 预测值 PDB 文件存放目录。
- `-o` 保存分数的输出目录。
- `-T` 指定核心数，默认为 4。
- `-B` 指定 Batch 大小，默认为 5000。

## 输出
/path/to/output/protein_scores.csv

| name     | RMSD         | 1Å    | 2Å    | ... | 128Å  | Average |
|:---------|:-------------|:------|:------|:----|:------|:--------|
| Protein1 | rmsd (float) | Score | Score | ... | Score | Score   |
| Protein2 | rmsd (float) | Score | Score | ... | Score | Score   |
| ...      | ...          | ...   | ...   | ... | ...   | ...     |

## 计算方法
- 使用 Biopython 进行坐标对齐。
- 采用 GDT 算法计算分数。
- 去除所有配体，以中心碳原子坐标代表残基坐标。
- 中心碳原子数量不等时，多余的/少的残基直接记为不满足精度要求（无论精度是多少）。

## 性能表现
- 测试环境
  - 采用默认参数 `-T 4 -B 5000`
  - 测试机器 `Windows 11 PC，CPU Intel 12600k`
  - 单份样品大小 146KB，154 残基
- 比对 50000 份样品用时 387061ms 。
- 内存占用小于 6GB 。


## 其他
- 仅分析两个输入目录下的同名（不含后缀）`.pdb` 和 `.ent` 文件。
- `-o` 仅指定输出目录，不精确到文件名。
- 输出 .csv 文件，文件名是固定的，请小心不要被覆盖。


## 致谢
- [JetBrains](https://www.jetbrains.com/zh-cn/)
- [ChatGPT](https://www.chatgpt.com)

[@SiriNatsume](https://github.com/SiriNatsume)
祝你愉快 :)
