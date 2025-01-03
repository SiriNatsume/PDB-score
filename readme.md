<div align="center">
     <img alt="img.jpg" height="200" src="avatar.png" width="200"/>
</div>
<h1 align="center">PDB-score</h1>

[中文文档请点击](https://github.com/SiriNatsume/PDB-score/blob/master/readme-zh.md)

## Features
Implemented GDT scoring for a large number of predicted and actual protein models, along with calculating RMSD after coordinate alignment, which can be used to evaluate the prediction models.

## Installation
```
pip install PDB-score
```

## Usage
```aiignore
psc [-h] -c /path/to/control -t /path/to/treatment -o /path/to/output [-T THREAT] [-B BATCH]
```
- `-c` Directory where the experimental PDB files are stored.
- `-t` Directory where the predicted PDB files are stored.
- `-o` Directory for saving the output scores.
- `-T` Specify the number of cores, default is 4.
- `-B` Specify the Batch size, default is 5000.

## Output
/path/to/output/protein_scores.csv

| name     | RMSD         | 1A    | 2A    | ... | 128A  | Average |
|:---------|:-------------|:------|:------|:----|:------|:--------|
| Protein1 | rmsd (float) | Score | Score | ... | Score | Score   |
| Protein2 | rmsd (float) | Score | Score | ... | Score | Score   |
| ...      | ...          | ...   | ...   | ... | ...   | ...     |

## Calculation Method
- Perform coordinate alignment using Biopython.
- Scores are calculated using the GDT (Global Distance Test) algorithm.
- All ligands are removed, and only the alpha carbon atoms are used to represent the residue coordinates.
- When the count of alpha carbons differs, the extra or missing residues are directly considered as failing to meet the accuracy criteria (regardless of the accuracy setting).

## Performance
- Test Environment:
  - Default parameters: `-T 4 -B 5000`
  - Test Machine: `Windows 11 PC, CPU Intel 12600k`
  - Single sample size: 146KB with 154 residues
- Comparing 50,000 samples took 387061ms.
- Memory usage is less than 6GB.

## Additional Notes
- Only analyze `.pdb` and `.ent` files with the same name (excluding extensions) in the two input directories.
- The `-o` option only specifies the output directory, not the file name.
- Outputs a `.csv` file with a fixed file name, so be careful not to overwrite it.

## Acknowledgments
- [JetBrains](https://www.jetbrains.com/)
- [ChatGPT](https://www.chatgpt.com)

[@SiriNatsume](https://github.com/SiriNatsume)  
Wishing you happiness :)