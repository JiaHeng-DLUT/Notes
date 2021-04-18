# mAP

- mean average precision
- 目标检测常用指标之一

### To calculate mAP, we need to know what AP is.

mAP 就是不同 IoU threshold 下，AP 的平均值，CoCo 取 [0.50:0.05:0.95]。

### To know what AP is, we need to know what P-R curve is.

AP 就是 P-R curve 与 X 轴和 Y 轴围成的面积，为计算面积，一般使用插值的方法，CoCo 取 [0:0.01:1]，共 101 个点，插值得到的 precision 为大于等于当前 recall 的最大 precision。

### To know what P-R curve is, we need to know what precision and recall are.

规定：

- `all detetections`: 所有检测框的数量
- `all ground truths`: 所有 GT 的数量

则有：

- 查准率 $\text{precision} = \frac{TP}{TP + FP}=\frac{TP}{\text{all detections}}$
- 查全率 $\text{recall} = \frac{TP}{TP + FN}=\frac{TP}{\text{all ground truths}}$

1. 当 IoU threshold 固定时，比如 IoU threshold = 0.5，所有的预测框都可以被分成 TP 和 FP 两大类：对于某个 GT，将 IoU 最大且 >= threshold 的预测框标记为 TP，其他的标记为 FP，即一个 GT 至多只能有一个预测框标记为 TP。
2. 每个预测框都有一个置信度（confidence），我们根据置信度进行排序，选择预测框，可以得到不同的 (recall, precision)，然后 recall 作为自变量，precision 作为因变量，画出折线图，即可得到 P-R curve。

### To know what precision and recall are, we need to know what TP, FP, FN and TN are.

ground truth (GT)

|     目标检测     |              |        |                                                          |
| :--------------: | :----------: | :----: | :------------------------------------------------------: |
| IoU > threshold  |      TP      | 真阳性 |                    同一 GT 只计算一次                    |
| IoU <= threshold | FP<br />误报 | 假阳性 | IoU <= threshold 的检测框数量 + 同一 GT 多余的检测框数量 |
| IoU > threshold  | FN<br />漏报 | 假阴性 |                   没有检测到的 GT 数量                   |
| IoU > threshold  |      TN      | 真阴性 |                   计算 mAP 时不会使用                    |

## References

1. [目标检测中的mAP是什么含义？ - AICV的回答 - 知乎](https://www.zhihu.com/question/53405779/answer/993913699)

