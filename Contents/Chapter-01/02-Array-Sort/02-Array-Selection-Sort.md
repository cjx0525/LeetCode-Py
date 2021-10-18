## 1. 算法思想

> 选择排序（Selection Sort）基本思想：
>
> 第 `i` 趟排序从序列的后 `n − i + 1 (i = 1, 2, …, n − 1)` 个元素中选择一个值最小的元素与该 `n - i + 1` 个元素的最前面那个元素交换位置，即与整个序列的第 `i` 个位置上的元素交换位置。如此下去，直到 `i = n − 1`，排序结束。

可以简述为：每一趟排序中，从剩余未排序元素中选择一个最小的元素，与未排好序的元素最前面的那个元素交换位置。

## 2. 算法步骤

- 在算法中设置整型变量 `i`，既可以作为排序趟数的计算，同时也作为执行第 `i` 趟排序时，参加排序的后 `n − i + 1` 个元素的第 `1` 个元素的位置。
- 整型变量 `min_i` 记录这 `n − i + 1` 个元素中值最小元素的位置。
- 每一趟排序开始，先另 `min_i = i` （即暂时假设序列的第 `i` 个元素为值最小者，以后经过比较后视实际情况再正式确定最小值元素的位置）。
- 第 `i` 趟排序比较结束时，这 `n − i + 1` 个元素中真正的值最小元素由此时的 `min_i` 指出。此时，若有 `min_i == i`，说明值最小元素就是这 `n − i + 1` 个元素的第 `1` 个元素，意味着此趟排序不必进行元素交换。

## 3. 动画演示

![](https://www.runoob.com/wp-content/uploads/2019/03/selectionSort.gif)

## 3. 算法分析

对于具有 `n` 个元素的序列采用选择排序方法要经过 `n - 1` 趟排序。

- 当原始序列是一个按值递增序列（升序）时，元素的移动次数最少，为 `0` 次。当序列初始时是一个按值递减序列（逆序）时，元素的移动次数最多，为 `3(n − 1)` 次（`3` 是交换 `arr[i]` 与 `arr[min_i]` 的执行次数）。
- 但是，无论序列中元素的初始排列状态如何，第 `i` 趟排序要找出值最小元素都需要进行 `n − i` 次元素之间的比较。因此，整个排序过程需要进行的元素之间的比较次数都相同，为 $∑^n_{i=2}(i - 1) = \frac{n(n−1)}{2}$ 次。
- 这说明选择排序法所进行的元素之间的比较次数与序列的原始状态无关，同时可以确定算法的时间复杂度为 $O(n^2)$。
- 由于值最小元素与未排好序的元素中第 `1` 个元素的交换动作是在不相邻的元素之间进行的，因此很有可能会改变值相同元素的前后位置，因此，选择排序法是一种不稳定的排序方法。

## 4. 代码实现

```Python
def selectionSort(arr):
    for i in range(len(arr) - 1):
        # 记录未排序序列中最小数的索引
        min_i = i
        for j in range(i + 1, len(arr)):
            if arr[j] < arr[min_i]:
                min_i = j
        # 如果找到最小数，将 i 位置上元素与最小数位置上元素进行交换
        if i != min_i:
            arr[i], arr[min_i] = arr[min_i], arr[i]
    return arr
```
