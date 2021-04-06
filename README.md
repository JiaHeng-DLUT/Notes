# notes

---

precision and recall

| Ground Truth \ Prediction | Positive | Negtive |
| :-----------------------: | :------: | :-----: |
|           True            |    TP    |   TN    |
|           False           |    FP    |   FN    |

$$
\text{precision} = \frac{TP}{TP + FP}
$$

$$
\text{recall} = \frac{TP}{TP + FN}
$$

|   去医院看病    |      |        |      |
| :-------------: | :--: | :----: | :--: |
| 有病，诊断有病  |  TP  | 真阳性 |      |
| 没病，诊断有病  |  FP  | 假阳性 | 误报 |
| 有病，诊断没病  |  FN  | 假阴性 | 漏报 |
| 没病，诊断没病· |  TN  | 真阴性 |      |

---

git

放弃工作区修改，**一定不能忘记--，否则就是切换 branch 了**。

```
git checkout -- filename
```
