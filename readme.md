<div align="center">
     <img alt="img.jpg" height="200" src="avatar.png" width="200"/>
</div>
<h1 align="center">PDB_score</h1>


## 功能
本软件包实现了对多个蛋白模型预测值和实际值的比较，并输出打分，可用于评估预测模型。


## 安装
```
pip install PDB_score
```


## 使用
```aiignore
psc -c /path/to/control -t /path/to/treatment -o /path/to/output
```
- `-c` 实验值 PDB 文件存放目录。
- `-t` 预测值 PDB 文件存放目录。
- `-o` 保存分数的输出目录。

## 输出
/path/to/output/protein_scores.csv

| /        | 1A    | 2A    | ... | 128A  |
|:---------|:------|:------|:----|:------|
| Protein1 | Score | Score | ... | Score |
| Protein2 | Score | Score | ... | Score |
| ...      | ...   | ...   | ... | ...   |

## 计算方法
- 采用 GDT 算法计算分数。
- 去除所有配体，以中心碳原子坐标代表残基坐标。
- 中心碳原子数量不等时，多余的/少的残基直接记为不满足精度要求（无论精度是多少）。



## 其他
- 仅分析输入目录下的 .pdb 文件。
- `-o` 仅指定输出目录，不精确到文件名。
- 输出 .csv 文件，文件名是固定的，请小心不要被覆盖。


## 致谢
- [JetBrains](https://www.jetbrains.com/zh-cn/)
- [ChatGPT](https://www.chatgpt.com)

[@SiriNatsume](https://github.com/SiriNatsume)
祝你愉快 :)