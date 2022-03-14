# java面试题集合
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说下你熟悉的排序算法**排序算法属于经典基础算法基本功**，笔试面试基本都会涉及和考察的，有原题也有变化，不过基础的几大排序算法还是得尽可能熟悉，能在思路熟悉的前提下手写出代码就更好了。  

### **0、排序算法说明**

#### 0.1 **排序的定义**

对一序列对象根据某个关键字进行排序。

**0.2 术语说明**

*   **稳定**：如果a原本在b前面，而a=b，排序之后a仍然在b的前面；
    
*   **不稳定**：如果a原本在b的前面，而a=b，排序之后a可能会出现在b的后面；
    
*   **内排序**：所有排序操作都在内存中完成；
    
*   **外排序**：由于数据太大，因此把数据放在磁盘中，而排序通过磁盘和内存的数据传输才能进行；
    
*   **时间复杂度：** 一个算法执行所耗费的时间。
    
*   **空间复杂度**：运行完一个程序所需内存的大小。
    

#### 0.3 算法总结

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X3BuZy9saWJZUnV2VUxUZFhhc0NyRmRUWlYyVm5ERk5yUEE3SmlhT0ljVzkzVjZQRkp6TmU0aWFzeElwYVp0MW5UVG0wYlRLRDRZSGljMk1Qd1UzUXh1aWJ4aHlzclJBLzY0MA?x-oss-process=image/format,png "img")

**图片名词解释：**

*   n: 数据规模
    
*   k: “桶”的个数
    
*   In-place: 占用常数内存，不占用额外内存
    
*   Out-place: 占用额外内存
    

#### 0.5 算法分类

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X3BuZy9saWJZUnV2VUxUZFhhc0NyRmRUWlYyVm5ERk5yUEE3SmlhOTVLNkRvcDNvaWNiT0dpYmt6Unh6aWJHQjFXbUlRU0g2alV0NHV2ZUtadVpqbTh4N2taSEo5VWt3LzY0MA?x-oss-process=image/format,png "img")

#### 比较和非比较的区别

常见的**快速排序、归并排序、堆排序、冒泡排序**等属于**比较排序**。**在排序的最终结果里，元素之间的次序依赖于它们之间的比较。每个数都必须和其他数进行比较，才能确定自己的位置。**  
在**冒泡排序**之类的排序中，问题规模为n，又因为需要比较n次，所以平均时间复杂度为O(n²)。在**归并排序、快速排序**之类的排序中，问题规模通过**分治法**消减为logN次，所以时间复杂度平均**O(nlogn)**。  
比较排序的优势是，适用于各种规模的数据，也不在乎数据的分布，都能进行排序。可以说，**比较排序适用于一切需要排序的情况。**

**计数排序、基数排序、桶排序**则属于**非比较排序**。非比较排序是通过确定每个元素之前，应该有多少个元素来排序。针对数组arr，计算arr\[i\]之前有多少个元素，则唯一确定了arr\[i\]在排序后数组中的位置。  
非比较排序只要确定每个元素之前的已有的元素个数即可，所有一次遍历即可解决。算法时间复杂度**O(n)**。  
**非比较排序时间复杂度底，但由于非比较排序需要占用空间来确定唯一位置。所以对数据规模和数据分布有一定的要求**。

### 1、冒泡排序（Bubble Sort）

冒泡排序是一种简单的排序算法。它重复地走访过要排序的数列，一次比较两个元素，如果它们的顺序错误就把它们交换过来。走访数列的工作是重复地进行直到没有再需要交换，也就是说该数列已经排序完成。这个算法的名字由来是因为越小的元素会经由交换慢慢`浮`到数列的顶端。

#### 1.1 算法描述

*   比较相邻的元素。如果第一个比第二个大，就交换它们两个；
    
*   对每一对相邻元素作同样的工作，从开始第一对到结尾的最后一对，这样在最后的元素应该会是最大的数；
    
*   针对所有的元素重复以上的步骤，除了最后一个；
    
*   重复步骤1~3，直到排序完成。
    

**1.2 动图演示**

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2dpZi9saWJZUnV2VUxUZFhhc0NyRmRUWlYyVm5ERk5yUEE3SmlhazRkSFFEUE52a3poQlo1MnRqaWFOYVRsU2ppYjM4UmxhaWFKTVNlRUdCdGs1ZWhWMjJiS1VzcUlRLzY0MA?x-oss-process=image/format,png)

#### 1.3 代码实现  

```
/**
     * 冒泡排序
     *
     * @param array
     * @return
     */
public static int[] bubbleSort(int[] array) {
  if (array.length == 0)
    return array;
  for (int i = 0; i < array.length; i++)
    for (int j = 0; j < array.length - 1 - i; j++)
      if (array[j + 1] < array[j]) {
        int temp = array[j + 1];
        array[j + 1] = array[j];
        array[j] = temp;
      }
  return array;
}
 
```

#### 1.4 **算法分析**

**最佳情况：T(n) = O(n) 最差情况：T(n) = O(n2) 平均情况：T(n) = O(n2)**

### 2、选择排序（Selection Sort）

表现**最稳定的排序算法之一**，因为**无论什么数据进去都是 O(n2) 的时间复杂度**，所以用到它的时候，数据规模越小越好。唯一的好处可能就是不占用额外的内存空间了吧。理论上讲，选择排序可能也是平时排序一般人想到的最多的排序方法了吧。

`选择排序(Selection-sort)` 是一种简单直观的排序算法。它的工作原理：首先在未排序序列中找到最小（大）元素，存放到排序序列的起始位置，然后，再从剩余未排序元素中继续寻找最小（大）元素，然后放到已排序序列的末尾。以此类推，直到所有元素均排序完毕。

#### 2.1 算法描述

n 个记录的直接选择排序可经过n-1趟直接选择排序得到有序结果。具体算法描述如下：

*   初始状态：无序区为R\[1..n\]，有序区为空；
    
*   第i趟排序(i=1,2,3…n-1)开始时，当前有序区和无序区分别为R\[1..i-1\]和R(i..n）。该趟排序从当前无序区中-选出关键字最小的记录 R\[k\]，将它与无序区的第1个记录R交换，使R\[1..i\]和R\[i+1..n)分别变为记录个数增加1个的新有序区和记录个数减少1个的新无序区；
    
*   n-1趟结束，数组有序化了。
    

#### **2.2 动图演示**

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2dpZi9saWJZUnV2VUxUZFhhc0NyRmRUWlYyVm5ERk5yUEE3SmlhRkVSY0xxVFN3a0JHRnpIRmJ6M2FDdE9jclFSUEJ0UTdmSmRkS0RPejNaZEgxYVBtVmMxTldnLzY0MA?x-oss-process=image/format,png)

#### 2.3 代码实现

```
/**
     * 选择排序
     * @param array
     * @return
     */
public static int[] selectionSort(int[] array) {
  if (array.length == 0)
    return array;
  for (int i = 0; i < array.length; i++) {
    int minIndex = i;
    for (int j = i; j < array.length; j++) {
      if (array[j] < array[minIndex]) //找到最小的数
        minIndex = j; //将最小数的索引保存
    }
    int temp = array[minIndex];
    array[minIndex] = array[i];
    array[i] = temp;
  }
  return array;
}
 
```

#### 2.4 **算法分析**

**最佳情况：T(n) = O(n2) 最差情况：T(n) = O(n2) 平均情况：T(n) = O(n2)**

### 3、插入排序（Insertion Sort）

`插入排序（Insertion-Sort）`的算法描述是一种简单直观的排序算法。它的工作原理是通过构建有序序列，对于未排序数据，在已排序序列中从后向前扫描，找到相应位置并插入。插入排序在实现上，通常采用 in-place 排序（即只需用到O(1)的额外空间的排序），因而在从后向前扫描过程中，需要反复把已排序元素逐步向后挪位，为最新元素提供插入空间。

#### 3.1 算法描述

一般来说，插入排序都采用 in-place 在数组上实现。具体算法描述如下：

*   从第一个元素开始，该元素可以认为已经被排序；
    
*   取出下一个元素，在已经排序的元素序列中从后向前扫描；
    
*   如果该元素（已排序）大于新元素，将该元素移到下一位置；
    
*   重复步骤3，直到找到已排序的元素小于或者等于新元素的位置；
    
*   将新元素插入到该位置后；
    
*   重复步骤2~5。
    

#### 3.2 动图演示

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2dpZi9saWJZUnV2VUxUZFhhc0NyRmRUWlYyVm5ERk5yUEE3SmlhaGljMmlhZjJZWkVqU2ljRkNBcXdUTWdOTGVQOTlLcVlJUmhzekl0VDF5RFVsczZpYWJhREtWT29WZy82NDA?x-oss-process=image/format,png)

#### 3.2 代码实现

```
/**
     * 插入排序
     * @param array
     * @return
     */
public static int[] insertionSort(int[] array) {
  if (array.length == 0)
    return array;
  int current;
  for (int i = 0; i < array.length - 1; i++) {
    current = array[i + 1];
    int preIndex = i;
    while (preIndex >= 0 && current < array[preIndex]) {
      array[preIndex + 1] = array[preIndex];
      preIndex--;
    }
    array[preIndex + 1] = current;
  }
  return array;
}
 

```
#### 3.4 **算法分析**

**最佳情况：T(n) = O(n) 最坏情况：T(n) = O(n2) 平均情况：T(n) = O(n2)**

### 4、希尔排序（Shell Sort）

希尔排序是`希尔（Donald Shell）`于1959年提出的一种排序算法。希尔排序也是一种插入排序，它是简单插入排序经过改进之后的一个更高效的版本，也称为缩小增量排序，同时该算法是冲破 O(n2）的第一批算法之一。它与插入排序的不同之处在于，它会优先比较距离较远的元素。希尔排序又叫缩小增量排序。

**希尔排序是把记录按下表的一定增量分组，对每组使用直接插入排序算法排序；随着增量逐渐减少，每组包含的关键词越来越多，当增量减至1时，整个文件恰被分成一组，算法便终止。**

#### 4.1 算法描述

我们来看下希尔排序的基本步骤，在此我们选择增量 gap=length/2，缩小增量继续以 gap = gap/2 的方式，这种增量选择我们可以用一个序列来表示，**{n/2,(n/2)/2…1}**，称为**增量序列**。希尔排序的增量序列的选择与证明是个数学难题，我们选择的这个增量序列是比较常用的，也是希尔建议的增量，称为希尔增量，但其实这个增量序列不是最优的。此处我们做示例使用希尔增量。

先将整个待排序的记录序列分割成为若干子序列分别进行直接插入排序，具体算法描述：

*   选择一个增量序列t1，t2，…，tk，其中ti>tj，tk=1；
    
*   按增量序列个数 k，对序列进行 k 趟排序；
    
*   每趟排序，根据对应的增量 ti，将待排序列分割成若干长度为 m 的子序列，分别对各子表进行直接插入排序。仅增量因子为1 时，整个序列作为一个表来处理，表长度即为整个序列的长度。
    

#### 4.2 过程演示

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X3BuZy9saWJZUnV2VUxUZFhhc0NyRmRUWlYyVm5ERk5yUEE3SmlhUHduc3NaNEdwdFVneHVzdHlhTTlYOVNnM2hMUE9lYUlJS09ITFc1aWJ0RDZlWmVGaWJrakhMWlEvNjQw?x-oss-process=image/format,png "img")

#### 4.3 代码实现

```
/**
     * 希尔排序
     *
     * @param array
     * @return
     */
public static int[] ShellSort(int[] array) {
  int len = array.length;
  int temp, gap = len / 2;
  while (gap > 0) {
    for (int i = gap; i < len; i++) {
      temp = array[i];
      int preIndex = i - gap;
      while (preIndex >= 0 && array[preIndex] > temp) {
        array[preIndex + gap] = array[preIndex];
        preIndex -= gap;
      }
      array[preIndex + gap] = temp;
    }
    gap /= 2;
  }
  return array;
}
 
```

#### 4.4 算法分析

**最佳情况：T(n) = O(nlog2 n) 最坏情况：T(n) = O(nlog2 n) 平均情况：T(n) =O(nlog2n)**　

### 5、归并排序（Merge Sort）

和选择排序一样，`归并排序`的性能不受输入数据的影响，但表现比选择排序好的多，因为始终都是 O(n log n）的时间复杂度。代价是需要额外的内存空间。

归并排序是建立在归并操作上的一种有效的排序算法。该算法是采用`分治法（Divide and Conquer）`的一个非常典型的应用。归并排序是一种稳定的排序方法。将已有序的子序列合并，得到完全有序的序列；即先使每个子序列有序，再使子序列段间有序。若将两个有序表合并成一个有序表，称为2-路归并。

#### 5.1 算法描述

*   把长度为n的输入序列分成两个长度为n/2的子序列；
    
*   对这两个子序列分别采用归并排序；
    
*   将两个排序好的子序列合并成一个最终的排序序列。
    

#### 5.2 动图演示

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2dpZi9saWJZUnV2VUxUZFhhc0NyRmRUWlYyVm5ERk5yUEE3SmlhS3c3WDdwN2pvQ01LVm13cDZrYTBUMmQ0akFuU0VpYmJBUU5hcnZkU0lEVTZ0ODNQSzRZeUhPUS82NDA?x-oss-process=image/format,png)

#### 5.3 代码实现

```
/**
     * 归并排序
     *
     * @param array
     * @return
     */
public static int[] MergeSort(int[] array) {
  if (array.length < 2) return array;
  int mid = array.length / 2;
  int[] left = Arrays.copyOfRange(array, 0, mid);
  int[] right = Arrays.copyOfRange(array, mid, array.length);
  return merge(MergeSort(left), MergeSort(right));
}
/**
     * 归并排序——将两段排序好的数组结合成一个排序数组
     *
     * @param left
     * @param right
     * @return
     */
public static int[] merge(int[] left, int[] right) {
  int[] result = new int[left.length + right.length];
  for (int index = 0, i = 0, j = 0; index < result.length; index++) {
    if (i >= left.length)
      result[index] = right[j++];
    else if (j >= right.length)
      result[index] = left[i++];
    else if (left[i] > right[j])
      result[index] = right[j++];
    else
      result[index] = left[i++];
  }
  return result;
}
 
```
#### 5\. 4 算法分析

**最佳情况：T(n) = O(n) 最差情况：T(n) = O(nlogn) 平均情况：T(n) = O(nlogn)**

### 6、快速排序（Quick Sort）

快速排序的基本思想：通过一趟排序将待排记录分隔成独立的两部分，其中一部分记录的关键字均比另一部分的关键字小，则可分别对这两部分记录继续进行排序，以达到整个序列有序。

#### 6.1 算法描述

快速排序使用分治法来把一个串（list）分为两个子串（sub-lists）。具体算法描述如下：

*   从数列中挑出一个元素，称为 `基准（pivot）`；
    
*   重新排序数列，所有元素比基准值小的摆放在基准前面，所有元素比基准值大的摆在基准的后面（相同的数可以到任一边）。在这个分区退出之后，该基准就处于数列的中间位置。这个称为分区（partition）操作；
    
*   递归地（recursive）把小于基准值元素的子数列和大于基准值元素的子数列排序。
    

#### 6.2 动图演示

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2dpZi9saWJZUnV2VUxUZFhhc0NyRmRUWlYyVm5ERk5yUEE3SmlhVUtNd3h2VGtid3RGQXJQUW5YSDVpYXNvMm03Wm5XT2lhdzA5WmIyZmhrdmpWbzlIS3VpYTJlNU9nLzY0MA?x-oss-process=image/format,png "img")

#### 6.3 代码实现

```
　　/**
     * 快速排序方法
     */
public static int[] QuickSort(int[] array, int start, int end) {
  if (array.length < 1 || start < 0 || end >= array.length || start > end) return null;
  int smallIndex = partition(array, start, end);
  if (smallIndex > start)
    QuickSort(array, start, smallIndex - 1);
  if (smallIndex < end)
    QuickSort(array, smallIndex + 1, end);
  return array;
}
/**
     * 快速排序算法——partition
     */
public static int partition(int[] array, int start, int end) {
  int pivot = (int) (start + Math.random() * (end - start + 1));
  int smallIndex = start - 1;
  swap(array, pivot, end);
  for (int i = start; i <= end; i++)
    if (array[i] <= array[end]) {
      smallIndex++;
      if (i > smallIndex)
        swap(array, i, smallIndex);
    }
  return smallIndex;
}
 
/**
     * 交换数组内两个元素
     */
public static void swap(int[] array, int i, int j) {
  int temp = array[i];
  array[i] = array[j];
  array[j] = temp;
}
 
```

#### 6.4 算法分析

**最佳情况：T(n) = O(nlogn) 最差情况：T(n) = O(n2) 平均情况：T(n) = O(nlogn)**　

### 7、堆排序（Heap Sort）

`堆排序（Heapsort）`是指利用堆这种数据结构所设计的一种排序算法。堆积是一个近似完全二叉树的结构，并同时满足堆积的性质：即子结点的键值或索引总是小于（或者大于）它的父节点。

#### 7.1 算法描述

*   将初始待排序关键字序列(R1,R2….Rn)构建成大顶堆，此堆为初始的无序区；
    
*   将堆顶元素R\[1\]与最后一个元素R\[n\]交换，此时得到新的无序区(R1,R2,……Rn-1)和新的有序区(Rn),且满足R\[1,2…n-1\]<=R\[n\]；
    
*   由于交换后新的堆顶R\[1\]可能违反堆的性质，因此需要对当前无序区(R1,R2,……Rn-1)调整为新堆，然后再次将R\[1\]与无序区最后一个元素交换，得到新的无序区(R1,R2….Rn-2)和新的有序区(Rn-1,Rn)。不断重复此过程直到有序区的元素个数为n-1，则整个排序过程完成。
    

#### 7.2 动图演示

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2dpZi9saWJZUnV2VUxUZFhhc0NyRmRUWlYyVm5ERk5yUEE3SmlhQVF3N0hxekFpYlp1SDZkU1AyYmczVXRIcjZ2R0wwbHluV0ExbmNpYkppYkNnb0t6a2JBeHNXNUxBLzY0MA?x-oss-process=image/format,png)

#### 7.3 代码实现  

```
//声明全局变量，用于记录数组array的长度；
static int len;
/**
     * 堆排序算法
     *
     * @param array
     * @return
     */
public static int[] HeapSort(int[] array) {
  len = array.length;
  if (len < 1) return array;
  //1.构建一个最大堆
  buildMaxHeap(array);
  //2.循环将堆首位（最大值）与末位交换，然后在重新调整最大堆
  while (len > 0) {
    swap(array, 0, len - 1);
    len--;
    adjustHeap(array, 0);
  }
  return array;
}
/**
     * 建立最大堆
     *
     * @param array
     */
public static void buildMaxHeap(int[] array) {
  //从最后一个非叶子节点开始向上构造最大堆
  for (int i = (len/2 - 1); i >= 0; i--) { //感谢 @让我发会呆 网友的提醒，此处应该为 i = (len/2 - 1) 
    adjustHeap(array, i);
  }
}
/**
     * 调整使之成为最大堆
     *
     * @param array
     * @param i
     */
public static void adjustHeap(int[] array, int i) {
  int maxIndex = i;
  //如果有左子树，且左子树大于父节点，则将最大指针指向左子树
  if (i * 2 < len && array[i * 2] > array[maxIndex])
    maxIndex = i * 2;
  //如果有右子树，且右子树大于父节点，则将最大指针指向右子树
  if (i * 2 + 1 < len && array[i * 2 + 1] > array[maxIndex])
    maxIndex = i * 2 + 1;
  //如果父节点不是最大值，则将父节点与最大值交换，并且递归调整与父节点交换的位置。
  if (maxIndex != i) {
    swap(array, maxIndex, i);
    adjustHeap(array, maxIndex);
  }
}
 
```

#### 7.4 算法分析

**最佳情况：T(n) = O(nlogn) 最差情况：T(n) = O(nlogn) 平均情况：T(n) = O(nlogn)**

### 8、计数排序（Counting Sort）

`计数排序`的核心在于将输入的数据值转化为键存储在额外开辟的数组空间中。作为一种线性时间复杂度的排序，计数排序要求输入的数据必须是有确定范围的整数。

计数排序(Counting sort)是一种稳定的排序算法。计数排序使用一个额外的数组C，其中第i个元素是待排序数组A中值等于i的元素的个数。然后根据数组C来将A中的元素排到正确的位置。它只能对整数进行排序。

#### 8.1 算法描述

*   找出待排序的数组中最大和最小的元素；
    
*   统计数组中每个值为i的元素出现的次数，存入数组C的第i项；
    
*   对所有的计数累加（从C中的第一个元素开始，每一项和前一项相加）；
    
*   反向填充目标数组：将每个元素i放在新数组的第C(i)项，每放一个元素就将C(i)减去1。
    

#### 8.2 动图演示

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2dpZi9saWJZUnV2VUxUZFhhc0NyRmRUWlYyVm5ERk5yUEE3SmlhZDRpYnVsdDBJWU9DSkVOMVMxS3A1RnNNNVJqQUt3OFdTTllpYXVKaWNZVXZkN1J1VWJLSDFhYkZRLzY0MA?x-oss-process=image/format,png "img")

#### 8.3 代码实现

```
/**
     * 计数排序
     *
     * @param array
     * @return
     */
public static int[] CountingSort(int[] array) {
  if (array.length == 0) return array;
  int bias, min = array[0], max = array[0];
  for (int i = 1; i < array.length; i++) {
    if (array[i] > max)
      max = array[i];
    if (array[i] < min)
      min = array[i];
  }
  bias = 0 - min;
  int[] bucket = new int[max - min + 1];
  Arrays.fill(bucket, 0);
  for (int i = 0; i < array.length; i++) {
    bucket[array[i] + bias]++;
  }
  int index = 0, i = 0;
  while (index < array.length) {
    if (bucket[i] != 0) {
      array[index] = i - bias;
      bucket[i]--;
      index++;
    } else
      i++;
  }
  return array;
}
```

#### 8.4 算法分析

当输入的元素是 n 个 0 到 k 之间的整数时，它的运行时间是 O(n + k)。计数排序不是比较排序，排序的速度快于任何比较排序算法。由于用来计数的数组C的长度取决于待排序数组中数据的范围（等于待排序数组的最大值与最小值的差加上1），这使得计数排序对于数据范围很大的数组，需要大量时间和内存。

**最佳情况：T(n) = O(n+k) 最差情况：T(n) = O(n+k) 平均情况：T(n) = O(n+k)**

### 9、桶排序（Bucket Sort）

`桶排序`是计数排序的升级版。它利用了函数的映射关系，高效与否的关键就在于这个映射函数的确定。

`桶排序 (Bucket sort)`的工作的原理：假设输入数据服从均匀分布，将数据分到有限数量的桶里，每个桶再分别排序（有可能再使用别的排序算法或是以递归方式继续使用桶排序进行排

#### 9.1 算法描述

*   人为设置一个BucketSize，作为每个桶所能放置多少个不同数值（例如当BucketSize==5时，该桶可以存放｛1,2,3,4,5｝这几种数字，但是容量不限，即可以存放100个3）；
    
*   遍历输入数据，并且把数据一个一个放到对应的桶里去；
    
*   对每个不是空的桶进行排序，可以使用其它排序方法，也可以递归使用桶排序；
    
*   从不是空的桶里把排好序的数据拼接起来。
    

**注意，如果递归使用桶排序为各个桶排序，则当桶数量为1时要手动减小 BucketSize 增加下一循环桶的数量，否则会陷入死循环，导致内存溢出。**

#### 9.2 图片演示

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X3BuZy9saWJZUnV2VUxUZFhhc0NyRmRUWlYyVm5ERk5yUEE3SmlhbHVsY3NmOTNZVjRob3YyTE5VRE1RR0JTQWljc2Yxb0RqTGNYZ2lic1JHTUlHOElZczJaSlUzWmcvNjQw?x-oss-process=image/format,png "img")

#### 9.3 代码实现

```
/**
     * 桶排序
     * 
     * @param array
     * @param bucketSize
     * @return
     */
public static ArrayList<Integer> BucketSort(ArrayList<Integer> array, int bucketSize) {
  if (array == null || array.size() < 2)
    return array;
  int max = array.get(0), min = array.get(0);
  // 找到最大值最小值
  for (int i = 0; i < array.size(); i++) {
    if (array.get(i) > max)
      max = array.get(i);
    if (array.get(i) < min)
      min = array.get(i);
  }
  int bucketCount = (max - min) / bucketSize + 1;
  ArrayList<ArrayList<Integer>> bucketArr = new ArrayList<>(bucketCount);
  ArrayList<Integer> resultArr = new ArrayList<>();
  for (int i = 0; i < bucketCount; i++) {
    bucketArr.add(new ArrayList<Integer>());
  }
  for (int i = 0; i < array.size(); i++) {
    bucketArr.get((array.get(i) - min) / bucketSize).add(array.get(i));
  }
  for (int i = 0; i < bucketCount; i++) {
    if (bucketSize == 1) { // 如果带排序数组中有重复数字时  感谢 @见风任然是风 朋友指出错误
      for (int j = 0; j < bucketArr.get(i).size(); j++)
        resultArr.add(bucketArr.get(i).get(j));
    } else {
      if (bucketCount == 1)
        bucketSize--;
      ArrayList<Integer> temp = BucketSort(bucketArr.get(i), bucketSize);
      for (int j = 0; j < temp.size(); j++)
        resultArr.add(temp.get(j));
    }
  }
  return resultArr;
}
 
```


#### 9.4 算法分析

桶排序最好情况下使用线性时间 O(n)，桶排序的时间复杂度，取决与对各个桶之间数据进行排序的时间复杂度，因为其它部分的时间复杂度都为 O(n)。很显然，桶划分的越小，各个桶之间的数据越少，排序所用的时间也会越少。但相应的空间消耗就会增大。

**最佳情况：T(n) = O(n+k) 最差情况：T(n) = O(n+k) 平均情况：T(n) = O(n2)**　　

### 10、基数排序（Radix Sort）

基数排序也是非比较的排序算法，对每一位进行排序，从最低位开始排序，复杂度为O(kn),为数组长度，k为数组中的数的最大的位数；

`基数排序`是按照低位先排序，然后收集；再按照高位排序，然后再收集；依次类推，直到最高位。有时候有些属性是有优先级顺序的，先按低优先级排序，再按高优先级排序。最后的次序就是高优先级高的在前，高优先级相同的低优先级高的在前。基数排序基于分别排序，分别收集，所以是稳定的。

#### 10.1 算法描述

*   取得数组中的最大数，并取得位数；
    
*   arr为原始数组，从最低位开始取每个位组成radix数组；
    
*   对radix进行计数排序（利用计数排序适用于小范围数的特点）；
    

#### 10.2 动图演示

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2dpZi9saWJZUnV2VUxUZFhhc0NyRmRUWlYyVm5ERk5yUEE3SmlhdmhXRVVwOXJ4bTVQRFQxNGNnOURMQ3VwZFVoUnNSdU5BSFlsN2x3OFFFTHVXTjB1NjZGTmdBLzY0MA?x-oss-process=image/format,png "img")

#### 10.3 代码实现

```
/**
     * 基数排序
     * @param array
     * @return
     */
public static int[] RadixSort(int[] array) {
  if (array == null || array.length < 2)
    return array;
  // 1.先算出最大数的位数；
  int max = array[0];
  for (int i = 1; i < array.length; i++) {
    max = Math.max(max, array[i]);
  }
  int maxDigit = 0;
  while (max != 0) {
    max /= 10;
    maxDigit++;
  }
  int mod = 10, div = 1;
  ArrayList<ArrayList<Integer>> bucketList = new ArrayList<ArrayList<Integer>>();
  for (int i = 0; i < 10; i++)
    bucketList.add(new ArrayList<Integer>());
  for (int i = 0; i < maxDigit; i++, mod *= 10, div *= 10) {
    for (int j = 0; j < array.length; j++) {
      int num = (array[j] % mod) / div;
      bucketList.get(num).add(array[j]);
    }
    int index = 0;
    for (int j = 0; j < bucketList.size(); j++) {
      for (int k = 0; k < bucketList.get(j).size(); k++)
        array[index++] = bucketList.get(j).get(k);
      bucketList.get(j).clear();
    }
  }
  return array;
}
 
```
#### 10.4 算法分析

**最佳情况：T(n) = O(n * k) 最差情况：T(n) = O(n * k) 平均情况：T(n) = O(n * k)**

基数排序有两种方法：

MSD 从高位开始进行排序 LSD 从低位开始进行排序

**基数排序 vs 计数排序 vs 桶排序**

这三种排序算法都利用了桶的概念，但对桶的使用方法上有明显差异：

*   基数排序：根据键值的每位数字来分配桶
    
*   计数排序：每个桶只存储单一键值
    
*   桶排序：每个桶存储一定范围的数值
    

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 一致性hash算法了解过吗？环境描述
----

> 在了解hash算法之前先去了解一下缓存中的一个应用场景，再来理解一致性hash算法就会简单很多。

### 场景描述

假设，公司有三台缓存服务器，用于缓存图片，这三台缓存服务器的编号为0号，1号，2号，现在有三万张图片需要缓存，`希望这么多的缓存数据能均匀的缓存到3台服务请求上去`**(也就是说每台机器上平均分配1万左右的数据)**，以便能够`分摊缓存的压力`。

*   此处的问题：

> 那么应该怎么做？如果我们没有任何规律的将3万张图片平均的缓存到3台服务器上，可不可以满足需求？

*   答案：

> 可以！但是如果这么做，当我们需要访问某个和缓存选项时，则需要遍历3台服务器，从这3万个缓存项中找到需要访问的缓存，整个遍历下来的过程时间长，效率低，`这样也就失去了缓存存在的价值和意义，缓存存在的目的就是提高速度，改善用户的体验，减轻后端服务器的压力，如果每次都要遍历整个缓存集群服务器，不用想都能累死.`

*   好一点的做法：

> 原始的做法是对缓存项的键进行hash，将hash后的结果对缓存服务器数量进行取模操作，通过取模后结果，决定缓存项要缓存在那一台服务器上，举例说明：假设以我们使用的图片名称作为访问图片的key，假设图片名称不能重复，那么我们可以使用以下公式，及计算出图片应该存放在那台服务器上。

*   公式：hash（图片名称）% N

> 因为图片名称是不能重复的，所以，当我们对同一个图片名称做相同的hash运算时得出的结果应该是不变的，如果有3台服务器，使用hash运算后的结果对3取余，那么余数也一定是0、1、2，正号跟之前服务器编号相同，如果求余的结果为1，就把图片名称对应的图片缓存在1号服务器上，2就和缓存到2号服务器上，那么当我们访问任意一个图片的时候，只要再次对图片名称进行运算即可得出对应的图片应该被放在那台缓存服务器上，只需要去对应的服务器上去查找即可，如果图片在对应的服务器上不存在，证明没有被缓存(接着会把这张图片缓存在这个服务器上)，也不用再去遍历其他缓存服务器了。通过此方法可以把3万图片随机分布到3台缓存服务器上，下次访问某张图片时，直接能够判断出该图片应该存放在那台缓存服务器上了。可以把上述算法称为：HASH算法还活着是取模算法

### 以下是运算原理图：

![Alt text](https://img-blog.csdnimg.cn/20190330182849616.png)

但是使用上述hash算法进行缓存时会出现一些缺陷，如果3台并不能满足我们的需求时那么应该怎么做?肯定是增加几台服务器就可以了，假设我们增加1台服务器，服务器的数量由3变成了4，此时仍然用上述方法对同一张图片进行缓存，那么这张图片所在的服务器的编号必定是与原来的3台服务器所在的 编号是不同的，因为除数3变成了4，被除数不变的情况下，余数肯定不同，这情况带来的结果就是当服务器数量变动时，所有和缓存的位置都要发生改变，也就是说缓存服务器数量发生改变时，`所有缓存数据在一定时间是失效的，当应用无法从缓存中和获取数据时，则会向后端服务器请求数据，`同理，如果3台缓存服务器中突然有一台出现了故障，，无法进行缓存数据，那么需要移除故障机器，`但是如果移除了一台缓存服务器后，数量从3变成了2，如果想访问有一张图片，这张图片缓存为位置必定发生改变，以前缓存的图片也会失去缓存的作用和意义`，由于==**`大量缓存在同一时间失效，造成了缓存的雪崩(血崩)，此时前端缓存已经无法起到成端部分压力的作用，后端服务器将会承担所有巨大压力，会导致整个系统可能会被压垮，==所以为了避免这类情况的发生，一致性hash算法诞生了！

*   综合一下上述出现的问题：

> 第一个问题：  
> 当缓存服务器数量发生变化时，会引起缓存的血崩，可能引起整体系统压力过大而崩溃（大量缓存同一时间失效），  
> 第二个问题：  
> 当缓存服务器数量发生变化时，几乎所有缓存的数据都会发生改变，怎么才能尽量减少受影响的缓存？

一致性hash算法概念
-----------

> 其实一致性hash算法也是取模运算，只是，上面描述的取模算法是对服务器数量进行取模，而一致性hash是对2^32取模

*   插入小知识：  
    `为什么非得对2^32取余？`

> 对232取余是有依据的IPV4最大数量就是232，所以这样就能保证所有的ip的地址进行取余时不会重复—对应hash环上面的正数。

1.  首先把2^32想象成有一个大大的圆，就像钟表上由60个点组成的圆，如图：  
    ![Alt text](https://img-blog.csdnimg.cn/20190330182925415.png)由2^32个点组成的圆环称为hash环。

> 圆环的正上方代表0，0点右侧第一个1以此类推2,3,4,5,6……一直到最后2^32-1。  
> 假设我们有3台缓存服务器，服务器A，B，C，然后用他们各自的IP地址进行hash计算，使用hash后的结果改过对2^32取模。`hash(服务器A的IP地址) % 2^32`  
> 通过上面的计算结果一定是一个0到232-1之间的一个整数，我们就用这个整数代表服务器A，既然这个整数肯定处于0到232-1之间，那么必定与hash环的上一个点与这个整数对应。刚才已经说明，使用这个整数代表服务器A，那么服务器A就可以映射到这个环上。

![Alt text](https://img-blog.csdnimg.cn/20190330182933656.png)

2.  同理服务器B和C也是相同的方法映射到hash环中  
    计算公式：

> `hash(服务器B的IP地址) % 2^32`  
> `hash(服务器C的IP地址) % 2^32`

算出结果然后将服务器映射到hash环上去。如图所示：  
![Alt text](https://img-blog.csdnimg.cn/20190330182943103.png)假设3台服务器均匀到映射到hash环上，(`这是理想得到情况`)

3.  假设，我们需要使用缓存服务器缓存图片

> 而且仍然使用图片的名称作为找到图片的Key，那么我们使用以下公式可以将图片映射到上图中的hash环上。  
> `hash(图片名称) % 2^32`

映射后得到的结果如下图：(红点点代表图片)  
![Alt text](https://img-blog.csdnimg.cn/20190330182952532.png)  
那么问题来了，图片和服务器都被映射到了hash环上，那么上图的图片到底应该缓存到那一台缓存服务器上呢？  
**答：**

> 应该被缓存到A服务器上，为什么？  
> 因为从图片开始的位置开始，沿着顺时针方向遇到的第一个服务器就是A服务器，所以会被缓存到A服务器上。如下图：

![Alt text](https://img-blog.csdnimg.cn/20190330182959826.png)

4.  一致性hash算法说明：

> 通过一致性hash算法这种方法，判断一个对象应该被缓存到那台服务器上的，将缓存服务器与被缓存对象都映射到hash环上以后，从被缓存对象的位置出发，沿着顺时针方向遇到的第一个服务器，就是当前对象将要缓存的服务器，由于被缓存对象与服务器hash后的值都是固定的，所以服务器不变的情况下，一张图片必定会被缓存到固定的服务器上，那么，当下次访问这张图片时，只要再次使用相同的算法进行计算，即可算出这张图片被缓存在那个服务器上，直接去对应的服务器上查找即可。

假设有4张图片需要缓存，如下图：  
![Alt text](https://img-blog.csdnimg.cn/20190330183008116.png)1、2图片缓存到A上，3缓存到B上，4缓存到C

一致性hash算法的优点
------------

> 一致性hash算法能够解决之前出现的问题吗？如果进行简单的取模，当服务器数量发生变化时，会产生缓存的雪崩，从而导致系统崩溃，那么用一致性hash能够避免这个问题吗？

1.  继续模拟测试实验！！  
    假设服务器B出现故障，需要移除B，如下图：  
    ![Alt text](https://img-blog.csdnimg.cn/20190330183019168.png)  
    在服务器B没有移除时，图片3应该缓存到B中，可是移除后，按照一致性hash算法是规则，3应该被缓存到C中，因为从3的位置顺时针除法遇到的第一个服务器节点是C，也就是说如果B出现故障移除后，3的缓存位置发生改变。  
    ![Alt text](https://img-blog.csdnimg.cn/20190330183029315.png)  
    这里的一致性hash算法的优点就体现出来了！  
    `图片4依然会被缓存到C中，图片1和2突然缓存到A中，与移除B之前没有任何区别，`这就是优点！

> 1）如果使用hash算法：`当服务器数量发生改变时，所有的服务器缓存在同一时间失效了`  
> 2）而使用一致性hash算法：`服务器数量发生改变时，并不是所有都会失效，而只有部分缓存失效，前端的缓存仍然能分担整个系统的压力，而不至于所有压力都在同一个时间集中到后端服务器上。`

hash环偏斜问题
---------

在最开始介绍概念年的时候，说的是在理想的情况下是**`均匀的分布到hash环上！`**如下图  
![Alt text](https://img-blog.csdnimg.cn/20190330183045524.png)  
但是理想是很丰满的，我们想象的和现实往往是不同的！  
![Alt text](https://img-blog.csdnimg.cn/20190330183100907.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM0NjcyMDMz,size_16,color_FFFFFF,t_70)  
在实际映射中，服务器可能会被映射成一下模样  
![Alt text](https://img-blog.csdnimg.cn/20190330183110752.png)  
那么被缓存的对象很有可能大部分集中缓存到某一台服务器上如下图:  
![Alt text](https://img-blog.csdnimg.cn/2019033018311934.png)

> 图上2、3、4、5、6、都很会存储到A服务器上，1会存到B上，C服务器一张也没有，三台服务器并没有合理的平均充分的利用，`缓存分布极度不均匀，重要的是如果A出现故障，会导致失效的数量也将达到最大值。在极端的情况下依然会出现系统崩溃的问题！`

以上情况被称之为hash环偏斜，那么**如何防止hash环偏斜呢？**

虚拟节点
----

“虚拟节点”是“实际节点”(实际的物理服务器)在hash环上的复制品，一个实际节点可以对应多个虚拟节点。如下图：  
![Alt text](https://img-blog.csdnimg.cn/20190330183128931.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM0NjcyMDMz,size_16,color_FFFFFF,t_70)  
ABC三台服务分别虚拟出一个虚拟节点（也可以虚拟出更多的虚拟节点）`引入虚拟节点的概念后，缓存的分布就均衡的多了，上图中3、4、5、的图片都被放到了节点A中如果不放心可以虚拟出更多的虚拟节点，以便减少hash环偏斜所带来的影响，虚拟节点越多，hash环上的节点就越多，缓存均匀分布的概率就越大！！！`
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 布隆过滤器了解过吗？为什么要有布隆过滤器
==================================================================================================================

在日常生活中，包括在设计计算机软件时，我们经常要判断一个元素是否在一个集合中。比如在字处理软件中，需要检查一个英语单词是否拼写正确（也就是要判断 它是否在已知的字典中）；在 FBI，一个嫌疑人的名字是否已经在嫌疑名单上；在网络爬虫里，一个网址是否被访问过等等。最直接的方法就是将集合中全部的元素存在计算机中，遇到一个新 元素时，将它和集合中的元素直接比较即可。一般来讲，计算机中的集合是用哈希表（hash table）来存储的。它的好处是快速准确，缺点是费存储空间。当集合比较小时，这个问题不显著，但是当集合巨大时，哈希表存储效率低的问题就显现出来 了。比如说，一个象 Yahoo,Hotmail 和 Gmai 那样的公众电子邮件（email）提供商，总是需要过滤来自发送垃圾邮件的人（spamer）的垃圾邮件。一个办法就是记录下那些发垃圾邮件的 email 地址。由于那些发送者不停地在注册新的地址，全世界少说也有几十亿个发垃圾邮件的地址，将他们都存起来则需要大量的网络服务器。**如果用哈希表，每存储一亿 个 email 地址， 就需要 1.6GB 的内存（用哈希表实现的具体办法是将每一个 email 地址对应成一个八字节的信息指纹， 然后将这些信息指纹存入哈希表，由于哈希表的存储效率一般只有 50%，因此一个 email 地址需要占用十六个字节。一亿个地址大约要 1.6GB， 即十六亿字节的内存）。因此存贮几十亿个邮件地址可能需要上百 GB 的内存。除非是超级计算机，一般服务器是无法存储的。**

简介
==

本质上布隆过滤器是一种数据结构**，比较巧妙的概率型数据结构**（probabilistic data structure），特点是高效地插入和查询，可以用来告诉你 “**某样东西一定不存在或者可能存在**”。

相比于传统的 List、Set、Map 等数据结构，它更高效、占用空间更少，但是缺点是其返回的结果是概率性的，而不是确切的。

布隆过滤器是一种多哈希函数映射的快速查找算法。它可以判断出某个元素肯定不在集合里或者可能在集合里，即它不会漏报，但可能会误报。**通常应用在一些需要快速判断某个元素是否属于集合，但不严格要求100％正确的场合**。

基本原理
----

布隆过滤器是一个 bit 向量或者说 bit 数组，长这样：![](https://img-blog.csdnimg.cn/20190507104635641.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3h1c2hpeXUxOTk2ODE4,size_16,color_FFFFFF,t_70)

如果我们要映射一个值到布隆过滤器中，我们需要使用多个不同的哈希函数生成多个哈希值，并对每个生成的哈希值指向的 bit 位置 1，例如针对值 “baidu” 和三个不同的哈希函数分别生成了哈希值 1、4、7，则上图转变为：![](https://img-blog.csdnimg.cn/20190507104704728.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3h1c2hpeXUxOTk2ODE4,size_16,color_FFFFFF,t_70)

Ok，我们现在再存一个值 “tencent”，如果哈希函数返回 3、4、8 的话，图继续变为：![](https://img-blog.csdnimg.cn/2019050710473546.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3h1c2hpeXUxOTk2ODE4,size_16,color_FFFFFF,t_70)

值得注意的是，4 这个 bit 位由于两个值的哈希函数都返回了这个 bit 位，因此它被覆盖了。现在我们如果想查询 “dianping” 这个值是否存在，哈希函数返回了 1、5、8三个值，结果我们发现 5 这个 bit 位上的值为 0，说明没有任何一个值映射到这个 bit 位上，因此我们可以很确定地说 “dianping” 这个值不存在。而当我们需要查询 “baidu” 这个值是否存在的话，那么哈希函数必然会返回 1、4、7，然后我们检查发现这三个 bit 位上的值均为 1，那么我们可以说 “baidu” 存在了么？答案是不可以，只能是 “baidu” 这个值可能存在。

这是为什么呢？答案跟简单，**因为随着增加的值越来越多，被置为 1 的 bit 位也会越来越多，这样某个值 “taobao” 即使没有被存储过，但是万一哈希函数返回的三个 bit 位都被其他值置位了 1 ，那么程序还是会判断 “taobao” 这个值存在。**

是否支持删除
------

目前我们知道布隆过滤器可以支持 add 和 isExist 操作，那么 delete 操作可以么，答案是不可以，例如上图中的 bit 位 4 被两个值共同覆盖的话，一旦你删除其中一个值例如 “tencent” 而将其置位 0，那么下次判断另一个值例如 “baidu” 是否存在的话，会直接返回 false，而实际上你并没有删除它。

如何解决这个问题，**答案是计数删除**。但是计数删除需要存储一个数值，而不是原先的 bit 位，会增大占用的内存大小。这样的话，增加一个值就是将对应索引槽上存储的值加一**（即存储的不是0,1，而是0,1,2,3，。。。），删除则是减一，判断是否存在则是看值是否大于0。**

误判率
---

误判率就是在插入n个元素后，某元素被判断为“可能在集合里”，但实际不在集合里的概率，此时这个元素哈希之后的k个比特位置都被置为1。

假设哈希函数等概率地选择每个数组位置，即哈希后的值符合均匀分布，那么每个元素等概率地哈希到位数组的m个比特位上，与其他元素被哈希到哪些位置无关(独立事件)。设定数组总共有m个比特位，有k个哈希函数。在插入一个元素时，一个特定比特没有被某个哈希函数置为1的概率是：

![1](https://imgconvert.csdnimg.cn/aHR0cDovL2ltZzQudGJjZG4uY24vTDEvNDYxLzEvMGMwOGViZTUxMWNkZjg0YmFlYWM3Mzk4MjczMWJjYjg1YTZkMjgxNQ?x-oss-process=image/format,png)

插入一个元素后，这个比特没有被任意哈希函数置为1的概率是：

![2](https://imgconvert.csdnimg.cn/aHR0cDovL2ltZzEudGJjZG4uY24vTDEvNDYxLzEvZTVmMWZhYzA5ODBjZDAxNTNiMDE5YzNmZmUzN2MzMjM2NWFlOWVmYg?x-oss-process=image/format,png)

在插入了n个元素后，这个特定比特仍然为0的概率是：

![3](https://imgconvert.csdnimg.cn/aHR0cDovL2ltZzIudGJjZG4uY24vTDEvNDYxLzEvNzk0NmI2MTA5ODNhYjkzZjk3ZjI5MjRkYzUxNjQwOWExODIwYmI5MQ?x-oss-process=image/format,png)

所以这个比特被置为1的概率是：

![4](https://imgconvert.csdnimg.cn/aHR0cDovL2ltZzMudGJjZG4uY24vTDEvNDYxLzEvOGMzYjVhN2QyMGZhMmI4MzA5NGViNzBjYThhOTk0NzNjN2FmOGFjMg?x-oss-process=image/format,png)

**现在检测一个不在集合里的元素。经过哈希之后的这k个数组位置任意一个位置都是1的概率如上。这k个位置都为1的概率是**：

![5](https://imgconvert.csdnimg.cn/aHR0cDovL2ltZzIudGJjZG4uY24vTDEvNDYxLzEvYTUyNDdjNGRmZmFhMTBkMmFhZjU3NWFiZjc2YjdmYWEzNjJjZDZiMQ?x-oss-process=image/format,png)

### 哈希函数个数和布隆过滤器长度

对于给定的m和n，**让“误报率”最小的k值为**：

![6](https://imgconvert.csdnimg.cn/aHR0cDovL2ltZzEudGJjZG4uY24vTDEvNDYxLzEvMGIwZjFkNzZhMWY5ZTM2NWFkNGU5YjQzMDgzZjg2NjVhZDg3OTA2Mg?x-oss-process=image/format,png)

此时“误报率”为：

![7](https://imgconvert.csdnimg.cn/aHR0cDovL2ltZzEudGJjZG4uY24vTDEvNDYxLzEvNmRiMTNmOGYwYzJiMzQ0YTI0MGZlYzM3NmU3NGNiMWNhOWM1MjFlNQ?x-oss-process=image/format,png)

**可以简化为**：

![9](https://imgconvert.csdnimg.cn/aHR0cDovL2ltZzEudGJjZG4uY24vTDEvNDYxLzEvZjg2YjY2MzRkNGU1MzM2MTk4MzgzNGY0N2I3YzdiMjRmY2NmNTZmNw?x-oss-process=image/format,png)

**上面的公式，可以看到，设定一个误判率p，可以得到m=x*n  得到x，就可以得到k**

在leveldb中，设定的误判率<=1%,所以m/n是9.6，即10个比特，此时k=6.72，即7bit，即需要7次hash，每个元素占7bit，总共需要m=n*9.6个比特作为布隆过滤器的位数组数据。

**结果是对于误报率<=1%,对于插入n个元素，要有7个哈希函数，9.6*n 个比特作为布隆过滤器的长度**

![](https://img-blog.csdnimg.cn/20190507110620758.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3h1c2hpeXUxOTk2ODE4,size_16,color_FFFFFF,t_70)

复杂度
---

### 空间

空间就是布隆过滤器的长度m，可以看到最优长度m=x*n，插入n个数，空间复杂度为O(n)

### 时间

进行一次哈希操作时间是常数时间，每插入一个数，要执行k次哈希运算和k次置1，还是常数时间

插入n个数，时间复杂度为O(n)

检验一个数在不在布隆过滤器中，时间为常数时间O(C)

优缺点
---

### 优点

1.  存储空间和插入/查询时间都是常数，远远超过一般的算法
2.  Hash函数相互之间没有关系，方便由硬件并行实现
3.  不需要存储元素本身，在某些对保密要求非常严格的场合有优势

### 缺点

1.  有一定的误识别率
2.  删除困难

BloomFilter和BItMap的区别
---------------------

**其实主要的区别在于两者，一个value对应位图的位置不同**

**bitmap，是一一对应，保证一个value对应一个格，所以只需对应一格，还十分准确**

**BloomFilter 是hashcode，不能保证一个value对应一格，所以要有多个hash函数，还有失误率，而且还不能删除，但是BloomFilter节省了空间，还能面对string这种肯定不能一一对应的场景**

应用
--

搜索引擎中的海量网页去重

leveldb等数据库中快速判断元素是否存在，可以显著减少磁盘访问

Google 著名的分布式数据库 Bigtable 使用了布隆过滤器来查找不存在的行或列，以减少磁盘查找的IO次数。

Squid 网页代理缓存服务器在 [cache digests ](http://wiki.squid-cache.org/SquidFaq/CacheDigests)中使用了也布隆过滤器。

Venti 文档存储系统也采用布隆过滤器来检测先前存储的数据。

SPIN 模型检测器也使用布隆过滤器在大规模验证问题时跟踪可达状态空间。

Google Chrome浏览器使用了布隆过滤器加速安全浏览服务。

在很多Key-Value系统中也使用了布隆过滤器来加快查询过程，如 Hbase，Accumulo，Leveldb，一般而言，Value 保存在磁盘中，访问磁盘需要花费大量时间，然而使用布隆过滤器可以快速判断某个Key对应的Value是否存在，因此可以避免很多不必要的磁盘IO操作，只是引入布隆过滤器会带来一定的内存消耗，下图是在Key-Value系统中布隆过滤器的典型使用：

![](https://img-blog.csdnimg.cn/20190507111550697.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3h1c2hpeXUxOTk2ODE4,size_16,color_FFFFFF,t_70)

java实现
======

Hash工具类
-------

这里的hash函数与string的那个hashcode方法基本一样，就是将31换成seed，最后mod maxLength，保证bitSet的范围

    package algorithm.find.bloomfilter; /**BloomFilter的hash工具类，用来对对应的value生成hashcode * */public class BloomHash {		/**	 * Hash工具类返回的hashcode的最大长度<br>	 * maxLength为2的n次方，返回的hashcode为[0,2^n-1]	 */	public int maxLength;		/**	 * Hash函数生成哈希码的关键字	 */	public int seed; 	public BloomHash(int maxLength, int seed) {		this.maxLength = maxLength;		this.seed = seed;	}		/**返回字符串string的hashcode，大小为[0,maxLength-1]	 * @param string	 * @return	 */	public int hashCode(String string){		int result=0;		//这个构建hashcode的方式类似于java的string的hashcode方法		//只是我这里是可以设置的seed，它那里是31		for(int i=0;i<string.length();i++){			result=result+seed*string.charAt(i);		}		//maxLength-1=111111,相当于result mod (maxLength-1)  		//保证结果在[0,maxLength-1]		return (maxLength-1)&result;	}		 }

BitSet类
-------

bloomfilter类对位图的操作基于java.util.BitSet  ，所以做个基本介绍它的api

BitSet的底层实现是使用long数组作为内部存储结构的，所以BitSet的大小为long类型大小(64位)的整数倍

**BitSet(int nbits)**``：创建一个位set，它的初始大小足以显式表示索引范围在 `0` 到 nbits-1 的位``

**bitSet.set(index)** 将index位 置1

**bitSet.get(index)**   将index位 返回

BloomFilter
-----------

注释很详细，总共7个hash函数，100万左右的bit位

对位图的操作基于上面的bitset

    package algorithm.find.bloomfilter; import java.util.BitSet; public class BloomFilter {			/**	 * 构建hash函数的关键字，总共7个	 */	private static final int[] HashSeeds=new int[]{3,5,7,11,13,17,19}; 		/**	 * Hash工具类的数组	 */	private static BloomHash[] HashList=new BloomHash[HashSeeds.length];		/**	 * BloomFilter的长度，最好为插入数量的10倍，目前为2的20次方，大约100万个	 */	private static final int BloomLength=1<<20;		/**	 * 对位的操作类，java自带的BitSet，共BloomLength个bit	 */	private BitSet bitSet=new BitSet(BloomLength);			public BloomFilter(){		//初始化Hash工具类的数组,每个hash工具类的hash函数都不同		for(int i=0;i<HashSeeds.length;i++){			HashList[i]=new BloomHash(BloomLength, HashSeeds[i]);		}	}		/**在布隆过滤器中加入值value，在多个hash函数生成的hashcode对应的位置上，置1	 * @param value 字符串，如果为数字，可以自己转化成string	 */	public void addValue(String value){		for(int i=0;i<HashSeeds.length;i++){			//根据对应的hash函数得到hashcode			int hashcode=HashList[i].hashCode(value);			//在位图中，将对应的位，设置为1			bitSet.set(hashcode);		}	}		/**在布隆过滤器中,检验是否可能有值value	 * @param value	 * @return 如果返回false，则一定没有<br> 如果返回true，就代表有可能有	 */	public boolean existsValue(String value){		boolean result=true;		for(int i=0;i<HashSeeds.length;i++){			//根据对应的hash函数得到hashcode			int hashcode=HashList[i].hashCode(value);			//将result与对应位置上的0或1 做与运算			//如果全为1，则result最后为1			//如果有一个位置上为0，则最后result为0			result=result&bitSet.get(hashcode);		}				return result;			} 			}

测试
--

    package algorithm.find.bloomfilter; public class Main { 	public static void main(String[] args) {		BloomFilter filter=new BloomFilter();		filter.addValue("1234");		System.out.println(filter.existsValue("1234"));		System.out.println(filter.existsValue("12341"));	} }

Counting Bloom Filter
=====================

从前面对Bloom Filter的介绍可以看出，标准的Bloom Filter是一种很简单的数据结构，它只支持插入和查找两种操作。在所要表达的集合是静态集合的时候，标准Bloom Filter可以很好地工作，但是如果要表达的集合经常变动，标准Bloom Filter的弊端就显现出来了，因为它不支持删除操作。

**Counting Bloom Filter的出现解决了这个问题，它将标准Bloom Filter位数组的每一位扩展为一个小的计数器（Counter），在插入元素时给对应的k（k为哈希函数个数）个Counter的值分别加1，删除元素时给对应的k个Counter的值分别减1。Counting Bloom Filter通过多占用几倍的存储空间的代价，给Bloom Filter增加了删除操作。**下一个问题自然就是，到底要多占用几倍呢？

![](https://img-blog.csdnimg.cn/20200621160332936.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3h1c2hpeXUxOTk2ODE4,size_16,color_FFFFFF,t_70)

我们先计算第i个Counter被增加j次的概率，其中n为集合元素个数，k为哈希函数个数，m为Counter个数（对应着原来位数组的大小）：

[![](https://imgconvert.csdnimg.cn/aHR0cDovL3N0YXRpYy5vc2NoaW5hLm5ldC91cGxvYWRzL2ltZy8yMDEzMDUvMjkwOTI5NTBfNERJbS5qcGc?x-oss-process=image/format,png)](http://static.oschina.net/uploads/img/201305/29092950_4DIm.jpg)

上面等式右端的表达式中，前一部分表示从nk次哈希中选择j次，中间部分表示j次哈希都选中了第i个Counter，后一部分表示其它nk – j次哈希都没有选中第i个Counter。因此，第i个Counter的值大于j的概率可以限定为：

[![](https://imgconvert.csdnimg.cn/aHR0cDovL3N0YXRpYy5vc2NoaW5hLm5ldC91cGxvYWRzL2ltZy8yMDEzMDUvMjkwOTI5NTBfck5vYy5qcGc?x-oss-process=image/format,png)](http://static.oschina.net/uploads/img/201305/29092950_rNoc.jpg)

上式第二步缩放中应用了估计阶乘的斯特林公式：

[![](https://imgconvert.csdnimg.cn/aHR0cDovL3N0YXRpYy5vc2NoaW5hLm5ldC91cGxvYWRzL2ltZy8yMDEzMDUvMjkwOTI5NTBfSTdVei5naWY)](http://static.oschina.net/uploads/img/201305/29092950_I7Uz.gif)

k的最优值为(ln2)m/n，现在我们限制k ≤ (ln2)m/n，就可以得到如下结论：

[![](https://imgconvert.csdnimg.cn/aHR0cDovL3N0YXRpYy5vc2NoaW5hLm5ldC91cGxvYWRzL2ltZy8yMDEzMDUvMjkwOTI5NTFfY0lNby5qcGc?x-oss-process=image/format,png)](http://static.oschina.net/uploads/img/201305/29092951_cIMo.jpg)

如果每个Counter分配4位，那么当Counter的值达到16时就会溢出。这个概率为：

[![](https://imgconvert.csdnimg.cn/aHR0cDovL3N0YXRpYy5vc2NoaW5hLm5ldC91cGxvYWRzL2ltZy8yMDEzMDUvMjkwOTI5NTFfWGtTQS5qcGc?x-oss-process=image/format,png)](http://static.oschina.net/uploads/img/201305/29092951_XkSA.jpg)

这个值足够小，**因此对于大多数应用程序来说，4位就足够了。**

Spectral Bloom Filter
=====================

Bloom filter将集合中的元素映射到位数组中，用k（k为哈希函数个数）个映射位是否全1表示元素在不在这个集合中。Counting bloom filter（CBF）将位数组中的每一位扩展为一个counter，从而支持了元素的删除操作。

**一旦位扩展成了counter，每一个counter就不仅能表示这一地址有无映射，还能表示映射的个数。这一扩展使得存储的数据包含了更多信息，然而遗憾的是，CBF仅仅利用这个扩展支持了删除操作，并没有将信息中蕴含的潜力完全挖掘出来。**毫无疑问，Spectral Bloom Filter（SBF）的提出者就看到了这种潜力。

标准的bloom filter和CBF解决的只是集合元素的membership问题，即判断一个元素是否属于某个集合。**但有时我们不但想知道集合中是否存在一个元素，我们还想知道这个元素在集合中的出现次数。**例如在一些数据流（data stream）应用中，我们关心的也许不是一个数据元素是否属于某个集合，而是它的出现频率。很自然地，我们希望能从counter中得到这些信息。但是，counter反映的只是映射数，如何将其与集合元素的出现次数关联呢？

**在CBF中加入一个元素时，k个哈希位置的counter都要加1。也就是说，如果不考虑碰撞（collision），出现次数为n的元素对应的k个counter的值都为n。即使考虑到碰撞的因素，只要k个位置不全出现碰撞，k个counter中的最小值仍是n。**令元素x对应的k个counter的最小值为mx，x的出现频率为fx，从上面的分析我们不难看出，**fx ≠ mx的概率和标准bloom filter的false positive概率相同，因为二者出现的充要条件都是k个哈希位置同时出现碰撞。**

上面这个结果其实就是SBF的理论基础。**SBF扩展了CBF，使得用户不但可以进行membership query，还可以查询集合元素的出现频率。在查询元素x的出现频率时，SBF返回mx，出错的概率和false positive rate相同。注意，由于fx ≤ mx，所以查询的结果即使不准，也可以得到一个上界，而且这个上界和实际值fx一般情况下不会相差太远。**

到现在为止讲的都是概念，我们还没有看到SBF和CBF在构造上有什么不同。当然，如果不改变CBF就可以加入新的feature，那最好不过了，可惜事情没有这么简单。**CBF的counter在只支持membership query的时候，4位就够了，如果想要支持元素的出现频率查询，4位就远远不够。由于元素有可能成百上千次重复出现，而且完全没法预测，所以SBF的counter必须能够动态伸缩。**

为实现counter的高效存储，我们先简化问题，来看最少需要多少位才能存储所有的counter。假设SBF要表示M个元素的集合（可能包含重复元素），counter数组的长度为m（对应着bloom filter的位数组），显然所有counter需要的最少位数N为

![](https://img-blog.csdnimg.cn/20200621162742675.png)

其中Ci表示counter数组中第i个counter的大小，即哈希函数映射到第i位的次数。用N位存储counter，其实相当于把所有的counter化成二进制位串然后连在一起。这样当然占用的位数最少，但如何访问长度不一的counter是个大问题。不管怎么样，在不考虑增删操作的情况下，我们想要达到的目标就是在保证查询操作快速的基础上，使得存储位数尽量接近N。

SBF并没有发明什么异乎寻常的高超技巧，和你大概能想到的一样，**它构建了一套索引结构。首先SBF将N位的基本位串分成m/logN段，每一段包含logN个counter，然后将每一段的offset记下来。由于offset要占用logN位，所以记录子串offset的数组（论文中叫Coarse Vector）总长度为m位。**

![](https://img-blog.csdnimg.cn/202006211637520.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3h1c2hpeXUxOTk2ODE4,size_16,color_FFFFFF,t_70)

**有了Coarse Vector，我们就可以随机访问任何一个子串了。**这时我们有两种选择，要么把子串继续分成子段，要么将子串中所有counter的offset记下来（即上图中的OV，Offset Vector）。子串有长有短，但所含counter个数相同，也就是记录counter的offset数组长度相同，这就意味着把长子串用来记录offset比较划算。SBF规定子串长度超过log3N位的，直接用offset数组记录counter位置，否则再继续分。N位基本位串中最多有N/log3N个长度不超过log3N的子串，所以在这一层所有的offset数组加起来长度最多为N/log3N × (logN × logN) = N/logN位。

长度不超过log3N位的子串，我们将其再分成loglogN段，每一段包含logN/loglogN个counter。由于offset要占用loglog3N = 3loglogN位，所以整个offset数组总长度为3loglogN ×logN/loglogN = 3logN位。这一层所有的offset数组加起来长度最多为m/logN × 3logN ＝ 3m位。

并不是子串的每一个子段都用offset数组来存储counter的位置，和前面一样，仍然只记录较长的子段。假设子段长度为T，这里的阀值设为T0 = (loglogN)3，当T > T0时，子段的counter位置用offset数组记录。由于子段包含loglogN个counter，且每一个offset可以用3loglogN位表示，因此offset数组的长度最多为loglogN × 3loglogN ＝ 3(loglogN)2 « T。这一层的所有的offset数组长度加起来也不过O(N)。

现在就剩了T ≤ T0的情况，这时SBF也不继续分了，而是将所有这类情况存储在一个全局查询表里。关于这个查询表，这里就不多做介绍了，有兴趣的可以去读一下原始论文。总之，**在不考虑增删操作的情况下，SBF的counter存储所要达到的目标就是只使用O(N) + O(m)位，构建时间为O(m)。通过上面构建的复杂的索引结构，这个目标是达到了！**

删除操作相对来说比较好处理，因为它不会导致存储空间的增加。但是也不能坐视不管，因为大量的删除操作会导致本该释放的空间仍然被占用。SBF采取的策略是，**单个删除操作只影响相关的counter，整个存储结构并不更新，但经过一系列连续的删除操作后，整个存储结构会被重建。**

**增加操作稍微麻烦点，因为它意味着原来分配的存储空间不再够用。SBF采取的应对策略有点像我们平时排工作计划时留buffer的做法。**我们在安排工作时，如果一件事估计需要10天才能做完，我们写计划时不会写成刚好10天，因为事态的发展有太多动态变化的因素。**我们会在计划里给自己留一点buffer，将10天的工作写成12天。**

**SBF处理增加操作时也采取相似的策略，它给原本只需要N位的基本位串增加єm（є > 0，m为counter个数）位的buffer**，以应对将来可能出现的增加操作。**SBF将这єm位buffer插入到m个counter之间，每1/є个counter增加1位buffer。当某个counter需要更多位数时，它就找离自己最近的buffer位。如果找到的buffer位就在自己的尾部，就直接用掉它；如果隔了一个或几个counter，它就将隔的这几个counter往后“推”，然后使用腾出来的buffer位。最后，counter移动之后，别忘了索引结构也需要更新。**

到此为止，SBF的基本结构就介绍完毕。**回顾一下，SBF是一种扩展版的counting bloom filter（CBF），它不仅支持membership query，还支持元素在multi-set中的出现频率查询。实际上，前者只是后者的一种特例，membership query无非是元素出现频率为1的查询。元素出现频率用k（哈希函数个数）个counter中的最小值来近似表示。这种近似使得一个元素对应的k个counter中，最小的那个比其它的更有价值。**基于这个考虑，论文作者又对SBF的构建过程进行了优化，并给出了两种优化算法。

在membership query上，由于SBF和CBF都沿用bloom filter的基本结构，因此很难在membership query上提高查询效率。但在查询元素出现频率（大于1的情况）时，由于SBF采用counter中的最小值来近似表示元素的出现频率，使得各个counter的重要性有所差别，因此CBF将counter一视同仁的做法就有提高的空间。

先来看第一种优化算法Minimal Increase。这种算法的思想比较简单，从它的名字大家也能猜出个大概。它的基本思想是：**既然在查询元素出现频率时我们只关心counter的最小值，那在增加元素时我们就只增加最小值。如果有多个counter都是最小值，把它们都增加；如果连续加入r个相同的元素，就把最小值（一个或多个counter）加r，其它counter的值或者维持不变，或者设为最小值加r，看哪一个比较大。**这种算法是一种聪明的偷工减料：原来增加一个元素时要增加k（哈希函数个数）个counter，现在只需要增加最小值。而counter的增加次数一旦减少，就意味着hashing时碰撞的次数减少，因此查询元素出现频率时出错的可能性也就随之降低。经论文作者证明，Minimal Increase使查询错误率降低了k倍。

当然，偷工减料不可能只有好处。**Minimal Increase最大的弊端就是不支持删除操作。**很明显，由于增加元素时增加的counter不确定，因此删除元素时也无从下手。如果将k个counter都减少，就会造成false negative的出现（查询结果表明集合不包含某元素而实际上包含）。由于这个严重的弊端，Minimal Increase的应用前景被大打折扣。

下面我们来看一种既支持增删操作又降低查询错误率的算法Recurring Minimum。这种算法的基本思想是：**发现有可能出错的情况，然后将它们单独处理。**先解释一下什么是recurring minimum。SBF中如果一个元素对应的k个counter中有一个以上都维持最小值，就称它有recurring minimum（RM）。我们发现没有RM（即single minimum）的元素出现查询错误的概率很高，而有RM的元素错误概率很低。因此这种算法将没有RM的元素单独处理，在主SBF之外又增加了一个辅助的SBF，专门用来存储这类元素。由于这类元素所占比例不会太大，因此辅SBF可以只分配较小的空间，比如主SBF的一半大小。

采用Recurring Minimum**增加元素x时，先将x在主SBF对应的k个counter的值增加，然后再判断这k个counter有没有recurring minimum。如果有，就当什么事都没有发生，直接继续；如果没有，就意味着x出错的概率很大，这时我们将x存储在辅SBF上，counter的值设为x在主SBF对应counter的最小值。**

**删除元素和上面的操作类似，由于主SBF没有受算法的影响，所以不会出现false negative。**

在查询一个元素时，先看它在主SBF中有没有recurring minimum。如果有，就返回counter的最小值；否则检查辅SBF中的counter最小值，如果大于0就返回这个值，否则返回主SBF的值。

**由于有recurring minimum的情况本来出错概率就很小，而没有recurring minimum的情况又单独处理，也大大降低了出错概率，所以整个算法的错误率得以降低。Recurring Minimum算法的错误率虽然不及Minimum Increase，但比原来的错误率要好很多，可以说是用更多的空间换取了错误率的大幅降低。**
*** 
## ⭐️⭐️⭐️⭐️⭐️
## Zookeeper怎么实现服务注册？
### 1.ZooKeeper中的节点

ZooKeeper是一个树形结构的目录服务，支持变更推送，因此非常适合作为Dubbo服务的注册中心。

注：在ZooKeeper中，节点分为两类，第一类是指构成集群的机器，我们称之为机器节点；第二类是指数据模型中的数据单元，称之为数据节点ZNode。ZooKeeper将所有数据存储在内存中，数据模型是一棵树(ZNode Tree)，由斜杠（/）进行分割的路径，就是一个ZNode，例如/foo/path1。每个ZNode上都会保存自己的数据内容，同时还会保存一系列属性信息。

在ZooKeeper中，Znode可分为持久节点和临时节点两类，所谓持久节点是指一旦这个ZNode被创建了，除非主动进行ZNode的移除操作，否则这个ZNode将一直保存在ZooKeeper上。而临时节点就不一样了，它的生命周期和客户端会话绑定，一旦客户端会话失效，那么这个客户端创建的所有临时节点都会被移除。

基于ZooKeeper实现的注册中心节点结构示意图:

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210329181409751.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2x1eGluZzIwNQ==,size_16,color_FFFFFF,t_70#pic_center)

/dubbo:这是dubbo在ZooKeeper上创建的根节点；

/dubbo/com.foo.BarService:这是服务节点，代表了Dubbo的一个服务；

/dubbo/com.foo.BarService/providers:这是服务提供者的根节点，其子节点代表了每一个服务真正的提供者；

/dubbo/com.foo.BarService/consumers:这是服务消费者的根节点，其子节点代表每一个服务真正的消费者；

### 2.注册中心的工作流程

接下来以上述的BarService为例，说明注册中心的工作流程。

**1）服务提供方启动**

服务提供者在启动的时候，会在ZooKeeper上注册服务。所谓注册服务，其实就是在ZooKeeper的/dubbo/com.foo.BarService/providers节点下创建一个子节点，并写入自己的URL地址，这就代表了com.foo.BarService这个服务的一个提供者。

**2）服务消费者启动**

服务消费者在启动的时候，会向ZooKeeper注册中心订阅自己的服务。其实，就是读取并订阅ZooKeeper上/dubbo/com.foo.BarService/providers节点下的所有子节点，并解析出所有提供者的URL地址来作为该服务地址列表。

同时，服务消费者还会在ZooKeeper的/dubbo/com.foo.BarService/consumers节点下创建一个临时节点，并写入自己的URL地址，这就代表了com.foo.BarService这个服务的一个消费者。

**3）消费者远程调用提供者**

服务消费者，从提供者地址列表中，基于软负载均衡算法，选一个提供者进行调用，如果调用失败，再选另一个提供者调用。

**4）增加服务提供者**

增加提供者，也就是在providers下面新建子节点。一旦服务提供方有变动，zookeeper就会把最新的服务列表推送给消费者。

**5）减少服务提供者**

所有提供者在ZooKeeper上创建的节点都是临时节点，利用的是临时节点的生命周期和客户端会话相关的特性，因此一旦提供者所在的机器出现故障导致该提供者无法对外提供服务时，该临时节点就会自动从ZooKeeper上删除，同样，zookeeper会把最新的服务列表推送给消费者。

**6）zookeeper如何感知服务下线**  
zookeeper提供了“心跳检测”功能，它会定时向各个服务提供者发送一个请求（实际上建立的是一个 socket 长连接），如果长期没有响应，服务中心就认为该服务提供者已经“挂了”，并将其剔除。

服务消费方会监听zookeeper相应的路径，一旦路径上的数据有任何的变化，zookeeper就会将新的服务列表发送给消费方，消费方在获取到数据后，刷新本地缓存的列表。

**7）ZooKeeper宕机之后**

消费者每次调用服务提供方是不经过ZooKeeper的，消费者只是从zookeeper那里获取服务提供方地址列表。所以当zookeeper宕机之后，不会影响消费者调用服务提供者，影响的是zookeeper宕机之后如果提供者有变动，增加或者减少，无法把最新的服务提供者地址列表推送给消费者，所以消费者感知不到。
*** 
## ⭐️⭐️⭐️⭐️⭐️
## Zookeeper Leader选举过程是怎样的？**什么是Zab协议？**
-------------

Zab协议 的全称是 **Zookeeper Atomic Broadcast** （Zookeeper原子广播）。  
**Zookeeper 是通过 Zab 协议来保证分布式事务的最终一致性**。

1.  Zab协议是为分布式协调服务Zookeeper专门设计的一种 **支持崩溃恢复** 的 **原子广播协议** ，是Zookeeper保证数据一致性的核心算法。Zab借鉴了Paxos算法，但又不像Paxos那样，是一种通用的分布式一致性算法。**它是特别为Zookeeper设计的支持崩溃恢复的原子广播协议**。
    
2.  在Zookeeper中主要依赖Zab协议来实现数据一致性，基于该协议，zk实现了一种主备模型（即Leader和Follower模型）的系统架构来保证集群中各个副本之间数据的一致性。  
    这里的主备系统架构模型，就是指只有一台客户端（Leader）负责处理外部的写事务请求，然后Leader客户端将数据同步到其他Follower节点。
    

Zookeeper 客户端会随机的链接到 zookeeper 集群中的一个节点，如果是读请求，就直接从当前节点中读取数据；如果是写请求，那么节点就会向 Leader 提交事务，Leader 接收到事务提交，会广播该事务，只要超过半数节点写入成功，该事务就会被提交。

**Zab 协议的特性**：  
1）Zab 协议需要确保那些**已经在 Leader 服务器上提交（Commit）的事务最终被所有的服务器提交**。  
2）Zab 协议需要确保**丢弃那些只在 Leader 上被提出而没有被提交的事务**。

![](https://img-blog.csdnimg.cn/img_convert/8bbb6569ac9ec9d0ec33b09cc0dc4213.webp?x-oss-process=image/format,png)

模型图

* * *

Zab 协议实现的作用
-----------

1）**使用一个单一的主进程（Leader）来接收并处理客户端的事务请求**（也就是写请求），并采用了Zab的原子广播协议，将服务器数据的状态变更以 **事务proposal** （事务提议）的形式广播到所有的副本（Follower）进程上去。  
 

2）**保证一个全局的变更序列被顺序引用**。  
Zookeeper是一个树形结构，很多操作都要先检查才能确定是否可以执行，比如P1的事务t1可能是创建节点"/a"，t2可能是创建节点"/a/bb"，只有先创建了父节点"/a"，才能创建子节点"/a/b"。

为了保证这一点，Zab要保证同一个Leader发起的事务要按顺序被apply，同时还要保证只有先前Leader的事务被apply之后，新选举出来的Leader才能再次发起事务。  
 

3）**当主进程出现异常的时候，整个zk集群依旧能正常工作**。

* * *

Zab协议原理
-------

Zab协议要求每个 Leader 都要经历三个阶段：**发现，同步，广播**。

*   **发现**：要求zookeeper集群必须选举出一个 Leader 进程，同时 Leader 会维护一个 Follower 可用客户端列表。将来客户端可以和这些 Follower节点进行通信。
    
*   **同步**：Leader 要负责将本身的数据与 Follower 完成同步，做到多副本存储。这样也是提现了CAP中的高可用和分区容错。Follower将队列中未处理完的请求消费完成后，写入本地事务日志中。
    
*   **广播**：Leader 可以接受客户端新的事务Proposal请求，将新的Proposal请求广播给所有的 Follower。
    

* * *

Zab协议核心
-------

Zab协议的核心：**定义了事务请求的处理方式**

1）所有的事务请求必须由一个全局唯一的服务器来协调处理，这样的服务器被叫做 **Leader服务器**。其他剩余的服务器则是 **Follower服务器**。

2）Leader服务器 负责将一个客户端事务请求，转换成一个 **事务Proposal**，并将该 Proposal 分发给集群中所有的 Follower 服务器，也就是向所有 Follower 节点发送数据广播请求（或数据复制）

3）分发之后Leader服务器需要等待所有Follower服务器的反馈（Ack请求），**在Zab协议中，只要超过半数的Follower服务器进行了正确的反馈**后（也就是收到半数以上的Follower的Ack请求），那么 Leader 就会再次向所有的 Follower服务器发送 Commit 消息，要求其将上一个 事务proposal 进行提交。

![](https://img-blog.csdnimg.cn/img_convert/a69984b0cc8d06e5664880291f202a03.webp?x-oss-process=image/format,png)

事务请求处理

* * *

Zab协议内容
-------

Zab 协议包括两种基本的模式：**崩溃恢复** 和 **消息广播**

协议过程

当整个集群启动过程中，或者当 Leader 服务器出现网络中弄断、崩溃退出或重启等异常时，Zab协议就会 **进入崩溃恢复模式**，选举产生新的Leader。

当选举产生了新的 Leader，同时集群中有过半的机器与该 Leader 服务器完成了状态同步（即数据同步）之后，Zab协议就会退出崩溃恢复模式，**进入消息广播模式**。

这时，如果有一台遵守Zab协议的服务器加入集群，因为此时集群中已经存在一个Leader服务器在广播消息，那么该新加入的服务器自动进入恢复模式：找到Leader服务器，并且完成数据同步。同步完成后，作为新的Follower一起参与到消息广播流程中。  
 

协议状态切换

当Leader出现崩溃退出或者机器重启，亦或是集群中不存在超过半数的服务器与Leader保存正常通信，Zab就会再一次进入崩溃恢复，发起新一轮Leader选举并实现数据同步。同步完成后又会进入消息广播模式，接收事务请求。  
 

保证消息有序

在整个消息广播中，Leader会将每一个事务请求转换成对应的 proposal 来进行广播，并且在广播 事务Proposal 之前，Leader服务器会首先为这个事务Proposal分配一个全局单递增的唯一ID，称之为事务ID（即zxid），由于Zab协议需要保证每一个消息的严格的顺序关系，因此必须将每一个proposal按照其zxid的先后顺序进行排序和处理。

* * *

消息广播
----

1）在zookeeper集群中，数据副本的传递策略就是采用消息广播模式。zookeeper中农数据副本的同步方式与二段提交相似，但是却又不同。二段提交要求协调者必须等到所有的参与者全部反馈ACK确认消息后，再发送commit消息。要求所有的参与者要么全部成功，要么全部失败。二段提交会产生严重的阻塞问题。

2）Zab协议中 Leader 等待 Follower 的ACK反馈消息是指“只要半数以上的Follower成功反馈即可，不需要收到全部Follower反馈”

![](https://img-blog.csdnimg.cn/img_convert/ecda78479a4fd130d7d7351852b7182b.webp?x-oss-process=image/format,png)

消息广播流程图

  
 

消息广播具体步骤

1）客户端发起一个写操作请求。

2）Leader 服务器将客户端的请求转化为事务 Proposal 提案，同时为每个 Proposal 分配一个全局的ID，即zxid。

3）Leader 服务器为每个 Follower 服务器分配一个单独的队列，然后将需要广播的 Proposal 依次放到队列中取，并且根据 FIFO 策略进行消息发送。

4）Follower 接收到 Proposal 后，会首先将其以事务日志的方式写入本地磁盘中，写入成功后向 Leader 反馈一个 Ack 响应消息。

5）Leader 接收到超过半数以上 Follower 的 Ack 响应消息后，即认为消息发送成功，可以发送 commit 消息。

6）Leader 向所有 Follower 广播 commit 消息，同时自身也会完成事务提交。Follower 接收到 commit 消息后，会将上一条事务提交。

**zookeeper 采用 Zab 协议的核心，就是只要有一台服务器提交了 Proposal，就要确保所有的服务器最终都能正确提交 Proposal。这也是 CAP/BASE 实现最终一致性的一个体现。**

**Leader 服务器与每一个 Follower 服务器之间都维护了一个单独的 FIFO 消息队列进行收发消息，使用队列消息可以做到异步解耦。 Leader 和 Follower 之间只需要往队列中发消息即可。如果使用同步的方式会引起阻塞，性能要下降很多。**

* * *

崩溃恢复
----

**一旦 Leader 服务器出现崩溃或者由于网络原因导致 Leader 服务器失去了与过半 Follower 的联系，那么就会进入崩溃恢复模式。**

在 Zab 协议中，为了保证程序的正确运行，整个恢复过程结束后需要选举出一个新的 Leader 服务器。因此 Zab 协议需要一个高效且可靠的 Leader 选举算法，从而确保能够快速选举出新的 Leader 。

Leader 选举算法不仅仅需要让 Leader 自己知道自己已经被选举为 Leader ，同时还需要让集群中的所有其他机器也能够快速感知到选举产生的新 Leader 服务器。

崩溃恢复主要包括两部分：**Leader选举** 和 **数据恢复**

Zab 协议如何保证数据一致性

假设两种异常情况：  
1、一个事务在 Leader 上提交了，并且过半的 Folower 都响应 Ack 了，但是 Leader 在 Commit 消息发出之前挂了。  
2、假设一个事务在 Leader 提出之后，Leader 挂了。

要确保如果发生上述两种情况，数据还能保持一致性，那么 Zab 协议选举算法必须满足以下要求：

**Zab 协议崩溃恢复要求满足以下两个要求**：  
1）**确保已经被 Leader 提交的 Proposal 必须最终被所有的 Follower 服务器提交**。  
2）**确保丢弃已经被 Leader 提出的但是没有被提交的 Proposal**。

根据上述要求  
Zab协议需要保证选举出来的Leader需要满足以下条件：  
1）**新选举出来的 Leader 不能包含未提交的 Proposal** 。  
即新选举的 Leader 必须都是已经提交了 Proposal 的 Follower 服务器节点。  
2）**新选举的 Leader 节点中含有最大的 zxid** 。  
这样做的好处是可以避免 Leader 服务器检查 Proposal 的提交和丢弃工作。  
 

Zab 如何数据同步

1）完成 Leader 选举后（新的 Leader 具有最高的zxid），在正式开始工作之前（接收事务请求，然后提出新的 Proposal），Leader 服务器会首先确认事务日志中的所有的 Proposal 是否已经被集群中过半的服务器 Commit。

2）Leader 服务器需要确保所有的 Follower 服务器能够接收到每一条事务的 Proposal ，并且能将所有已经提交的事务 Proposal 应用到内存数据中。等到 Follower 将所有尚未同步的事务 Proposal 都从 Leader 服务器上同步过啦并且应用到内存数据中以后，Leader 才会把该 Follower 加入到真正可用的 Follower 列表中。  
 

Zab 数据同步过程中，如何处理需要丢弃的 Proposal

在 Zab 的事务编号 zxid 设计中，zxid是一个64位的数字。

其中低32位可以看成一个简单的单增计数器，针对客户端每一个事务请求，Leader 在产生新的 Proposal 事务时，都会对该计数器加1。而高32位则代表了 Leader 周期的 epoch 编号。

> epoch 编号可以理解为当前集群所处的年代，或者周期。每次Leader变更之后都会在 epoch 的基础上加1，这样旧的 Leader 崩溃恢复之后，其他Follower 也不会听它的了，因为 Follower 只服从epoch最高的 Leader 命令。

每当选举产生一个新的 Leader ，就会从这个 Leader 服务器上取出本地事务日志充最大编号 Proposal 的 zxid，并从 zxid 中解析得到对应的 epoch 编号，然后再对其加1，之后该编号就作为新的 epoch 值，并将低32位数字归零，由0开始重新生成zxid。

**Zab 协议通过 epoch 编号来区分 Leader 变化周期**，能够有效避免不同的 Leader 错误的使用了相同的 zxid 编号提出了不一样的 Proposal 的异常情况。

基于以上策略  
**当一个包含了上一个 Leader 周期中尚未提交过的事务 Proposal 的服务器启动时，当这台机器加入集群中，以 Follower 角色连上 Leader 服务器后，Leader 服务器会根据自己服务器上最后提交的 Proposal 来和 Follower 服务器的 Proposal 进行比对，比对的结果肯定是 Leader 要求 Follower 进行一个回退操作，回退到一个确实已经被集群中过半机器 Commit 的最新 Proposal**。

* * *

实现原理
----

**Zab 节点有三种状态**：

*   Following：当前节点是跟随者，服从 Leader 节点的命令。
*   Leading：当前节点是 Leader，负责协调事务。
*   Election/Looking：节点处于选举状态，正在寻找 Leader。

代码实现中，多了一种状态：Observing 状态  
这是 Zookeeper 引入 Observer 之后加入的，Observer 不参与选举，是只读节点，跟 Zab 协议没有关系。

**节点的持久状态**：

*   history：当前节点接收到事务 Proposal 的Log
*   acceptedEpoch：Follower 已经接受的 Leader 更改 epoch 的 newEpoch 提议。
*   currentEpoch：当前所处的 Leader 年代
*   lastZxid：history 中最近接收到的Proposal 的 zxid（最大zxid）  
     

Zab 的四个阶段

**1、选举阶段（Leader Election）**  
节点在一开始都处于选举节点，只要有一个节点得到超过半数节点的票数，它就可以当选准 Leader，只有到达第三个阶段（也就是同步阶段），这个准 Leader 才会成为真正的 Leader。

**Zookeeper 规定所有有效的投票都必须在同一个 轮次 中，每个服务器在开始新一轮投票时，都会对自己维护的 logicalClock 进行自增操作**。

每个服务器在广播自己的选票前，会将自己的投票箱（recvset）清空。该投票箱记录了所受到的选票。  
例如：Server\_2 投票给 Server\_3，Server\_3 投票给 Server\_1，则Server_1的投票箱为(2,3)、(3,1)、(1,1)。（每个服务器都会默认给自己投票）

前一个数字表示投票者，后一个数字表示被选举者。票箱中只会记录每一个投票者的最后一次投票记录，如果投票者更新自己的选票，则其他服务器收到该新选票后会在自己的票箱中更新该服务器的选票。

**这一阶段的目的就是为了选出一个准 Leader ，然后进入下一个阶段。**  
协议并没有规定详细的选举算法，后面会提到实现中使用的 Fast Leader Election。

![](https://img-blog.csdnimg.cn/img_convert/825b10a09607e37b7fac04f75d4580a3.webp?x-oss-process=image/format,png)

选举流程

  
 

**2、发现阶段（Descovery）**  
在这个阶段，Followers 和上一轮选举出的准 Leader 进行通信，同步 Followers 最近接收的事务 Proposal 。  
一个 Follower 只会连接一个 Leader，如果一个 Follower 节点认为另一个 Follower 节点，则会在尝试连接时被拒绝。被拒绝之后，该节点就会进入 Leader Election阶段。

**这个阶段的主要目的是发现当前大多数节点接收的最新 Proposal，并且准 Leader 生成新的 epoch ，让 Followers 接收，更新它们的 acceptedEpoch**。

![](https://img-blog.csdnimg.cn/img_convert/937b6cb405ea377e317913ab3223668b.webp?x-oss-process=image/format,png)

发现流程

  
 

**3、同步阶段（Synchronization）**  
**同步阶段主要是利用 Leader 前一阶段获得的最新 Proposal 历史，同步集群中所有的副本**。  
只有当 quorum（超过半数的节点） 都同步完成，准 Leader 才会成为真正的 Leader。Follower 只会接收 zxid 比自己 lastZxid 大的 Proposal。

![](https://img-blog.csdnimg.cn/img_convert/f179f84ddf4c21056abd15024542dfd1.png)

同步流程

  
 

**4、广播阶段（Broadcast）**  
到了这个阶段，Zookeeper 集群才能正式对外提供事务服务，并且 Leader 可以进行消息广播。同时，如果有新的节点加入，还需要对新节点进行同步。  
需要注意的是，Zab 提交事务并不像 2PC 一样需要全部 Follower 都 Ack，只需要得到 quorum（超过半数的节点）的Ack 就可以。

![](https://img-blog.csdnimg.cn/img_convert/a575aff8560a9b94bb75ef9c3f62e790.png)

广播流程

* * *

协议实现
----

协议的 Java 版本实现跟上面的定义略有不同，选举阶段使用的是 Fast Leader Election（FLE），它包含了步骤1的发现指责。因为FLE会选举拥有最新提议的历史节点作为 Leader，这样就省去了发现最新提议的步骤。

实际的实现将发现和同步阶段合并为 Recovery Phase（恢复阶段），所以，Zab 的实现实际上有三个阶段。

Zab协议三个阶段：

1）**选举（Fast Leader Election）**  
2）**恢复（Recovery Phase）**  
3）**广播（Broadcast Phase）**

**Fast Leader Election（快速选举）**  
前面提到的 FLE 会选举拥有最新Proposal history （lastZxid最大）的节点作为 Leader，这样就省去了发现最新提议的步骤。**这是基于拥有最新提议的节点也拥有最新的提交记录**

*   **成为 Leader 的条件：**  
    1）选 epoch 最大的  
    2）若 epoch 相等，选 zxid 最大的  
    3）若 epoch 和 zxid 相等，选择 server_id 最大的（zoo.cfg中的myid）

节点在选举开始时，都默认投票给自己，当接收其他节点的选票时，会根据上面的 **Leader条件** 判断并且更改自己的选票，然后重新发送选票给其他节点。**当有一个节点的得票超过半数，该节点会设置自己的状态为 Leading ，其他节点会设置自己的状态为 Following**。

![](https://img-blog.csdnimg.cn/img_convert/667db36fc93f0b97fd4a428f72a3cdfd.webp?x-oss-process=image/format,png)

选举过程

  
 

**Recovery Phase（恢复阶段）**  
这一阶段 Follower 发送他们的 lastZxid 给 Leader，Leader 根据 lastZxid 决定如何同步数据。这里的实现跟前面的 Phase 2 有所不同：Follower 收到 TRUNC 指令会终止 L.lastCommitedZxid 之后的 Proposal ，收到 DIFF 指令会接收新的 Proposal。

> history.lastCommitedZxid：最近被提交的 Proposal zxid  
> history.oldThreshold：被认为已经太旧的已经提交的 Proposal zxid
> 
>  
> 
> ![](https://img-blog.csdnimg.cn/img_convert/621a4e5260d84b1214fda80dae62e6bb.webp?x-oss-process=image/format,png)
> 
> 恢复阶段

* * *

什么情况下zab协议会进入崩溃恢复模式？
====================

*   1、当服务器启动时
    
*   2、当leader 服务器出现网络中断，崩溃或者重启的情况
    
*   3、当集群中已经不存在过半的服务器与Leader服务器保持正常通信。
    

* * *

zab协议进入崩溃恢复模式会做什么？
==================

1、当leader出现问题，zab协议进入崩溃恢复模式，并且选举出新的leader。当新的leader选举出来以后，如果集群中已经有过半机器完成了leader服务器的状态同（数据同步），退出崩溃恢复，进入消息广播模式。

2、当新的机器加入到集群中的时候，如果已经存在leader服务器，那么新加入的服务器就会自觉进入崩溃恢复模式，找到leader进行数据同步。

特殊情况下需要解决的两个问题：
===============

### 问题一：已经被处理的事务请求（proposal）不能丢（commit的）

> 当 leader 收到合法数量 follower 的 ACKs 后，就向各个 follower 广播 COMMIT 命令，同时也会在本地执行 COMMIT 并向连接的客户端返回「成功」。但是如果在各个 follower 在收到 COMMIT 命令前 leader 就挂了，导致剩下的服务器并没有执行都这条消息。

*   如何解决 _已经被处理的事务请求（proposal）不能丢（commit的）_ 呢？

1、选举拥有 proposal 最大值（即 zxid 最大） 的节点作为新的 leader。

> 由于所有提案被 COMMIT 之前必须有合法数量的 follower ACK，即必须有合法数量的服务器的事务日志上有该提案的 proposal，因此，zxid最大也就是数据最新的节点保存了所有被 COMMIT 消息的 proposal 状态。

2、新的 leader 将自己事务日志中 proposal 但未 COMMIT 的消息处理。

3、新的 leader 与 follower 建立先进先出的队列， 先将自身有而 follower 没有的 proposal 发送给 follower，再将这些 proposal 的 COMMIT 命令发送给 follower，以保证所有的 follower 都保存了所有的 proposal、所有的 follower 都处理了所有的消息。通过以上策略，能保证已经被处理的消息不会丢。

### 问题二：没被处理的事务请求（proposal）不能再次出现什么时候会出现事务请求被丢失呢？

> 当 leader 接收到消息请求生成 proposal 后就挂了，其他 follower 并没有收到此 proposal，因此经过恢复模式重新选了 leader 后，这条消息是被跳过的。 此时，之前挂了的 leader 重新启动并注册成了 follower，他保留了被跳过消息的 proposal 状态，与整个系统的状态是不一致的，需要将其删除。

*   如果解决呢？

Zab 通过巧妙的设计 zxid 来实现这一目的。

一个 zxid 是64位，高 32 是纪元（epoch）编号，每经过一次 leader 选举产生一个新的 leader，新 leader 会将 epoch 号 +1。低 32 位是消息计数器，每接收到一条消息这个值 +1，新 leader 选举后这个值重置为 0。

这样设计的好处是旧的 leader 挂了后重启，它不会被选举为 leader，因为此时它的 zxid 肯定小于当前的新 leader。当旧的 leader 作为 follower 接入新的 leader 后，新的 leader 会让它将所有的拥有旧的 epoch 号的未被 COMMIT 的 proposal 清除。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## Zookeeper是怎么保证数据一致性的？**什么是Zab协议？**
-------------

Zab协议 的全称是 **Zookeeper Atomic Broadcast** （Zookeeper原子广播）。  
**Zookeeper 是通过 Zab 协议来保证分布式事务的最终一致性**。

1.  Zab协议是为分布式协调服务Zookeeper专门设计的一种 **支持崩溃恢复** 的 **原子广播协议** ，是Zookeeper保证数据一致性的核心算法。Zab借鉴了Paxos算法，但又不像Paxos那样，是一种通用的分布式一致性算法。**它是特别为Zookeeper设计的支持崩溃恢复的原子广播协议**。
    
2.  在Zookeeper中主要依赖Zab协议来实现数据一致性，基于该协议，zk实现了一种主备模型（即Leader和Follower模型）的系统架构来保证集群中各个副本之间数据的一致性。  
    这里的主备系统架构模型，就是指只有一台客户端（Leader）负责处理外部的写事务请求，然后Leader客户端将数据同步到其他Follower节点。
    

Zookeeper 客户端会随机的链接到 zookeeper 集群中的一个节点，如果是读请求，就直接从当前节点中读取数据；如果是写请求，那么节点就会向 Leader 提交事务，Leader 接收到事务提交，会广播该事务，只要超过半数节点写入成功，该事务就会被提交。

**Zab 协议的特性**：  
1）Zab 协议需要确保那些**已经在 Leader 服务器上提交（Commit）的事务最终被所有的服务器提交**。  
2）Zab 协议需要确保**丢弃那些只在 Leader 上被提出而没有被提交的事务**。

![](https://img-blog.csdnimg.cn/img_convert/8bbb6569ac9ec9d0ec33b09cc0dc4213.webp?x-oss-process=image/format,png)

模型图

* * *

Zab 协议实现的作用
-----------

1）**使用一个单一的主进程（Leader）来接收并处理客户端的事务请求**（也就是写请求），并采用了Zab的原子广播协议，将服务器数据的状态变更以 **事务proposal** （事务提议）的形式广播到所有的副本（Follower）进程上去。  
 

2）**保证一个全局的变更序列被顺序引用**。  
Zookeeper是一个树形结构，很多操作都要先检查才能确定是否可以执行，比如P1的事务t1可能是创建节点"/a"，t2可能是创建节点"/a/bb"，只有先创建了父节点"/a"，才能创建子节点"/a/b"。

为了保证这一点，Zab要保证同一个Leader发起的事务要按顺序被apply，同时还要保证只有先前Leader的事务被apply之后，新选举出来的Leader才能再次发起事务。  
 

3）**当主进程出现异常的时候，整个zk集群依旧能正常工作**。

* * *

Zab协议原理
-------

Zab协议要求每个 Leader 都要经历三个阶段：**发现，同步，广播**。

*   **发现**：要求zookeeper集群必须选举出一个 Leader 进程，同时 Leader 会维护一个 Follower 可用客户端列表。将来客户端可以和这些 Follower节点进行通信。
    
*   **同步**：Leader 要负责将本身的数据与 Follower 完成同步，做到多副本存储。这样也是提现了CAP中的高可用和分区容错。Follower将队列中未处理完的请求消费完成后，写入本地事务日志中。
    
*   **广播**：Leader 可以接受客户端新的事务Proposal请求，将新的Proposal请求广播给所有的 Follower。
    

* * *

Zab协议核心
-------

Zab协议的核心：**定义了事务请求的处理方式**

1）所有的事务请求必须由一个全局唯一的服务器来协调处理，这样的服务器被叫做 **Leader服务器**。其他剩余的服务器则是 **Follower服务器**。

2）Leader服务器 负责将一个客户端事务请求，转换成一个 **事务Proposal**，并将该 Proposal 分发给集群中所有的 Follower 服务器，也就是向所有 Follower 节点发送数据广播请求（或数据复制）

3）分发之后Leader服务器需要等待所有Follower服务器的反馈（Ack请求），**在Zab协议中，只要超过半数的Follower服务器进行了正确的反馈**后（也就是收到半数以上的Follower的Ack请求），那么 Leader 就会再次向所有的 Follower服务器发送 Commit 消息，要求其将上一个 事务proposal 进行提交。

![](https://img-blog.csdnimg.cn/img_convert/a69984b0cc8d06e5664880291f202a03.webp?x-oss-process=image/format,png)

事务请求处理

* * *

Zab协议内容
-------

Zab 协议包括两种基本的模式：**崩溃恢复** 和 **消息广播**

协议过程

当整个集群启动过程中，或者当 Leader 服务器出现网络中弄断、崩溃退出或重启等异常时，Zab协议就会 **进入崩溃恢复模式**，选举产生新的Leader。

当选举产生了新的 Leader，同时集群中有过半的机器与该 Leader 服务器完成了状态同步（即数据同步）之后，Zab协议就会退出崩溃恢复模式，**进入消息广播模式**。

这时，如果有一台遵守Zab协议的服务器加入集群，因为此时集群中已经存在一个Leader服务器在广播消息，那么该新加入的服务器自动进入恢复模式：找到Leader服务器，并且完成数据同步。同步完成后，作为新的Follower一起参与到消息广播流程中。  
 

协议状态切换

当Leader出现崩溃退出或者机器重启，亦或是集群中不存在超过半数的服务器与Leader保存正常通信，Zab就会再一次进入崩溃恢复，发起新一轮Leader选举并实现数据同步。同步完成后又会进入消息广播模式，接收事务请求。  
 

保证消息有序

在整个消息广播中，Leader会将每一个事务请求转换成对应的 proposal 来进行广播，并且在广播 事务Proposal 之前，Leader服务器会首先为这个事务Proposal分配一个全局单递增的唯一ID，称之为事务ID（即zxid），由于Zab协议需要保证每一个消息的严格的顺序关系，因此必须将每一个proposal按照其zxid的先后顺序进行排序和处理。

* * *

消息广播
----

1）在zookeeper集群中，数据副本的传递策略就是采用消息广播模式。zookeeper中农数据副本的同步方式与二段提交相似，但是却又不同。二段提交要求协调者必须等到所有的参与者全部反馈ACK确认消息后，再发送commit消息。要求所有的参与者要么全部成功，要么全部失败。二段提交会产生严重的阻塞问题。

2）Zab协议中 Leader 等待 Follower 的ACK反馈消息是指“只要半数以上的Follower成功反馈即可，不需要收到全部Follower反馈”

![](https://img-blog.csdnimg.cn/img_convert/ecda78479a4fd130d7d7351852b7182b.webp?x-oss-process=image/format,png)

消息广播流程图

  
 

消息广播具体步骤

1）客户端发起一个写操作请求。

2）Leader 服务器将客户端的请求转化为事务 Proposal 提案，同时为每个 Proposal 分配一个全局的ID，即zxid。

3）Leader 服务器为每个 Follower 服务器分配一个单独的队列，然后将需要广播的 Proposal 依次放到队列中取，并且根据 FIFO 策略进行消息发送。

4）Follower 接收到 Proposal 后，会首先将其以事务日志的方式写入本地磁盘中，写入成功后向 Leader 反馈一个 Ack 响应消息。

5）Leader 接收到超过半数以上 Follower 的 Ack 响应消息后，即认为消息发送成功，可以发送 commit 消息。

6）Leader 向所有 Follower 广播 commit 消息，同时自身也会完成事务提交。Follower 接收到 commit 消息后，会将上一条事务提交。

**zookeeper 采用 Zab 协议的核心，就是只要有一台服务器提交了 Proposal，就要确保所有的服务器最终都能正确提交 Proposal。这也是 CAP/BASE 实现最终一致性的一个体现。**

**Leader 服务器与每一个 Follower 服务器之间都维护了一个单独的 FIFO 消息队列进行收发消息，使用队列消息可以做到异步解耦。 Leader 和 Follower 之间只需要往队列中发消息即可。如果使用同步的方式会引起阻塞，性能要下降很多。**

* * *

崩溃恢复
----

**一旦 Leader 服务器出现崩溃或者由于网络原因导致 Leader 服务器失去了与过半 Follower 的联系，那么就会进入崩溃恢复模式。**

在 Zab 协议中，为了保证程序的正确运行，整个恢复过程结束后需要选举出一个新的 Leader 服务器。因此 Zab 协议需要一个高效且可靠的 Leader 选举算法，从而确保能够快速选举出新的 Leader 。

Leader 选举算法不仅仅需要让 Leader 自己知道自己已经被选举为 Leader ，同时还需要让集群中的所有其他机器也能够快速感知到选举产生的新 Leader 服务器。

崩溃恢复主要包括两部分：**Leader选举** 和 **数据恢复**

Zab 协议如何保证数据一致性

假设两种异常情况：  
1、一个事务在 Leader 上提交了，并且过半的 Folower 都响应 Ack 了，但是 Leader 在 Commit 消息发出之前挂了。  
2、假设一个事务在 Leader 提出之后，Leader 挂了。

要确保如果发生上述两种情况，数据还能保持一致性，那么 Zab 协议选举算法必须满足以下要求：

**Zab 协议崩溃恢复要求满足以下两个要求**：  
1）**确保已经被 Leader 提交的 Proposal 必须最终被所有的 Follower 服务器提交**。  
2）**确保丢弃已经被 Leader 提出的但是没有被提交的 Proposal**。

根据上述要求  
Zab协议需要保证选举出来的Leader需要满足以下条件：  
1）**新选举出来的 Leader 不能包含未提交的 Proposal** 。  
即新选举的 Leader 必须都是已经提交了 Proposal 的 Follower 服务器节点。  
2）**新选举的 Leader 节点中含有最大的 zxid** 。  
这样做的好处是可以避免 Leader 服务器检查 Proposal 的提交和丢弃工作。  
 

Zab 如何数据同步

1）完成 Leader 选举后（新的 Leader 具有最高的zxid），在正式开始工作之前（接收事务请求，然后提出新的 Proposal），Leader 服务器会首先确认事务日志中的所有的 Proposal 是否已经被集群中过半的服务器 Commit。

2）Leader 服务器需要确保所有的 Follower 服务器能够接收到每一条事务的 Proposal ，并且能将所有已经提交的事务 Proposal 应用到内存数据中。等到 Follower 将所有尚未同步的事务 Proposal 都从 Leader 服务器上同步过啦并且应用到内存数据中以后，Leader 才会把该 Follower 加入到真正可用的 Follower 列表中。  
 

Zab 数据同步过程中，如何处理需要丢弃的 Proposal

在 Zab 的事务编号 zxid 设计中，zxid是一个64位的数字。

其中低32位可以看成一个简单的单增计数器，针对客户端每一个事务请求，Leader 在产生新的 Proposal 事务时，都会对该计数器加1。而高32位则代表了 Leader 周期的 epoch 编号。

> epoch 编号可以理解为当前集群所处的年代，或者周期。每次Leader变更之后都会在 epoch 的基础上加1，这样旧的 Leader 崩溃恢复之后，其他Follower 也不会听它的了，因为 Follower 只服从epoch最高的 Leader 命令。

每当选举产生一个新的 Leader ，就会从这个 Leader 服务器上取出本地事务日志充最大编号 Proposal 的 zxid，并从 zxid 中解析得到对应的 epoch 编号，然后再对其加1，之后该编号就作为新的 epoch 值，并将低32位数字归零，由0开始重新生成zxid。

**Zab 协议通过 epoch 编号来区分 Leader 变化周期**，能够有效避免不同的 Leader 错误的使用了相同的 zxid 编号提出了不一样的 Proposal 的异常情况。

基于以上策略  
**当一个包含了上一个 Leader 周期中尚未提交过的事务 Proposal 的服务器启动时，当这台机器加入集群中，以 Follower 角色连上 Leader 服务器后，Leader 服务器会根据自己服务器上最后提交的 Proposal 来和 Follower 服务器的 Proposal 进行比对，比对的结果肯定是 Leader 要求 Follower 进行一个回退操作，回退到一个确实已经被集群中过半机器 Commit 的最新 Proposal**。

* * *

实现原理
----

**Zab 节点有三种状态**：

*   Following：当前节点是跟随者，服从 Leader 节点的命令。
*   Leading：当前节点是 Leader，负责协调事务。
*   Election/Looking：节点处于选举状态，正在寻找 Leader。

代码实现中，多了一种状态：Observing 状态  
这是 Zookeeper 引入 Observer 之后加入的，Observer 不参与选举，是只读节点，跟 Zab 协议没有关系。

**节点的持久状态**：

*   history：当前节点接收到事务 Proposal 的Log
*   acceptedEpoch：Follower 已经接受的 Leader 更改 epoch 的 newEpoch 提议。
*   currentEpoch：当前所处的 Leader 年代
*   lastZxid：history 中最近接收到的Proposal 的 zxid（最大zxid）  
     

Zab 的四个阶段

**1、选举阶段（Leader Election）**  
节点在一开始都处于选举节点，只要有一个节点得到超过半数节点的票数，它就可以当选准 Leader，只有到达第三个阶段（也就是同步阶段），这个准 Leader 才会成为真正的 Leader。

**Zookeeper 规定所有有效的投票都必须在同一个 轮次 中，每个服务器在开始新一轮投票时，都会对自己维护的 logicalClock 进行自增操作**。

每个服务器在广播自己的选票前，会将自己的投票箱（recvset）清空。该投票箱记录了所受到的选票。  
例如：Server\_2 投票给 Server\_3，Server\_3 投票给 Server\_1，则Server_1的投票箱为(2,3)、(3,1)、(1,1)。（每个服务器都会默认给自己投票）

前一个数字表示投票者，后一个数字表示被选举者。票箱中只会记录每一个投票者的最后一次投票记录，如果投票者更新自己的选票，则其他服务器收到该新选票后会在自己的票箱中更新该服务器的选票。

**这一阶段的目的就是为了选出一个准 Leader ，然后进入下一个阶段。**  
协议并没有规定详细的选举算法，后面会提到实现中使用的 Fast Leader Election。

![](https://img-blog.csdnimg.cn/img_convert/825b10a09607e37b7fac04f75d4580a3.webp?x-oss-process=image/format,png)

选举流程

  
 

**2、发现阶段（Descovery）**  
在这个阶段，Followers 和上一轮选举出的准 Leader 进行通信，同步 Followers 最近接收的事务 Proposal 。  
一个 Follower 只会连接一个 Leader，如果一个 Follower 节点认为另一个 Follower 节点，则会在尝试连接时被拒绝。被拒绝之后，该节点就会进入 Leader Election阶段。

**这个阶段的主要目的是发现当前大多数节点接收的最新 Proposal，并且准 Leader 生成新的 epoch ，让 Followers 接收，更新它们的 acceptedEpoch**。

![](https://img-blog.csdnimg.cn/img_convert/937b6cb405ea377e317913ab3223668b.webp?x-oss-process=image/format,png)

发现流程

  
 

**3、同步阶段（Synchronization）**  
**同步阶段主要是利用 Leader 前一阶段获得的最新 Proposal 历史，同步集群中所有的副本**。  
只有当 quorum（超过半数的节点） 都同步完成，准 Leader 才会成为真正的 Leader。Follower 只会接收 zxid 比自己 lastZxid 大的 Proposal。

![](https://img-blog.csdnimg.cn/img_convert/f179f84ddf4c21056abd15024542dfd1.png)

同步流程

  
 

**4、广播阶段（Broadcast）**  
到了这个阶段，Zookeeper 集群才能正式对外提供事务服务，并且 Leader 可以进行消息广播。同时，如果有新的节点加入，还需要对新节点进行同步。  
需要注意的是，Zab 提交事务并不像 2PC 一样需要全部 Follower 都 Ack，只需要得到 quorum（超过半数的节点）的Ack 就可以。

![](https://img-blog.csdnimg.cn/img_convert/a575aff8560a9b94bb75ef9c3f62e790.png)

广播流程

* * *

协议实现
----

协议的 Java 版本实现跟上面的定义略有不同，选举阶段使用的是 Fast Leader Election（FLE），它包含了步骤1的发现指责。因为FLE会选举拥有最新提议的历史节点作为 Leader，这样就省去了发现最新提议的步骤。

实际的实现将发现和同步阶段合并为 Recovery Phase（恢复阶段），所以，Zab 的实现实际上有三个阶段。

Zab协议三个阶段：

1）**选举（Fast Leader Election）**  
2）**恢复（Recovery Phase）**  
3）**广播（Broadcast Phase）**

**Fast Leader Election（快速选举）**  
前面提到的 FLE 会选举拥有最新Proposal history （lastZxid最大）的节点作为 Leader，这样就省去了发现最新提议的步骤。**这是基于拥有最新提议的节点也拥有最新的提交记录**

*   **成为 Leader 的条件：**  
    1）选 epoch 最大的  
    2）若 epoch 相等，选 zxid 最大的  
    3）若 epoch 和 zxid 相等，选择 server_id 最大的（zoo.cfg中的myid）

节点在选举开始时，都默认投票给自己，当接收其他节点的选票时，会根据上面的 **Leader条件** 判断并且更改自己的选票，然后重新发送选票给其他节点。**当有一个节点的得票超过半数，该节点会设置自己的状态为 Leading ，其他节点会设置自己的状态为 Following**。

![](https://img-blog.csdnimg.cn/img_convert/667db36fc93f0b97fd4a428f72a3cdfd.webp?x-oss-process=image/format,png)

选举过程

  
 

**Recovery Phase（恢复阶段）**  
这一阶段 Follower 发送他们的 lastZxid 给 Leader，Leader 根据 lastZxid 决定如何同步数据。这里的实现跟前面的 Phase 2 有所不同：Follower 收到 TRUNC 指令会终止 L.lastCommitedZxid 之后的 Proposal ，收到 DIFF 指令会接收新的 Proposal。

> history.lastCommitedZxid：最近被提交的 Proposal zxid  
> history.oldThreshold：被认为已经太旧的已经提交的 Proposal zxid
> 
>  
> 
> ![](https://img-blog.csdnimg.cn/img_convert/621a4e5260d84b1214fda80dae62e6bb.webp?x-oss-process=image/format,png)
> 
> 恢复阶段

* * *

什么情况下zab协议会进入崩溃恢复模式？
====================

*   1、当服务器启动时
    
*   2、当leader 服务器出现网络中断，崩溃或者重启的情况
    
*   3、当集群中已经不存在过半的服务器与Leader服务器保持正常通信。
    

* * *

zab协议进入崩溃恢复模式会做什么？
==================

1、当leader出现问题，zab协议进入崩溃恢复模式，并且选举出新的leader。当新的leader选举出来以后，如果集群中已经有过半机器完成了leader服务器的状态同（数据同步），退出崩溃恢复，进入消息广播模式。

2、当新的机器加入到集群中的时候，如果已经存在leader服务器，那么新加入的服务器就会自觉进入崩溃恢复模式，找到leader进行数据同步。

特殊情况下需要解决的两个问题：
===============

### 问题一：已经被处理的事务请求（proposal）不能丢（commit的）

> 当 leader 收到合法数量 follower 的 ACKs 后，就向各个 follower 广播 COMMIT 命令，同时也会在本地执行 COMMIT 并向连接的客户端返回「成功」。但是如果在各个 follower 在收到 COMMIT 命令前 leader 就挂了，导致剩下的服务器并没有执行都这条消息。

*   如何解决 _已经被处理的事务请求（proposal）不能丢（commit的）_ 呢？

1、选举拥有 proposal 最大值（即 zxid 最大） 的节点作为新的 leader。

> 由于所有提案被 COMMIT 之前必须有合法数量的 follower ACK，即必须有合法数量的服务器的事务日志上有该提案的 proposal，因此，zxid最大也就是数据最新的节点保存了所有被 COMMIT 消息的 proposal 状态。

2、新的 leader 将自己事务日志中 proposal 但未 COMMIT 的消息处理。

3、新的 leader 与 follower 建立先进先出的队列， 先将自身有而 follower 没有的 proposal 发送给 follower，再将这些 proposal 的 COMMIT 命令发送给 follower，以保证所有的 follower 都保存了所有的 proposal、所有的 follower 都处理了所有的消息。通过以上策略，能保证已经被处理的消息不会丢。

### 问题二：没被处理的事务请求（proposal）不能再次出现什么时候会出现事务请求被丢失呢？

> 当 leader 接收到消息请求生成 proposal 后就挂了，其他 follower 并没有收到此 proposal，因此经过恢复模式重新选了 leader 后，这条消息是被跳过的。 此时，之前挂了的 leader 重新启动并注册成了 follower，他保留了被跳过消息的 proposal 状态，与整个系统的状态是不一致的，需要将其删除。

*   如果解决呢？

Zab 通过巧妙的设计 zxid 来实现这一目的。

一个 zxid 是64位，高 32 是纪元（epoch）编号，每经过一次 leader 选举产生一个新的 leader，新 leader 会将 epoch 号 +1。低 32 位是消息计数器，每接收到一条消息这个值 +1，新 leader 选举后这个值重置为 0。

这样设计的好处是旧的 leader 挂了后重启，它不会被选举为 leader，因为此时它的 zxid 肯定小于当前的新 leader。当旧的 leader 作为 follower 接入新的 leader 后，新的 leader 会让它将所有的拥有旧的 epoch 号的未被 COMMIT 的 proposal 清除。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## zookeeper是如何保证事务的顺序一致性的？
zookeeper采用了全局递增的事务Id来标识，所有的proposal（提议）都在被提出的时候加上了zxid，zxid实际上是一个64位的数字，高32位是epoch（时期; 纪元; 世; 新时代）用来标识leader周期，如果有新的leader产生出来，epoch会自增，低32位用来递增计数。当新产生proposal的时候，会依据数据库的两阶段过程，首先会向其他的server发出事务执行请求，如果超过半数的机器都能执行并且能够成功，那么就会开始执行。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Zookeeper 下 Server工作状态```
服务器具有四种状态，分别是LOOKING、FOLLOWING、LEADING、OBSERVING。
LOOKING：寻找Leader状态。当服务器处于该状态时，它会认为当前集群中没有Leader，因此需要进入Leader选举状态。
FOLLOWING：跟随者状态。表明当前服务器角色是Follower。
LEADING：领导者状态。表明当前服务器角色是Leader。
OBSERVING：观察者状态。表明当前服务器角色是Observer。
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 服务器角色```
Leader
事务请求的唯一调度和处理者，保证集群事务处理的顺序性
集群内部各服务的调度者

Follower
处理客户端的非事务请求，转发事务请求给Leader服务器
参与事务请求Proposal的投票
参与Leader选举投票

Observer
3.3.0版本以后引入的一个服务器角色，在不影响集群事务处理能力的基础上提升集群的非事务处理能力
处理客户端的非事务请求，转发事务请求给Leader服务器
不参与任何形式的投票
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## ACL权限控制机制```
1）UGO（User/Group/Others）
目前在Linux/Unix文件系统中使用，也是使用最广泛的权限控制方式。是一种粗粒度的文件系统权限控制模式。

2）ACL（Access Control List）访问控制列表
包括三个方面：

权限模式（Scheme）
IP：从IP地址粒度进行权限控制
Digest：最常用，用类似于 username:password 的权限标识来进行权限配置，便于区分不同应用来进行权限控制
World：最开放的权限控制方式，是一种特殊的digest模式，只有一个权限标识“world:anyone”
Super：超级用户

授权对象
授权对象指的是权限赋予的用户或一个指定实体，例如IP地址或是机器灯。

权限 Permission
CREATE：数据节点创建权限，允许授权对象在该Znode下创建子节点
DELETE：子节点删除权限，允许授权对象删除该数据节点的子节点
READ：数据节点的读取权限，允许授权对象访问该数据节点并读取其数据内容或子节点列表等
WRITE：数据节点更新权限，允许授权对象对该数据节点进行更新操作
ADMIN：数据节点管理权限，允许授权对象对该数据节点进行ACL相关设置操作
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 服务端处理Watcher实现```
1）服务端接收Watcher并存储
接收到客户端请求，处理请求判断是否需要注册Watcher，需要的话将数据节点的节点路径和ServerCnxn（ServerCnxn代表一个客户端和服务端的连接，实现了Watcher的process接口，此时可以看成一个Watcher对象）存储在WatcherManager的WatchTable和watch2Paths中去。

2）Watcher触发
以服务端接收到 setData() 事务请求触发NodeDataChanged事件为例：

封装WatchedEvent
将通知状态（SyncConnected）、事件类型（NodeDataChanged）以及节点路径封装成一个WatchedEvent对象
查询Watcher
从WatchTable中根据节点路径查找Watcher
没找到；说明没有客户端在该数据节点上注册过Watcher
找到；提取并从WatchTable和Watch2Paths中删除对应Watcher（从这里可以看出Watcher在服务端是一次性的，触发一次就失效了）

3）调用process方法来触发Watcher
这里process主要就是通过ServerCnxn对应的TCP连接发送Watcher事件通知。
```
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 客户端注册Watcher实现```
调用getData()/getChildren()/exist()三个API，传入Watcher对象
标记请求request，封装Watcher到WatchRegistration
封装成Packet对象，发服务端发送request
收到服务端响应后，将Watcher注册到ZKWatcherManager中进行管理
请求返回，完成注册。
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Zookeeper Watcher 机制
Zookeeper允许客户端向服务端的某个Znode注册一个Watcher监听，当服务端的一些指定事件触发了这个Watcher，服务端会向指定客户端发送一个事件通知来实现分布式的通知功能，然后客户端根据Watcher通知状态和事件类型做出业务上的改变。

工作机制：
```
客户端注册watcher
服务端处理watcher
客户端回调watcher
```

Watcher特性总结：

* 一次性
无论是服务端还是客户端，一旦一个Watcher被触发，Zookeeper都会将其从相应的存储中移除。这样的设计有效的减轻了服务端的压力，不然对于更新非常频繁的节点，服务端会不断的向客户端发送事件通知，无论对于网络还是服务端的压力都非常大。

* 客户端串行执行
客户端Watcher回调的过程是一个串行同步的过程。

* 轻量
Watcher通知非常简单，只会告诉客户端发生了事件，而不会说明事件的具体内容。
客户端向服务端注册Watcher的时候，并不会把客户端真实的Watcher对象实体传递到服务端，仅仅是在客户端请求中使用boolean类型属性进行了标记。

watcher event异步发送watcher的通知事件从server发送到client是异步的，这就存在一个问题，不同的客户端和服务器之间通过socket进行通信，由于网络延迟或其他因素导致客户端在不通的时刻监听到事件，由于Zookeeper本身提供了ordering guarantee，即客户端监听事件后，才会感知它所监视znode发生了变化。所以我们使用Zookeeper不能期望能够监控到节点每次的变化。Zookeeper只能保证最终的一致性，而无法保证强一致性。

注册watcher getData、exists、getChildren

触发watcher create、delete、setData

当一个客户端连接到一个新的服务器上时，watch将会被以任意会话事件触发。当与一个服务器失去连接的时候，是无法接收到watch的。而当client重新连接时，如果需要的话，所有先前注册过的watch，都会被重新注册。通常这是完全透明的。只有在一个特殊情况下，watch可能会丢失：对于一个未创建的znode的exist watch，如果在客户端断开连接期间被创建了，并且随后在客户端连接上之前又删除了，这种情况下，这个watch事件可能会被丢失。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Zookeeper文件系统
Zookeeper提供一个多层级的节点命名空间（节点称为znode）。与文件系统不同的是，这些节点都可以设置关联的数据，而文件系统中只有文件节点可以存放数据而目录节点不行。

Zookeeper为了保证高吞吐和低延迟，在内存中维护了这个树状的目录结构，这种特性使得Zookeeper不能用于存放大量的数据，每个节点的存放数据上限为1M。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## ZooKeeper提供了什么？
1、文件系统

2、通知机制

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 分布式集群中为什么会有Master？
在分布式环境中，有些业务逻辑只需要集群中的某一台机器进行执行，其他的机器可以共享这个结果，这样可以大大减少重复计算，提高性能，于是就需要进行leader选举。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Zookeeper有哪几种部署模式？
单机模式、伪集群模式、集群模式。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 数据同步有哪些方式？
整个集群完成Leader选举之后，Learner（Follower和Observer的统称）回向Leader服务器进行注册。当Learner服务器想Leader服务器完成注册后，进入数据同步环节。

数据同步流程：（均以消息传递的方式进行）
*  Learner向Learder注册
*  数据同步
*  同步确认

Zookeeper的数据同步通常分为四类：

* 直接差异化同步（DIFF同步）
* 先回滚再差异化同步（TRUNC+DIFF同步）
* 仅回滚同步（TRUNC同步）
* 全量同步（SNAP同步）

在进行数据同步前，Leader服务器会完成数据同步初始化：

* peerLastZxid：从learner服务器注册时发送的ACKEPOCH消息中提取lastZxid（该Learner服务器最后处理的ZXID）
* minCommittedLog：Leader服务器Proposal缓存队列committedLog中最小ZXID
* maxCommittedLog：Leader服务器Proposal缓存队列committedLog中最大ZXID

## 直接差异化同步（DIFF同步）
场景：peerLastZxid介于minCommittedLog和maxCommittedLog之间

## 先回滚再差异化同步（TRUNC+DIFF同步）

场景：当新的Leader服务器发现某个Learner服务器包含了一条自己没有的事务记录，那么就需要让该Learner服务器进行事务回滚--回滚到Leader服务器上存在的，同时也是最接近于peerLastZxid的ZXID

## 仅回滚同步（TRUNC同步）
场景：peerLastZxid 大于 maxCommittedLog

## 全量同步（SNAP同步）

* 场景一：peerLastZxid 小于 minCommittedLog
* 场景二：Leader服务器上没有Proposal缓存队列且peerLastZxid不等于lastProcessZxid

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 集群支持动态添加机器吗？
其实就是水平扩容了，Zookeeper在这方面不太好。两种方式：

* 全部重启：关闭所有Zookeeper服务，修改配置之后启动。不影响之前客户端的会话。
* 逐个重启：在过半存活即可用的原则下，一台机器重启不影响整个集群对外提供服务。这是比较常用的方式。
3.5版本开始支持动态扩容。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 集群最少要几台机器，集群规则是怎样的?
集群规则为2N+1台，N>0，即3台。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说下进程的状态
* 就绪：进程已处于准备好运行的状态，即进程已分配到除CPU外的所有必要资源后，只要再获得CPU，便可立即执行
* 执行：进程已经获得CPU，程序正在执行状态
* 阻塞：正在执行的进程由于发生某事件（如I/O请求、申请缓冲区失败等）暂时无法继续执行的状态

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何处理死锁问题
忽略该问题。例如鸵鸟算法，该算法可以应用在极少发生死锁的的情况下。为什么叫鸵鸟算法呢，因为传说中鸵鸟看到危险就把头埋在地底下，可能鸵鸟觉得看不到危险也就没危险了吧。跟掩耳盗铃有点像。

检测死锁并且恢复。

仔细地对资源进行动态分配，使系统始终处于安全状态以避免死锁。

通过破除死锁四个必要条件之一，来防止死锁产生。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Zookeeper对节点的watch监听通知是永久的吗？为什么不是永久的?
不是。官方声明：一个Watch事件是一个一次性的触发器，当被设置了Watch的数据发生了改变的时候，则服务器将这个改变发送给设置了Watch的客户端，以便通知它们。

为什么不是永久的，举个例子，如果服务端变动频繁，而监听的客户端很多情况下，每次变动都要通知到所有的客户端，给网络和服务器造成很大压力。

一般是客户端执行getData(“/节点A”,true)，如果节点A发生了变更或删除，客户端会得到它的watch事件，但是在之后节点A又发生了变更，而客户端又没有设置watch事件，就不再给客户端发送。

在实际应用中，很多情况下，我们的客户端不需要知道服务端的每一次变动，我只要最新的数据即可。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Zookeeper 和 Dubbo 的关系？
Zookeeper的作用：

zookeeper用来注册服务和进行负载均衡，哪一个服务由哪一个机器来提供必需让调用者知道，简单来说就是ip地址和服务名称的对应关系。当然也可以通过硬编码的方式把这种对应关系在调用方业务代码中实现，但是如果提供服务的机器挂掉调用者无法知晓，如果不更改代码会继续请求挂掉的机器提供服务。zookeeper通过心跳机制可以检测挂掉的机器并将挂掉机器的ip和服务对应关系从列表中删除。至于支持高并发，简单来说就是横向扩展，在不更改代码的情况通过添加机器来提高运算能力。通过添加新的机器向zookeeper注册服务，服务的提供者多了能服务的客户就多了。

dubbo：

是管理中间层的工具，在业务层到数据仓库间有非常多服务的接入和服务提供者需要调度，dubbo提供一个框架解决这个问题。
注意这里的dubbo只是一个框架，至于你架子上放什么是完全取决于你的，就像一个汽车骨架，你需要配你的轮子引擎。这个框架中要完成调度必须要有一个分布式的注册中心，储存所有服务的元数据，你可以用zk，也可以用别的，只是大家都用zk。

zookeeper和dubbo的关系：

Dubbo 的将注册中心进行抽象，它可以外接不同的存储媒介给注册中心提供服务，有 ZooKeeper，Memcached，Redis 等。
引入了 ZooKeeper 作为存储媒介，也就把 ZooKeeper 的特性引进来。首先是负载均衡，单注册中心的承载能力是有限的，在流量达到一定程度的时 候就需要分流，负载均衡就是为了分流而存在的，一个 ZooKeeper 群配合相应的 Web 应用就可以很容易达到负载均衡；资源同步，单单有负载均衡还不 够，节点之间的数据和资源需要同步，ZooKeeper 集群就天然具备有这样的功能；命名服务，将树状结构用于维护全局的服务地址列表，服务提供者在启动 的时候，向 ZooKeeper 上的指定节点 /dubbo/${serviceName}/providers 目录下写入自己的 URL 地址，这个操作就完成了服务的发布。 其他特性还有 Mast 选举，分布式锁等。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Zookeeper的典型应用场景```
数据发布/订阅
负载均衡
命名服务
分布式协调/通知
集群管理
Master选举
分布式锁
分布式队列
```
*** 
## ⭐️⭐️⭐️⭐️⭐️
## ZAB和Paxos算法的联系与区别？
## 相同点

* 两者都存在一个类似于Leader进程的角色，由其负责协调多个Follower进程的运行
* Leader进程都会等待超过半数的Follower做出正确的反馈后，才会将一个提案进行提交
* ZAB协议中，每个Proposal中都包含一个 epoch 值来代表当前的Leader周期，Paxos中名字为Ballot

## 不同点

ZAB用来构建高可用的分布式数据主备系统（Zookeeper），Paxos是用来构建分布式一致性状态机系统。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## ZooKeeper是什么？
ZooKeeper是一个开放源码的分布式协调服务，它是集群的管理者，监视着集群中各个节点的状态根据节点提交的反馈进行下一步合理操作。最终，将简单易用的接口和性能高效、功能稳定的系统提供给用户。

分布式应用程序可以基于Zookeeper实现诸如数据发布/订阅、负载均衡、命名服务、分布式协调/通知、集群管理、Master选举、分布式锁和分布式队列等功能。

Zookeeper保证了如下分布式一致性特性：
```
顺序一致性
原子性
单一视图
可靠性
实时性（最终一致性）
```

客户端的读请求可以被集群中的任意一台机器处理，如果读请求在节点上注册了监听器，这个监听器也是由所连接的zookeeper机器来处理。对于写请求，这些请求会同时发给其他zookeeper机器并且达成一致后，请求才会返回成功。因此，随着zookeeper的集群机器增多，读请求的吞吐会提高但是写请求的吞吐会下降。

有序性是zookeeper中非常重要的一个特性，所有的更新都是全局有序的，每个更新都有一个唯一的时间戳，这个时间戳称为zxid（Zookeeper Transaction Id）。而读请求只会相对于更新有序，也就是读请求的返回结果中会带有这个zookeeper最新的zxid。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Zookeeper怎么实现分布式锁？
有了zookeeper的一致性文件系统，锁的问题变得容易。锁服务可以分为两类，一个是保持独占，另一个是控制时序。

对于第一类，我们将zookeeper上的一个znode看作是一把锁，通过createznode的方式来实现。所有客户端都去创建 /distribute_lock 节点，最终成功创建的那个客户端也即拥有了这把锁。用完删除掉自己创建的distribute_lock 节点就释放出锁。

对于第二类， /distribute_lock 已经预先存在，所有客户端在它下面创建临时顺序编号目录节点，和选master一样，编号最小的获得锁，用完删除，依次方便。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 了解过Zookeeper的ZAB协议吗？
ZAB协议是为分布式协调服务Zookeeper专门设计的一种支持崩溃恢复的原子广播协议。

ZAB协议包括两种基本的模式：崩溃恢复和消息广播。

当整个zookeeper集群刚刚启动或者Leader服务器宕机、重启或者网络故障导致不存在过半的服务器与Leader服务器保持正常通信时，所有进程（服务器）进入崩溃恢复模式，首先选举产生新的Leader服务器，然后集群中Follower服务器开始与新的Leader服务器进行数据同步，当集群中超过半数机器与该Leader服务器完成数据同步之后，退出恢复模式进入消息广播模式，Leader服务器开始接收客户端的事务请求生成事物提案来进行事务请求处理。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Zookeeper有哪些节点类型？
* PERSISTENT-持久节点
除非手动删除，否则节点一直存在于Zookeeper上

* EPHEMERAL-临时节点
临时节点的生命周期与客户端会话绑定，一旦客户端会话失效（客户端与zookeeper连接断开不一定会话失效），那么这个客户端创建的所有临时节点都会被移除。

* PERSISTENT_SEQUENTIAL-持久顺序节点
基本特性同持久节点，只是增加了顺序属性，节点名后边会追加一个由父节点维护的自增整型数字。

* EPHEMERAL_SEQUENTIAL-临时顺序节点
基本特性同临时节点，增加了顺序属性，节点名后边会追加一个由父节点维护的自增整型数字。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Tomcat一个请求的完整过程```
首先 dns 解析 wo.de.tian机器，一般是ng服务器ip地址 
然后 ng根据server的配置，寻找路径为 yy/的机器列表，ip和端口 
最后 选择其中一台机器进行访问—->下面为详细过程

1) 请求被发送到本机端口8080，被在那里侦听的Coyote HTTP/1.1 Connector获得 
2) Connector把该请求交给它所在的Service的Engine来处理，并等待来自Engine的回应 
3) Engine获得请求localhost/yy/index.jsp，匹配它所拥有的所有虚拟主机Host 
4) Engine匹配到名为localhost的Host（即使匹配不到也把请求交给该Host处理，因为该Host被定义为该Engine的默认主机） 
5) localhost Host获得请求/yy/index.jsp，匹配它所拥有的所有Context 
6) Host匹配到路径为/yy的Context（如果匹配不到就把该请求交给路径名为”“的Context去处理） 
7) path=”/yy”的Context获得请求/index.jsp，在它的mapping table中寻找对应的servlet 
8) Context匹配到URL PATTERN为*.jsp的servlet，对应于JspServlet类 
9) 构造HttpServletRequest对象和HttpServletResponse对象，作为参数调用JspServlet的doGet或doPost方法 
10)Context把执行完了之后的HttpServletResponse对象返回给Host 
11)Host把HttpServletResponse对象返回给Engine 
12)Engine把HttpServletResponse对象返回给Connector 
13)Connector把HttpServletResponse对象返回给客户browser
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## zk节点宕机如何处理？
Zookeeper本身也是集群，推荐配置不少于3个服务器。Zookeeper自身也要保证当一个节点宕机时，其他节点会继续提供服务。

如果是一个Follower宕机，还有2台服务器提供访问，因为Zookeeper上的数据是有多个副本的，数据并不会丢失；

如果是一个Leader宕机，Zookeeper会选举出新的Leader。

ZK集群的机制是只要超过半数的节点正常，集群就能正常提供服务。只有在ZK节点挂得太多，只剩一半或不到一半节点能工作，集群才失效。

所以:

3个节点的cluster可以挂掉1个节点(leader可以得到2票>1.5)

2个节点的cluster就不能挂掉任何1个节点了(leader可以得到1票<=1)

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何添加JMS远程监控
```
对于部署在局域网内其它机器上的Tomcat，可以打开JMX监控端口，局域网其它机器就可以通过这个端口查看一些常用的参数（但一些比较复杂的功能不支持），同样是在JVM启动参数中配置即可，配置如下： 
-Dcom.sun.management.jmxremote.ssl=false  -Dcom.sun.management.jmxremote.authenticate=false 
-Djava.rmi.server.hostname=192.168.71.38 设置JVM的JMS监控监听的IP地址，主要是为了防止错误的监听成127.0.0.1这个内网地址 
-Dcom.sun.management.jmxremote.port=1090 设置JVM的JMS监控的端口 
-Dcom.sun.management.jmxremote.ssl=false 设置JVM的JMS监控不实用SSL 
-Dcom.sun.management.jmxremote.authenticate=false 设置JVM的JMS监控不需要认证

```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## tomcat共享session如何处理？
目前的处理方式有如下几种： 
```
1).使用Tomcat本身的Session复制功能 
参考http://ajita.iteye.com/blog/1715312（Session复制的配置） 
方案的有点是配置简单，缺点是当集群数量较多时，Session复制的时间会比较长，影响响应的效率 
2).使用第三方来存放共享Session 
目前用的较多的是使用memcached来管理共享Session，借助于memcached-sesson-manager来进行Tomcat的Session管理 
参考http://ajita.iteye.com/blog/1716320（使用MSM管理Tomcat集群session） 
3).使用黏性session的策略 
对于会话要求不太强（不涉及到计费，失败了允许重新请求下等）的场合，同一个用户的session可以由nginx或者apache交给同一个Tomcat来处理，这就是所谓的session sticky策略，目前应用也比较多 

nginx默认不包含session sticky模块，需要重新编译才行（windows下我也不知道怎么重新编译） 
优点是处理效率高多了，缺点是强会话要求的场合不合适 
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## tomcat垃圾回收策略调优了解吗？
```
垃圾回收的设置也是在catalina.sh中，调整JAVA_OPTS变量。 
具体设置如下： 
JAVA_OPTS="$JAVA_OPTS -Xmx3550m -Xms3550m -Xss128k -XX:+UseParallelGC  -XX:MaxGCPauseMillis=100" 
具体的垃圾回收策略及相应策略的各项参数如下： 
串行收集器（JDK1.5以前主要的回收方式） 
-XX:+UseSerialGC:设置串行收集器 
并行收集器（吞吐量优先） 
示例： 
java -Xmx3550m -Xms3550m -Xmn2g -Xss128k -XX:+UseParallelGC  -XX:MaxGCPauseMillis=100 

-XX:+UseParallelGC：选择垃圾收集器为并行收集器。此配置仅对年轻代有效。即上述配置下，年轻代使用并发收集，而年老代仍旧使用串行收集。 
-XX:ParallelGCThreads=20：配置并行收集器的线程数，即：同时多少个线程一起进行垃圾回收。此值最好配置与处理器数目相等。 
-XX:+UseParallelOldGC：配置年老代垃圾收集方式为并行收集。JDK6.0支持对年老代并行收集 
-XX:MaxGCPauseMillis=100:设置每次年轻代垃圾回收的最长时间，如果无法满足此时间，JVM会自动调整年轻代大小，以满足此值。 
-XX:+UseAdaptiveSizePolicy：设置此选项后，并行收集器会自动选择年轻代区大小和相应的Survivor区比例，以达到目标系统规定的最低相应时间或者收集频率等，此值建议使用并行收集器时，一直打开。 
并发收集器（响应时间优先） 
示例：java -Xmx3550m -Xms3550m -Xmn2g -Xss128k -XX:+UseConcMarkSweepGC 
-XX:+UseConcMarkSweepGC：设置年老代为并发收集。测试中配置这个以后，-XX:NewRatio=4的配置失效了，原因不明。所以，此时年轻代大小最好用-Xmn设置。 
-XX:+UseParNewGC: 设置年轻代为并行收集。可与CMS收集同时使用。JDK5.0以上，JVM会根据系统配置自行设置，所以无需再设置此值。 
-XX:CMSFullGCsBeforeCompaction：由于并发收集器不对内存空间进行压缩、整理，所以运行一段时间以后会产生“碎片”，使得运行效率降低。此值设置运行多少次GC以后对内存空间进行压缩、整理。 
-XX:+UseCMSCompactAtFullCollection：打开对年老代的压缩。可能会影响性能，但是可以消除碎片 

```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## tomcat内存调优了解过吗？
```
内存方式的设置是在catalina.sh中，调整一下JAVA_OPTS变量即可，因为后面的启动参数会把JAVA_OPTS作为JVM的启动参数来处理。 
具体设置如下： 
JAVA_OPTS="$JAVA_OPTS -Xmx3550m -Xms3550m -Xss128k -XX:NewRatio=4 -XX:SurvivorRatio=4" 
其各项参数如下： 
-Xmx3550m：设置JVM最大可用内存为3550M。 
-Xms3550m：设置JVM促使内存为3550m。此值可以设置与-Xmx相同，以避免每次垃圾回收完成后JVM重新分配内存。 
-Xmn2g：设置年轻代大小为2G。整个堆大小=年轻代大小 + 年老代大小 + 持久代大小。持久代一般固定大小为64m，所以增大年轻代后，将会减小年老代大小。此值对系统性能影响较大，Sun官方推荐配置为整个堆的3/8。 
-Xss128k：设置每个线程的堆栈大小。JDK5.0以后每个线程堆栈大小为1M，以前每个线程堆栈大小为256K。更具应用的线程所需内存大小进行调整。在相同物理内存下，减小这个值能生成更多的线程。但是操作系统对一个进程内的线程数还是有限制的，不能无限生成，经验值在3000~5000左右。 
-XX:NewRatio=4:设置年轻代（包括Eden和两个Survivor区）与年老代的比值（除去持久代）。设置为4，则年轻代与年老代所占比值为1：4，年轻代占整个堆栈的1/5 
-XX:SurvivorRatio=4：设置年轻代中Eden区与Survivor区的大小比值。设置为4，则两个Survivor区与一个Eden区的比值为2:4，一个Survivor区占整个年轻代的1/6 
-XX:MaxPermSize=16m:设置持久代大小为16m。 
-XX:MaxTenuringThreshold=0：设置垃圾最大年龄。如果设置为0的话，则年轻代对象不经过Survivor区，直接进入年老代。对于年老代比较多的应用，可以提高效率。如果将此值设置为一个较大值，则年轻代对象会在Survivor区进行多次复制，这样可以增加对象再年轻代的存活时间，增加在年轻代即被回收的概论。 

```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## tomcat 如何优化？
```
1、优化连接配置.这里以tomcat7的参数配置为例，需要修改conf/server.xml文件，修改连接数，关闭客户端dns查询。

参数解释：

URIEncoding=”UTF-8″ :使得tomcat可以解析含有中文名的文件的url，真方便，不像apache里还有搞个mod_encoding，还要手工编译

maxSpareThreads : 如果空闲状态的线程数多于设置的数目，则将这些线程中止，减少这个池中的线程总数。

minSpareThreads : 最小备用线程数，tomcat启动时的初始化的线程数。

enableLookups : 这个功效和Apache中的HostnameLookups一样，设为关闭。

connectionTimeout : connectionTimeout为网络连接超时时间毫秒数。

maxThreads : maxThreads Tomcat使用线程来处理接收的每个请求。这个值表示Tomcat可创建的最大的线程数，即最大并发数。

acceptCount : acceptCount是当线程数达到maxThreads后，后续请求会被放入一个等待队列，这个acceptCount是这个队列的大小，如果这个队列也满了，就直接refuse connection

maxProcessors与minProcessors : 在 Java中线程是程序运行时的路径，是在一个程序中与其它控制线程无关的、能够独立运行的代码段。它们共享相同的地址空间。多线程帮助程序员写出CPU最 大利用率的高效程序，使空闲时间保持最低，从而接受更多的请求。

通常Windows是1000个左右，Linux是2000个左右。

useURIValidationHack:

我们来看一下tomcat中的一段源码：

【security】

if (connector.getUseURIValidationHack()) {

String uri = validate(request.getRequestURI());

if (uri == null) {

res.setStatus(400);

res.setMessage(“Invalid URI”);

throw new IOException(“Invalid URI”);

} else {

req.requestURI().setString(uri);

// Redoing the URI decoding

req.decodedURI().duplicate(req.requestURI());

req.getURLDecoder().convert(req.decodedURI(), true);

可以看到如果把useURIValidationHack设成”false”，可以减少它对一些url的不必要的检查从而减省开销。

enableLookups=”false” ： 为了消除DNS查询对性能的影响我们可以关闭DNS查询，方式是修改server.xml文件中的enableLookups参数值。

disableUploadTimeout ：类似于Apache中的keeyalive一样

给Tomcat配置gzip压缩(HTTP压缩)功能

compression=”on” compressionMinSize=”2048″

compressableMimeType=”text/html,text/xml,text/JavaScript,text/css,text/plain”

HTTP 压缩可以大大提高浏览网站的速度，它的原理是，在客户端请求网页后，从服务器端将网页文件压缩，再下载到客户端，由客户端的浏览器负责解压缩并浏览。相对于普通的浏览过程HTML,CSS,javascript , Text ，它可以节省40%左右的流量。更为重要的是，它可以对动态生成的，包括CGI、PHP , JSP , ASP , Servlet,SHTML等输出的网页也能进行压缩，压缩效率惊人。

1)compression=”on” 打开压缩功能

2)compressionMinSize=”2048″ 启用压缩的输出内容大小，这里面默认为2KB

3)noCompressionUserAgents=”gozilla, traviata” 对于以下的浏览器，不启用压缩

4)compressableMimeType=”text/html,text/xml”　压缩类型

最后不要忘了把8443端口的地方也加上同样的配置，因为如果我们走https协议的话，我们将会用到8443端口这个段的配置，对吧？

<!–enable tomcat ssl–>

<Connector port=”8443″ protocol=”HTTP/1.1″

URIEncoding=”UTF-8″ minSpareThreads=”25″ maxSpareThreads=”75″

enableLookups=”false” disableUploadTimeout=”true” connectionTimeout=”20000″

acceptCount=”300″ maxThreads=”300″ maxProcessors=”1000″ minProcessors=”5″

useURIValidationHack=”false”

compression=”on” compressionMinSize=”2048″

compressableMimeType=”text/html,text/xml,text/javascript,text/css,text/plain”

SSLEnabled=”true”

scheme=”https” secure=”true”

clientAuth=”false” sslProtocol=”TLS”

keystoreFile=”d:/tomcat2/conf/shnlap93.jks” keystorePass=”aaaaaa”

/>

好了，所有的Tomcat优化的地方都加上了。

```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## tomcat容器是如何创建servlet类实例？用到了什么原理？
当容器启动时，会读取在webapps目录下所有的web应用中的web.xml文件，然后对xml文件进行解析，

并读取servlet注册信息。然后，将每个应用中注册的servlet类都进行加载，并通过反射的方式实例化。

（有时候也是在第一次请求时实例化）在servlet注册时加上如果为正数，则在一开始就实例化，

如果不写或为负数，则第一次请求实例化。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Tomcat有几种部署方式？
1）直接把Web项目放在webapps下，Tomcat会自动将其部署

2）在server.xml文件上配置 Context 节点，设置相关的属性即可

3）通过Catalina来进行配置:进入到conf\Catalina\localhost文件下，创建一个xml文件，该文件的名字就是站点的名字。

编写XML的方式来进行设置。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## tomcat 有哪几种Connector 运行模式(优化)？
```
bio：传统的Java I/O操作，同步且阻塞IO。
maxThreads="150"//Tomcat使用线程来处理接收的每个请求。这个值表示Tomcat可创建的最大的线程数。默认值200。可以根据机器的时期性能和内存大小调整，一般可以在400-500。最大可以在800左右。 
minSpareThreads="25"---Tomcat初始化时创建的线程数。默认值4。如果当前没有空闲线程，且没有超过maxThreads，一次性创建的空闲线程数量。Tomcat初始化时创建的线程数量也由此值设置。 
maxSpareThreads="75"--一旦创建的线程超过这个值，Tomcat就会关闭不再需要的socket线程。默认值50。一旦创建的线程超过此数值，Tomcat会关闭不再需要的线程。线程数可以大致上用 “同时在线人数*每秒用户操作次数*系统平均操作时间” 来计算。 
acceptCount="100"----指定当所有可以使用的处理请求的线程数都被使用时，可以放到处理队列中的请求数，超过这个数的请求将不予处理。默认值10。如果当前可用线程数为0，则将请求放入处理队列中。这个值限定了请求队列的大小，超过这个数值的请求将不予处理。 
connectionTimeout="20000" --网络连接超时，默认值20000，单位：毫秒。设置为0表示永不超时，这样设置有隐患的。通常可设置为30000毫秒。 

nio：JDK1.4开始支持，同步阻塞或同步非阻塞IO。
指定使用NIO模型来接受HTTP请求 
protocol="org.apache.coyote.http11.Http11NioProtocol" 指定使用NIO模型来接受HTTP请求。默认是BlockingIO，配置为protocol="HTTP/1.1" 
acceptorThreadCount="2" 使用NIO模型时接收线程的数目 

aio(nio.2)：JDK7开始支持，异步非阻塞IO。

apr：Tomcat将以JNI的形式调用Apache HTTP服务器的核心动态链接库来处理文件读取或网络传输操作，从而大大地 提高Tomcat对静态文件的处理性能。


<!--
      <Connector connectionTimeout="20000" port="8000" protocol="HTTP/1.1" redirectPort="8443" uriEncoding="utf-8"/>
    -->
    <!-- protocol 启用 nio模式，(tomcat8默认使用的是nio)(apr模式利用系统级异步io) -->
    <!-- minProcessors最小空闲连接线程数-->
    <!-- maxProcessors最大连接线程数-->
    <!-- acceptCount允许的最大连接数，应大于等于maxProcessors-->
    <!-- enableLookups 如果为true,requst.getRemoteHost会执行DNS查找，反向解析ip对应域名或主机名-->
    <Connector port="8080" protocol="org.apache.coyote.http11.Http11NioProtocol" 
        connectionTimeout="20000"
        redirectPort="8443
        maxThreads=“500” 
        minSpareThreads=“100” 
        maxSpareThreads=“200”
        acceptCount="200"
        enableLookups="false"       
    />
    
其他配置

maxHttpHeaderSize="8192" http请求头信息的最大程度，超过此长度的部分不予处理。一般8K。 
URIEncoding="UTF-8" 指定Tomcat容器的URL编码格式。 
disableUploadTimeout="true" 上传时是否使用超时机制 
enableLookups="false"--是否反查域名，默认值为true。为了提高处理能力，应设置为false 
compression="on"   打开压缩功能 
compressionMinSize="10240" 启用压缩的输出内容大小，默认为2KB 
noCompressionUserAgents="gozilla, traviata"   对于以下的浏览器，不启用压缩 
compressableMimeType="text/html,text/xml,text/javascript,text/css,text/plain" 哪些资源类型需要压缩 

```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Tomcat的缺省端口是多少，怎么修改？
```
1）找到Tomcat目录下的conf文件夹

2）进入conf文件夹里面找到server.xml文件

3）打开server.xml文件

4）在server.xml文件里面找到下列信息

<Connector connectionTimeout="20000" port="8080" protocol="HTTP/1.1" redirectPort="8443" uriEncoding="utf-8"/>
port="8080"改成你想要的端口
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## SpringCloud Config可以实现实时刷新吗?
springcloud config实时刷新采用 `SpringCloud Bus`消息总线

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring Cloud Bus 原理？
发送端（endpoint）构造事件event，将其publish到context上下文中（spring cloud bus有一个父上下文，bootstrap），然后将事件发送到channel中（json串message），接收端从channel中获取到message，将message转为事件event，然后将event事件publish到context上下文中，最后接收端（Listener）收到event，调用服务进行处理。
整个流程中，只有发送/接收端从context上下文中取事件和发送事件是需要我们在代码中明确写出来的，其它部分都由框架封装完成。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是 Spring Cloud Bus?
Spring Cloud Bus就像个分布式执行器，用于扩展的 Spring Boot应用程序的配置文件，但也可以用作应用程序之间的通信通道。

Spring Cloud Bus不能单独完成通信，需要配合MQ支持

Spring Cloud Bus一般是配合Spring Cloud Config做配置中心的

Spring Cloud config实时刷新也必须采用 SpringCloud Bus消息总线

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何实现动态Zuul网关路由转发？
通过`path`配置拦截请求，通过 `Serviceld`到配置中心获取转发的服务列表，zuul内部使用 `Ribbon`实现本地负载均衡和转发。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## ZuulFilter有哪些常用方法？
`Run()`：过滤器的具体业务逻辑

`shouldFilter()`：判断过滤器是否有效

`filterOrder()`：过滤器执行顺序

`filterType()`：过滤器拦截位置

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是服务雪崩效应?
雪崩效应是在大型互联网项目中，当某个服务发生宕机时，调用这个服务的其他服务也会发生宕机，大型项目的微服务之间的调用是互通的，这样就会将服务的不可用逐步扩大到各个其他服务中，从而使整个项目的服务宕机崩溃。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是服务熔断？什么是服务降级？
## 服务熔断
```
熔断机制是应对`雪崩效应`的一种微服务`链路保护机制`。
当某个微服务不可用或者响应时间太长时，会进行服务降级，进而熔断该节点微服务的调用，快速返回“错误”的响应信息。当检测到该节点微服务调用响应正常后恢复调用链路。
在SpringCloud框架里熔断机制通过`Hystrix`实现，Hystrix会监控微服务间调用的状况，当失败的调用到一定阈值，缺省是5秒内调用20次，如果失败，就会启动熔断机制。
```

## 服务降级

服务降级，一般是从整体负荷考虑。就是当某个服务熔断之后，服务器将不再被调用，此时客户端可以自己准备一个本地的`fallback回调`，返回一个缺省值。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## zuul的工作流程?
在Spring Cloud Netflix中，Zuul巧妙的整合了Eureka来实现面向服务的路由。

实际上，API网关将自己注册到Eureka服务注册中心上，也会从注册中心获取所有服务以及它们的实例清单。在Eureka的帮助下，API网关已经维护了系统中所有`serviceId与实例地址的映射关系`。当有外部请求到达API网关的时候，根据请求的URL找到最匹配的path，API网关就可以知道要将该请求"路由"到哪个具体的serviceId上去。 最终通过`Ribbon的负载均衡策略`实现请求的路由。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是zuul?
zuul是对SpringCloud提供的成熟对的`路由方案`，他会根据请求的路径不同，网关会定位到指定的微服务，并代理请求到不同的微服务接口，他对外隐蔽了微服务的真正接口地址。
三个重要概念：

- `动态路由表`：Zuul支持Eureka路由，手动配置路由，这俩种都支持自动更新

- `路由定位`：根据请求路径，Zuul有自己的一套定位服务规则以及路由表达式匹配

- `反向代理`：客户端请求到路由网关，网关受理之后，在对目标发送请求，拿到响应之后在 给客户端

Zuul的应用场景： 对外暴露，权限校验，服务聚合，日志审计等


*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说说Eureka的自我保护机制？
当一个服务未按时进行心跳续约时，在生产环境下，因为网络延迟等原因，此时就把服务剔除列表并不妥当，因为服务可能没有宕机。 Eureka就会把当前实例的注册信息保护起来，不予剔除。生产环境下这很有效，保证了大多数服务依然可用。但是有可能会造成一些挂掉的服务被剔除有延迟。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Eureka的工作原理？
`Eureka`：服务注册中心（可以是一个集群），对外暴露自己的地址
`提供者`：启动后向Eureka注册自己信息（地址，提供什么服务）
`消费者`：向Eureka订阅服务，Eureka会将对应服务的所有提供者地址列表发送给消费者，并且定期更新
`心跳(续约)`：提供者定期通过http方式向Eureka刷新自己的状态（每30s定时向EurekaServer发起请求）

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Netflix Feign？它的优点是什么？
Feign是受到Retrofit，JAXRS-2.0和WebSocket启发的java客户端联编程序。Feign的第一个目标是将约束分母的复杂性统一到http apis，而不考虑其稳定性。在employee-consumer的例子中，我们使用了employee-producer使用REST模板公开的REST服务。

但是我们必须编写大量代码才能执行以下步骤

- 使用功能区进行负载平衡。
- 获取服务实例，然后获取基本URL。
- 利用REST模板来使用服务。 前面的代码如下

```java
@Controller
public class ConsumerControllerClient {
 
@Autowired
private LoadBalancerClient loadBalancer;
 
public void getEmployee() throws RestClientException, IOException {
 
    ServiceInstance serviceInstance=loadBalancer.choose("employee-producer");
 
    System.out.println(serviceInstance.getUri());
 
    String baseUrl=serviceInstance.getUri().toString();
 
    baseUrl=baseUrl+"/employee";
 
    RestTemplate restTemplate = new RestTemplate();
    ResponseEntity<String> response=null;
    try{
    response=restTemplate.exchange(baseUrl,
            HttpMethod.GET, getHeaders(),String.class);
    }catch (Exception ex)
    {
        System.out.println(ex);
    }
    System.out.println(response.getBody());
}
```

之前的代码，有像NullPointer这样的例外的机会，并不是最优的。我们将看到如何使用Netflix Feign使呼叫变得更加轻松和清洁。如果Netflix Ribbon依赖关系也在类路径中，那么Feign默认也会负责负载平衡。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Hystrix断路器？我们需要它吗？
由于某些原因，employee-consumer公开服务会引发异常。在这种情况下使用Hystrix我们定义了一个回退方法。如果在公开服务中发生异常，则回退方法返回一些默认值。

![image.png](https://ae02.alicdn.com/kf/Hd68c396fc6a5452bb99b044ecfe4c25eO.png)

如果firstPage method() 中的异常继续发生，则Hystrix电路将中断，并且员工使用者将一起跳过firtsPage方法，并直接调用回退方法。 断路器的目的是给第一页方法或第一页方法可能调用的其他方法留出时间，并导致异常恢复。可能发生的情况是，在负载较小的情况下，导致异常的问题有更好的恢复机会 。

![image.png](https://ae01.alicdn.com/kf/H10def95b98ee4f87a8bef48fce1dfd05u.png)

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Hystrix？它如何实现容错？
Hystrix是一个延迟和容错库，旨在隔离远程系统，服务和第三方库的访问点，当出现故障是不可避免的故障时，停止级联故障并在复杂的分布式系统中实现弹性。

通常对于使用微服务架构开发的系统，涉及到许多微服务。这些微服务彼此协作。 

思考以下微服务

![image.png](https://ae02.alicdn.com/kf/Hf2e1a3c90dfc4d4b8bf47fed84f33ce2F.png)

假设如果上图中的微服务9失败了，那么使用传统方法我们将传播一个异常。但这仍然会导致整个系统崩溃。 

随着微服务数量的增加，这个问题变得更加复杂。微服务的数量可以高达1000.这是hystrix出现的地方 我们将使用Hystrix在这种情况下的Fallback方法功能。我们有两个服务employee-consumer使用由employee-consumer公开的服务。 

简化图如下所示 

![image.png](https://ae01.alicdn.com/kf/H1d170470fdc8431e868c5dd1bb676c27w.png)

现在假设由于某种原因，employee-producer公开的服务会抛出异常。我们在这种情况下使用Hystrix定义了一个回退方法。这种后备方法应该具有与公开服务相同的返回类型。如果暴露服务中出现异常，则回退方法将返回一些值。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring Cloud由哪些组件组成？
`Eureka`：服务注册与发现

`Zuul`：服务网关

`Ribbon`：客户端负载均衡

`Feign`：声明性的Web服务客户端

`Hystrix`：断路器

`Config`：分布式统一配置管理

等20几个框架，开源一直在更新

![0e9c7b73ca58fcbd7ee8f5b7c3fe450.png](http://img1.sycdn.imooc.com/5f309a610001d87510410539.jpg)


*** 
## ⭐️⭐️⭐️⭐️⭐️
## 服务注册和发现是什么意思？Spring Cloud如何实现？
当我们开始一个项目时，我们通常在属性文件中进行所有的配置。随着越来越多的服务开发和部署，添加和修改这些属性变得更加复杂。有些服务可能会下降，而某些位置可能会发生变化。手动更改属性可能会产生问题。 Eureka服务注册和发现可以在这种情况下提供帮助。由于所有服务都在Eureka服务器上注册并通过调用Eureka服务器完成查找，因此无需处理服务地点的任何更改和处理。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 使用Spring Cloud有什么优势？
使用Spring Boot开发分布式微服务时，我们面临以下问题

- 与分布式系统相关的复杂性-这种开销包括网络问题，延迟开销，带宽问题，安全问题。
- 服务发现-服务发现工具管理群集中的流程和服务如何查找和互相交谈。它涉及一个服务目录，在该目录中注册服务，然后能够查找并连接到该目录中的服务。
- 冗余-分布式系统中的冗余问题。
- 负载平衡 --负载平衡改善跨多个计算资源的工作负荷，诸如计算机，计算机集群，网络链路，中央处理单元，或磁盘驱动器的分布。
- 性能-问题 由于各种运营开销导致的性能问题。
- 部署复杂性-Devops技能的要求。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是 Spring Cloud？
spring cloud 是一系列框架的有序集合。它利用 spring boot 的开发便利性巧妙地简化了分布式系统基础设施的开发，如服务发现注册、配置中心、消息总线、负载均衡、断路器、数据监控等，都可以用 spring boot 的开发风格做到一键启动和部署。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 保护SpringBoot应用有哪些方法？
- 在生产中使用HTTPS
- 使用Snyk检查你的依赖关系
- 升级到最新版本
- 启用CSRF保护
- 使用内容安全策略防止XSS攻击

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring Boot的核心注解是哪些？他由哪几个注解组成的？
启动类上面的注解是@SpringBootApplication，他也是SpringBoot的核心注解，主要组合包含了以下3个注解：

```
@SpringBootConfiguration：组合了@Configuration注解，实现配置文件的功能；
@EnableAutoConfiguration：打开自动配置的功能，也可以关闭某个自动配置的选项，如关闭数据源自动配置的功能：@SpringBootApplication(exclude={DataSourceAutoConfiguration.class})；
@ComponentScan：Spring组件扫描。
```
*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring Boot中如何解决跨域问题？
跨域可以在前端通过JSONP来解决，但是JSONP只可以发送GET请求，无法发送其他类型的请求，在RESTful风格的应用中，就显得非常鸡肋，因此推荐在后端通过（CORS，Cross-origin resource sharing）来解决跨域问题。这种解决方案并非Spring Boot特有的，在传统的SSM框架中，就可以通过CORS来解决跨域问题，只不过之前我们是在XML文件中配置CORS，现在可以通过实现WebMvcConfigurer接口然后重写addCorsMappings方法解决跨域问题。

```java
@Configuration
public class CorsConfig implements WebMvcConfigurer {

    @Override
    public void addCorsMappings(CorsRegistry registry) {
        registry.addMapping("/**")
                .allowedOrigins("*")
                .allowCredentials(true)
                .allowedMethods("GET", "POST", "PUT", "DELETE", "OPTIONS")
                .maxAge(3600);
    }

}


```

项目中前后端分离部署，所以需要解决跨域的问题。
我们使用cookie存放用户登录的信息，在spring拦截器进行权限控制，当权限不符合时，直接返回给用户固定的json结果。
当用户登录以后，正常使用；当用户退出登录状态时或者token过期时，由于拦截器和跨域的顺序有问题，出现了跨域的现象。
我们知道一个http请求，先走filter，到达servlet后才进行拦截器的处理，如果我们把cors放在filter里，就可以优先于权限拦截器执行。

```java
@Configuration
public class CorsConfig {

    @Bean
    public CorsFilter corsFilter() {
        CorsConfiguration corsConfiguration = new CorsConfiguration();
        corsConfiguration.addAllowedOrigin("*");
        corsConfiguration.addAllowedHeader("*");
        corsConfiguration.addAllowedMethod("*");
        corsConfiguration.setAllowCredentials(true);
        UrlBasedCorsConfigurationSource urlBasedCorsConfigurationSource = new UrlBasedCorsConfigurationSource();
        urlBasedCorsConfigurationSource.registerCorsConfiguration("/**", corsConfiguration);
        return new CorsFilter(urlBasedCorsConfigurationSource);
    }

}

```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 比较一下Spring Security和Shiro各自的优缺点？
由于Spring Boot官方提供了大量的非常方便的开箱即用的Starter，包括Spring Security的Starter，使得在SpringBoot中使用Spring Security变得更加容易，甚至只需要添加一个一来就可以保护所有接口，所以如果是SpringBoot项目，一般选择Spring Security。当然这只是一个建议的组合，单纯从技术上来说，无论怎么组合，都是没有问题的。

Shiro和Spring Security相比，主要有如下特点：
```
Spring Security是一个重量级的安全管理框架；Shiro则是一个轻量级的安全管理框架；
Spring Security概念复杂，配置繁琐；Shiro概念简单、配置简单；
Spring Security功能强大；Shiro功能简单
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何实现Spring Boot应用程序的安全性？
为了实现Spring Boot的安全性，使用spring-boot-starter-security依赖项，并且必须添加安全配置。它只需要很少代码。配置类将必须扩展WebSecurityConfigurerAdapter并覆盖其方法。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Swagger？你用Spring Boot实现了吗？
Swagger 广泛用于可视化 API，使用 Swagger UI 为前端开发人员提供在线沙箱。Swagger 是用于生成 RESTful Web 服务的可视化表示的工具，规范和完整框架实现。它使文档能够以与服务器相同的速度更新。当通过 Swagger 正确定义时，消费者可以使用最少量的实现逻辑来理解远程服务并与其进行交互。因此，Swagger消除了调用服务时的猜测。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何使用配置文件通过 Spring Boot 配置特定环境的配置？
配置文件不是设别环境的关键。

在下面的例子中，我们将会用到两个配置文件

-  dev
-  prod

缺省的应用程序配置在 application.properties 中。让我们来看下面的例子：

application.properties

```
basic.value= true   
   basic.message= Dynamic Message   
   basic.number= 100 
```

我们想要为 dev 文件自定义 application.properties 属性。我们需要创建一个名为 application-dev.properties 的文件，并且重写我们想要自定义的属性。

application-dev.properties

```
basic.message: Dynamic Message in DEV 
```

一旦你特定配置了配置文件，你需要在环境中设定一个活动的配置文件。

有多种方法可以做到这一点：

-  在 VM 参数中使用 Dspring.profiles.active=prod
-  在 application.properties 中使用 spring.profiles.active=prod

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何使用 Spring Boot 部署到不同的服务器？
你需要做下面两个步骤：

-  在一个项目中生成一个 war 文件。
-  将它部署到你最喜欢的服务器（websphere 或者 Weblogic 或者 Tomcat and so on）。

第一步：这本入门指南应该有所帮助：

https://spring.io/guides/gs/convert-jar-to-war/

第二步：取决于你的服务器。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何在 Spring Boot 中添加通用的 JS 代码？1\. 在pom.xml文件中引入依赖
-------------------

当前引入的是js1.12.4版本,根据各自需要引入相应版本。

    <!--js-->
            <dependency>
                <groupId>org.webjars</groupId>
                <artifactId>jquery</artifactId>
                <version>1.12.4</version>
            </dependency>
    

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200222134746317.png)

2\. 在HTML页面应用
-------------

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200222134927214.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzM3OTQwMTI3,size_16,color_FFFFFF,t_70)
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是嵌入式服务器？我们为什么要使用嵌入式服务器呢?
思考一下在你的虚拟机上部署应用程序需要些什么。

第一步： 安装 Java

第二部： 安装 Web 或者是应用程序的服务器（Tomat/Wbesphere/Weblogic 等等）

第三部： 部署应用程序 war 包

如果我们想简化这些步骤，应该如何做呢？

让我们来思考如何使服务器成为应用程序的一部分？

你只需要一个安装了 Java 的虚拟机，就可以直接在上面部署应用程序了，

是不是很爽？

这个想法是嵌入式服务器的起源。

当我们创建一个可以部署的应用程序的时候，我们将会把服务器（例如，tomcat）嵌入到可部署的服务器中。

例如，对于一个 Spring Boot 应用程序来说，你可以生成一个包含 Embedded Tomcat 的应用程序 jar。你就可以想运行正常 Java 应用程序一样来运行 web 应用程序了。

嵌入式服务器就是我们的可执行单元包含服务器的二进制文件（例如，tomcat.jar）。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么我们需要 spring-boot-maven-plugin?
spring-boot-maven-plugin 提供了一些像 jar 一样打包或者运行应用程序的命令。

-  spring-boot:run 运行你的 SpringBooty 应用程序。
-  spring-boot：repackage 重新打包你的 jar 包或者是 war 包使其可执行
-  spring-boot：start 和 spring-boot：stop 管理 Spring Boot 应用程序的生命周期（也可以说是为了集成测试）。
-  spring-boot:build-info 生成执行器可以使用的构造信息。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring Initializr 是创建 Spring Boot Projects 的唯一方法吗？
不是的。

Spring Initiatlizr 让创建 Spring Boot 项目变的很容易，但是，你也可以通过设置一个 maven 项目并添加正确的依赖项来开始一个项目。

在我们的 Spring 课程中，我们使用两种方法来创建项目。

第一种方法是 start.spring.io 。

另外一种方法是在项目的标题为“Basic Web Application”处进行手动设置。

手动设置一个 maven 项目

这里有几个重要的步骤：

-  在 Eclipse 中，使用文件 - 新建 Maven 项目来创建一个新项目
-  添加依赖项。
-  添加 maven 插件。
-  添加 Spring Boot 应用程序类。

到这里，准备工作已经做好！

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 怎么使用 Maven 来构建一个 SpringBoot 程序？
就像引入其他库一样，我们可以在 Maven 工程中加入 SpringBoot 依赖。然而，最好是从 *spring-boot-starter-parent* 项目中继承以及声明依赖到 Spring Boot starters。这样做可以使我们的项目可以重用 SpringBoot 的默认配置。

继承 *spring-boot-starter-parent* 项目依赖很简单 – 我们只需要在 *pom.xml* 中定义一个 *parent* 节点：

```
 <parent>
     <groupId>org.springframework.boot</groupId>
     <artifactId>spring-boot-starter-parent</artifactId>
     <version>2.1.1.RELEASE</version>
 </parent>
```

我们可以在 Maven central 中找到 *spring-boot-starter-parent* 的最新版本。

使用 starter 父项目依赖很方便，但并非总是可行。例如，如果我们公司都要求项目继承标准 POM，我们就不能依赖 SpringBoot starter 了。

这种情况，我们可以通过对 POM 元素的依赖管理来处理：

```xml
 <dependencyManagement>
      <dependencies>
          <dependency>
              <groupId>org.springframework.boot</groupId>
              <artifactId>spring-boot-dependencies</artifactId>
              <version>2.1.1.RELEASE</version>
              <type>pom</type>
             <scope>import</scope>
          </dependency>
     </dependencies>
 </dependencyManagement>
```



*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何在 Spring Boot 中禁用 Actuator 端点安全性？
默认情况下，所有敏感的 HTTP 端点都是安全的，只有具有 ACTUATOR 角色的用户才能访问它们。安全性是使用标准的 HttpServletRequest.isUserInRole 方法实施的。 我们可以使用来禁用安全性。只有在执行机构端点在防火墙后访问时，才建议禁用安全性。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring Boot 中的监视器是什么？
Spring boot actuator 是 spring 启动框架中的重要功能之一。Spring boot 监视器可帮助您访问生产环境中正在运行的应用程序的当前状态。有几个指标必须在生产环境中进行检查和监控。即使一些外部应用程序可能正在使用这些服务来向相关人员触发警报消息。监视器模块公开了一组可直接作为 HTTP URL 访问的REST 端点来检查状态。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何重新加载 Spring Boot 上的更改，而无需重新启动服务器？
这可以使用 DEV 工具来实现。通过这种依赖关系，您可以节省任何更改，嵌入式tomcat 将重新启动。Spring Boot 有一个开发工具（DevTools）模块，它有助于提高开发人员的生产力。Java 开发人员面临的一个主要挑战是将文件更改自动部署到服务器并自动重启服务器。开发人员可以重新加载 Spring Boot 上的更改，而无需重新启动服务器。这将消除每次手动部署更改的需要。Spring Boot 在发布它的第一个版本时没有这个功能。这是开发人员最需要的功能。DevTools 模块完全满足开发人员的需求。该模块将在生产环境中被禁用。它还提供 H2 数据库控制台以更好地测试应用程序。

```xml
<dependency>
<groupId>org.springframework.boot</groupId>
<artifactId>spring-boot-devtools</artifactId>
<optional>true</optional>
</dependency>
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring 和 SpringBoot 有什么不同？
Spring 框架提供多种特性使得 web 应用开发变得更简便，包括依赖注入、数据绑定、切面编程、数据存取等等。

随着时间推移，Spring 生态变得越来越复杂了，并且应用程序所必须的配置文件也令人觉得可怕。这就是 Spirng Boot 派上用场的地方了 – 它使得 Spring 的配置变得更轻而易举。

实际上，Spring 是 *unopinionated*（予以配置项多，倾向性弱） 的，Spring Boot 在平台和库的做法中更 *opinionated* ，使得我们更容易上手。

这里有两条 SpringBoot 带来的好处：

- 根据 classpath 中的 artifacts 的自动化配置应用程序
- 提供非功能性特性例如安全和健康检查给到生产环境中的应用程序

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 创建一个 Spring Boot Project 的最简单的方法是什么？
Spring Initializr是启动 Spring Boot Projects 的一个很好的工具。

我们需要做以下几步：

- 登录 Spring Initializr，按照以下方式进行选择：
- 选择 com.in28minutes.springboot 为组
- 选择 studet-services 为组件
- 选择下面的依赖项
- Web
- Actuator
- DevTools
- 点击生 GenerateProject
- 将项目导入 Eclipse。文件 - 导入 - 现有的 Maven 项目

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring Boot 有哪些优点？
Spring Boot 的优点有：

1、减少开发，测试时间和努力。

2、使用 JavaConfig 有助于避免使用 XML。

3、避免大量的 Maven 导入和各种版本冲突。

4、提供意见发展方法。

5、通过提供默认值快速开始开发。

6、没有单独的 Web 服务器需要。这意味着你不再需要启动 Tomcat，Glassfish或其他任何东西。

7、需要更少的配置 因为没有 web.xml 文件。只需添加用@ Configuration 注释的类，然后添加用@Bean 注释的方法，Spring 将自动加载对象并像以前一样对其进行管理。您甚至可以将@Autowired 添加到 bean 方法中，以使 Spring 自动装入需要的依赖关系中。

8、基于环境的配置 使用这些属性，您可以将您正在使用的环境传递到应用程序：-Dspring.profiles.active = {enviornment}。在加载主应用程序属性文件后，Spring 将在（application{environment} .properties）中加载后续的应用程序属性文件。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是springbootSpring Boot是由Pivotal团队提供的框架，其设计目的是用来简化新Spring应用的初始搭建以及开发过程。

该框架使用了特定的方式来进行配置，从而使开发人员不再需要定义样板化的配置。通过这种方式，Spring Boot致力于在蓬勃发展的快速应用开发领域（rapid application development）成为领导者。

spring大家都知道，boot是启动的意思。所以，spring boot其实就是一个启动spring项目的一个工具而已。从最根本上来讲，Spring Boot就是一些库的集合，它能够被任意项目的构建系统所使用。

spring boot并不是一个全新的框架，它不是spring解决方案的一个替代品，而是spring的一个封装。所以，你以前可以用spring做的事情，现在用spring boot都可以做。

现在流行微服务与分布式系统，springboot就是一个非常好的微服务开发框架，你可以使用它快速的搭建起一个系统。同时，你也可以使用spring cloud（Spring Cloud是一个基于Spring Boot实现的云应用开发工具）来搭建一个分布式的网站。
*** 
## ⭐️⭐️⭐️⭐️⭐️
## ApplicationContext通常的实现是什么?
- FileSystemXmlApplicationContext ：此容器从一个XML文件中加载beans的定义，XML Bean 配置文件的全路径名必须提供给它的构造函数。
- ClassPathXmlApplicationContext：此容器也从一个XML文件中加载beans的定义，这里，你需要正确设置classpath因为这个容器将在classpath里找bean配置。
- WebXmlApplicationContext：此容器加载一个XML文件，此文件定义了一个WEB应用的所有bean。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring AOP 实现原理
实现AOP的技术，主要分为两大类：

一是采用动态代理技术，利用截取消息的方式，对该消息进行装饰，以取代原有对象行为的执行；二是采用静态织入的方式，引入特定的语法创建“方面”，从而使得编译器可以在编译期间织入有关“方面”的代码。

Spring AOP 的实现原理其实很简单：AOP 框架负责动态地生成 AOP 代理类，这个代理类的方法则由 Advice和回调目标对象的方法所组成, 并将该对象可作为目标对象使用。AOP 代理包含了目标对象的全部方法，但AOP代理中的方法与目标对象的方法存在差异，AOP方法在特定切入点添加了增强处理，并回调了目标对象的方法。

Spring AOP使用动态代理技术在运行期织入增强代码。使用两种代理机制：基于JDK的动态代理（JDK本身只提供接口的代理）和基于CGlib的动态代理。

(1) JDK的动态代理

JDK的动态代理主要涉及java.lang.reflect包中的两个类：Proxy和InvocationHandler。其中InvocationHandler只是一个接口，可以通过实现该接口定义横切逻辑，并通过反射机制调用目标类的代码，动态的将横切逻辑与业务逻辑织在一起。而Proxy利用InvocationHandler动态创建一个符合某一接口的实例，生成目标类的代理对象。

其代理对象必须是某个接口的实现, 它是通过在运行期间创建一个接口的实现类来完成对目标对象的代理.只能实现接口的类生成代理，而不能针对类。

(2)CGLib

CGLib采用底层的字节码技术，为一个类创建子类，并在子类中采用方法拦截的技术拦截所有父类的调用方法，并顺势织入横切逻辑.它运行期间生成的代理对象是目标类的扩展子类.所以无法通知final、private的方法,因为它们不能被覆写.是针对类实现代理,主要是为指定的类生成一个子类，覆盖其中方法。

在spring中默认。况下使用JDK动态代理实现AOP,如果proxy-target-class设置为true或者使用了优化策略那么会使用CGLIB来创建动态代理.Spring　AOP在这两种方式的实现上基本一样．以JDK代理为例，会使用JdkDynamicAopProxy来创建代理，在invoke()方法首先需要织入到当前类的增强器封装到拦截器链中，然后递归的调用这些拦截器完成功能的织入，最终返回代理对象。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 有哪些不同类型的IOC(依赖注入)？
构造器依赖注入：构造器依赖注入在容器触发构造器的时候完成，该构造器有一系列的参数，每个参数代表注入的对象。

Setter方法依赖注入：首先容器会触发一个无参构造函数或无参静态工厂方法实例化对象，之后容器调用bean中的setter方法完成Setter方法依赖注入。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 解释自动装配的各种模式？
自动装配提供五种不同的模式供Spring容器用来自动装配beans之间的依赖注入:

no：默认的方式是不进行自动装配，通过手工设置ref 属性来进行装配bean。

byName：通过参数名自动装配，Spring容器查找beans的属性，这些beans在XML配置文件中被设置为byName。之后容器试图匹配、装配和该bean的属性具有相同名字的bean。

byType：通过参数的数据类型自动自动装配，Spring容器查找beans的属性，这些beans在XML配置文件中被设置为byType。之后容器试图匹配和装配和该bean的属性类型一样的bean。如果有多个bean符合条件，则抛出错误。

constructor：这个同byType类似，不过是应用于构造函数的参数。如果在BeanFactory中不是恰好有一个bean与构造函数参数相同类型，则抛出一个严重的错误。

autodetect：如果有默认的构造方法，通过 construct的方式自动装配，否则使用 byType的方式自动装配。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Resource 是如何被查找、加载的？Resource 接口是 Spring 资源访问策略的抽象，它本身并不提供任何资源访问实现，具体的资源访问由该接口的实现类完成——每个实现类代表一种资源访问策略。 

Spring 为 Resource 接口提供了如下实现类：

```
UrlResource：访问网络资源的实现类。
ClassPathResource：访问类加载路径里资源的实现类。
FileSystemResource：访问文件系统里资源的实现类。
ServletContextResource：访问相对于 ServletContext 路径里的资源的实现类
InputStreamResource：访问输入流资源的实现类。
ByteArrayResource：访问字节数组资源的实现类。 
```

这些 Resource 实现类，针对不同的的底层资源，提供了相应的资源访问逻辑，并提供便捷的包装，以利于客户端程序的资源访问。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## BeanFactory和ApplicationContext有什么区别？
ApplicationContext提供了一种解决文档信息的方法，一种加载文件资源的方式(如图片)，他们可以向监听他们的beans发送消息。另外，容器或者容器中beans的操作，这些必须以bean工厂的编程方式处理的操作可以在应用上下文中以声明的方式处理。应用上下文实现了MessageSource，该接口用于获取本地消息，实际的实现是可选的。

相同点：两者都是通过xml配置文件加载bean，ApplicationContext和BeanFacotry相比，提供了更多的扩展功能。

不同点：BeanFactory是延迟加载，如果Bean的某一个属性没有注入，BeanFacotry加载后，直至第一次使用调用getBean方法才会抛出异常；而ApplicationContext则在初始化自身是检验，这样有利于检查所依赖属性是否注入；所以通常情况下我们选择使用ApplicationContext。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring 事务底层原理
## 划分处理单元——IoC

由于spring解决的问题是对单个数据库进行局部事务处理的，具体的实现首先用spring中的IoC划分了事务处理单元。并且将对事务的各种配置放到了ioc容器中（设置事务管理器，设置事务的传播特性及隔离机制）。

## AOP拦截需要进行事务处理的类

Spring事务处理模块是通过AOP功能来实现声明式事务处理的，具体操作（比如事务实行的配置和读取，事务对象的抽象），用TransactionProxyFactoryBean接口来使用AOP功能，生成proxy代理对象，通过TransactionInterceptor完成对代理方法的拦截，将事务处理的功能编织到拦截的方法中。读取ioc容器事务配置属性，转化为spring事务处理需要的内部数据结构（TransactionAttributeSourceAdvisor），转化为TransactionAttribute表示的数据对象。

## 对事务处理实现（事务的生成、提交、回滚、挂起）

spring委托给具体的事务处理器实现。实现了一个抽象和适配。适配的具体事务处理器：DataSource数据源支持、hibernate数据源事务处理支持、JDO数据源事务处理支持，JPA、JTA数据源事务处理支持。这些支持都是通过设计PlatformTransactionManager、AbstractPlatforTransaction一系列事务处理的支持。 为常用数据源支持提供了一系列的TransactionManager。

## 总结

PlatformTransactionManager实现了TransactionInterception接口，让其与TransactionProxyFactoryBean结合起来，形成一个Spring声明式事务处理的设计体系。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring事务中有哪几种事务传播行为？
在TransactionDefinition接口中定义了八个表示事务传播行为的常量。

支持当前事务的情况：
```
PROPAGATION_REQUIRED：如果当前存在事务，则加入该事务；如果当前没有事务，则创建一个新的事务。
PROPAGATION_SUPPORTS： 如果当前存在事务，则加入该事务；如果当前没有事务，则以非事务的方式继续运行。
PROPAGATION_MANDATORY： 如果当前存在事务，则加入该事务；如果当前没有事务，则抛出异常。（mandatory：强制性）。
``

不支持当前事务的情况：
```
PROPAGATION_REQUIRES_NEW： 创建一个新的事务，如果当前存在事务，则把当前事务挂起。
PROPAGATION_NOT_SUPPORTED： 以非事务方式运行，如果当前存在事务，则把当前事务挂起。
PROPAGATION_NEVER： 以非事务方式运行，如果当前存在事务，则抛出异常。
```

其他情况：
```
PROPAGATION_NESTED： 如果当前存在事务，则创建一个事务作为当前事务的嵌套事务来运行；如果当前没有事务，则该取值等价于PROPAGATION_REQUIRED。
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring事务中的隔离级别有哪几种？
在TransactionDefinition接口中定义了五个表示隔离级别的常量：

ISOLATION_DEFAULT：使用后端数据库默认的隔离级别，Mysql默认采用的REPEATABLE_READ隔离级别；Oracle默认采用的READ_COMMITTED隔离级别。

ISOLATION_READ_UNCOMMITTED：最低的隔离级别，允许读取尚未提交的数据变更，可能会导致脏读、幻读或不可重复读。

ISOLATION_READ_COMMITTED：允许读取并发事务已经提交的数据，可以阻止脏读，但是幻读或不可重复读仍有可能发生

ISOLATION_REPEATABLE_READ：对同一字段的多次读取结果都是一致的，除非数据是被本身事务自己所修改，可以阻止脏读和不可重复读，但幻读仍有可能发生。

ISOLATION_SERIALIZABLE：最高的隔离级别，完全服从ACID的隔离级别。所有的事务依次逐个执行，这样事务之间就完全不可能产生干扰，也就是说，该级别可以防止脏读、不可重复读以及幻读。但是这将严重影响程序的性能。通常情况下也不会用到该级别。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring事务管理的方式有几种？```
1.编程式事务：在代码中硬编码（不推荐使用）。
2.声明式事务：在配置文件中配置（推荐使用），分为基于XML的声明式事务和基于注解的声明式事务。
```
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 将一个类声明为Spring的bean的注解有哪些？
我们一般使用@Autowired注解去自动装配bean。而想要把一个类标识为可以用@Autowired注解自动装配的bean，可以采用以下的注解实现：
```
1.@Component注解。通用的注解，可标注任意类为Spring组件。如果一个Bean不知道属于哪一个层，可以使用@Component注解标注。
2.@Repository注解。对应持久层，即Dao层，主要用于数据库相关操作。
3.@Service注解。对应服务层，即Service层，主要涉及一些复杂的逻辑，需要用到Dao层（注入）。
4.@Controller注解。对应Spring MVC的控制层，即Controller层，主要用于接受用户请求并调用Service层的方法返回数据给前端页面。
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## @Component和@Bean的区别是什么？```
1.作用对象不同。@Component注解作用于类，而@Bean注解作用于方法。
2.@Component注解通常是通过类路径扫描来自动侦测以及自动装配到Spring容器中（我们可以使用@ComponentScan注解定义要扫描的路径）。@Bean注解通常是在标有该注解的方法中定义产生这个bean，告诉Spring这是某个类的实例，当我需要用它的时候还给我。
3.@Bean注解比@Component注解的自定义性更强，而且很多地方只能通过@Bean注解来注册bean。比如当引用第三方库的类需要装配到Spring容器的时候，就只能通过@Bean注解来实现。
```
*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring框架中用到了哪些设计模式？```
1.工厂设计模式：Spring使用工厂模式通过BeanFactory和ApplicationContext创建bean对象。
2.代理设计模式：Spring AOP功能的实现。
3.单例设计模式：Spring中的bean默认都是单例的。
4.模板方法模式：Spring中的jdbcTemplate、hibernateTemplate等以Template结尾的对数据库操作的类，它们就使用到了模板模式。
5.包装器设计模式：我们的项目需要连接多个数据库，而且不同的客户在每次访问中根据需要会去访问不同的数据库。这种模式让我们可以根据客户的需求能够动态切换不同的数据源。
6.观察者模式：Spring事件驱动模型就是观察者模式很经典的一个应用。
7.适配器模式：Spring AOP的增强或通知（Advice）使用到了适配器模式、Spring MVC中也是用到了适配器模式适配Controller。
```
*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring MVC的工作原理了解嘛？```
1.客户端（浏览器）发送请求，直接请求到DispatcherServlet。
2.DispatcherServlet根据请求信息调用HandlerMapping，解析请求对应的Handler。
3.解析到对应的Handler（也就是我们平常说的Controller控制器）。
4.HandlerAdapter会根据Handler来调用真正的处理器来处理请求和执行相对应的业务逻辑。
5.处理器处理完业务后，会返回一个ModelAndView对象，Model是返回的数据对象，View是逻辑上的View。
6.ViewResolver会根据逻辑View去查找实际的View。
7.DispatcherServlet把返回的Model传给View（视图渲染）。
8.把View返回给请求者（浏览器）。
```
*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring中的bean生命周期了解过吗？```
1.Bean容器找到配置文件中Spring Bean的定义。
2.Bean容器利用Java Reflection API创建一个Bean的实例。
3.如果涉及到一些属性值，利用set()方法设置一些属性值。
4.如果Bean实现了BeanNameAware接口，调用setBeanName()方法，传入Bean的名字。
5.如果Bean实现了BeanClassLoaderAware接口，调用setBeanClassLoader()方法，传入ClassLoader对象的实例。
6.如果Bean实现了BeanFactoryAware接口，调用setBeanClassFacotory()方法，传入ClassLoader对象的实例。
7.与上面的类似，如果实现了其他*Aware接口，就调用相应的方法。
8.如果有和加载这个Bean的Spring容器相关的BeanPostProcessor对象，执行postProcessBeforeInitialization()方法。
9.如果Bean实现了InitializingBean接口，执行afeterPropertiesSet()方法。
10.如果Bean在配置文件中的定义包含init-method属性，执行指定的方法。
11.如果有和加载这个Bean的Spring容器相关的BeanPostProcess对象，执行postProcessAfterInitialization()方法。
12.当要销毁Bean的时候，如果Bean实现了DisposableBean接口，执行destroy()方法。
13.当要销毁Bean的时候，如果Bean在配置文件中的定义包含destroy-method属性，执行指定的方法。
```
*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring中的单例bean的线程安全问题了解吗？
大部分时候我们并没有在系统中使用多线程，所以很少有人会关注这个问题。单例bean存在线程问题，主要是因为当多个线程操作同一个对象的时候，对这个对象的非静态成员变量的写操作会存在线程安全问题。

有两种常见的解决方案：

1.在bean对象中尽量避免定义可变的成员变量（不太现实）。

2.在类中定义一个ThreadLocal成员变量，将需要的可变成员变量保存在ThreadLocal中（推荐的一种方式）。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring中的bean的作用域有哪些？```
1.singleton：唯一bean实例，Spring中的bean默认都是单例的。
2.prototype：每次请求都会创建一个新的bean实例。
3.request：每一次HTTP请求都会产生一个新的bean，该bean仅在当前HTTP request内有效。
4.session：每一次HTTP请求都会产生一个新的bean，该bean仅在当前HTTP session内有效。
5.global-session：全局session作用域，仅仅在基于Portlet的Web应用中才有意义，Spring5中已经没有了。Portlet是能够生成语义代码（例如HTML）片段的小型Java Web插件。它们基于Portlet容器，可以像Servlet一样处理HTTP请求。但是与Servlet不同，每个Portlet都有不同的会话。
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring AOP和AspectJ AOP有什么区别？
Spring AOP是属于运行时增强，而AspectJ是编译时增强。Spring AOP基于代理（Proxying），而AspectJ基于字节码操作（Bytecode Manipulation）。

Spring AOP已经集成了AspectJ，AspectJ应该算得上是Java生态系统中最完整的AOP框架了。AspectJ相比于Spring AOP功能更加强大，但是Spring AOP相对来说更简单。

如果我们的切面比较少，那么两者性能差异不大。但是，当切面太多的话，最好选择AspectJ，它比SpringAOP快很多。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 谈谈自己对于Spring AOP的理解
AOP（Aspect-Oriented Programming，面向切面编程）能够将那些与业务无关，却为业务模块所共同调用的逻辑或责任（例如事务处理、日志管理、权限控制等）封装起来，便于减少系统的重复代码，降低模块间的耦合度，并有利于未来的可扩展性和可维护性。

Spring AOP是基于动态代理的，如果要代理的对象实现了某个接口，那么Spring AOP就会使用JDK动态代理去创建代理对象；而对于没有实现接口的对象，就无法使用JDK动态代理，转而使用CGlib动态代理生成一个被代理对象的子类来作为代理。
当然也可以使用AspectJ，Spring AOP中已经集成了AspectJ，AspectJ应该算得上是Java生态系统中最完整的AOP框架了。使用AOP之后我们可以把一些通用功能抽象出来，在需要用到的地方直接使用即可，这样可以大大简化代码量。我们需要增加新功能也方便，提高了系统的扩展性。日志功能、事务管理和权限管理等场景都用到了AOP。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 谈谈自己对于Spring IOC的理解
IOC（Inversion Of Controll，控制反转）是一种设计思想，就是将原本在程序中手动创建对象的控制权，交由给Spring框架来管理。IOC在其他语言中也有应用，并非Spring特有。IOC容器是Spring用来实现IOC的载体，IOC容器实际上就是一个Map(key, value)，Map中存放的是各种对象。

将对象之间的相互依赖关系交给IOC容器来管理，并由IOC容器完成对象的注入。这样可以很大程度上简化应用的开发，把应用从复杂的依赖关系中解放出来。IOC容器就像是一个工厂一样，当我们需要创建一个对象的时候，只需要配置好配置文件/注解即可，完全不用考虑对象是如何被创建出来的。在实际项目中一个Service类可能由几百甚至上千个类作为它的底层，假如我们需要实例化这个Service，可能要每次都搞清楚这个Service所有底层类的构造函数，这可能会把人逼疯。如果利用IOC的话，你只需要配置好，然后在需要的地方引用就行了，大大增加了项目的可维护性且降低了开发难度。

Spring时代我们一般通过XML文件来配置Bean，后来开发人员觉得用XML文件来配置不太好，于是Sprng Boot注解配置就慢慢开始流行起来。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring Boot自动配置原理springboot执行启动类后，为什么我们就可以直接使用[http://localhost:8080/](http://localhost:8080/)访问了呢？

我们查看启动类，发现特别的地方有两个：

        注解：@SpringBootApplication

       run方法：SpringApplication.run()

我们先看看注解@SpringBootApplication

在启动类上有注解@SpringBootApplication，查看@SpringBootApplication源码

![](https://img-blog.csdnimg.cn/20200329225128553.png)

从上面的源码我们主要看看@SpringBootConfiguration、@EnableAutoConfiguration和@ComponentScan注解。

1、@SpringBootConfiguration

查看@SpringBootConfiguration源码

![](https://img-blog.csdnimg.cn/20200329225841665.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3l1MTc1NTEyODE0Nw==,size_16,color_FFFFFF,t_70)

从@SpringBootConfiguration源码可以看到，在这个注解的上面有@Configuration注解，这个注解的作用就是声明当前类是一个配置类，然后Spring会自动扫描到添加了`@Configuration`的类，并且读取其中的配置信息。而`@SpringBootConfiguration`是来声明当前类是SpringBoot应用的配置类，项目中只能有一个。

2、@EnableAutoConfiguration

查看@EnableAutoConfiguration源码

![](https://img-blog.csdnimg.cn/20200329232451838.png)

接着查看AutoConfigurationImportSelector类

![](https://img-blog.csdnimg.cn/20200329232621636.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3l1MTc1NTEyODE0Nw==,size_16,color_FFFFFF,t_70)

在AutoConfigurationImportSelector类中我们找到selectImports方法，在这个方法中查看调用的getCandidateConfigurations方法

![](https://img-blog.csdnimg.cn/20200329232904454.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3l1MTc1NTEyODE0Nw==,size_16,color_FFFFFF,t_70)

其中，SpringFactoriesLoader.loadFactoryNames 方法的作用就是从META-INF/spring.factories文件中读取指定  
类对应的类名称列表。在这个方法出错时，会显示found in META-INF/spring.factories。

我们接着找到这个包（即：org.springframework.boot.autoconfigure）下面对应的META-INF/spring.factories文件，打开这个文件我们可以看到，spring.factories 文件中有关自动配置的配置信息，如：mvc的自动配置

![](https://img-blog.csdnimg.cn/2020032923394137.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3l1MTc1NTEyODE0Nw==,size_16,color_FFFFFF,t_70)

以下就以mvc为例看一看

在spring.factories 文件中找到WebMvcAutoConfiguration，进入源码

![](https://img-blog.csdnimg.cn/20200330211504824.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3l1MTc1NTEyODE0Nw==,size_16,color_FFFFFF,t_70)

查看WebMvcProperties源码，找到了内部资源视图解析器的prefix和suffix属性。

![](https://img-blog.csdnimg.cn/20200330211713760.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3l1MTc1NTEyODE0Nw==,size_16,color_FFFFFF,t_70)

ResourceProperties中主要定义了静态资源（.js,.html,.css等)的路径：

![](https://img-blog.csdnimg.cn/20200330211838237.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3l1MTc1NTEyODE0Nw==,size_16,color_FFFFFF,t_70)

此外，在WebMvcAutoConfiguration源码中，找到视图解析器相应的源码

![](https://img-blog.csdnimg.cn/20200330212412354.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3l1MTc1NTEyODE0Nw==,size_16,color_FFFFFF,t_70)

处理器适配器（HandlerAdapter）：

![](https://img-blog.csdnimg.cn/20200330212520898.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3l1MTc1NTEyODE0Nw==,size_16,color_FFFFFF,t_70)

3、@ComponentScan

查看@ComponentScan源码

![](https://img-blog.csdnimg.cn/20200329230419798.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3l1MTc1NTEyODE0Nw==,size_16,color_FFFFFF,t_70)

通过源码的注释我们可以了解到，这个注解的作用是配置组件扫描的指令，扫描的包是该类所在包及其子包。

所以，在我们写启动类时，一般都会放在一个比较前的包目录中。
*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring Boot手动装配有哪几种方式？```
1. 使用模式注解 @Component 等（Spring2.5+）
2. 使用配置类 @Configuration 与 @Bean （Spring3.0+）
3. 使用模块装配 @EnableXXX 与 @Import （Spring3.1+）
```

其中使用 @Component 及衍生注解很常见，咱开发中常用的套路，不再赘述。

但模式注解只能在自己编写的代码中标注，无法装配jar包中的组件。为此可以使用 @Configuration 与 @Bean，手动装配组件（如上一篇的 @Configuration 示例）。但这种方式一旦注册过多，会导致编码成本高，维护不灵活等问题。

SpringFramework 提供了模块装配功能，通过给配置类标注 @EnableXXX 注解，再在注解上标注 @Import 注解，即可完成组件装配的效果。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring是怎么解决循环依赖的？
整个IOC容器解决循环依赖，用到的几个重要成员：
```
singletonObjects：一级缓存，存放完全初始化好的Bean的集合，从这个集合中取出来的Bean可以立马返回
earlySingletonObjects：二级缓存，存放创建好但没有初始化属性的Bean的集合，它用来解决循环依赖
singletonFactories：三级缓存，存放单实例Bean工厂的集合
singletonsCurrentlyInCreation：存放正在被创建的Bean的集合
```

IOC容器解决循环依赖的思路：

```
1. 初始化Bean之前，将这个BeanName放入三级缓存
2. 创建Bean将准备创建的Bean放入 singletonsCurrentlyInCreation （正在创建的Bean）
3. createNewInstance 方法执行完后执行 addSingletonFactory，将这个实例化但没有属性赋值的Bean放入二级缓存，并从三级缓存中移除
4. 属性赋值&自动注入时，引发关联创建
5. 关联创建时，检查“正在被创建的Bean”中是否有即将注入的Bean。如果有，检查二级缓存中是否有当前创建好但没有赋值初始化的Bean。如果没有，检查三级缓存中是否有正在创建中的Bean。至此一般会有，将这个Bean放入二级缓存，并从三级缓存中移除
6. 之后Bean被成功注入，最后执行 addSingleton，将这个完全创建好的Bean放入一级缓存，从二级缓存和三级缓存移除，并记录已经创建了的单实例Bean
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring由哪些模块组成?
以下是Spring 框架的基本模块：

- Core module
- Bean module
- Context module
- Expression Language module
- JDBC module
- ORM module
- OXM module
- Java Messaging Service(JMS) module
- Transaction module
- Web module
- Web-Servlet module
- Web-Struts module
- Web-Portlet module

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 使用Spring框架的好处是什么？
- 轻量：Spring 是轻量的，基本的版本大约2MB。
- 控制反转：Spring通过控制反转实现了松散耦合，对象们给出它们的依赖，而不是创建或查找依赖的对象们。
- 面向切面的编程(AOP)：Spring支持面向切面的编程，并且把应用业务逻辑和系统服务分开。
- 容器：Spring 包含并管理应用中对象的生命周期和配置。
- MVC框架：Spring的WEB框架是个精心设计的框架，是Web框架的一个很好的替代品。
- 事务管理：Spring 提供一个持续的事务管理接口，可以扩展到上至本地事务下至全局事务（JTA）。
- 异常处理：Spring 提供方便的API把具体技术相关的异常（比如由JDBC，Hibernate or JDO抛出的）转化为一致的unchecked 异常。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是spring?
Spring 是个java企业级应用的开源开发框架。Spring主要用来开发Java应用，但是有些扩展是针对构建J2EE平台的web应用。Spring 框架目标是简化Java企业级应用开发，并通过POJO为基础的编程模型促进良好的编程习惯。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Session Manager 会话管理介绍一下
## Session

所谓session，即用户访问应用时保持的连接关系，在多次交互中应用能够识别出当前访问的用户是谁，且可以在多次交互中保存一些数据。
```
Subject subject = SecurityUtils.getSubject();
Session session = subject.getSession();
session.getId(); // 获取当前session的唯一标识
session.getHost(); // 获取当前Subject的主机地址，该地址是通过HostAuthenticationToken.getHost()提供的
session.getTimeOut(); // 获取超时时间
session.setTimeOut(); // 设置超时时间（不设置默认是全局过期时间）
session.touch(); // 更新最后访问时间
session.stop(); // 销毁session，当Subject.logout()时会自动调用stop方法来销毁会话。如果在web中，调用javax.servlet.http.HttpSession.invalidate()也会自动调用shiro session.top方法进行销毁shiro的会话
session.setAttribute(“key”,”123”); // 设置session属性
session.getAttribute(“key”); // 获取session属性
session.removeAttribute(“key”); // 删除属性
```

注：Shiro提供的会话可以用于javaSE/javaEE环境，不依赖于任何底层容器，可以独立使用，是完整的会话模块。

## Session manager 会话管理器

会话管理器管理着应用中所有Subject的会话的创建、维护、删除、失效、验证等工作。是Shiro的核心组件，顶层组件SecurityManager直接继承了SessionManager，且提供了SessionSecurityManager实现直接把会话管理委托给相应的SessionManager、DefaultSecurityManager及DefaultWebSecurityManager 默认SecurityManager都继承了SessionSecurityManager。

Shiro提供了三个默认实现：
* DefaultSessionManager：DefaultSecurityManager使用的默认实现，用于JavaSE环境；
* ServletContainerSessionManager: DefaultWebSecurityManager使用的默认实现，用于Web环境，其直接使用Servlet容器的会话；
* DefaultWebSessionManager：用于Web环境的实现，可以替代ServletContainerSessionManager，自己维护着会话，直接废弃了Servlet容器的会话管理。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## shiro拦截器的执行流程
## 基于表单登录拦截器

onPreHandle主要流程：
```
1）首先判断是否已经登录过了，如果已经登录过了继续拦截器链即可；
2）如果没有登录，看看是否是登录请求，如果是get方法的登录页面请求，则继续拦截器链（到请求页面），否则如果是get方法的其他页面请求则保存当前请求并重定向到登录页面；
3）如果是post方法的登录页面表单提交请求，则收集用户名/密码登录即可，如果失败了保存错误消息到“shiroLoginFailure”并返回到登录页面；
4）如果登录成功了，且之前有保存的请求，则重定向到之前的这个请求，否则到默认的成功页面。
```

## 任意角色授权拦截器

流程：
```
1）首先判断用户有没有任意角色，如果没有返回false，将到onAccessDenied进行处理；
2）如果用户没有角色，接着判断用户有没有登录，如果没有登录先重定向到登录；
3）如果用户没有角色且设置了未授权页面（unauthorizedUrl），那么重定向到未授权页面；否则直接返回401未授权错误码。
```

## 默认拦截器

* 身份验证相关的
```
authc 基于表单的拦截器，即验证成功之后才能访问 /=authc
authcBasic Basic HTTP身份验证拦截器，主要属性：applicationName
logout 退出 /logout=logout
user 用户拦截器 /=user
anon 匿名拦截器，一般用于静态资源过滤 /static/=anon
```
* 授权相关的
```
roles 角色授权拦截器，主要属性：loginUrl，unauthorizedUrl /admin/=roles[admin]
perms 权限授权拦截器 /user/=perms[“user:create”]
port 端口拦截器，主要属性: port(80) /test=port[80]
rest rest风格拦截器 /users=rest[user]，会自动拼接出“user:read,user:create,user:update,user:delete”
ssl ssl拦截器，只有请求协议是https才能通过
```
*** 
## ⭐️⭐️⭐️⭐️⭐️
## Realm 域如何使用？
定义Realm（自定义Realm继承AuthorizingRealm即可）

1）UserRealm父类AuthorizingRealm将获取Subject相关信息分成两步：获取身份验证信息（doGetAuthenticationInfo）及授权信息（doGetAuthorizationInfo）

2）doGetAuthenticationInfo获取身份验证相关信息：首先根据传入的用户名获取User信息；如果user为空，那么抛出没找到账号异常UnknownAccountExecption；如果user找到但却被锁定了抛出锁定异常LockedAccountException；最后生成AuthenticationInfo信息，交给间接父类AuthenticatingRealm使用CredentialsMatcher进行判断密码是否匹配，如果不匹配将抛出密码错误异常信息IncorrectCredentialsException；如果密码重试次数太多将抛出超出重试次数异常ExcessiveAttemptsException；在组装SimpleAuthenticationInfo信息时，需要传入：身份信息（用户名）、凭据（密文密码）、盐（username+salt），CredentialsMatcher使用盐加密传入的明文密码和此处的密文密码进行匹配。

3）doGetAuthorizationInfo获取授权信息：PrincipalCollection是一个身份集合，因为只用到了一个Realm，所以直接调用getPrimaryPrincipal得到之前传入的用户名即可；然后根据用户名调用UserService接口获取角色及权限信息。


AuthenticationInfo的两个作用

1）如果Realm是AuthenticatingRealm子类，则提供给AuthenticatingRealm内部使用的CredentialsMatcher进行凭据验证；（如果没有继承它需要在自己的Realm中实现验证）；
2）提供给SecurityManager来创建Subject（提供身份信息）；

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Cryptography 加密的过程是这样的？
## 编码/解码

Shiro提供了base64和16进制字符串编码/解码的API支持,方便一些编码解码操作
```
Base64.encodeToString(str.getBytes())编码
Base64.decodeToString(base64Encoded) 解码
```

## 散列算法

常见散列算法如MD5,SHA等

```
1）首先创建一个DfaultHashService,默认使用SHA-512算法；
2）可以通过hashAlgorithmName属性修改算法；
3）可以通过privateSalt设置一个私盐，其在散列时自动与用户传入的公盐混合产生一个新盐；
4）可以通过generatePublicSalt属性在用户没有传入公盐的情况下是否生成公盐；
5）可以设置randomNumberGenerator用于生成公盐；
6）可以设置hashIterations属性来修改默认加密迭代次数；
7）需要构建一个HashRequest,传入算法、数据、公盐、迭代次数。
```

## 生成随机数
```java
SecureRandomNumberGenerator randomNumberGenerator = new SecureRandomNumberGenerator();
randomNumberGenerator.setSeed(“159”.getBytes());
String hex = randomNumberGenerator.nextBytes().toHex();
```

## 加密/解密

提供对称式加密/解密算法的支持，如AES、Blowfish等。

PasswordService/CredentialsMatcher
用于提供加密密码及验证密码服务
Shiro默认提供了`PasswordService`实现`DefaultPasswordService`;`CredentialsMatcher`实现`PasswordMatcher`及`HashedCredentialsMatcher`(更强大)
`HashedCredentialsMatcher`实现密码验证服务
Shiro提供了`CredentialsMatcher`的散列实现`HashedCredentialsMatcher`,和`PasswordMatcher`不同的是，它只是用于密码验证，且可以提供自己的盐，而不是随机生成盐，且生成密码散列值的算法需要自己写，因为能提供自己的盐

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Authorization 授权的方式和流程是怎样的？1.什么是授权
=======

授权，也叫访问控制，即在应用中控制谁能访问哪些资源（如访问页面/编辑数据/页面操作等）。在授权中需了解的几个关键对象：主体(Subject)、资源（Resource）、权限（Permission）、角色（Role）

2.授权三要素
=======

*   权限 
*   角色
    
    > 通常代表一组行为或职责.这些行为演化为你在一个软件应用中能或者不能做的事情。角色通常是分配给用户帐户的，因此，通过分配，用户能够“做”的事情可以归属于各种角色
    
    *   **隐式角色**：一个角色代表着一系列的操作，当需要对某一操作进行授权验证时，只需判断是否是该角色即可。这种角色权限相对简单、模糊，不利于扩展
    *   **显式角色**：一个角色拥有一个权限的集合。授权验证时，需要判断当前角色是否拥有该权限。这种角色权限可以对该角色进行详细的权限描述，适合更复杂的权限设计。 **Shiro官方推荐使用这种方式。**
*   用户
    
    > 通常我们将一系列的权限分配给角色，一个用户可以拥有多个角色。这样我们就能控制用户拥有哪些权限

3.授权方式：
=======

* 编码方式授权
* 基于注解的授权
* JSP标签授权

4.授权流程：
=======

1）首先调用Subject.isPermitted*/hasRole*接口，其会委托给SecurityManager，而SecurityManager接着会委托给Authorizer；

2）Authorizer是真正的授权者，如果我们调用如isPermitted(“user:view”), 其首先会通过PermissionResolver把字符串转换成相应的Permission实例；

3）在进行授权之前，其会调用相应的Realm获取Subject相应的角色/权限用于匹配传入的角色/权限；

4）Authorizer会判断Realm的角色/权限是否和传入的匹配，如果有多个Realm，会委托给ModularRealmAuthorizer进行循环判断，如果匹配如isPermitted*/hasRole*会返回true, 否则返回false表示授权失败。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说下Authentication 身份验证的流程
principals：身份，即主体的标识属性，可以是任何东西，如用户名、邮箱等，唯一即可。

credentials：证明/凭证，即只有主体知道的安全值，如密码/数字证书等。

身份认证流程：

1）首先调用Subject.login(token)进行登录，其会自动委托给SecurityManager，调用之前必须通过SecurityUtils.setSecurityManager()设置；

2）SecurityManager负责真正的身份验证逻辑；它会委托给Authenticator进行身份验证；

3）Authenticator才是真正的身份验证者，shiro api中核心的身份认证入口点，此处可以自定义插入自己的实现；

4）Authenticator可能会委托给相应的AuthenticationStrategy进行多Realm身份验证，默认ModularRealmAuthenticator会调用AuthenticationStrategy进行多Realm身份验证；

5）Authenticator会把相应的token传入Realm，从Realm获取身份验证信息，如果没有返回/抛出异常表示身份验证失败了。此处可以配置多个Realm，将按照相应的顺序及策略进行访问。

6）Authenticator的职责是验证用户账号，是shiro api中身份验证核心的入口点。

7）AuthenticationStrategy 认证策略 ModularRealmAuthenticator默认使用AtLeastOneSuccessfulStrategy策略

1> FirstSuccessfulStrategy：只要有一个Realm验证成功即可，只返回第一个Realm身份验证成功的认证信息，其他的忽略；

2> AtLeastOneSuccessfulStrategy：只要有一个Realm验证成功即可，和FirstSuccessfulStrategy不同，返回所有Realm身份验证成功的认证信息；

3> AllSuccessfulStrategy：所有Realm验证成功才算成功，且返回所有Realm身份验证成功的认证信息，如果有一个失败就失败了。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## Shiro有哪些组件？
Authentication：身份认证/登录，验证用户是不是拥有相应的身份；

Authorization：授权，即权限验证，验证某个已认证的用户是否拥有某个权限；即判断用户是否能做事情，常见的如：验证某个用户是否拥有某个角色。或者细粒度的验证某个用户对某个资源是否具有某个权限；

Session Manager：会话管理，即用户登录后就是一次会话，在没有退出之前，它的所有信息都在会话中；会话可以是普通JavaSE环境的，也可以是如Web环境的；

Cryptography：加密，保护数据的安全性，如密码加密存储到数据库，而不是明文存储；

Web Support：Web支持，可以非常容易的集成到Web环境；

Caching：缓存，比如用户登录后，其用户信息、拥有的角色/权限不必每次去查，这样可以提高效率；

Concurrency：shiro支持多线程应用的并发验证，即如在一个线程中开启另一个线程，能把权限自动传播过去；

Testing：提供测试支持；

Run As：允许一个用户假装为另一个用户（如果他们允许）的身份进行访问；

Remember Me：记住我，这个是非常常见的功能，即一次登录后，下次再来的话不用登录了。

记住一点，Shiro不会去维护用户、维护权限；这些需要我们自己去设计/提供；然后通过相应的接口注入给Shiro即可。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## Shiro的优点```
1、简单的身份验证，支持多种数据源
2、对角色的简单授权，支持细粒度的授权（方法）
3、支持一级缓存，以提升应用程序的性能
4、内置基于POJO的企业会话管理，适用于web及非web环境
5、非常简单的API加密
6、不跟任何框架绑定，可以独立运行
```
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 解释下Shiro的核心概念：Subject、SecurityManager、Realm* Subject：主体，代表了当前“用户”，这个用户不一定是一个具体的人，与当前应用交互的任何东西都是Subject，如爬虫、机器人等；即一个抽象概念；所有Subject都绑定到SecurityManager，与Subject的所有交互都会委托给SecurityManager；可以把Subject认为是一个门面；SecurityManager才是实际的执行者。
* SecurityManager：安全管理器；即所有与安全有关的操作都会与SecurityManager交互；且它管理着所有Subject；可以看出它是shiro的核心, SecurityManager相当于spring mvc中的dispatcherServlet前端控制器。
* Realm：域，shiro从Realm获取安全数据(如用户、角色、权限)，就是说SecurityManager要验证用户身份，那么它需要从Realm获取相应的用户进行比较以确定用户身份是否合法；也需要从Realm得到用户相应的角色/权限进行验证用户是否能进行操作；可以把Realm看成DataSource，即安全数据源。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是shiro
Shiro是一个强大易用的java安全框架，提供了认证、授权、加密、会话管理、与web集成、缓存等功能，对于任何一个应用程序，都可以提供全面的安全服务，相比其他安全框架，shiro要简单的多。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## init(ServletConfig)方法执行次数
   该方法执行在单线程的环境下，因此开发者不用考虑线程安全的问题。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何读取Servlet的初始化参数？
ServletConfig中定义了如下的方法用来读取初始化参数的信息：

* public String getInitParameter(String name)
* 参数：初始化参数的名称。
* 返回：初始化参数的值，如果没有配置，返回null。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何配置Servlet的初始化参数？
在web.xml中该Servlet的定义标记中，比如：

```  xaml
  <servlet>
     <servlet-name>TimeServlet</servlet-name>
     <servlet-class>com.allanlxf.servlet.basic.TimeServlet</servlet-class>
    **<init-param>
      <param-name>user</param-name>
      <param-value>username</param-value>
    </init-param>
    <init-param>
      <param-name>blog</param-name>
      <param-value>http://。。。</param-value>
    </init-param>
  </servlet>
```

配置了两个初始化参数user和blog它们的值分别为**username**和[http://](http://allanlxf.blog.sohu.com/)。。。， 这样以后要修改用户名和博客的地址不需要修改Servlet代码，只需修改配置文件即可。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Request对象的主要方法
setAttribute(String name,Object)：设置名字为name的request的参数值

getAttribute(String name)：返回由name指定的属性值

getAttributeNames()：返回request对象所有属性的名字集合，结果是一个枚举的实例

getCookies()：返回客户端的所有Cookie对象，结果是一个Cookie数组

getCharacterEncoding()：返回请求中的字符编码方式

getContentLength()：返回请求的Body的长度

getHeader(String name)：获得HTTP协议定义的文件头信息

getHeaders(String name)：返回指定名字的request Header的所有值，结果是一个枚举的实例

getHeaderNames()：返回所以request Header的名字，结果是一个枚举的实例

getInputStream()：返回请求的输入流，用于获得请求中的数据

getMethod()：获得客户端向服务器端传送数据的方法

getParameter(String name)：获得客户端传送给服务器端的有name指定的参数值

getParameterNames()：获得客户端传送给服务器端的所有参数的名字，结果是一个枚举的实例

getParameterValues(String name)：获得有name指定的参数的所有值

getProtocol()：获取客户端向服务器端传送数据所依据的协议名称

getQueryString()：获得查询字符串

getRequestURI()：获取发出请求字符串的客户端地址

getRemoteAddr()：获取客户端的IP地址

getRemoteHost()：获取客户端的名字

getSession([Boolean create])：返回和请求相关Session

getServerName()：获取服务器的名字

getServletPath()：获取客户端所请求的脚本文件的路径

getServerPort()：获取服务器的端口号

removeAttribute(String name)：删除请求中的一个属性

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 你知道哪些会话跟踪技术？
会话作用域 ServletsJSP 页面描述

1）page是代表与一个页面相关的对象和属性。一个页面由一个编译好的 Java servlet 类（可以带有任何的 include 指令，但是没有 include 动作）表示。这既包括 servlet 又包括被编译成 servlet 的 JSP 页面

2）request是代表与 Web 客户机发出的一个请求相关的对象和属性。一个请求可能跨越多个页面，涉及多个 Web 组件（由于 forward 指令和 include 动作的关系）

3）session是代表与用于某个 Web 客户机的一个用户体验相关的对象和属性。一个 Web 会话可以也经常会跨越多个客户机请求

4）application是代表与整个 Web 应用程序相关的对象和属性。这实质上是跨越整个 Web 应用程序，包括多个页面、请求和会话的一个全局作用域

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 页面间对象传递的方法
request，session，application，cookie等

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么情况下调用doGet()和doPost()？
JSP页面中的form标签里的method属性为get时调用doGet()，为post时调用doPost()；超链接跳转页面时调用doGet()

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Servlet的基本架构
```
public class ServletName extends HttpServlet {
  public void doPost(HttpServletRequest request, HttpServletResponse response) throws

      ServletException, IOException  {
      }

  public void doGet(HttpServletRequest request, HttpServletResponse response) throws

      ServletException, IOException  {
      }

}
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Servlet和JSP的区别？
Servlet是服务器端的程序，动态生成html页面发送到客户端，但是这样程序里会有很多out.println(),java与html语言混在一起很乱，造成编写逻辑控制的后台工程师和设计前端网页的前端工程师彼此很难独立开展工作，所以后来sun公司推出了JSP，其实JSP就是Servlet，每次运行的时候JSP都首先被编译成servlet文件，然后再被编译成.class文件运行。有了jsp，在MVC项目中servlet不再负责动态生成页面，转而去负责控制程序逻辑的作用，控制jsp与javabean之间的流转。其实对jsp也有封装的模板工具velocity和freemarker。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## Servlet的生命周期？
- 根据Servlet的配置参数<load-on-startup>1</load-on-startup>来决定实例化时机，没有配置该参数项或者为负数，则第一次访问的时候才会被实例化并调用init () 函数，如果为0或者正整数，则服务器启动的时候就会被加载，加载顺序由小到达。Servlet 通过调用 init () 方法进行初始化。

- 客户端请求到达后，Servlet 调用 service() 方法来处理客户端的请求。

- 服务器关闭，或者Servlet长时间没有使用，Servlet 通过调用 destroy() 方法终止（结束）。

最后，Servlet 是由 JVM 的垃圾回收器进行垃圾回收的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 任何一台Broker突然宕机了怎么办？
Broker主从架构以及多副本策略。Master收到消息后会同步给Slave，这样一条消息就不止一份了，Master宕机了还有slave中的消息可用，保证了MQ的可靠性和高可用性。而且Rocket MQ4.5.0开始就支持了Dlegder模式，基于raft的，做到了真正意义的HA。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 再说说RocketMQ 是如何保证数据的高容错性的?
* 在不开启容错的情况下，轮询队列进行发送，如果失败了，重试的时候过滤失败的Broker
* 如果开启了容错策略，会通过RocketMQ的预测机制来预测一个Broker是否可用
* 如果上次失败的Broker可用那么还是会选择该Broker的队列
* 如果上述情况失败，则随机选择一个进行发送
* 在发送消息的时候会记录一下调用的时间与是否报错，根据该时间去预测broker的可用时间

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 高吞吐量下如何优化生产者和消费者的性能?
1）开发
* 同一group下，多机部署，并行消费
* 单个Consumer提高消费线程个数
* 批量消费。消息批量拉取，业务逻辑批量处理。

2）运维
* 网卡调优
* jvm调优
* 多线程与cpu调优
* Page Cache

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如果让你来动手实现一个分布式消息中间件，整体架构你会如何设计实现?
* 需要考虑能快速扩容、天然支持集群
* 持久化的姿势
* 高可用性
* 数据0丢失的考虑
* 服务端部署简单、client端使用简单

*** 
## ⭐️⭐️⭐️⭐️⭐️
## RocketMQ在分布式事务支持这块机制的底层原理?
分布式系统中的事务可以使用TCC（Try、Confirm、Cancel）、2pc来解决分布式系统中的消息原子性

RocketMQ 4.3+提供分布事务功能，通过 RocketMQ 事务消息能达到分布式事务的最终一致

RocketMQ实现方式：
* Half Message：预处理消息，当broker收到此类消息后，会存储到RMQ_SYS_TRANS_HALF_TOPIC的消息消费队列中

* 检查事务状态：Broker会开启一个定时任务，消费RMQ_SYS_TRANS_HALF_TOPIC队列中的消息，每次执行任务会向消息发送者确认事务执行状态（提交、回滚、未知），如果是未知，Broker会定时去回调在重新检查。

* 超时：如果超过回查次数，默认回滚消息。

也就是他并未真正进入Topic的queue，而是用了临时queue来放所谓的half message，等提交事务后才会真正的将half message转移到topic下的queue。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## rocketMQ的消息堆积如何处理
首先要找到是什么原因导致的消息堆积，是Producer太多了，Consumer太少了导致的还是说其他情况，总之先定位问题。

然后看下消息消费速度是否正常，正常的话，可以通过上线更多consumer临时解决消息堆积问题。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## RocketMQ如何保证消息不丢失？
首先在如下三个部分都可能会出现丢失消息的情况：
* Producer端
* Broker端
* Consumer端

1）Producer端如何保证消息不丢失

采取send()同步发消息，发送结果是同步感知的。

发送失败后可以重试，设置重试次数。默认3次。

producer.setRetryTimesWhenSendFailed(10);

集群部署，比如发送失败了的原因可能是当前Broker宕机了，重试的时候会发送到其他Broker上。

2）Broker端如何保证消息不丢失

修改刷盘策略为同步刷盘。默认情况下是异步刷盘的。

flushDiskType = SYNC_FLUSH

集群部署，主从模式，高可用。

3）Consumer端如何保证消息不丢失

完全消费正常后在进行手动ack确认。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何让RocketMQ保证消息的顺序消费？
首先多个queue只能保证单个queue里的顺序，queue是典型的FIFO，天然顺序。多个queue同时消费是无法绝对保证消息的有序性的。所以总结如下：

同一topic，同一个QUEUE，发消息的时候一个线程去发送消息，消费的时候 一个线程去消费一个queue里的消息。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 消息重复消费如何解决？
影响消息正常发送和消费的重要原因是网络的不确定性。

引起重复消费的原因

1）ACK

正常情况下在consumer真正消费完消息后应该发送ack，通知broker该消息已正常消费，从queue中剔除

当ack因为网络原因无法发送到broker，broker会认为词条消息没有被消费，此后会开启消息重投机制把消息再次投递到consumer

2）消费模式

在CLUSTERING模式下，消息在broker中会保证相同group的consumer消费一次，但是针对不同group的consumer会推送多次

解决方案：

1）数据库表

处理消息前，使用消息主键在表中带有约束的字段中insert

2）Map

单机时可以使用map ConcurrentHashMap -> putIfAbsent   guava cache

3）Redis

分布式锁搞起来。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## RocketMQ如何做负载均衡？
通过Topic在多Broker中分布式存储实现。

1）producer端

发送端指定message queue发送消息到相应的broker，来达到写入时的负载均衡：

提升写入吞吐量，当多个producer同时向一个broker写入数据的时候，性能会下降

消息分布在多broker中，为负载消费做准备

默认策略是随机选择：

producer维护一个index

每次取节点会自增

index向所有broker个数取余

自带容错策略

其他实现：

* SelectMessageQueueByHash
* hash的是传入的args
* SelectMessageQueueByRandom
* SelectMessageQueueByMachineRoom 没有实现
* 也可以自定义实现MessageQueueSelector接口中的select方法


2）consumer端

采用的是平均分配算法来进行负载均衡。

其他负载均衡算法

* 平均分配策略(默认)(AllocateMessageQueueAveragely) 
* 环形分配策略(AllocateMessageQueueAveragelyByCircle) 
* 手动配置分配策略(AllocateMessageQueueByConfig) 
* 机房分配策略(AllocateMessageQueueByMachineRoom) 
* 一致性哈希分配策略(AllocateMessageQueueConsistentHash) 
* 靠近机房策略(AllocateMachineRoomNearby)

*** 
## ⭐️⭐️⭐️⭐️⭐️
## broker如何处理拉取请求的？
Consumer首次请求Broker

Broker中是否有符合条件的消息

* 如果有

响应Consumer

等待下次Consumer的请求

* 如果没有

DefaultMessageStore#ReputMessageService#run方法

PullRequestHoldService 来Hold连接，每个5s执行一次检查pullRequestTable有没有消息，有的话立即推送

每隔1ms检查commitLog中是否有新消息，有的话写入到pullRequestTable

当有新消息的时候返回请求

挂起consumer的请求，即不断开连接，也不返回数据

使用consumer的offset

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 消费消息是push还是pull？
RocketMQ没有真正意义的push，都是pull，虽然有push类，但实际底层实现采用的是长轮询机制，即拉取方式。

broker端属性 longPollingEnable 标记是否开启长轮询。默认开启。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## RocketMQ消费模式有几种？
## 集群消费
一条消息只会被同Group中的一个Consumer消费
多个Group同时消费一个Topic时，每个Group都会有一个Consumer消费到数据

## 广播消费
消息将对一 个Consumer Group 下的各个 Consumer 实例都消费一遍。即即使这些 Consumer 属于同一个Consumer Group ，消息也会被 Consumer Group 中的每个 Consumer 都消费一次。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## RocketMQ Broker中的消息被消费后会立即删除吗？
不会，每条消息都会持久化到CommitLog中，每个Consumer连接到Broker后会维持消费进度信息，当有消息消费后只是当前Consumer的消费进度（CommitLog的offset）更新了。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## RocketMQ中的Topic和JMS的queue有什么区别？
queue就是来源于数据结构的FIFO队列。而Topic是个抽象的概念，每个Topic底层对应N个queue，而数据也真实存在queue上的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis集群各个节点之间是怎么保持数据一致性的？先说结论：redis集群无法保证强一致性

既然无法保证强一致性，也就是说有可能出现写数据丢失的情况，比如一个客户端发一个写请求给master，master再同步到slave之前就给client一个回执。这个时候会存在一个时间窗口，master 和 slave之间的数据是不一致的。但是redis的最终一致性会使master和slave的数据是最终一致。

另外还有一个可能，在客户端收到了master的一个写请求回执之后，此时master准备把数据同步到slave，同步之前突然挂了，那么这个数据真的就是会丢失了。

如果为了保证强一致，比如我们每秒刷盘进行持久化，那么牺牲了这个吞吐量，就特别类似我们常说的同步复制了。但是redis集群是没有实现强一致的。

除了这种情况会丢数据，还有另外一种情况会丢。

有6个节点的集群，A,B,C,A1,B1,C1, 客户端Z1，这个时候如果发生了网络分区

Z1和B之间的网络 与 A,C,A1,B1,C1断开了

客户端Z1还是会向B写数据，B也会接受这个数据。如果故障时间很短，那没有什么问题；

如果故障时间很长，长到B1这个slave变成master了。那么客户端写Z1的这个数据就丢失了。这时候有个最大时间窗口**maximum window机制**

**如果大的分区里面的slave节点升为master节点，小分区里面的master节点将不再接受写请求**

This amount of time is a very important configuration directive of Redis Cluster, and is called the **node timeout**.

在大集群里面，如果过了node timeout这个时间，master就认为是失败了，那么这个时候备升主

Similarly after node timeout has elapsed without a master node to be able to sense the majority of the other master nodes, it enters an error state and stops accepting writes.

我觉得redis的这个文档写的也有一点疑问：在这个时间窗口之内，小分区里面的客户端还是忘master B一直写数据，但是过了时间窗口后就不能写了，那么这段时间写到master 的数据不是也是丢失了吗？

我们小结一下：

1、redis保证最终一致性

2、用最终一致性换取了高吞吐量

3、主节点挂了的时候，如果数据没有同步到备节点，是会出现数据丢失的情况

4、发生网络分区的时候也可能会丢数据，这个时候有个node timeout时间概念
*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis如何实现分布式锁？分布式锁常见的三种实现方式：

1.  数据库乐观锁；
    
2.  基于Redis的分布式锁；
    
3.  基于ZooKeeper的分布式锁。
    

本地面试考点是，你对Redis使用熟悉吗？Redis中是如何实现分布式锁的。

要点
--

Redis要实现分布式锁，以下条件应该得到满足

**互斥性**

*   在任意时刻，只有一个客户端能持有锁。
    

**不能死锁**

*   客户端在持有锁的期间崩溃而没有主动解锁，也能保证后续其他客户端能加锁。
    

**容错性**

*   只要大部分的Redis节点正常运行，客户端就可以加锁和解锁。
    

实现
--

可以直接通过 `set key value px milliseconds nx` 命令实现加锁， 通过Lua脚本实现解锁。

```lua
//获取锁（unique_value可以是UUID等）
SET resource_name unique_value NX PX  30000
 
//释放锁（lua脚本中，一定要比较value，防止误解锁）
if redis.call("get",KEYS[1]) == ARGV[1] then
    return redis.call("del",KEYS[1])
else
    return 0
end
```

**代码解释**

*   set 命令要用 `set key value px milliseconds nx`，替代 `setnx + expire` 需要分两次执行命令的方式，保证了原子性，
    
*   value 要具有唯一性，可以使用`UUID.randomUUID().toString()`方法生成，用来标识这把锁是属于哪个请求加的，在解锁的时候就可以有依据；
    
*   释放锁时要验证 value 值，防止误解锁；
    
*   通过 Lua 脚本来避免 Check And Set 模型的并发问题，因为在释放锁的时候因为涉及到多个Redis操作 （利用了eval命令执行Lua脚本的原子性）；
    

**加锁代码分析**

首先，set()加入了NX参数，可以保证如果已有key存在，则函数不会调用成功，也就是只有一个客户端能持有锁，满足互斥性。其次，由于我们对锁设置了过期时间，即使锁的持有者后续发生崩溃而没有解锁，锁也会因为到了过期时间而自动解锁（即key被删除），不会发生死锁。最后，因为我们将value赋值为requestId，用来标识这把锁是属于哪个请求加的，那么在客户端在解锁的时候就可以进行校验是否是同一个客户端。

**解锁代码分析**

将Lua代码传到jedis.eval()方法里，并使参数KEYS\[1\]赋值为lockKey，ARGV\[1\]赋值为requestId。在执行的时候，首先会获取锁对应的value值，检查是否与requestId相等，如果相等则解锁（删除key）。

**存在的风险**

如果存储锁对应key的那个节点挂了的话，就可能存在丢失锁的风险，导致出现多个客户端持有锁的情况，这样就不能实现资源的独享了。

1.  客户端A从master获取到锁
    
2.  在master将锁同步到slave之前，master宕掉了（Redis的主从同步通常是异步的）。  
    主从切换，slave节点被晋级为master节点
    
3.  客户端B取得了同一个资源被客户端A已经获取到的另外一个锁。导致存在同一时刻存不止一个线程获取到锁的情况。
    

redlock算法出现
-----------

这个场景是假设有一个 redis cluster，有 5 个 redis master 实例。然后执行如下步骤获取一把锁：

1.  获取当前时间戳，单位是毫秒；
    
2.  跟上面类似，轮流尝试在每个 master 节点上创建锁，过期时间较短，一般就几十毫秒；
    
3.  尝试在大多数节点上建立一个锁，比如 5 个节点就要求是 3 个节点 n / 2 + 1；
    
4.  客户端计算建立好锁的时间，如果建立锁的时间小于超时时间，就算建立成功了；
    
5.  要是锁建立失败了，那么就依次之前建立过的锁删除；
    
6.  只要别人建立了一把分布式锁，你就得不断轮询去尝试获取锁。
    

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X3BuZy84S0tySEs1aWM2WEQ3Z0JHUEY1b3g3Y1Q4UjNZaWJQaWFYbWRrU1NYejViTDR3RGxjYlZwaWFiSHBjYTJjcUY1aE5xQU5TQWdiUUFxYnhaVkhLbEMwTjlGSFEvNjQw?x-oss-process=image/format,png)

Redis 官方给出了以上两种基于 Redis 实现分布式锁的方法，详细说明可以查看：

> https://redis.io/topics/distlock 。

Redisson实现
----------

Redisson是一个在Redis的基础上实现的Java驻内存数据网格（In-Memory Data Grid）。它不仅提供了一系列的分布式的Java常用对象，还实现了可重入锁（Reentrant Lock）、公平锁（Fair Lock、联锁（MultiLock）、 红锁（RedLock）、 读写锁（ReadWriteLock）等，还提供了许多分布式服务。

Redisson提供了使用Redis的最简单和最便捷的方法。Redisson的宗旨是促进使用者对Redis的关注分离（Separation of Concern），从而让使用者能够将精力更集中地放在处理业务逻辑上。

**Redisson 分布式重入锁用法**

Redisson 支持单点模式、主从模式、哨兵模式、集群模式，这里以单点模式为例：

```
// 1.构造redisson实现分布式锁必要的Config
Config config = new Config();
config.useSingleServer().setAddress("redis://127.0.0.1:5379").setPassword("123456").setDatabase(0);
// 2.构造RedissonClient
RedissonClient redissonClient = Redisson.create(config);
// 3.获取锁对象实例（无法保证是按线程的顺序获取到）
RLock rLock = redissonClient.getLock(lockKey);
try {
    /**
     * 4.尝试获取锁
     * waitTimeout 尝试获取锁的最大等待时间，超过这个值，则认为获取锁失败
     * leaseTime   锁的持有时间,超过这个时间锁会自动失效（值应设置为大于业务处理的时间，确保在锁有效期内业务能处理完）
     */
    boolean res = rLock.tryLock((long)waitTimeout, (long)leaseTime, TimeUnit.SECONDS);
    if (res) {
        //成功获得锁，在这里处理业务
    }
} catch (Exception e) {
    throw new RuntimeException("aquire lock fail");
}finally{
    //无论如何, 最后都要解锁
    rLock.unlock();
}
```

加锁流程图

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X3BuZy84S0tySEs1aWM2WEQ3Z0JHUEY1b3g3Y1Q4UjNZaWJQaWFYbW9vcmtuSWZTOERmcGdVckxMUEZad0dqQ0cyejZFRU1JdDIyYkZQTEN1SktMemhIOGpiQm8zZy82NDA?x-oss-process=image/format,png)

解锁流程图

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X3BuZy84S0tySEs1aWM2WEQ3Z0JHUEY1b3g3Y1Q4UjNZaWJQaWFYbUJpYkd4QmdGalVpYWdIOHZpYXVrbVBPd1BZS1p5TnJIZXVZNUg5UGtENzB2RHNpYzZOTUtvcE1ydGcvNjQw?x-oss-process=image/format,png)

我们可以看到，RedissonLock是可重入的，并且考虑了失败重试，可以设置锁的最大等待时间， 在实现上也做了一些优化，减少了无效的锁申请，提升了资源的利用率。

需要特别注意的是，RedissonLock 同样没有解决 节点挂掉的时候，存在丢失锁的风险的问题。而现实情况是有一些场景无法容忍的，所以 Redisson 提供了实现了redlock算法的 RedissonRedLock，RedissonRedLock 真正解决了单点失败的问题，代价是需要额外的为 RedissonRedLock 搭建Redis环境。

所以，如果业务场景可以容忍这种小概率的错误，则推荐使用 RedissonLock， 如果无法容忍，则推荐使用 RedissonRedLock。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何避免消息重复投递或重复消费？
在消息生产时，MQ内部针对每条生产者发送的消息生成一个inner-msg-id，作为去重和幂等的依据（消息投递失败并重传），避免重复的消息进入队列；在消息消费时，要求消息体中必须要有一个bizId（对于同一业务全局唯一，如支付ID、订单ID、帖子ID等）作为去重和幂等的依据，避免同一条消息被重复消费。

这个问题针对业务场景来答分以下几点：

1.比如，你拿到这个消息做数据库的insert操作。那就容易了，给这个消息做一个唯一主键，那么就算出现重复消费的情况，就会导致主键冲突，避免数据库出现脏数据。

2.再比如，你拿到这个消息做redis的set的操作，那就容易了，不用解决，因为你无论set几次结果都是一样的，set操作本来就算幂等操作。

3.如果上面两种情况还不行，上大招。准备一个第三方介质,来做消费记录。以redis为例，给消息分配一个全局id，只要消费过该消息，将<id,message>以K-V形式写入redis。那消费者开始消费前，先去redis中查询有没消费记录即可。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何确保消息接收方消费了消息？
接收方消息确认机制：消费者接收每一条消息后都必须进行确认（消息接收和消息确认是两个不同操作）。只有消费者确认了消息，RabbitMQ才能安全地把消息从队列中删除。这里并没有用到超时机制，RabbitMQ仅通过Consumer的连接中断来确认是否需要重新发送消息。也就是说，只要连接不中断，RabbitMQ给了Consumer足够长的时间来处理消息。

下面罗列几种特殊情况：

* 如果消费者接收到消息，在确认之前断开了连接或取消订阅，RabbitMQ会认为消息没有被分发，然后重新分发给下一个订阅的消费者。（可能存在消息重复消费的隐患，需要根据bizId去重）
* 如果消费者接收到消息却没有确认消息，连接也未断开，则RabbitMQ认为该消费者繁忙，将不会给该消费者分发更多的消息。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 消息怎么路由？
从概念上来说，消息路由必须有三部分：交换器、路由、绑定。生产者把消息发布到交换器上；绑定决定了消息如何从路由器路由到特定的队列；消息最终到达队列，并被消费者接收。

消息发布到交换器时，消息将拥有一个路由键（routing key），在消息创建时设定。
通过队列路由键，可以把队列绑定到交换器上。
消息到达交换器后，RabbitMQ会将消息的路由键与队列的路由键进行匹配（针对不同的交换器有不同的路由规则）。如果能够匹配到队列，则消息会投递到相应队列中；如果不能匹配到任何队列，消息将进入 “黑洞”。

常用的交换器主要分为一下三种：

* direct：如果路由键完全匹配，消息就被投递到相应的队列
* fanout：如果交换器收到消息，将会广播到所有绑定的队列上
* topic：可以使来自不同源头的消息能够到达同一个队列。 使用topic交换器时，可以使用通配符，比如：“*” 匹配特定位置的任意文本， “.” 把路由键分为了几部分，“#” 匹配所有规则等。特别注意：发往topic交换器的消息不能随意的设置选择键（routing_key），必须是由"."隔开的一系列的标识符组成。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 消息如何分发？
若该队列至少有一个消费者订阅，消息将以循环（round-robin）的方式发送给消费者。每条消息只会分发给一个订阅的消费者（前提是消费者能够正常处理消息并进行确认）。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 消息基于什么传输？
由于TCP连接的创建和销毁开销较大，且并发数受系统资源限制，会造成性能瓶颈。RabbitMQ使用信道的方式来传输数据。信道是建立在真实的TCP连接内的虚拟连接，且每条TCP连接上的信道数量没有限制。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## vhost 是什么？起什么作用？
vhost 可以理解为虚拟 broker ，即 mini-RabbitMQ  server。其内部均含有独立的 queue、exchange 和 binding 等，但最最重要的是，其拥有独立的权限系统，可以做到 vhost 范围的用户控制。当然，从 RabbitMQ 的全局角度，vhost 可以作为不同权限隔离的手段（一个典型的例子就是不同的应用可以跑在不同的 vhost 中）。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## RabbitMQ 有几种广播类型?
三种广播模式：

①fanout：所有bind到此exchange的queue都可以接收消息(纯广播，绑定到RabbitMQ的接受者都能收到消息);

②direct：通过routingKey和exchange决定的那个唯一的queue可以接收消息;

③topic：所有符合routingKey(此时可以是一个表达式)的routingKey所bind的queue可以接收消息;

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 要保证消息持久化成功的条件有哪些?
①声明队列必须设置持久化durable设置为 true。

②消息推送投递模式必须设置持久化，deliveryMode设置为2(持久)。

③消息已经到达持久化交换器。

④消息已经到达持久化队列。

以上四个条件都满足才能保证消息持久化成功。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何确保消息正确地发送至RabbitMQ?如何确保消息接收方消费了消息?
1、发送方确认模式

①将信道设置成confirm模式(发送方确认模式)，则所有在信道上发布的消息都会被指派一个唯一的ID。

②一旦消息被投递到目的队列后，或者消息被写入磁盘后(可持久化的消息)，信道会发送一个确认给生产者(包含消息唯一 ID)。

③如果RabbitMQ发生内部错误从而导致消息丢失，会发送一条 nack(notacknowledged，未确认)消息。

④发送方确认模式是异步的，生产者应用程序在等待确认的同时，可以继续发送消息。当确认消息到达生产者应用程序，生产者应用程序的回调方法就会被触发来处理确认消息。

2、接收方确认机制

①消费者接收每一条消息后都必须进行确认(消息接收和消息确认是两个不同操作)。只有消费者确认了消息，RabbitMQ 才能安全地把消息从队列中删除。

②这里并没有用到超时机制，RabbitMQ仅通过Consumer的连接中断来确认是否需要重新发送消息。也就是说，只要连接不中断，RabbitMQ给了Consumer足够长的时间来处理消息。保证数据的最终一致性。

3、下面罗列几种特殊情况

①如果消费者接收到消息，在确认之前断开了连接或取消订阅，RabbitMQ会认为消息没有被分发，然后重新分发给下一个订阅的消费者。(可能存在消息重复消费的隐患，需要去重)

②如果消费者接收到消息却没有确认消息，连接也未断开，则RabbitMQ认为该消费者繁忙，将不会给该消费者分发更多的消息。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## RabbitMQ有哪些重要的角色?
RabbitMQ中重要的角色有：生产者、消费者和代理：

①生产者：消息的创建者，负责创建和推送数据到消息服务器;

②消费者：消息的接收方，用于处理数据和确认消息;

③代理：就是RabbitMQ本身，用于扮演“快递”的角色，本身不生产消息，只是扮演“快递”的角色。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## RabbitMQ的使用场景有哪些?
①跨系统的异步通信，所有需要异步交互的地方都可以使用消息队列。就像我们除了打电话(同步)以外，还需要发短信，发电子邮件(异步)的通讯方式。

②多个应用之间的耦合，由于消息是平台无关和语言无关的，而且语义上也不再是函数调用，因此更适合作为多个应用之间的松耦合的接口。基于消息队列的耦合，不需要发送方和接收方同时在线。在企业应用集成(EAI)中，文件传输，共享数据库，消息队列，远程过程调用都可以作为集成的方法。

③应用内的同步变异步，比如订单处理，就可以由前端应用将订单信息放到队列，后端应用从队列里依次获得消息处理，高峰时的大量订单可以积压在队列里慢慢处理掉。由于同步通常意味着阻塞，而大量线程的阻塞会降低计算机的性能。

④消息驱动的架构(EDA)，系统分解为消息队列，和消息制造者和消息消费者，一个处理流程可以根据需要拆成多个阶段(Stage)，阶段之间用队列连接起来，前一个阶段处理的结果放入队列，后一个阶段从队列中获取消息继续处理。

⑤应用需要更灵活的耦合方式，如发布订阅，比如可以指定路由规则。

⑥跨局域网，甚至跨城市的通讯(CDN行业)，比如北京机房与广州机房的应用程序的通信。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## RabbitMQ 怎么避免消息丢失？
①消息持久化;

②ACK确认机制;

③设置集群镜像模式;

④消息补偿机制。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## RabbitMQ 的消息是怎么发送的？
首先客户端必须连接到 RabbitMQ 服务器才能发布和消费消息，客户端和 rabbit server 之间会创建一个 tcp 连接，一旦 tcp 打开并通过了认证（认证就是你发送给 rabbit 服务器的用户名和密码），你的客户端和 RabbitMQ 就创建了一条 amqp 信道（channel），信道是创建在“真实” tcp 上的虚拟连接，amqp 命令都是通过信道发送出去的，每个信道都会有一个唯一的 id，不论是发布消息，订阅队列都是通过这个信道完成的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 若cluster中拥有某个queue的owner node失效了，且该queue 被声明具有durable属性，是否能够成功从其他node上重新声明该 queue ？
不能，在这种情况下，将得到404 NOT_FOUND错误。只能等queue所 属的node恢复后才能使用该queue。但若该queue本身不具有durable 属性，则可在其他node上重新声明。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 客户端连接到cluster中的任意node上是否都能正常工作？
是的。客户端感觉不到有何不同。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在单node系统和多node构成的cluster系统中声明queue、exchange，以及进行binding会有什么不同？
当你在单node上声明queue时，只要该node上相关元数据进行了变 更，你就会得到Queue.Declare-ok回应；而在cluster上声明queue，则要 求cluster上的全部node都要进行元数据成功更新，才会得到 Queue.Declare-ok回应。另外，若node类型为RAM node则变更的数据 仅保存在内存中，若类型为disk node则还要变更保存在磁盘上的数据。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是元数据？元数据分为哪些类型？包括哪些内容？与cluster相关的元数据有哪些？元数据是如何保存的？元数据在cluster中是如何分布的？
在非cluster模式下，元数据主要分为Queue元数据（queue名字和属性 等）、Exchange元数据（exchange名字、类型和属性等）、Binding元数据 （存放路由关系的查找表）、Vhost元数据（vhost范围内针对前三者的名字空 间约束和安全属性设置）。

在cluster模式下，还包括cluster中node位置信息和node关系信息。元数据按照erlang node的类型确定是仅保存于RAM中，还是同时保存在RAM和disk上。元数据在cluster中是全node 分布的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## RabbitMQ有什么优缺点？
优点：解耦、异步、削峰；

缺点：降低了系统的稳定性：本来系统运行好好的，现在你非要加入个消息队列进去，那消息队列挂了，你的系统不是呵呵了。因此，系统可用性会降低；

增加了系统的复杂性：加入了消息队列，要多考虑很多方面的问题，比如：一致性问题、如何保证消息不被重复消费、如何保证消息可靠性传输等。因此，需要考虑的东西更多，复杂性增大。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是RabbitMQ？为什么使用RabbitMQ？
RabbitMQ是一款开源的，Erlang编写的，基于AMQP协议的，消息中间件；

可以用它来：解耦、异步、削峰。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Nginx 常用配置？
```nginx
worker_processes  8; # 工作进程个数
worker_connections  65535; # 每个工作进程能并发处理（发起）的最大连接数（包含所有连接数）
error_log         /data/logs/nginx/error.log; # 错误日志打印地址
access_log      /data/logs/nginx/access.log; # 进入日志打印地址
log_format  main  '$remote_addr"$request" ''$status $upstream_addr "$request_time"'; # 进入日志格式

## 如果未使用 fastcgi 功能的，可以无视
fastcgi_connect_timeout=300; # 连接到后端 fastcgi 超时时间
fastcgi_send_timeout=300; # 向 fastcgi 请求超时时间(这个指定值已经完成两次握手后向fastcgi传送请求的超时时间)
fastcgi_rend_timeout=300; # 接收 fastcgi 应答超时时间，同理也是2次握手后
fastcgi_buffer_size=64k; # 读取 fastcgi 应答第一部分需要多大缓冲区，该值表示使用1个64kb的缓冲区读取应答第一部分(应答头),可以设置为fastcgi_buffers选项缓冲区大小
fastcgi_buffers 4 64k; # 指定本地需要多少和多大的缓冲区来缓冲fastcgi应答请求，假设一个php或java脚本所产生页面大小为256kb,那么会为其分配4个64kb的缓冲来缓存
fastcgi_cache TEST; # 开启fastcgi缓存并为其指定为TEST名称，降低cpu负载,防止502错误发生

listen       80; # 监听端口
server_name  rrc.test.jiedaibao.com; # 允许域名
root  /data/release/rrc/web; # 项目根目录
index  index.php index.html index.htm; # 访问根文件
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Nginx 常用命令？
* 启动 nginx 。
* 停止 nginx -s stop 或 nginx -s quit 。
* 重载配置 ./sbin/nginx -s reload(平滑重启) 或 service nginx reload 。
* 重载指定配置文件 .nginx -c /usr/local/nginx/conf/nginx.conf 。
* 查看 nginx 版本 nginx -v 。
* 检查配置文件是否正确 nginx -t 。
* 显示帮助信息 nginx -h 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## fastcgi 与 cgi 的区别？
1）cgi

web 服务器会根据请求的内容，然后会 fork 一个新进程来运行外部 c 程序（或 perl 脚本…）， 这个进程会把处理完的数据返回给 web 服务器，最后 web 服务器把内容发送给用户，刚才 fork 的进程也随之退出。

如果下次用户还请求改动态脚本，那么 web 服务器又再次 fork 一个新进程，周而复始的进行。

2）fastcgi

web 服务器收到一个请求时，他不会重新 fork 一个进程（因为这个进程在 web 服务器启动时就开启了，而且不会退出），web 服务器直接把内容传递给这个进程（进程间通信，但 fastcgi 使用了别的方式，tcp 方式通信），这个进程收到请求后进行处理，把结果返回给 web 服务器，最后自己接着等待下一个请求的到来，而不是退出。

综上，差别在于是否重复 fork 进程，处理请求。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## ngx_http_upstream_module的作用是什么?
ngx_http_upstream_module用于定义可通过fastcgi传递、proxy传递、uwsgi传递、memcached传递和scgi传递指令来引用的服务器组。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在Nginx中如何在URL中保留双斜线?
要在URL中保留双斜线，就必须使用merge_slashes_off；语法:merge_slashes [on/off] ； 默认值: merge_slashes on ；环境: http，server

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在Nginx中，如何使用未定义的服务器名称来阻止处理请求?
只需将请求删除的服务器就可以定义为：

```
Server {

listen 80;

server_name “ “ ;

return 444;

}
```

这里，服务器名被保留为一个空字符串，它将在没有“主机”头字段的情况下匹配请求，而一个特殊的`Nginx`的非标准代码`444`被返回，从而终止连接。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 请解释Nginx如何处理HTTP请求。
Nginx使用反应器模式。主事件循环等待操作系统发出准备事件的信号，这样数据就可以从套接字读取，在该实例中读取到缓冲区并进行处理。单个线程可以提供数万个并发连接。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 列举Nginx服务器的最佳用途。
Nginx服务器的最佳用法是在网络上部署动态HTTP内容，使用SCGI、WSGI应用程序服务器、用于脚本的FastCGI处理程序。它还可以作为负载均衡器。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 使用“反向代理服务器”的优点是什么?
反向代理服务器可以隐藏源服务器的存在和特征。它充当互联网云和web服务器之间的中间层。这对于安全方面来说是很好的，特别是当您使用web托管服务时。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Nginx应用场景？
* http服务器。Nginx是一个http服务可以独立提供http服务。可以做网页静态服务器。
* 虚拟主机。可以实现在一台服务器虚拟出多个网站，例如个人网站使用的虚拟机。
* 反向代理，负载均衡。当网站的访问量达到一定程度后，单台服务器不能满足用户的请求时，需要用多台服务器集群可以使用* * nginx做反向代理。并且多台服务器可以平均分担负载，不会应为某台服务器负载高宕机而某台服务器闲置的情况。
* nginx中也可以配置安全管理、比如可以使用Nginx搭建API接口网关,对每个接口服务进行拦截。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Nginx的优缺点？
## 优点：
* 占内存小，可实现高并发连接，处理响应快
* 可实现http服务器、虚拟主机、方向代理、负载均衡
* Nginx配置简单
* 可以不暴露正式的服务器IP地址

## 缺点：
* 动态处理差：nginx处理静态文件好,耗费内存少，但是处理动态页面则很鸡肋，现在一般前端用nginx作为反向代理抗住压力，

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Nginx怎么处理请求的？
- nginx接收一个请求后，首先由listen和server_name指令匹配server模块，再匹配server模块里的location，location就是实际地址

```
 server {            						# 第一个Server区块开始，表示一个独立的虚拟主机站点
        listen       80；      					# 提供服务的端口，默认80
        server_name  localhost；       			# 提供服务的域名主机名
        location / {            				# 第一个location区块开始
            root   html；       				# 站点的根目录，相当于Nginx的安装目录
            index  index.html index.htm；      	# 默认的首页文件，多个用空格分开
        }          			

```


*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么要用Nginx？
跨平台、配置简单、方向代理、高并发连接：处理2-3万并发连接数，官方监测能支持5万并发，内存消耗小：开启10个nginx才占150M内存 ，nginx处理静态文件好，耗费内存少，

而且Nginx内置的健康检查功能：如果有一个服务器宕机，会做一个健康检查，再发送的请求就不会发送到宕机的服务器了。重新将请求提交到其他的节点上。

使用Nginx还能：

* 节省宽带：支持GZIP压缩，可以添加浏览器本地缓存
* 稳定性高：宕机的概率非常小
* 接收用户请求是异步的

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 请解释一下什么是 Nginx ？
Nginx ，是一个 Web 服务器和反向代理服务器，用于 HTTP、HTTPS、SMTP、POP3 和 IMAP 协议。

目前使用的最多的 Web 服务器或者代理服务器，像淘宝、新浪、网易、迅雷等都在使用。

Nginx 的主要功能如下：
* 作为 http server (代替 Apache ，对 PHP 需要 FastCGI 处理器支持)
* FastCGI：Nginx 本身不支持 PHP 等语言，但是它可以通过 FastCGI 来将请求扔给某些语言或框架处理。
* 反向代理服务器
* 实现负载均衡
* 虚拟主机

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说说Netty的执行流程？
* 创建ServerBootStrap实例
* 设置并绑定Reactor线程池：EventLoopGroup，EventLoop就是处理所有注册到本线程的Selector上面的Channel
* 设置并绑定服务端的channel
* 创建处理网络事件的ChannelPipeline和handler，网络时间以流的形式在其中流转，handler完成多数的功能定制：比如编解码 SSl安全认证
* 绑定并启动监听端口
* 当轮训到准备就绪的channel后，由Reactor线程：NioEventLoop执行pipline中的方法，最终调度并执行channelHandler

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Netty 支持哪些心跳类型设置？
* readerIdleTime：为读超时时间（即测试端一定时间内未接受到被测试端消息）。
* writerIdleTime：为写超时时间（即测试端一定时间内向被测试端发送消息）。
* allIdleTime：所有类型的超时时间。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Netty 发送消息有几种方式？
Netty 有两种发送消息的方式：

直接写入 Channel 中，消息从 ChannelPipeline 当中尾部开始移动；
写入和 ChannelHandler 绑定的 ChannelHandlerContext 中，消息从 ChannelPipeline 中的下一个 ChannelHandler 中移动。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Netty 中有哪些重要组件？
Channel：Netty 网络操作抽象类，它除了包括基本的 I/O 操作，如 bind、connect、read、write 等。

EventLoop：主要是配合 Channel 处理 I/O 操作，用来处理连接的生命周期中所发生的事情。

ChannelFuture：Netty 框架中所有的 I/O 操作都为异步的，因此我们需要 ChannelFuture 的 addListener()注册一个 ChannelFutureListener 监听事件，当操作执行成功或者失败时，监听就会自动触发返回结果。

ChannelHandler：充当了所有处理入站和出站数据的逻辑容器。ChannelHandler 主要用来处理各种事件，这里的事件很广泛，比如可以是连接、数据接收、异常、数据转换等。

ChannelPipeline：为 ChannelHandler 链提供了容器，当 channel 创建时，就会被自动分配到它专属的 ChannelPipeline，这个关联是永久性的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Netty 的心跳机制了解么？
在 TCP 保持长连接的过程中，可能会出现断网等网络异常出现，异常发生的时候， client 与 server 之间如果没有交互的话，它们是无法发现对方已经掉线的。为了解决这个问题, 我们就需要引入 心跳机制。

心跳机制的工作原理是: 在 client 与 server 之间在一定时间内没有数据交互时, 即处于 idle 状态时, 客户端或服务器就会发送一个特殊的数据包给对方, 当接收方收到这个数据报文后, 也立即发送一个特殊的数据报文, 回应发送方, 此即一个 PING-PONG 交互。所以, 当某一端收到心跳消息后, 就知道了对方仍然在线, 这就确保 TCP 连接的有效性.

TCP 实际上自带的就有长连接选项，本身是也有心跳包机制，也就是 TCP 的选项：SO_KEEPALIVE。但是，TCP 协议层面的长连接灵活性不够。所以，一般情况下我们都是在应用层协议上实现自定义心跳机制的，也就是在 Netty 层面通过编码实现。通过 Netty 实现心跳机制的话，核心类是 IdleStateHandler 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Netty 的零拷贝了解么？
维基百科是这样介绍零拷贝的：“零复制（英语：Zero-copy；也译零拷贝）技术是指计算机执行操作时，CPU 不需要先将数据从某处内存复制到另一个特定区域。这种技术通常用于通过网络传输文件时节省 CPU 周期和内存带宽。

在 OS 层面上的 Zero-copy 通常指避免在 用户态(User-space) 与 内核态(Kernel-space) 之间来回拷贝数据。而在 Netty 层面 ，零拷贝主要体现在对于数据操作的优化。

Netty 中的零拷贝体现在以下几个方面：

* 使用 Netty 提供的 CompositeByteBuf 类, 可以将多个ByteBuf 合并为一个逻辑上的 ByteBuf, 避免了各个 ByteBuf 之间的拷贝。
* ByteBuf 支持 slice 操作, 因此可以将 ByteBuf 分解为多个共享同一个存储区域的 ByteBuf, 避免了内存的拷贝。
* 通过 FileRegion 包装的FileChannel.tranferTo 实现文件传输, 可以直接将文件缓冲区的数据发送到目标 Channel, 避免了传统通过循环 write 方式导致的内存拷贝问题。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## Netty 的应用场景了解吗？
Netty 主要用来做网络通信。

* 作为 RPC 框架的网络通信工具 ：我们在分布式系统中，不同服务节点之间经常需要相互调用，这个时候就需要 RPC 框架了。不同服务节点之间的通信是如何做的呢？可以使用 Netty 来做。比如我调用另外一个节点的方法的话，至少是要让对方知道我调用的是哪个类中的哪个方法以及相关参数吧！

* 实现一个自己的 HTTP 服务器 ：通过 Netty 我们可以自己实现一个简单的 HTTP 服务器，这个大家应该不陌生。说到 HTTP 服务器的话，作为 Java 后端开发，我们一般使用 Tomcat 比较多。一个最基本的 HTTP 服务器可要以处理常见的 HTTP Method 的请求，比如 POST 请求、GET 请求等等。

* 实现一个即时通讯系统 ：使用 Netty 我们可以实现一个可以聊天类似微信的即时通讯系统，这方面的开源项目还蛮多的，可以自行去 Github 找一找。

* 实现消息推送系统 ：市面上有很多消息推送系统都是基于 Netty 来做的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么要用 Netty？
* 统一的 API，支持多种传输类型，阻塞和非阻塞的。
* 简单而强大的线程模型。
* 自带编解码器解决 TCP 粘包/拆包问题。
* 自带各种协议栈。
* 真正的无连接数据包套接字支持。
* 比直接使用 Java 核心 API 有更高的吞吐量、更低的延迟、更低的资源消耗和更少的内存复制。
* 安全性不错，有完整的 SSL/TLS 以及 StartTLS 支持。
* 社区活跃
* 成熟稳定，经历了大型项目的使用和考验，而且很多开源项目都使用到了 Netty， 比如我们经常接触的 Dubbo、RocketMQ 等等。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Netty 是什么？
Netty 是一个 基于 NIO 的 client-server(客户端服务器)框架，使用它可以快速简单地开发网络应用程序。

它极大地简化并优化了 TCP 和 UDP 套接字服务器等网络编程,并且性能以及安全性等很多方面甚至都要更好。

支持多种协议 如 FTP，SMTP，HTTP 以及各种二进制和基于文本的传统协议。

用官方的总结就是：Netty 成功地找到了一种在不妥协可维护性和性能的情况下实现易于开发，性能，稳定性和灵活性的方法。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## UDP协议会有粘包拆包的问题吗？为什么？
UDP不会有这个问题。

因为TCP是“数据流”协议，UDP是“数据报”协议。

UDP协议的数据包之间是没有联系，而且有明确边界的。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## 了解过粘包拆包吗？为什么会出现粘包拆包？怎么处理粘包拆包？
粘包的主要原因：发送方写入数据<套接字缓冲区大小；接收方读取套接字缓冲区数据不够及时。

拆包的主要原因：发送方写入数据>套接字缓冲区大小；发送方发送的数据大于协议的MTU（最大传输单元），不得已必须拆包。

如何处理：

1、消息长度固定；

2、消息之间用分隔符分隔；

3、在消息头保留一个字段，用于描述消息的长度。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Reactor模型？Reactor的3种版本都知道吗？
Reactor模式究竟是个什么东西呢？这要从事件驱动的开发方式说起。我们知道，对于应用服务器，一个主要规律就是，CPU的处理速度是要远远快于IO速度的，如果CPU为了IO操作（例如从Socket读取一段数据）而阻塞显然是不划算的。好一点的方法是分为多进程或者线程去进行处理，但是这样会带来一些进程切换的开销，试想一个进程一个数据读了500ms，期间进程切换到它3次，但是CPU却什么都不能干，就这么切换走了，是不是也不划算？

这时先驱们找到了事件驱动，或者叫回调的方式，来完成这件事情。这种方式就是，应用业务向一个中间人注册一个回调（event handler），当IO就绪后，就这个中间人产生一个事件，并通知此handler进行处理。这种回调的方式，也体现了“好莱坞原则”（Hollywood principle）-“Don't call us, we'll call you”，在我们熟悉的IoC中也有用到。看来软件开发真是互通的！

好了，我们现在来看Reactor模式。在前面事件驱动的例子里有个问题：我们如何知道IO就绪这个事件，谁来充当这个中间人？Reactor模式的答案是：由一个不断等待和循环的单独进程（线程）来做这件事，它接受所有handler的注册，并负责先操作系统查询IO是否就绪，在就绪后就调用指定handler进行处理，这个角色的名字就叫做Reactor。

Reactor的3种版本：单线程模式、多线程模式、主从多线程模式

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 你了解过哪些IO模型？
### java IO模型

IO模型就是说用什么样的通道进行数据的发送和接收，Java共支持3种网络编程IO模式:BIO，NIO，AIO

### BIO(Blocking IO)

同步阻塞模型，一个客户端连接对应一个处理线程

#### 缺点:

1、IO代码里read操作是阻塞操作，如果连接不做数据读写操作会导致线程阻塞，浪费资源 2、如果线程很多，会导致服务器线程太多，压力太大。

#### 应用场景:

BIO 方式适用于连接数目比较小且固定的架构， 这种方式对服务器资源要求比较高， 但程序简单易理解。  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200712231721825.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pqeV9sb3ZlX2phdmE=,size_16,color_FFFFFF,t_70)

### NIO(Non Blocking IO)

同步非阻塞，服务器实现模式为一个线程可以处理多个请求(连接)，客户端发送的连接请求都会注册到多路复用器selector上，多路复用 器轮询到连接有IO请求就进行处理。  
I/O多路复用底层一般用的Linux API(select，poll，epoll)来实现，他们的区别如下表:  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200712231833400.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pqeV9sb3ZlX2phdmE=,size_16,color_FFFFFF,t_70)

#### 应用场景:

NIO方式适用于连接数目多且连接比较短(轻操作) 的架构， 比如聊天服务器， 弹幕系统， 服务器间通讯，编程比较复杂， JDK1.4 开 始支持  
NIO 有三大核心组件: Channel(通道)， Buffer(缓冲区)，Selector(选择器)  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200712232001412.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pqeV9sb3ZlX2phdmE=,size_16,color_FFFFFF,t_70)

1.  channel 类似于流，每个 channel 对应一个 buffer缓冲区，buffer 底层就是个数组
2.  channel 会注册到 selector 上，由 selector 根据 channel 读写事件的发生将其交由某个空闲的线程处理
3.  selector 可以对应一个或多个线程
4.  NIO 的 Buffer 和 channel 都是既可以读也可以写

### AIO(NIO 2.0)

异步非阻塞， 由操作系统完成后回调通知服务端程序启动线程去处理， 一般适用于连接数较多且连接时间较长的应用 应用场景:  
AIO方式适用于连接数目多且连接比较长(重操作) 的架构，JDK7 开始支持

### BIO、 NIO、 AIO 对比

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200712232149252.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pqeV9sb3ZlX2phdmE=,size_16,color_FFFFFF,t_70)
*** 
## ⭐️⭐️⭐️⭐️⭐️
## MySQL有哪些锁？以及各种锁的作用？在 MySQL 里，根据加锁的范围，可以分为**全局锁、表级锁和行锁**三类。

![](https://img-blog.csdnimg.cn/1e37f6994ef44714aba03b8046b1ace2.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM0ODI3Njc0,size_16,color_FFFFFF,t_70)

### 全局锁

> 全局锁是怎么用的？

要使用全局锁，则要执行这条命：

    flush tables with read lock
    

执行后，**整个数据库就处于只读状态了**，这时其他线程执行以下操作，都会被阻塞：

*   对数据的增删查改操作，比如 insert、delete、update等语句；
*   对表结构的更改操作，比如 alter table、drop table 等语句。

如果要释放全局锁，则要执行这条命令：

    unlock tables
    

当然，当会话断开了，全局锁会被自动释放。

> 全局锁应用场景是什么？

全局锁主要应用于做**全库逻辑备份**，这样在备份数据库期间，不会因为数据或表结构的更新，而出现备份文件的数据与预期的不一样。

举个例子大家就知道了。

在全库逻辑备份期间，假设不加全局锁的场景，看看会出现什么意外的情况。

如果在全库逻辑备份期间，有用户购买了一件商品，一般购买商品的业务逻辑是会涉及到多张数据库表的更细，比如在用户表更新该用户的余额，然后在商品表更新被购买的商品的库存。

那么，有可能出现这样的顺序：

1.  先备份了用户表的数据；
2.  然后有用户发起了购买商品的操作；
3.  接着再备份商品表的数据。

也就是在备份用户表和商品表之间，有用户购买了商品。

这种情况下，备份的结果是用户表中该用户的余额并没有扣除，反而商品表中该商品的库存被减少了，如果后面用这个备份文件恢复数据库数据的话，用户钱没少，而库存少了，等于用户白嫖了一件商品。

所以，在全库逻辑备份期间，加上全局锁，就不会出现上面这种情况了。

> 加全局锁又会带来什么缺点呢？

加上全局锁，意味着整个数据库都是只读状态。

那么如果数据库里有很多数据，备份就会花费很多的时间，关键是备份期间，业务只能读数据，而不能更新数据，这样会造成业务停滞。

> 既然备份数据库数据的时候，使用全局锁会影响业务，那有什么其他方式可以避免？

有的，如果数据库的引擎支持的事务支持**可重复读的隔离级别**，那么在备份数据库之前先开启事务，会先创建 Read View，然后整个事务执行期间都在用这个 Read View，而且由于 MVCC 的支持，备份期间业务依然可以对数据进行更新操作。

因为在可重复读的隔离级别下，即使其他事务更新了表的数据，也不会影响备份数据库时的 Read View，这就是事务四大特性中的隔离性，这样备份期间备份的数据一直是在开启事务时的数据。

备份数据库的工具是 mysqldump，在使用 mysqldump 时加上 `–single-transaction` 参数的时候，就会在备份数据库之前先开启事务。这种方法只适用于支持「可重复读隔离级别的事务」的存储引擎。

InnoDB 存储引擎默认的事务隔离级别正是可重复读，因此可以采用这种方式来备份数据库。

但是，对于 MyISAM 这种不支持事务的引擎，在备份数据库时就要使用全局锁的方法。

### 表级锁

> MySQL 表级锁有哪些？具体怎么用的。

MySQL 里面表级别的锁有这几种：

*   表锁；
*   元数据锁（MDL）;
*   意向锁；
*   AUTO-INC 锁；

#### 表锁

先来说说***表锁***。

如果我们想对学生表（t_student）加表锁，可以使用下面的命令：

    //表级别的共享锁，也就是读锁；
    lock tables t_student read;
    
    //表级别的独占锁，也就是写锁；
    lock tables t_stuent wirte;
    

需要注意的是，表锁除了会限制别的线程的读写外，也会限制本线程接下来的读写操作。

也就是说如果本线程对学生表加了「共享表锁」，那么本线程接下来如果要对学生表执行写操作的语句，是会被阻塞的，当然其他线程对学生表进行写操作时也会被阻塞，直到锁被释放。

要释放表锁，可以使用下面这条命令，会释放当前会话的所有表锁：

    unlock tables
    

另外，当会话退出后，也会释放所有表锁。

不过尽量避免在使用 InnoDB 引擎的表使用表锁，因为表锁的颗粒度太大，会影响并发性能，**InnoDB 牛逼的地方在于实现了颗粒度更细的行级锁**。

#### 元数据锁

再来说说***元数据锁（MDL）***。

我们不需要显示的使用 MDL，因为当我们对数据库表进行操作时，会自动给这个表加上 MDL：

*   对一张表进行 CRUD 操作时，加的是 **MDL 读锁**；
*   对一张表做结构变更操作的时候，加的是 **MDL 写锁**；

MDL 是为了保证当用户对表执行 CRUD 操作时，防止其他线程对这个表结构做了变更。

当有线程在执行 select 语句（ 加 MDL 读锁）的期间，如果有其他线程要更改该表的结构（ 申请 MDL 写锁），那么将会被阻塞，直到执行完 select 语句（ 释放 MDL 读锁）。

反之，当有线程对表结构进行变更（ 加 MDL 写锁）的期间，如果有其他线程执行了 CRUD 操作（ 申请 MDL 读锁），那么就会被阻塞，直到表结构变更完成（ 释放 MDL 写锁）。

> MDL 不需要显示调用，那它是在什么时候释放的?

MDL 是在事务提交后才会释放，这意味着**事务执行期间，MDL 是一直持有的**。

那如果数据库有一个长事务（所谓的长事务，就是开启了事务，但是一直还没提交），那在对表结构做变更操作的时候，可能会发生意想不到的事情，比如下面这个顺序的场景：

1.  首先，线程 A 先启用了事务（但是一直不提交），然后执行一条 select 语句，此时就先对该表加上 MDL 读锁；
2.  然后，线程 B 也执行了同样的 select 语句，此时并不会阻塞，因为「读读」并不冲突；
3.  接着，线程 C 修改了表字段，此时由于线程 A 的事务并没有提交，也就是 MDL 读锁还在占用着，这时线程 C 就无法申请到 MDL 写锁，就会被阻塞，

那么在线程 C 阻塞后，后续有对该表的 select 语句，就都会被阻塞，如果此时有大量该表的 select 语句的请求到来，就会有大量的线程被阻塞住，这时数据库的线程很快就会爆满了。

> 为什么线程 C 因为申请不到 MDL 写锁，而导致后续的申请读锁的查询操作也会被阻塞？

这是因为申请 MDL 锁的操作会形成一个队列，队列中**写锁获取优先级高于读锁**，一旦出现 MDL 写锁等待，会阻塞后续该表的所有 CRUD 操作。

所以为了能安全的对表结构进行变更，在对表结构变更前，先要看看数据库中的长事务，是否有事务已经对表加上了 MDL 读锁，如果可以考虑 kill 掉这个长事务，然后再做表结构的变更。

#### 意向锁

接着，说说***意向锁***。

*   在使用 InnoDB 引擎的表里对某些记录加上「共享锁」之前，需要先在表级别加上一个「意向共享锁」；
*   在使用 InnoDB 引擎的表里对某些纪录加上「独占锁」之前，需要先在表级别加上一个「意向独占锁」；

也就是，当执行插入、更新、删除操作，需要先对表加上「意向独占锁」，然后对该记录加独占锁。

而普通的 select 是不会加行级锁的，普通的 select 语句是利用 MVCC 实现一致性读，是无锁的。

不过，select 也是可以对记录加共享锁和独占锁的，具体方式如下：

    //先在表上加上意向共享锁，然后对读取的记录加独占锁
    select ... lock in share mode;
    
    //先表上加上意向独占锁，然后对读取的记录加独占锁
    select ... for update;
    

**意向共享锁和意向独占锁是表级锁，不会和行级的共享锁和独占锁发生冲突，而且意向锁之间也不会发生冲突，只会和共享表锁（_lock tables … read_）和独占表锁（_lock tables … write_）发生冲突。**

表锁和行锁是满足读读共享、读写互斥、写写互斥的。

如果没有「意向锁」，那么加「独占表锁」时，就需要遍历表里所有记录，查看是否有记录存在独占锁，这样效率会很慢。

那么有了「意向锁」，由于在对记录加独占锁前，先会加上表级别的意向独占锁，那么在加「独占表锁」时，直接查该表是否有意向独占锁，如果有就意味着表里已经有记录被加了独占锁，这样就不用去遍历表里的记录。

所以，**意向锁的目的是为了快速判断表里是否有记录被加锁**。

#### AUTO-INC 锁

最后，说说 _**AUTO-INC 锁**_。

在为某个字段声明 `AUTO_INCREMENT` 属性时，之后可以在插入数据时，可以不指定该字段的值，数据库会自动给该字段赋值递增的值，这主要是通过 AUTO-INC 锁实现的。

AUTO-INC 锁是特殊的表锁机制，锁**不是再一个事务提交后才释放，而是再执行完插入语句后就会立即释放**。

**在插入数据时，会加一个表级别的 AUTO-INC 锁**，然后为被 `AUTO_INCREMENT` 修饰的字段赋值递增的值，等插入语句执行完成后，才会把 AUTO-INC 锁释放掉。

那么，一个事务在持有 AUTO-INC 锁的过程中，其他事务的如果要向该表插入语句都会被阻塞，从而保证插入数据时，被 `AUTO_INCREMENT` 修饰的字段的值是连续递增的。

但是， AUTO-INC 锁再对大量数据进行插入的时候，会影响插入性能，因为另一个事务中的插入会被阻塞。

因此， 在 MySQL 5.1.22 版本开始，InnoDB 存储引擎提供了一种**轻量级的锁**来实现自增。

一样也是在插入数据的时候，会为被 `AUTO_INCREMENT` 修饰的字段加上轻量级锁，**然后给该字段赋值一个自增的值，就把这个轻量级锁释放了，而不需要等待整个插入语句执行完后才释放锁**。

InnoDB 存储引擎提供了个 innodb\_autoinc\_lock_mode 的系统变量，是用来控制选择用 AUTO-INC 锁，还是轻量级的锁。

*   当 innodb\_autoinc\_lock_mode = 0，就采用 AUTO-INC 锁；
*   当 innodb\_autoinc\_lock_mode = 2，就采用轻量级锁；
*   当 innodb\_autoinc\_lock_mode = 1，这个是默认值，两种锁混着用，如果能够确定插入记录的数量就采用轻量级锁，不确定时就采用 AUTO-INC 锁。

不过，当 innodb\_autoinc\_lock_mode = 2 是性能最高的方式，但是会带来一定的问题。因为并发插入的存在，在每次插入时，自增长的值可能不是连续的，**这在有主从复制的场景中是不安全的**。

> 行级锁有哪些？

InnoDB 引擎是支持行级锁的，而 MyISAM 引擎并不支持行级锁。

行级锁的类型主要有三类：

*   Record Lock，记录锁，也就是仅仅把一条记录锁上；
*   Gap Lock，间隙锁，锁定一个范围，但是不包含记录本身；
*   Next-Key Lock：Record Lock + Gap Lock 的组合，锁定一个范围，并且锁定记录本身。

前面也提到，普通的 select 语句是不会对记录加锁的，如果要在查询时对记录加行锁，可以使用下面这两个方式：

    //对读取的记录加共享锁
    select ... lock in share mode;
    
    //对读取的记录加独占锁
    select ... for update;
    

上面这两条语句必须再一个事务中，当事务提交了，锁就会被释放，因此在使用这两条语句的时候，要加上 begin、start transaction 或者 set autocommit = 0。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## MySQL分库分表了解过吗？
**一、前言**
========

在互联网还未崛起的时代,我们的传统应用都有这样一个特点：访问量、数据量都比较小，单库单表都完全可以支撑整个业务。随着互联网的发展和用户规模的迅速扩大,对系统的要求也越来越高。因此传统的MySQL单库单表架构的性能问题就暴露出来了。而有下面几个因素会影响数据库性能:

**1.1** **数据量**
---------------

MySQL单库数据量在5000万以内性能比较好,超过阈值后性能会随着数据量的增大而变弱。MySQL单表数据量是500w-1000w之间性能比较好,超过1000w性能也会下降。

**1.2** **磁盘**
--------------

因为单个服务的磁盘空间是有限制的,如果并发压力下,所有的请求都访问同一个节点,肯定会对磁盘IO造成非常大的影响。

**1.3** **数据库连接**
-----------------

数据库连接是非常稀少的资源,如果一个库里既有用户、商品、订单相关的数据,当海量用户同时操作时,数据库连接就很可能成为瓶颈。

为了提升性能,所以我们必须要解决上述几个问题,那就有必要引进**分库分表**。

**二、垂直拆分 or 水平拆分？**
===================

关系型数据库本身比较容易成为系统瓶颈，单机存储容量、连接数、处理能力都有限。当单表的数据量达到1000W或100G以后，由于查询维度较多，即使添加从库、优化索引，做很多操作时性能仍下降严重。此时就要考虑对其进行切分了，切分的目的就在于减少数据库的负担，缩短查询时间。

数据库分布式核心内容无非就是**数据切分（****Sharding****）**，以及切分后对数据的定位、整合。数据切分就是将数据分散存储到多个数据库中，使得单一数据库中的数据量变小，通过扩充主机的数量缓解单一数据库的性能问题，从而达到提升数据库操作性能的目的。

数据切分根据其切分类型，可以分为两种方式：**垂直（纵向）切分**和**水平（横向）切分**

当我们单个库太大时,我们先要看一下是因为表太多还是数据量太大，如果是**表太多**,则应该将部分表进行迁移(可以按业务区分),这就是所谓的**垂直切分**。如果是**数据量太大**,则需要将表拆成更多的小表,来减少单表的数据量,这就是所谓的**水平拆分**。

**三、垂直拆分**
==========

垂直切分常见有**垂直分库**和**垂直分表**两种。

**3.1** **垂直分库**
----------------

垂直分库针对的是一个系统中的不同业务进行拆分,比如用户一个库,商品一个库,订单一个库。 一个购物网站对外提供服务时,会同时对用户、商品、订单表进行操作。没拆分之前, 全部都是落到单一的库上的,这会让数据库的单库处理能力成为瓶颈。如果垂直分库后还是将用户、商品、订单放到同一个服务器上,只是分到了不同的库,这样虽然会减少单库的压力,但是随着用户量增大,这会让整个数据库的处理能力成为瓶颈,还有单个服务器的磁盘空间、内存也会受非常大的影响。 所以我们要将其拆分到多个服务器上，这样上面的问题都解决了，以后也不会面对单机资源问题。这种做法与"微服务治理"的做法相似，每个微服务使用单独的一个数据库。

![](https://img-blog.csdnimg.cn/20200225163309370.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2N5OTczMDcxMjYz,size_16,color_FFFFFF,t_70)

**3.2** **垂直分表**
----------------

也就是“大表拆小表”，**基于列字段**进行的。一般是表中的字段较多，将不常用的， 数据较大，长度较长（比如text类型字段）的字段数据拆分到“扩展表“。一般是针对那种几百列的大表，也避免查询时，数据量太大造成的**“****跨页****”****问题**。MySQL底层是通过**数据页**存储的，一条记录占用空间过大会导致跨页（**页溢出**），造成额外的性能开销（IO操作变多）。另外数据库以页为单位将数据加载到内存中，而页中存储的是行数据，页大小固定，一行数据占用空间越小，页中存储的行数据就越多。这样表中字段长度较短且访问频率较高，内存能加载更多的数据，内存命中率更高，减少了磁盘IO，从而提升了数据库性能。

![](https://img-blog.csdnimg.cn/20200225163309263.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2N5OTczMDcxMjYz,size_16,color_FFFFFF,t_70)

**3.3** **垂直拆分的优缺点**
--------------------

**优点：**

*   解决业务系统层面的耦合，业务清晰
*   与微服务的治理类似，也能对不同业务的数据进行分级管理、维护、监控、扩展等
*   高并发场景下，垂直切分一定程度的提升IO、数据库连接数、单机硬件资源的瓶颈

**缺点：**

*   部分表无法join，只能通过接口聚合方式解决，提升了开发的复杂度
*   单机的ACID被打破，需要引入分布式事务，而分布式事务处理复杂
*   依然存在单表数据量过大的问题（需要水平切分）
*   靠外键去进行约束的场景会受到影响
    

**四、水平拆分**
==========

当一个应用难以再细粒度的垂直切分，或切分后数据量行数巨大，存在单库读写、存储性能瓶颈，这时候就需要进行水平切分了。

水平切分分为**库内分表**和**分库分表**，是根据表内数据内在的逻辑关系，将同一个表按不同的条件分散到多个数据库或多个表中，每个表中只包含一部分数据，从而使得单个表的数据量变小，达到分布式的效果。如图所示：

![](https://img-blog.csdnimg.cn/20200225163309431.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2N5OTczMDcxMjYz,size_16,color_FFFFFF,t_70)

**4.1** **水平分表**
----------------

和垂直分表有一点类似,不过垂直分表是基于列的,而水平分表是基于全表的。水平拆分可以大大减少单表数据量,提升查询效率。这里的水平分表指的是在一个数据库进行的**库内分表**。

库内分表只解决了单一表数据量过大的问题，但没有将表分布到不同机器的库上，因此对于减轻MySQL数据库的压力来说，帮助不是很大，大家还是竞争同一个物理机的CPU、内存、网络IO，最好通过分库分表来解决。

**4.2** **水平分库分表**
------------------

将单张表的数据切分到多个服务器上去，每个服务器具有相同的库与表，只是表中数据集合不同。 水平分库分表能够有效的缓解单机和单库的性能瓶颈和压力，突破IO、连接数、硬件资源等的瓶颈。

**4.3** **水平拆分的优缺点**
--------------------

**优点：**

*   不存在单库数据量过大、高并发的性能瓶颈，提升系统稳定性和负载能力
*   应用端改造较小，不需要拆分业务模块

**缺点：**

*   ACID被打破，跨分片的事务一致性难以保证
*   跨库的join关联查询性能较差
*   数据多次扩展难度和维护量极大
*   靠外键去进行约束的场景会受到影响
    
*   依赖单库的自增ID会受到影响

**五、几种常用的分库分表的策略**
==================

**5.1** **根据数值范围**
------------------

按照时间区间或ID区间来切分。例如：按日期将不同月甚至是日的数据分散到不同的库中；将userId为1~9999的记录分到第一个库，10000~20000的分到第二个库，以此类推。某种意义上，某些系统中使用的"冷热数据分离"，将一些使用较少的历史数据迁移到其他库中，业务功能上只提供热点数据的查询，也是类似的实践。

这样的优点在于：

*   单表大小可控
*   天然便于水平扩展，后期如果想对整个分片集群扩容时，只需要添加节点即可，无需对其他分片的数据进行迁移
*   使用分片字段进行范围查找时，连续分片可快速定位分片进行快速查询，有效避免跨分片查询的问题。

缺点：

*   **热点数据**成为性能瓶颈。连续分片可能存在数据热点，例如按时间字段分片，有些分片存储最近时间段内的数据，可能会被频繁的读写，而有些分片存储的历史数据，则很少被查询

![](https://img-blog.csdnimg.cn/20200225163309398.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2N5OTczMDcxMjYz,size_16,color_FFFFFF,t_70)

**5.2** **根据数值取模**
------------------

一般采用hash取模mod的切分方式，例如：将 Customer 表根据 cusno 字段切分到4个库中，余数为0的放到第一个库，余数为1的放到第二个库，以此类推。这样同一个用户的数据会分散到同一个库中，如果查询条件带有cusno字段，则可明确定位到相应库去查询。再比如说有用户表user,将其分成3个表user0,user1,user2.路由规则是对3取模,当uid=1时,对应到的是user1,uid=2时,对应的是user2.

优点：

*   数据分片相对比较均匀，不容易出现热点和并发访问的瓶颈

缺点：

*   后期分片集群扩容时，需要迁移旧的数据（使用**一致性hash算法**能较好的避免这个问题），否则会导致历史数据失效。
*   容易面临跨分片查询的复杂问题。比如上例中，如果频繁用到的查询条件中不带cusno时，将会导致无法定位数据库，从而需要同时向4个库发起查询，再在内存中合并数据，取最小集返回给应用，分库反而成为拖累。

![](https://img-blog.csdnimg.cn/20200225163309495.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2N5OTczMDcxMjYz,size_16,color_FFFFFF,t_70)

**5.3** **根据地理位置**
------------------

根据地理位置，将相同地区的放到一张表中，比如华南区一个表,华北一个表。

**六、分库分表后带来的问题**
================

分库分表能有效的缓解单机和单库带来的性能瓶颈和压力，突破网络IO、硬件资源、连接数的瓶颈，同时也带来了一些问题。下面将描述这些技术挑战以及对应的解决思路。 

**6.1** **事务一致性问题**
-------------------

### **6.1.1** **分布式事务**

当更新内容同时分布在不同库中，不可避免会带来跨库事务问题。跨分片事务也是分布式事务，没有简单的方案，一般可使用"XA协议"和"两阶段提交"处理。

分布式事务的几种解决方案：

1.  使用分布式事务中间件
2.  使用MySQL自带的针对跨库的事务一致性方案(XA),不过性能要比单库的慢10倍左右。
3.  能否避免掉跨库操作(比如将用户和商品放在同一个库中)

分布式事务能最大限度保证了数据库操作的原子性。但在提交事务时需要协调多个节点，推后了提交事务的时间点，延长了事务的执行时间。导致事务在访问共享资源时发生冲突或死锁的概率增高。随着数据库节点的增多，这种趋势会越来越严重，从而成为系统在数据库层面上水平扩展的枷锁。

### **6.1.2** **最终一致性**

对于那些性能要求很高，但对一致性要求不高的系统，往往不苛求系统的实时一致性，只要在允许的时间段内达到最终一致性即可，可采用事务补偿的方式。与事务在执行中发生错误后立即回滚的方式不同，**事务补偿**是一种事后检查补救的措施，一些常见的实现方法有：对数据进行对账检查，基于日志进行对比，定期同标准数据来源进行同步等等。事务补偿还要结合业务系统来考虑。

**6.2** **跨节点关联查询** **join** **问题**
-----------------------------------

切分之前，系统中很多列表和详情页所需的数据可以通过sql join来完成。而切分之后，数据可能分布在不同的节点上，此时join带来的问题就比较麻烦了，考虑到性能，尽量避免使用join查询。

解决这个问题的一些方法：

### **6.2.1** **全局表**

全局表，也可看做是"数据字典表"，就是系统中所有模块都可能依赖的一些表，为了避免跨库join查询，可以将这类表在每个数据库中都保存一份。这些数据通常很少会进行修改，所以也不担心一致性的问题。

### **6.2.2** **字段冗余**

一种典型的反范式设计，利用空间换时间，为了性能而避免join查询。例如：订单表保存userId时候，也将userName冗余保存一份，这样查询订单详情时就不需要再去查询"买家user表"了。

但这种方法适用场景也有限，比较适用于依赖字段比较少的情况。而冗余字段的数据一致性也较难保证，就像上面订单表的例子，买家修改了userName后，是否需要在历史订单中同步更新呢？这也要结合实际业务场景进行考虑。

### **6.2.3** **数据组装**

在系统层面，分两次查询，第一次查询的结果集中找出关联数据id，然后根据id发起第二次请求得到关联数据。最后将获得到的数据进行字段拼装。

### **6.2.4 ER****分片**

关系型数据库中，如果可以先确定表之间的关联关系，并将那些存在关联关系的表记录存放在同一个分片上，那么就能较好的避免跨分片join问题。在1:1或1:n的情况下，通常按照主表的ID主键切分。如下图所示：

![](https://img-blog.csdnimg.cn/20200225163309571.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2N5OTczMDcxMjYz,size_16,color_FFFFFF,t_70)

这样一来，Data Node1上面的order订单表与orderdetail订单详情表就可以通过orderId进行局部的关联查询了，Data Node2上也一样。

**6.3** **跨节点分页、排序、函数问题**
-------------------------

跨节点多库进行查询时，会出现limit分页、order by排序等问题。分页需要按照指定字段进行排序，当排序字段就是分片字段时，通过分片规则就比较容易定位到指定的分片；当排序字段非分片字段时，就变得比较复杂了。需要先在不同的分片节点中将数据进行排序并返回，然后将不同分片返回的结果集进行汇总和再次排序，最终返回给用户。如图所示：

![](https://img-blog.csdnimg.cn/20200225163309660.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2N5OTczMDcxMjYz,size_16,color_FFFFFF,t_70)

上图中只是取第一页的数据，对性能影响还不是很大。但是如果取得页数很大，情况则变得复杂很多，因为各分片节点中的数据可能是随机的，为了排序的准确性，需要将所有节点的前N页数据都排序好做合并，最后再进行整体的排序，这样的操作时很耗费CPU和内存资源的，所以页数越大，系统的性能也会越差。

在使用Max、Min、Sum、Count之类的函数进行计算的时候，也需要先在每个分片上执行相应的函数，然后将各个分片的结果集进行汇总和再次计算，最终将结果返回。如图所示：

![](https://img-blog.csdnimg.cn/20200225163309691.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2N5OTczMDcxMjYz,size_16,color_FFFFFF,t_70)

总之**，**因为我们是将数据分散存储到不同的库、表里的,当我们查询指定数据列表时,数据来源于不同的子库或者子表,就必然会引发结果集合并、排序的问题。如果每次查询都需要排序、合并等操作,性能肯定会受非常大的影响。走缓存是一种解决方案。

**6.4** **全局主键避重问题**
--------------------

在分库分表环境中，由于表中数据同时存在不同数据库中，主键值平时使用的自增长将无用武之地，某个分区数据库自生成的ID无法保证全局唯一。因此需要单独设计全局主键，以避免跨库主键重复问题。有一些常见的主键生成策略：

### **6.4.1** **UUID**

UUID标准形式包含32个16进制数字，分为5段，形式为8-4-4-4-12的36个字符，例如：550e8400-e29b-41d4-a716-446655440000

UUID是主键是最简单的方案，本地生成，性能高，没有网络耗时。但缺点也很明显，由于UUID非常长，会占用大量的存储空间；另外，作为主键建立索引和基于索引进行查询时都会存在性能问题，在InnoDB下，UUID的无序性会引起数据位置频繁变动。

### **6.4.2** **结合数据库维护主键****ID****表**

在数据库中建立 sequence 表：

    CREATE TABLE `sequence` (   `id` bigint(20) unsigned NOT NULL auto_increment,   `stub` char(1) NOT NULL default '',   PRIMARY KEY  (`id`),   UNIQUE KEY `stub` (`stub`) ) ENGINE=MyISAM;

stub字段设置为唯一索引，同一stub值在sequence表中只有一条记录，可以同时为多张表生成全局ID。sequence表的内容，如下所示：

    +-------------------+------+  | id                | stub | +-------------------+------+  | 72157623227190423 |    a | +-------------------+------+ 

使用 MyISAM 存储引擎而不是 InnoDB，以获取更高的性能。MyISAM使用的是表级别的锁，对表的读写是串行的，所以不用担心在并发时两次读取同一个ID值。

当需要全局唯一的64位ID时，执行：

    REPLACE INTO sequence (stub) VALUES ('a');  SELECT LAST_INSERT_ID(); 

这两条语句是Connection级别的，select last\_insert\_id() 必须与 replace into 在同一数据库连接下才能得到刚刚插入的新ID。

使用replace into代替insert into好处是避免了表行数过大，不需要另外定期清理。

此方案较为简单，但缺点也明显：存在单点问题，强依赖DB，当DB异常时，整个系统都不可用。配置主从可以增加可用性，但当主库挂了，主从切换时，数据一致性在特殊情况下难以保证。另外性能瓶颈限制在单台MySQL的读写性能。

flickr团队使用的一种主键生成策略，与上面的sequence表方案类似，但更好的解决了单点和性能瓶颈的问题。

这一方案的整体思想是：建立2个以上的全局ID生成的服务器，每个服务器上只部署一个数据库，每个库有一张sequence表用于记录当前全局ID。表中ID增长的步长是库的数量，起始值依次错开，这样能将ID的生成散列到各个数据库上。如下图所示：

![](https://img-blog.csdnimg.cn/20200225163309863.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2N5OTczMDcxMjYz,size_16,color_FFFFFF,t_70)

由两个数据库服务器生成ID，设置不同的auto_increment值。第一台sequence的起始值为1，每次步长增长2，另一台的sequence起始值为2，每次步长增长也是2。结果第一台生成的ID都是奇数（1, 3, 5, 7 ...），第二台生成的ID都是偶数（2, 4, 6, 8 ...）。

这种方案将生成ID的压力均匀分布在两台机器上。同时提供了系统容错，第一台出现了错误，可以自动切换到第二台机器上获取ID。但有以下几个缺点：系统添加机器，水平扩展时较复杂；每次获取ID都要读写一次DB，DB的压力还是很大，只能靠堆机器来提升性能。

可以基于flickr的方案继续优化，使用批量的方式降低数据库的写压力，每次获取一段区间的ID号段，用完之后再去数据库获取，可以大大减轻数据库的压力。如下图所示：

![](https://img-blog.csdnimg.cn/20200225163309804.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2N5OTczMDcxMjYz,size_16,color_FFFFFF,t_70)

还是使用两台DB保证可用性，数据库中只存储当前的最大ID。ID生成服务每次批量拉取6个ID，先将max\_id修改为5，当应用访问ID生成服务时，就不需要访问数据库，从号段缓存中依次派发0~5的ID。当这些ID发完后，再将max\_id修改为11，下次就能派发6~11的ID。于是，数据库的压力降低为原来的1/6。

### **6.4.3** **Snowflake****分布式自增****ID****算法**

Twitter的snowflake算法解决了分布式系统生成全局ID的需求，生成64位的Long型数字，组成部分：

*   第一位未使用
*   接下来41位是毫秒级时间，41位的长度可以表示69年的时间
*   5位datacenterId，5位workerId。10位的长度最多支持部署1024个节点
*   最后12位是毫秒内的计数，12位的计数顺序号支持每个节点每毫秒产生4096个ID序列

![](https://img-blog.csdnimg.cn/20200225163309952.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2N5OTczMDcxMjYz,size_16,color_FFFFFF,t_70)

这样的好处是：毫秒数在高位，生成的ID整体上按时间趋势递增；不依赖第三方系统，稳定性和效率较高，理论上QPS约为409.6w/s（1000*2^12），并且整个分布式系统内不会产生ID碰撞；可根据自身业务灵活分配bit位。

不足就在于：强依赖机器时钟，如果时钟回拨，则可能导致生成ID重复。

**综上**

结合数据库和snowflake的唯一ID方案，可以参考业界较为成熟的解法：[Leaf——美团点评分布式ID生成系统](https://tech.meituan.com/MT_Leaf.html)，并考虑到了高可用、容灾、分布式下时钟等问题。

**6.5** **数据迁移、扩容问题**
---------------------

当业务高速发展，面临性能和存储的瓶颈时，才会考虑分片设计，此时就不可避免的需要考虑历史数据迁移的问题。一般做法是先读出历史数据，然后按指定的分片规则再将数据写入到各个分片节点中。此外还需要根据当前的数据量和QPS，以及业务发展的速度，进行容量规划，推算出大概需要多少分片（一般建议单个分片上的单表数据量不超过1000W）

如果采用数值范围分片，只需要添加节点就可以进行扩容了，不需要对分片数据迁移。如果采用的是数值取模分片，针对数据量的递增,可能需要动态的增加表，此时因为reHash有可能导致数据迁移问题，则考虑后期的扩容问题就相对比较麻烦。

**6.6** **外键约束问题**
------------------

外键约束问题比较难解决，不能完全依赖数据库本身来完成之前的功能。如果需要对分库后的单表做外键约束，就需要分库后每个单库的数据是内聚的，否则就只能靠应用层的判断，容错方式了。

**七****.** **什么时候考虑切分**
=======================

下面讲述一下什么时候需要考虑做数据切分。

**7.1** **能不切分尽量不要切分**
----------------------

并不是所有表都需要进行切分，主要还是看数据的增长速度。切分后会在某种程度上提升业务的复杂度，数据库除了承载数据的存储和查询外，协助业务更好的实现需求也是其重要工作之一。

不到万不得已不用轻易使用分库分表这个大招，避免"过度设计"和"过早优化"。分库分表之前，不要为分而分，先尽力去做力所能及的事情，例如：升级硬件、升级网络、读写分离、索引优化等等。当数据量达到单表的瓶颈时候，再考虑分库分表。

**7.2** **数据量过大，正常运维影响业务访问**
----------------------------

这里说的运维，指：

1.  对数据库备份，如果单表太大，备份时需要大量的磁盘IO和网络IO。例如1T的数据，网络传输占50MB时候，需要20000秒才能传输完毕，整个过程的风险都是比较高的
2.  对一个很大的表进行DDL修改时，MySQL会锁住全表，这个时间会很长，这段时间业务不能访问此表，影响很大。如果使用pt-online-schema-change，使用过程中会创建触发器和影子表，也需要很长的时间。在此操作过程中，都算为风险时间。将数据表拆分，总量减少，有助于降低这个风险。
3.  大表会经常访问与更新，就更有可能出现锁等待。将数据切分，用空间换时间，变相降低访问压力

**7.3** **随着业务发展，需要对某些字段垂直拆分**
------------------------------

举个例子，假如项目一开始设计的用户表如下：

    id                   bigint             #用户的IDname                 varchar            #用户的名字last_login_time      datetime           #最近登录时间personal_info        text               #私人信息.....                                   #其他信息字段

在项目初始阶段，这种设计是满足简单的业务需求的，也方便快速迭代开发。而当业务快速发展时，用户量从10w激增到10亿，用户非常的活跃，每次登录会更新 last\_login\_name 字段，使得 user 表被不断update，压力很大。而其他字段：id, name, personal\_info 是不变的或很少更新的，此时在业务角度，就要将 last\_login\_time 拆分出去，新建一个 user\_time 表。

personal\_info 属性是更新和查询频率较低的，并且text字段占据了太多的空间。这时候，就要对此垂直拆分出 user\_ext 表了。

**7.4** **数据量快速增长**
-------------------

随着业务的快速发展，单表中的数据量会持续增长，当性能接近瓶颈时，就需要考虑水平切分，做分库分表了。此时一定要选择合适的切分规则，提前预估好数据容量

**7.5** **安全性和可用性**
-------------------

鸡蛋不要放在一个篮子里。在业务层面上垂直切分，将不相关的业务的数据库分隔，因为每个业务的数据量、访问量都不同，不能因为一个业务把数据库搞挂而牵连到其他业务。利用垂直切分，一个数据库出现问题，只会影响到部分业务，不会使所有的业务都瘫痪。利用水平切分，当一个数据库出现问题时，不会影响到100%的用户，每个库只承担业务的一部分数据，这样整体的可用性就能提高。

**八、****案例分析**
==============

**8.1** **用户中心业务场景**
--------------------

用户中心是一个非常常见的业务，主要提供用户注册、登录、查询/修改等功能，其核心表为：

    User(uid, login_name, passwd, sex, age, nickname)uid为用户ID,  主键login_name, passwd, sex, age, nickname,  用户属性

任何脱离业务的架构设计都是耍流氓，在进行分库分表前，需要对业务场景需求进行梳理：

*   用户侧：前台访问，访问量较大，需要保证高可用和高一致性。主要有两类需求：
    *   用户登录：通过login_name/phone/email查询用户信息，1%请求属于这种类型
    *   用户信息查询：登录之后，通过uid来查询用户信息，99%请求属这种类型
*   运营侧：后台访问，支持运营需求，按照年龄、性别、登陆时间、注册时间等进行分页的查询。是内部系统，访问量较低，对可用性、一致性的要求不高。

**8.2** **水平切分方法**
------------------

当数据量越来越大时，需要对数据库进行水平切分，上文描述的切分方法有"根据数值范围"和"根据数值取模"。

"根据数值范围"：以主键uid为划分依据，按uid的范围将数据水平切分到多个数据库上。例如：user-db1存储uid范围为0~1000w的数据，user-db2存储uid范围为1000w~2000wuid数据。

*   优点是：扩容简单，如果容量不够，只要增加新db即可。
*   不足是：请求量不均匀，一般新注册的用户活跃度会比较高，所以新的user-db2会比user-db1负载高，导致服务器利用率不平衡

"根据数值取模"：也是以主键uid为划分依据，按uid取模的值将数据水平切分到多个数据库上。例如：user-db1存储uid取模得1的数据，user-db2存储uid取模得0的uid数据。

*   优点是：数据量和请求量分布均均匀
*   不足是：扩容麻烦，当容量不够时，新增加db，需要rehash。需要考虑对数据进行平滑的迁移。

**8.3** **非****uid****的查询方法**
-----------------------------

水平切分后，对于按uid查询的需求能很好的满足，可以直接路由到具体数据库。而按非uid的查询，例如login_name，就不知道具体该访问哪个库了，此时需要遍历所有库，性能会降低很多。

对于用户侧，可以采用"建立非uid属性到uid的映射关系"的方案；对于运营侧，可以采用"前台与后台分离"的方案。

### **8.****3.1** **建立非****uid****属性到****uid****的映射关系**

**1）映射关系**

例如：login_name不能直接定位到数据库，可以建立login_name→uid的映射关系，用索引表或缓存来存储。当访问login_name时，先通过映射表查询出login_name对应的uid，再通过uid定位到具体的库。

映射表只有两列，可以承载很多数据，当数据量过大时，也可以对映射表再做水平切分。这类kv格式的索引结构，可以很好的使用cache来优化查询性能，而且映射关系不会频繁变更，缓存命中率会很高。

**2）基因法**

分库基因：假如通过uid分库，分为8个库，采用uid%8的方式进行路由，此时是由uid的最后3bit来决定这行User数据具体落到哪个库上，那么这3bit可以看为分库基因。

上面的映射关系的方法需要额外存储映射表，按非uid字段查询时，还需要多一次数据库或cache的访问。如果想要消除多余的存储和查询，可以通过f函数取login\_name的基因作为uid的分库基因。生成uid时，参考上文所述的分布式唯一ID生成方案，再加上最后3位bit值=f(login\_name)。当查询login\_name时，只需计算f(login\_name)%8的值，就可以定位到具体的库。不过这样需要提前做好容量规划，预估未来几年的数据量需要分多少库，要预留一定bit的分库基因。

![](https://img-blog.csdnimg.cn/20200225163309896.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2N5OTczMDcxMjYz,size_16,color_FFFFFF,t_70)

### **8.3.2** **前台与后台分离**

对于用户侧，主要需求是以单行查询为主，需要建立login_name/phone/email到uid的映射关系，可以解决这些字段的查询问题。

而对于运营侧，很多批量分页且条件多样的查询，这类查询计算量大，返回数据量大，对数据库的性能消耗较高。此时，如果和用户侧公用同一批服务或数据库，可能因为后台的少量请求，占用大量数据库资源，而导致用户侧访问性能降低或超时。

这类业务最好采用"前台与后台分离"的方案，运营侧后台业务抽取独立的service和db，解决和前台业务系统的耦合。由于运营侧对可用性、一致性的要求不高，可以不访问实时库，而是通过binlog异步同步数据到运营库进行访问。在数据量很大的情况下，还可以使用ES搜索引擎或Hive来满足后台复杂的查询方式。

**九、使用分库分表中间件**
===============

站在巨人的肩膀上能省力很多，目前分库分表已经有一些较为成熟的开源解决方案：

*   [sharding-jdbc（当当）](https://github.com/shardingjdbc)
*   [TSharding（蘑菇街）](https://github.com/baihui212/tsharding)
*   [Atlas（奇虎360）](https://github.com/Qihoo360/Atlas)
*   [Cobar（阿里巴巴）](https://github.com/alibaba/cobar)
*   [MyCAT（基于Cobar）](http://www.mycat.io/)
*   [Oceanus（58同城）](https://github.com/58code/Oceanus)
*   [Vitess（谷歌）](https://github.com/vitessio/vitess)

**简单介绍其中的两个中简介：**

**Mycat**

Mycat发展到现在，适用的场景已经很丰富，而且不断有新用户给出新的创新性的方案，以下是几个典型的应用场景：

*   单纯的读写分离，此时配置最为简单，支持读写分离，主从切换
*   分库分表，对于超过1000万的表进行分片，最大支持1000亿的单表分片
*   多租户应用，每个应用一个库，但应用程序只连接Mycat，从而不改造程序本身，实现多租户化报表系统，借助于Mycat的分表能力，处理大规模报表的统计
*   替代Hbase，分析大数据作为海量数据实时查询的一种简单有效方案，比如100亿条频繁查询的记录需要在3秒内查询出来结果，除了基于主键的查询，还可能存在范围查询或其他属性查询，此时Mycat可能是最简单有效的选择.

**Sharding-JDBC**

当当网开发的简单易用、轻量级的中间件。

**一些分库分表中间件的简介图：**

![](https://img-blog.csdnimg.cn/20200225164455997.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2N5OTczMDcxMjYz,size_16,color_FFFFFF,t_70)

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 有做过MySQL的索引优化吗
### 一、MySQL索引基础

首先，我们将从索引基础开始介绍一下什么是索引，分析索引的几种类型，并探讨一下如何创建索引以及索引设计的基本原则。

此部分用于测试索引创建的user表的结构如下：

    desc user;

![](https://img-blog.csdnimg.cn/20210219100528130.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pvdWxpcGluZzEyMzQ1Ng==,size_16,color_FFFFFF,t_70)

**1\. 什么是索引？**

> "索引（在MySQL中也叫“键key”）是存储引擎快速找到记录的一种数据结构。"
> 
> ——《高性能MySQL》

 我们需要知道索引其实是一种数据结构，其功能是帮助我们快速匹配查找到需要的数据行，是数据库性能优化最常用的工具之一。其作用相当于超市里的导购员、书本里的目录。

**2\. 索引类型**

可以使用**SHOW INDEX FROM table_name**;查看索引详情：

![](https://img-blog.csdnimg.cn/20210219101031639.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pvdWxpcGluZzEyMzQ1Ng==,size_16,color_FFFFFF,t_70)

**主键索引 PRIMARY KEY**：它是一种特殊的唯一索引，不允许有空值。一般是在建表的时候同时创建主键索引。注意：一个表只能有一个主键。 

**唯一索引 UNIQUE**：唯一索引列的值必须唯一，但允许有空值。如果是组合索引，则列值的组合必须唯一。可以通过ALTER TABLE table_name ADD UNIQUE (column);创建唯一索引：

    ALTER TABLE user ADD UNIQUE u_phone (phone);

![](https://img-blog.csdnimg.cn/20210220111258570.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pvdWxpcGluZzEyMzQ1Ng==,size_16,color_FFFFFF,t_70)

** 删除索引命令**

    DROP INDEX <索引名> ON <表名>
    

    drop  user index on idx_name_age_position;

**语法说明如下：**

*   `<索引名>`：要删除的索引名。
*   `<表名>`：    指定该索引所在的表名。

**唯一组合索引命令**

    ALTER TABLE table_name ADD UNIQUE <索引名> (<列>,<列>)

    ALTER TABLE user ADD UNIQUE u_name_age (user_name,age);

![](https://img-blog.csdnimg.cn/2021022011273850.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pvdWxpcGluZzEyMzQ1Ng==,size_16,color_FFFFFF,t_70)

**普通索引 INDEX**：这是最基本的索引，命令如下

    ALTER TABLE <table_name> ADD INDEX <idx_name> (<column>);

**语法说明如下：**

*   `<`idx_name`>`：要添加的索引名称
*   `<`table_name`>`：    指定该索引所在的表名
*   `<`column`>`：    指定要添加索引的列

    alter table user add index idx_satus (status);

![](https://img-blog.csdnimg.cn/20210220113229580.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pvdWxpcGluZzEyMzQ1Ng==,size_16,color_FFFFFF,t_70)

   
**组合索引 INDEX**：即一个索引包含多个列，多用于避免回表查询，命令如下

    ALTER TABLE <table_name> ADD INDEX <idx_name> (<column1>,<column2>);

**语法说明如下：**

*   `<`idx_name`>`：要添加的索引名称
*   `<`table_name`>`：    指定该索引所在的表名
*   `<`column1`>`：    指定要添加索引的列1
*   `<`column2`>`：    指定要添加索引的列2

    alter table user add index idx_user_age (user_name,age);

![](https://img-blog.csdnimg.cn/20210220114011671.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pvdWxpcGluZzEyMzQ1Ng==,size_16,color_FFFFFF,t_70)

**全文索引 FULLTEXT**：也称全文检索，是目前搜索引擎使用的一种关键技术,命令如下

    ALTER TABLE <table_name> ADD FULLTEXT <f_name> (<column>);

**语法说明如下：**

*   `<`table_name`>`：    指定该索引所在的表名
*   `<`f_name`>`：   要添加的索引名称
*   `<`column`>`：    指定要添加索引的列

![](https://img-blog.csdnimg.cn/20210220115656557.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pvdWxpcGluZzEyMzQ1Ng==,size_16,color_FFFFFF,t_70)

索引一经创建不能修改，如果要修改索引，只能删除重建。

**3、索引设计的原则**

1.  适合索引的列是出现在where子句中的列，或者连接子句中指定的列；
2.  基数较小的类，索引效果较差，没有必要在此列建立索引；
3.  使用短索引，如果对长字符串列进行索引，应该指定一个前缀长度，这样能够节省大量索引空间；
4.  不要过度索引。索引需要额外的磁盘空间，并降低写操作的性能。在修改表内容的时候，索引会进行更新甚至重构，索引列越多，这个时间就会越长。所以只保持需要的索引有利于查询即可。

### 二、MySQL索引优化实战

上面我们介绍了索引的基本内容，这部分我们介绍索引优化实战。在介绍索引优化实战之前，首先要介绍两个与索引相关的重要概念，这两个概念对于索引优化至关重要。

此部分用于测试的user表结构：

![](https://img-blog.csdnimg.cn/20210220133100244.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pvdWxpcGluZzEyMzQ1Ng==,size_16,color_FFFFFF,t_70)

**1、索引相关的重要概念**

**基数：**单个列唯一键（distict_keys）的数量叫做基数。

    select count(distinct user_name),count(distinct gender) from user;
    

![](https://img-blog.csdnimg.cn/20210220134114656.png)

user表的总行数是6，gender列的基数是3，说明gender列里面有大量重复值，name列的基数等于总行数，说明name列没有重复值，相当于主键。

返回数据的比例：user表中共有6条数据：

![](https://img-blog.csdnimg.cn/20210220134842728.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pvdWxpcGluZzEyMzQ1Ng==,size_16,color_FFFFFF,t_70)

查询满足性别为0（男）的记录数：

![](https://img-blog.csdnimg.cn/20210220135004545.png)

那么返回记录的比例数是：

![](https://img-blog.csdnimg.cn/20210220135320857.png)

同理，查询name为'smile'的记录数：

![](https://img-blog.csdnimg.cn/20210220135443858.png)

现在问题来了，假设name、age 列都有索引，那么SELECT * FROM user WHERE age = 28 ;

SELECT * FROM user WHERE name = 'smile'；都能命中索引吗？

user表的索引详情：

![](https://img-blog.csdnimg.cn/20210220135634590.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pvdWxpcGluZzEyMzQ1Ng==,size_16,color_FFFFFF,t_70)

 SELECT * FROM user WHERE age = 28；没有命中索引，注意filtered的值就是上面我们计算的返回记录的比例数。

    EXPLAIN select * from user where age = 28;
    

![](https://img-blog.csdnimg.cn/20210220140043588.png)

SELECT * FROM user WHERE name = 'smile';命中了索引index_name，因为走索引直接就能找到要查询的记录，所以filtered的值为100。

![](https://img-blog.csdnimg.cn/20210220140206138.png)

组合索引底层还是使用B+树索引，并且还是只有一棵树，只是此时的排序会：首先按照第一个索引排序，在第一个索引相同的情况下，再按第二个索引排序，依次类推。

这也是为什么有“**最佳左前缀原则**”的原因，因为右边（后面）的索引都是在左边（前面）的索引排序的基础上进行排序的，如果没有左边的索引，**单独看右边的索引，其实是无序的。**

还是以字典为例，我们如果要查第2个字母为 k 的，通过目录是无法快速找的，因为首字母 A - Z 里面都可能包含第2个字母为 k 的。

**回表**：当对一个列创建索引之后，索引会包含该列的键值及键值对应行所在的rowid。通过索引中记录的rowid访问表中的数据就叫回表。回表次数太多会严重影响SQL性能，如果回表次数太多，就不应该走索引扫描，应该直接走全表扫描。

EXPLAIN命令结果中的Using Index意味着不会回表，通过索引就可以获得主要的数据。Using Where则意味着需要回表取数据。

### **三、 索引优化实战**

有些时候虽然数据库有索引，但是并不被优化器选择使用。我们可以通过' SHOW STATUS LIKE 'Handler_read% ';查看索引的使用情况：

![](https://img-blog.csdnimg.cn/20210220141219627.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pvdWxpcGluZzEyMzQ1Ng==,size_16,color_FFFFFF,t_70)

Handler\_read\_key：如果索引正在工作，Handler\_read\_key的值将很高。

Handler\_read\_rnd_next：数据文件中读取下一行的请求数，如果正在进行大量的表扫描，值将较高，则说明索引利用不理想。

索引优化规则：

1）如果MySQL估计使用索引比全表扫描还慢，则不会使用索引。

返回数据的比例是重要的指标，比例越低越容易命中索引。记住这个范围值——30%，后面所讲的内容都是建立在返回数据的比例在30%以内的基础上。

2）前导模糊查询不能命中索引。

    EXPLAIN SELECT * FROM user WHERE user_name LIKE '%s%'; 

![](https://img-blog.csdnimg.cn/20210220141514632.png)

非前导模糊查询则可以使用索引，可优化为使用非前导模糊查询：

    EXPLAIN SELECT * FROM user WHERE user_name name LIKE 's%';

![](https://img-blog.csdnimg.cn/20210220141714440.png)

3）数据类型出现隐式转换的时候不会命中索引，特别是当列类型是字符串，一定要将字符常量值用引号引起来。

    EXPLAIN SELECT * FROM user WHERE user_name = 1;

![](https://img-blog.csdnimg.cn/20210220141901416.png)

    EXPLAIN SELECT * FROM user WHERE user_name = '1';

![](https://img-blog.csdnimg.cn/20210220142024803.png)

4）**union** 能够命中索引，建议使用**union**。**in、or**不能命中索引

**union:**

    EXPLAIN SELECT*FROM user WHERE status =1UNION ALLSELECT*FROM user WHERE status = 2;

![](https://img-blog.csdnimg.cn/20210220142322252.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pvdWxpcGluZzEyMzQ1Ng==,size_16,color_FFFFFF,t_70)

**in:**

    EXPLAIN SELECT * FROM user WHERE status IN (1,2);

 ![](https://img-blog.csdnimg.cn/2021022014260746.png)

**or:**

    EXPLAIN SELECT * FROM user WHERE status=1 OR status=2;

 ![](https://img-blog.csdnimg.cn/20210220151045945.png)

如上图，实际上并没有走索引，为什么？

为什么where条件中使用or索引不起作用？where条件中使用or，索引就会失效，会造成全表扫描    是误区！！！

一，要求使用的所有字段，都必须建立索引。

二，数据量太少，制定执行计划时发现全表扫描比索引查找更快。

![](https://img-blog.csdnimg.cn/20210220151341196.png)

5）负向条件查询不能使用索引，可以优化为in查询。

负向条件有：!=、<>、not in、not exists、not like等。

负向条件不能命中缓存：

EXPLAIN SELECT * FROM user WHERE status !=1 AND status != 2;

![](https://img-blog.csdnimg.cn/20210220153819773.png)

可以优化为in查询，但是前提是区分度要高，返回数据的比例在30%以内：

![](https://img-blog.csdnimg.cn/20210220153523360.png)

8）范围条件查询可以命中索引。范围条件有：<、<=、>、>=、between等。

status,age列分别创建索引

user表索引详情：

![](https://img-blog.csdnimg.cn/20210220154534689.png)

范围条件查询可以命中索引：

    EXPLAIN SELECT * FROM user WHERE status > 5;

![](https://img-blog.csdnimg.cn/202102201546591.png)

范围列可以用到索引（联合索引必须是最左前缀），但是范围列后面的列无法用到索引，索引最多用于一个范围列，如果查询条件中有两个范围列则无法全用到索引：

    EXPLAIN SELECT * FROM user WHERE status>5 AND age<24;

![](https://img-blog.csdnimg.cn/20210220154840290.png)

如果是范围查询和等值查询同时存在，优先匹配等值查询列的索引：

    EXPLAIN SELECT * FROM user WHERE status>5 AND age = 28;

![](https://img-blog.csdnimg.cn/20210220155335436.png)

8）数据库执行计算不会命中索引。

EXPLAIN SELECT * FROM user WHERE age>24;

![](https://img-blog.csdnimg.cn/img_convert/53ef79c6525a04fad6a89c29f9ecec4f.png)

EXPLAIN SELECT * FROM user WHERE age+1>24;

![](https://img-blog.csdnimg.cn/img_convert/ca5be39966ca4d25216fdc613fdffcff.png)

计算逻辑应该尽量放到业务层处理，节省数据库的CPU的同时最大限度的命中索引。

9）利用覆盖索引进行查询，避免回表。

被查询的列，数据能从索引中取得，而不用通过行定位符row-locator再到row上获取，即“被查询列要被所建的索引覆盖”，这能够加速查询速度。

user表的索引详情：

![](https://img-blog.csdnimg.cn/img_convert/48998278e5002861b5e90901b06d4553.png)

因为status字段是索引列，所以直接从索引中就可以获取值，不必回表查询：

Using Index代表从索引中查询：

EXPLAIN SELECT status FROM user where status=1;

![](https://img-blog.csdnimg.cn/img_convert/dc0e47cd120c4974cf6b6b9445daf153.png)

当查询其他列时，就需要回表查询，这也是为什么要避免SELECT*的原因之一：

EXPLAIN SELECT * FROM user where status=1;

![](https://img-blog.csdnimg.cn/img_convert/926899c098a4d50778771d2afa01319b.png)

10）建立索引的列，不允许为null。

单列索引不存null值，复合索引不存全为null的值，如果列允许为null，可能会得到“不符合预期”的结果集，所以，请使用not null约束以及默认值。

remark列建立索引：

ALTER TABLE user ADD INDEX index_remark (remark);

![](https://img-blog.csdnimg.cn/img_convert/cac1e5ba623f98ce8b1b56237d182850.png)

IS NULL可以命中索引：

EXPLAIN SELECT * FROM user WHERE remark IS NULL;

![](https://img-blog.csdnimg.cn/img_convert/52c8aebeab20f0d9e8d0e1969eee486c.png)

IS NOT NULL不能命中索引：

EXPLAIN SELECT * FROM user WHERE remark IS NOT NULL;

![](https://img-blog.csdnimg.cn/img_convert/131c0318048278423ef9ca9fed848d47.png)

虽然IS NULL可以命中索引，但是NULL本身就不是一种好的数据库设计，应该使用NOT NULL约束以及默认值。

a. 更新十分频繁的字段上不宜建立索引：因为更新操作会变更B+树，重建索引。这个过程是十分消耗数据库性能的。

b. 区分度不大的字段上不宜建立索引：类似于性别这种区分度不大的字段，建立索引的意义不大。因为不能有效过滤数据，性能和全表扫描相当。另外返回数据的比例在30%以外的情况下，优化器不会选择使用索引。

c. 业务上具有唯一特性的字段，即使是多个字段的组合，也必须建成唯一索引。虽然唯一索引会影响insert速度，但是对于查询的速度提升是非常明显的。另外，即使在应用层做了非常完善的校验控制，只要没有唯一索引，在并发的情况下，依然有脏数据产生。

d. 多表关联时，要保证关联字段上一定有索引。

e. 创建索引时避免以下错误观念：索引越多越好，认为一个查询就需要建一个索引；宁缺勿滥，认为索引会消耗空间、严重拖慢更新和新增速度；抵制唯一索引，认为业务的唯一性一律需要在应用层通过“先查后插”方式解决；过早优化，在不了解系统的情况下就开始优化。

**3\. 小结**

对于自己编写的SQL查询语句，要尽量使用EXPLAIN命令分析一下，做一个对SQL性能有追求的程序员。衡量一个程序员是否靠谱，SQL能力是一个重要的指标。作为后端程序员，深以为然。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说说InnoDB的MVCC机制本文详细的介绍了什么是MVCC？为什么要有MVCC？以及MVCC的内部实现原理：包括Undo Log的版本链是如何组织的，RR、RC两个级别下一致性读是如何实现的等。通过案例、插图，以最通俗易懂的方式，让你彻底掌握MVCC的来龙去脉。

### 什么是MVCC

`MVCC (Multiversion Concurrency Control)` 中文全称叫多版本并发控制，是现代数据库（包括 `MySQL`、`Oracle`、`PostgreSQL` 等）引擎实现中常用的处理读写冲突的手段，目的在于提高数据库高并发场景下的吞吐性能。

如此一来不同的事务在并发过程中，`SELECT` 操作可以不加锁而是通过 `MVCC` 机制读取指定的版本历史记录，并通过一些手段保证保证读取的记录值符合事务所处的隔离级别，从而解决并发场景下的读写冲突。

下面举一个多版本读的例子，例如两个事务 `A` 和 `B` 按照如下顺序进行更新和读取操作

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2pwZy9ScGxkbkxNcDk5anJDNWliMWdNZ0JUblNKYWF1UHhHYzROY0s0aWJGY21hVXBac3RzUmdBOGZibUp3MlZFRTZMNEZrSjFBOXllZlRKaWNNVjc5aDFIZ3kxdy82NDA?x-oss-process=image/format,png)

在事务 `A` 提交前后，事务 `B` 读取到的 `x` 的值是什么呢？答案是：事务 `B` 在不同的隔离级别下，读取到的值不一样。

1.  如果事务 `B` 的隔离级别是读未提交（RU），那么两次读取均读取到 `x` 的最新值，即 `20`。
    
2.  如果事务 `B` 的隔离级别是读已提交（RC），那么第一次读取到旧值 `10`，第二次因为事务 `A` 已经提交，则读取到新值 20。
    
3.  如果事务 `B` 的隔离级别是可重复读或者串行（RR，S），则两次均读到旧值 `10`，不论事务 `A` 是否已经提交。
    

可见在不同的隔离级别下，数据库通过 `MVCC` 和隔离级别，让事务之间并行操作遵循了某种规则，来保证单个事务内前后数据的一致性。

### 为什么需要MVCC

`InnoDB` 相比 `MyISAM` 有两大特点，一是支持事务而是支持行级锁，事务的引入带来了一些新的挑战。相对于串行处理来说，并发事务处理能大大增加数据库资源的利用率，提高数据库系统的事务吞吐量，从而可以支持可以支持更多的用户。但并发事务处理也会带来一些问题，主要包括以下几种情况：

1.  更新丢失（`Lost Update`）：当两个或多个事务选择同一行，然后基于最初选定的值更新该行时，由于每个事务都不知道其他事务的存在，就会发生丢失更新问题 —— 最后的更新覆盖了其他事务所做的更新。如何避免这个问题呢，最好在一个事务对数据进行更改但还未提交时，其他事务不能访问修改同一个数据。
    
2.  脏读（`Dirty Reads`）：一个事务正在对一条记录做修改，在这个事务并提交前，这条记录的数据就处于不一致状态；这时，另一个事务也来读取同一条记录，如果不加控制，第二个事务读取了这些尚未提交的脏数据，并据此做进一步的处理，就会产生未提交的数据依赖关系。这种现象被形象地叫做 “脏读”。
    
3.  不可重复读（`Non-Repeatable Reads`）：一个事务在读取某些数据已经发生了改变、或某些记录已经被删除了！这种现象叫做“不可重复读”。
    
4.  幻读（`Phantom Reads`）：一个事务按相同的查询条件重新读取以前检索过的数据，却发现其他事务插入了满足其查询条件的新数据，这种现象就称为 “幻读”。
    

以上是并发事务过程中会存在的问题，解决更新丢失可以交给应用，但是后三者需要数据库提供事务间的隔离机制来解决。**实现隔离机制的方法主要有两种**：

1.  加读写锁
    
2.  一致性快照读，即 `MVCC`
    

但本质上，隔离级别是一种在并发性能和并发产生的副作用间的妥协，通常数据库均倾向于采用 `Weak Isolation`。

### InnoDB MVCC实现原理

`InnoDB` 中 `MVCC` 的实现方式为：每一行记录都有两个隐藏列：`DATA_TRX_ID`、`DATA_ROLL_PTR`（如果没有主键，则还会多一个隐藏的主键列）。

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2pwZy9ScGxkbkxNcDk5anJDNWliMWdNZ0JUblNKYWF1UHhHYzRFRkFGaWJVVnM0NTMxeEdlWVJoOExUeFlRQjF6dVdqbkxUOFczTWxpYVVXZHFFamwwQ2U3OGZudy82NDA?x-oss-process=image/format,png)

DATA\_TRX\_ID

记录最近更新这条行记录的`事务 ID`，大小为 `6` 个字节

DATA\_ROLL\_PTR

表示指向该行回滚段`（rollback segment）`的指针，大小为 `7` 个字节，`InnoDB` 便是通过这个指针找到之前版本的数据。该行记录上所有旧版本，在 `undo` 中都通过链表的形式组织。

DB\_ROW\_ID

行标识（隐藏单调自增 `ID`），大小为 `6` 字节，如果表没有主键，`InnoDB` 会自动生成一个隐藏主键，因此会出现这个列。另外，每条记录的头信息（`record header`）里都有一个专门的 `bit`（`deleted_flag`）来表示当前记录是否已经被删除。

#### 如何组织版本链

> 关于 Redo Log 和 Undo Log 的相关概念可见之前的文章 InnoDB 中的 redo 和 undo log

上文提到，在多个事务并行操作某行数据的情况下，不同事务对该行数据的 UPDATE 会产生多个版本，然后通过回滚指针组织成一条 `Undo Log` 链，这节我们通过一个简单的例子来看一下 `Undo Log` 链是如何组织的，`DATA_TRX_ID` 和 `DATA_ROLL_PTR` 两个参数在其中又起到什么样的作用。

还是以上文 `MVCC` 的例子，事务 `A` 对值 `x` 进行更新之后，该行即产生一个新版本和旧版本。假设之前插入该行的事务 `ID` 为 `100`，事务 `A` 的 `ID` 为 `200`，该行的隐藏主键为 `1`。

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2pwZy9ScGxkbkxNcDk5anJDNWliMWdNZ0JUblNKYWF1UHhHYzQ4VDh1Q2ZuMHRwWWI0bms4dnBCQmp4c29TeUQ1cUpsNVJWdVhRemlhcmdiWnhVaWJ1NWZObkNXQS82NDA?x-oss-process=image/format,png)

事务 `A` 的操作过程为：

1.  对 `DB_ROW_ID = 1` 的这行记录加排他锁
    
2.  把该行原本的值拷贝到 `undo log` 中，`DB_TRX_ID` 和 `DB_ROLL_PTR` 都不动
    
3.  修改该行的值这时产生一个新版本，更新 `DATA_TRX_ID` 为修改记录的事务 `ID`，将 `DATA_ROLL_PTR` 指向刚刚拷贝到 `undo log` 链中的旧版本记录，这样就能通过 `DB_ROLL_PTR` 找到这条记录的历史版本。如果对同一行记录执行连续的 `UPDATE`，`Undo Log` 会组成一个链表，遍历这个链表可以看到这条记录的变迁
    
4.  记录 `redo log`，包括 `undo log` 中的修改
    

那么 `INSERT` 和 `DELETE` 会怎么做呢？其实相比 `UPDATE` 这二者很简单，`INSERT` 会产生一条新纪录，它的 `DATA_TRX_ID` 为当前插入记录的事务 `ID`；`DELETE` 某条记录时可看成是一种特殊的 `UPDATE`，其实是软删，真正执行删除操作会在 `commit` 时，`DATA_TRX_ID` 则记录下删除该记录的事务 `ID`。

#### 如何实现一致性读-ReadView

在 `RU` 隔离级别下，直接读取版本的最新记录就 OK，对于 `SERIALIZABLE` 隔离级别，则是通过加锁互斥来访问数据，因此不需要 `MVCC` 的帮助。因此 `MVCC` 运行在 `RC` 和 `RR`这两个隔离级别下，当 `InnoDB` 隔离级别设置为二者其一时，在 `SELECT` 数据时就会用到版本链

> 核心问题是版本链中哪些版本对当前事务可见？

`InnoDB` 为了解决这个问题，设计了 `ReadView`（可读视图）的概念。

* RR下ReadView的生成

在 `RR` 隔离级别下，每个事务 `touch first read` 时（本质上就是执行第一个 `SELECT`语句时，后续所有的 `SELECT` 都是复用这个 `ReadView`，其它 `update`, `delete`, `insert` 语句和一致性读 `snapshot` 的建立没有关系），会将当前系统中的所有的活跃事务拷贝到一个列表生成` ReadView`。

下图中事务 `A` 第一条 `SELECT` 语句在事务 `B` 更新数据前，因此生成的 `ReadView` 在事务 `A` 过程中不发生变化，即使事务 `B` 在事务 `A` 之前提交，但是事务 `A` 第二条查询语句依旧无法读到事务 `B` 的修改。

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2pwZy9ScGxkbkxNcDk5anJDNWliMWdNZ0JUblNKYWF1UHhHYzRJZ05uQ1A3ZDZSSGVGblVqWGhyOWowRktrbEk2M2JnbHVvQ0tZVm5QbTVteG1oWGRHZTB2YUEvNjQw?x-oss-process=image/format,png)

下图中，事务 `A` 的第一条 `SELECT` 语句在事务 `B` 的修改提交之后，因此可以读到事务 `B`的修改。但是注意，如果事务 `A` 的第一条 `SELECT` 语句查询时，事务 `B` 还未提交，那么事务 `A` 也查不到事务 `B` 的修改。

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2pwZy9ScGxkbkxNcDk5anJDNWliMWdNZ0JUblNKYWF1UHhHYzRQdk0xYVo2bnczTDQxeWZTMElQcjdLRzJsNGxDeGZlSUx1U2RpYWxla0FoWEFUWlhvc0U4YVZ3LzY0MA?x-oss-process=image/format,png)

* RC下ReadView的生成

在 `RC` 隔离级别下，每个 `SELECT` 语句开始时，都会重新将当前系统中的所有的活跃事务拷贝到一个列表生成 `ReadView`。二者的区别就在于生成 `ReadView` 的时间点不同，一个是事务之后第一个 `SELECT` 语句开始、一个是事务中每条 `SELECT` 语句开始。

`ReadView` 中是当前活跃的事务 `ID` 列表，称之为 `m_ids`，其中最小值为 `up_limit_id`，最大值为 `low_limit_id`，事务 `ID` 是事务开启时 `InnoDB` 分配的，其大小决定了事务开启的先后顺序，因此我们可以通过 `ID` 的大小关系来决定版本记录的可见性，具体判断流程如下：

1.  如果被访问版本的 `trx_id` 小于 `m_ids` 中的最小值 `up_limit_id`，说明生成该版本的事务在 `ReadView` 生成前就已经提交了，所以该版本可以被当前事务访问。
    
2.  如果被访问版本的 `trx_id` 大于 `m_ids` 列表中的最大值 `low_limit_id`，说明生成该版本的事务在生成 `ReadView` 后才生成，所以该版本不可以被当前事务访问。需要根据 `Undo Log` 链找到前一个版本，然后根据该版本的 DB\_TRX\_ID 重新判断可见性。
    
3.  如果被访问版本的 `trx_id` 属性值在 `m_ids` 列表中最大值和最小值之间（包含），那就需要判断一下 `trx_id` 的值是不是在 `m_ids` 列表中。如果在，说明创建 `ReadView` 时生成该版本所属事务还是活跃的，因此该版本不可以被访问，需要查找 Undo Log 链得到上一个版本，然后根据该版本的 `DB_TRX_ID` 再从头计算一次可见性；如果不在，说明创建 `ReadView` 时生成该版本的事务已经被提交，该版本可以被访问。
    
4.  此时经过一系列判断我们已经得到了这条记录相对 `ReadView` 来说的可见结果。此时，如果这条记录的 `delete_flag` 为 `true`，说明这条记录已被删除，不返回。否则说明此记录可以安全返回给客户端。
    

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2pwZy9ScGxkbkxNcDk5anJDNWliMWdNZ0JUblNKYWF1UHhHYzQ5N0p3T0pBcHRDTThNdW1qbGVFYXZ5aWFIVlI3cTZUbDd2cHRzYlVqZklqVjFwT1czelJRNGlhQS82NDA?x-oss-process=image/format,png)

### 举个例子

#### RC下的MVCC判断流程

我们现在回看刚刚的查询过程，为什么事务 `B` 在 `RC` 隔离级别下，两次查询的 `x` 值不同。`RC` 下 `ReadView` 是在语句粒度上生成的。

当事务 `A` 未提交时，事务 `B` 进行查询，假设事务 `B` 的事务 `ID` 为 `300`，此时生成 `ReadView` 的 `m_ids` 为 \[200，300\]，而最新版本的 `trx_id` 为 `200`，处于 `m_ids`中，则该版本记录不可被访问，查询版本链得到上一条记录的 trx_id 为 `100`，小于 `m_ids`的最小值 `200`，因此可以被访问，此时事务 `B` 就查询到值 `10` 而非 `20`。

待事务 `A` 提交之后，事务 `B` 进行查询，此时生成的 `ReadView` 的 `m_ids` 为 \[300\]，而最新的版本记录中 `trx_id` 为 `200`，小于 `m_ids` 的最小值 `300`，因此可以被访问到，此时事务 `B` 就查询到 `20`。

#### RR下的MVCC判断流程

如果在 `RR` 隔离级别下，为什么事务 `B` 前后两次均查询到 `10` 呢？`RR` 下生成 `ReadView` 是在事务开始时，m_ids 为 \[200,300\]，后面不发生变化，因此即使事务 `A` 提交了，`trx_id` 为 `200` 的记录依旧处于 `m_ids` 中，不能被访问，只能访问版本链中的记录 `10`。

### 一个争论点

其实并非所有的情况都能套用 `MVCC` 读的判断流程，特别是针对在事务进行过程中，另一个事务已经提交修改的情况下，这时不论是 `RC` 还是 `RR`，直接套用 `MVCC` 判断都会有问题，例如 `RC` 下：

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2pwZy9ScGxkbkxNcDk5anJDNWliMWdNZ0JUblNKYWF1UHhHYzRyd0Y3d0M3ZTVGSWJ4N0c1MGpWOTI5eFRZQWZ5aWE0Q2hwZ0JvOG54ZkFiUzZaR2FDUW5DOFVBLzY0MA?x-oss-process=image/format,png)

事务 `A` 的 `trx_id = 200`，事务 `B` 的 `trx_id = 300`，且事务 `B` 修改了数据之后在事务 `A` 之前提交，此时 `RC` 下事务 `A` 读到的数据为事务 `B` 修改后的值，这是很显然的。下面我们套用下 `MVCC` 的判断流程，考虑到事务 `A` 第二次 `SELECT` 时，`m_ids` 应该为 \[200\]，此时该行数据最新的版本 `DATA_TRX_ID = 300` 比 `200` 大，照理应该不能被访问，但实际上事务 `A` 选取了这条记录返回。

这里其实应该结合 `RC` 的本质来看，`RC` 的本质就是事务中每一条 `SELECT` 语句均可以看到其他已提交事务对数据的修改，那么只要该事物已经提交其结果就是可见的，与这两个事务开始的先后顺序无关，不完全适用于 MVCC 读。

`RR` 级别下还是用之前那张图：

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2pwZy9ScGxkbkxNcDk5anJDNWliMWdNZ0JUblNKYWF1UHhHYzRQdk0xYVo2bnczTDQxeWZTMElQcjdLRzJsNGxDeGZlSUx1U2RpYWxla0FoWEFUWlhvc0U4YVZ3LzY0MA?x-oss-process=image/format,png)

这张图的流程中，事务 `B` 的 `trx_id = 300` 比事务 `A` `200` 小，且事务 `B` 先于事务 `A` 提交，按照 `MVCC` 的判断流程，事务 `A` 生成的 `ReadView` 为 \[200\]，最新版本的行记录 `DATA_TRX_ID = 300` 比 `200` 大，照理不能访问到，但是事务 `A` 实际上读到了事务 `B` 已经提交的修改。这里还是结合 `RR` 本质进行解释，`RR` 的本质是从第一个 `SELECT` 语句生成 `ReadView` 开始，任何已经提交过的事务的修改均可见。

###  写在最后

`RC`、`RR` 两种隔离级别的事务在执行普通的读操作时，通过访问版本链的方法，使得事务间的读写操作得以并发执行，从而提升系统性能。`RC`、`RR` 这两个隔离级别的一个很大不同就是生成 `ReadView` 的时间点不同，`RC` 在每一次 `SELECT` 语句前都会生成一个 `ReadView`，事务期间会更新，因此在其他事务提交前后所得到的 `m_ids` 列表可能发生变化，使得先前不可见的版本后续又突然可见了。而 `RR` 只在事务的第一个 `SELECT` 语句时生成一个 `ReadView`，事务操作期间不更新。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说说InnoDB的索引原理本文主要从整体上把INNODB的索引涉及到的知识点进行梳理，让读者从整体把握索引的原理，具体内容还需要读者自行查看MySQL技术内幕一书，因为网上大多数文章基本都是拷贝这本书的内容，并且有些文章会误导读者，具体的内容还是耐心点看书吧！

### 1.索引是什么？

索引就像是一本书的目录，假设我们想要在书中找到某一小节的内容，如果没有目录，我们是不是要从头到尾顺序找一遍，这非常浪费时间，但有了目录，我们就可以快速定位到该小节的页码，并找到该小结的内容。索引的作用就是这样，可以帮助我们快速找到指定的内容。

### 2.MySQL  InnoDB索引的存储结构

InnoDB使用的是B+tree数据结构，所有的记录都在叶子节点上，并且是按照顺序存放的，根节点和分支节点中不保存数据，只用于索引。具体可以看这篇文章：[B+tree数据结构](https://www.cnblogs.com/dongguacai/p/7241860.html)

### 3.MySql的系统架构图

![](https://img-blog.csdnimg.cn/20190722191327844.jpeg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2Z4a2NzZG4=,size_16,color_FFFFFF,t_70)

  
从图中可以看出，mysql底层是使用文件系统来存储数据库。对于文件系统，大家需要区了解一下扇区、磁盘块等相关内容，这部分是mysql索引物理实现的基础。

### 4.InnoDB的逻辑存储结构

从InnoDB存储引擎的逻辑存储结构看，所有的数据都被逻辑地存放在一个空间中，称之为表空间。表空间又由段（segment）、区（extent）、页（page）组成。逻辑存储结构如下图所示：

![](https://img-blog.csdnimg.cn/20190722191726441.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2Z4a2NzZG4=,size_16,color_FFFFFF,t_70)

** 表空间**：在默认情况下InnoDB引擎有一个共享表孔甲ibdata1，即所有的数据都存放在这个表空间中，如果用户启用了参数innodb\_file\_per_table，则每张表内的数据可以单独存放到一个表空间内。此时，你会发现每一个表都有一个 表名.frm文件和 表名.ibd文件。注意：这些单独的表空间文件只存储该表的数据、索引和插入缓冲BITMAP等信息。其余信息还是存放在默认的表空间。

**区**：区是由连续页组成的空间，每个区的大小位1MB.为了保证区中页的连续性，InnoDB存储引擎一次从磁盘申请4-5个区。默认情况下，存储引擎页的大小为16KB，即一个区中一共有64个连续的页。

**页**：页是InnoDB磁盘管理的最小单位，默认大小是16KB.常见的页类型有：数据页 undo页 系统页 插入缓冲位图页等。页的数据结构如下图所示：

![](https://img-blog.csdnimg.cn/20190722192411794.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2Z4a2NzZG4=,size_16,color_FFFFFF,t_70)

**记录行**：InnoDB存储引擎是面向行的，也就是说数据是按行存入.ibd文件的，而行是有格式的，就像TCP协议一样，每一个二进制都代表了各自的含义，无规矩不成方圆。InnoDB行格式有四种，Compact、Redundant、Compressed和Dynamic。只要了解一种就可以了，大同小异，大体意思就是我这一行的长度是多少，下一条记录的位置在哪里等。数据结构如下图所示：

![](https://img-blog.csdnimg.cn/20190722192846575.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2Z4a2NzZG4=,size_16,color_FFFFFF,t_70)

以上数据结构都是从逻辑层面进行的抽象，那么物理结构是怎样的呢？

我们现在在本地数据库添加一个student表，并向其中添加两条记录。如下图所示：

![](https://img-blog.csdnimg.cn/20190722193712430.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2Z4a2NzZG4=,size_16,color_FFFFFF,t_70)

我们使用 UltraEdit软件打开School.ibd文件，如下图所示：

![](https://img-blog.csdnimg.cn/20190722193339303.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2Z4a2NzZG4=,size_16,color_FFFFFF,t_70)

 数据页是从0x0000c0000(16K*3=0xc000)处开始，这也就验证之前说的页的大小是16KB，保证了同一页的数据在连续的磁盘块上，提高了查询效率。具体的二进制文件分析请看MySQL技术内幕。

### 5.InnoDB和MyISAM索引的区别

MYISAM是按列值与行号来组织索引的。它的叶子节点中保存的实际上是指向存放数据的物理块的指针。MYISAM使用的是非聚簇索引，非聚簇索引的两颗B+树看上去没有任何不同，节点的结构完全一致只是存储的内容不一样。主键索引的B+树存储的是主键，而辅助索引B+树存储的是辅助键。表数据存储在独立的地方，这两颗B+树的叶子节点保存了数据存储的真实物理地址。

InnoDB 只聚集在同一个页面中的记录。通常向下读取一个节点的动作可能会是一次磁盘IO操作，不过非叶节点通常会在初始阶段载入内存以加快访问速度。聚集索引保存的是数据的复制，所以控制的是逻辑顺序，即使物理地址发生改变，行号变化，都不会影响聚集索引。InnoDB主键索引的叶节点存储的是主键值和剩余的列值，也就是存储了真实的记录，而辅助键索引存储的是索引值和主键值，这样设计的好处是，当记录由于行移动或者数据页分裂合并等操作造成记录的位置发生改变时，只需要更新主键索引，其他的辅助键索引完全不用变。而MyISAM叶节点存储的都是真实物理地址，所以当记录的地址发生改变时，所有的索引都需要更新。

如下图所示：

![](https://img-blog.csdnimg.cn/20190722194732815.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2Z4a2NzZG4=,size_16,color_FFFFFF,t_70)

### 6. 使用自增ID做主键的理由

聚簇索引的物理存放顺序和主键索引的顺序是相同的，只要索引是相邻的，那么对应的数据也一定相邻的存放在磁盘上。而如果主键不是自增ID，可以想象，聚簇索引需要不断的进行分页，调整记录的物理地址，这样是非常耗费时间的。使用自增主键可以让索引结构变得紧凑，磁盘碎片少，效率高。

### 7.聚簇索引的列的选择

*   主键列,该列在where子句中使用并且插入是随机的。
*   按范围存取的列，如pri\_order > 100 and pri\_order < 200。
*   在group by或order by中使用的列。
*   不经常修改的列。
*   在连接操作中使用的列。

**总结**：InnoDB索引巧妙的利用文件系统中磁盘块的概念，使用页来进行作为B+tree树的节点，这样可以在从磁盘读取每一个页的时候，保证同一页的数据相邻存放，提高了读取的效率。

**思考题**：我们知道聚簇索引适合范围存取，假设我们对列  A添加辅助索引 ，然后以A列作为查询条件：

> select * from student where A>10 and A<100 这个查询是怎么使用索引的？如何提高查询效率？

答案：Multi_Range Read优化  随机访问转化为顺序访问。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 配置文件不会变多，配置的节点主机会变多？
不会

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Mycat的在分库分表之后，它是怎么支持联表查询的？
- 使用好ER表
- 善用全局表
- 在sql上添加注解

```
/*!mycat:catlet=io.mycat.catlets.ShareJoin */
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Mycat中全局ID方案有哪些？程序自定义全局ID的方案有哪些？
1.mycat的全局id方案

（1）本地文件方式
sequnceHandlerType = 0

配置sequence_conf.properties

使用next value for MYCATSEQ_XXX

（2）数据库方式

sequnceHandlerType = 1

配置sequence_db_conf.properties

使用next value for MYCATSEQ_XXX或者指定autoIncrement

（3）本地时间戳方式

ID= 64 位二进制 (42(毫秒)+5(机器 ID)+5(业务编码)+12(重复累加)

sequnceHandlerType = 2

配置sequence_time_conf.properties

指定autoIncrement

2. 程序方式

（1）Snowflake

（2）UUID

（3）Redis

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 进行库表拆分时，拆分规则怎么取舍？
1.不存在热点数据时，则使用连续分片

2.存在热点数据时，使用离散分片或者是综合分片

3.离散分片暂时迁移比较麻烦（但是mycat给出了数据迁移的脚本，虽然现在还是不是很完美），综合分片占用总机器数量多

*** 
## ⭐️⭐️⭐️⭐️⭐️
## mycat分库可以分成100个库吗？
我们说一般数据量大的话我们使用的是mycat中间件进行分片处理，如果更大的话，我们可以使用oracle数据库，如果更大的话可以使用hadoop或是云存储数据，不需要mycat作为工具手段。衡量的标准是项目有没有对应的硬件设备。 如果没有，基本就是使用mysql 因为搭建一套云环境或者大数据的环境基本都是超大型的公司。比如大数据中的所有的技术，例如hbase 或者是一大堆的服务器 一大堆的网络路由设备 或是私有云。或者是一大堆的数据库运维实施人员都是成本

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 搭建mycat的核心配置文件有哪些？
schem.xml 配置参数：逻辑库，逻辑表，数据节点。节点主机

rule.xml：分片规则

server.xml：连接mycat的用户信息（账号和密码）

这里是使用中间件做数据切分，感兴趣的小伙伴还可以了解一下mysql的分库分表高可用方案

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在项目组中，切分后的库从哪里而来？
在开发中是基于原有库创建出来，并且原有库和切分后的库是数据表的设计是保持一致的。dm_order1,dm_order2,dm_order3这些库是需要和dm_order的设计保持一致的！！！！

附注：所以，切分后的库例如dm_order1,dm_order2,dm_order3这些都是有数据库维护团队创建出来的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么叫混合切分
项目组中如果有水平切分，那项目组里的开发方式就叫混合切分。或者项目组里就是单纯的垂直切分。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Mycat是什么？
Mycat是基于MySQL的数据库中间件，目的是为了降低数据库的压力。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Mybatis都有哪些Executor执行器？它们之间的区别是什么？
Mybatis有三种基本的Executor执行器，SimpleExecutor、ReuseExecutor、BatchExecutor。

SimpleExecutor：每执行一次update或select，就开启一个Statement对象，用完立刻关闭Statement对象。

ReuseExecutor：执行update或select，以sql作为key查找Statement对象，存在就使用，不存在就创建，用完后，不关闭Statement对象，而是放置于Map<String, Statement>内，供下一次使用。简言之，就是重复使用Statement对象。

BatchExecutor：执行update（没有select，JDBC批处理不支持select），将所有sql都添加到批处理中（addBatch()），等待统一执行（executeBatch()），它缓存了多个Statement对象，每个Statement对象都是addBatch()完毕后，等待逐一执行executeBatch()批处理。与JDBC批处理相同。

作用范围：Executor的这些特点，都严格限制在SqlSession生命周期范围内。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Mybatis是否支持延迟加载？如果支持，它的实现原理是什么？
Mybatis仅支持association关联对象和collection关联集合对象的延迟加载，association指的就是一对一，collection指的就是一对多查询。在Mybatis配置文件中，可以配置是否启用延迟加载lazyLoadingEnabled=true|false。

它的原理是，使用CGLIB创建目标对象的代理对象，当调用目标方法时，进入拦截器方法，比如调用a.getB().getName()，拦截器invoke()方法发现a.getB()是null值，那么就会单独发送事先保存好的查询关联B对象的sql，把B查询上来，然后调用a.setB(b)，于是a的对象b属性就有值了，接着完成a.getB().getName()方法的调用。这就是延迟加载的基本原理。

当然了，不光是Mybatis，几乎所有的包括Hibernate，支持延迟加载的原理都是一样的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Mybatis能执行一对一、一对多的关联查询吗？都有哪些实现方式，以及它们之间的区别。
答：能，Mybatis不仅可以执行一对一、一对多的关联查询，还可以执行多对一，多对多的关联查询，多对一查询，其实就是一对一查询，只需要把selectOne()修改为selectList()即可；多对多查询，其实就是一对多查询，只需要把selectOne()修改为selectList()即可。

　　关联对象查询，有两种实现方式，一种是单独发送一个sql去查询关联对象，赋给主对象，然后返回主对象。另一种是使用嵌套查询，嵌套查询的含义为使用join查询，一部分列是A对象的属性值，另外一部分列是关联对象B的属性值，好处是只发一个sql查询，就可以把主对象和其关联对象查出来。

　　那么问题来了，join查询出来100条记录，如何确定主对象是5个，而不是100个？其去重复的原理是 resultMap标签内的 id 子标签，指定了唯一确定一条记录的id列，Mybatis根据 id 列值来完成100条记录的去重复功能， id 可以有多个，代表了联合主键的语意。

　　同样主对象的关联对象，也是根据这个原理去重复的，尽管一般情况下，只有主对象会有重复记录，关联对象一般不会重复。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Mybatis全局配置文件中有哪些标签?分别代表什么意思?
* configuration 配置
* properties 属性:可以加载properties配置文件的信息
* settings 设置：可以设置mybatis的全局属性
* typeAliases 类型命名
* typeHandlers 类型处理器
* objectFactory 对象工厂
* plugins 插件
* environments 环境
* environment 环境变量
* transactionManager 事务管理器
* dataSource 数据源
* mappers 映射器

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说一下resultMap和resultType？
resultmap是手动提交，人为提交，resulttype是自动提交

MyBatis中在查询进行select映射的时候，返回类型可以用resultType，也可以用resultMap，resultType是直接表示返回类型的，而resultMap则是对外部ResultMap的引用，但是resultType跟resultMap不能同时存在。

在MyBatis进行查询映射时，其实查询出来的每一个属性都是放在一个对应的Map里面的，其中键是属性名，值则是其对应的值。

1.当提供的返回类型属性是resultType时，MyBatis会将Map里面的键值对取出赋给resultType所指定的对象对应的属性。所以其实MyBatis的每一个查询映射的返回类型都是ResultMap，只是当提供的返回类型属性是resultType的时候，MyBatis对自动的给把对应的值赋给resultType所指定对象的属性。

2.当提供的返回类型是resultMap时，因为Map不能很好表示领域模型，就需要自己再进一步的把它转化为对应的对象，这常常在复杂查询中很有作用。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Mybatis动态SQL？
1) 传统的JDBC的方法，在组合SQL语句的时候需要去拼接，稍微不注意就会少少了一个空格，标点符号，都会导致系统错误。Mybatis的动态SQL就是为了解决这种问题而产生的；Mybatis的动态SQL语句值基于OGNL表达式的，方便在SQL语句中实现某些逻辑；可以使用标签组合成灵活的sql语句，提供开发的效率。

 2) Mybatis的动态SQL标签主要由以下几类： If语句（简单的条件判断） Choose(when/otherwise),相当于java语言中的switch，与jstl中choose类似 Trim(对包含的内容加上prefix，或者suffix) Where(主要是用来简化SQL语句中where条件判断，能智能的处理and/or 不用担心多余的语法导致的错误) Set(主要用于更新时候) Foreach(一般使用在mybatis in语句查询时特别有用)

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Mybatis的Xml映射文件中，不同的Xml映射文件，id是否可以重复？
不同的Xml映射文件，如果配置了namespace，那么id可以重复；如果没有配置namespace，那么id不能重复

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何获取自动生成的(主)键值?
```
<insert id=”insertname” usegeneratedkeys=”true” keyproperty=”id”>
     insert into names (name) values (#{name})
</insert>
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Mybatis是如何将sql执行结果封装为目标对象并返回的？都有哪些映射形式？
第一种是使用resultMap标签，逐一定义数据库列名和对象属性名之间的映射关系。

第二种是使用sql列的别名功能，将列的别名书写为对象属性名。

有了列名与属性名的映射关系后，Mybatis通过反射创建对象，同时使用反射给对象的属性逐一赋值并返回，那些找不到映射关系的属性，是无法完成赋值的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 当实体类的属性名和表种字段名不一致怎么办?
有两种解决方案:可以在sql语句给字段名取别名,别名于实体类属性名同名,也可以用resultMap来映射字段名和实体类属性名一一对应.


*** 
## ⭐️⭐️⭐️⭐️⭐️
## #{}和${}的区别是什么？
\#{}是预编译处理，${}是字符串替换。

Mybatis在处理#{}时，会将sql中的#{}替换为?号，调用PreparedStatement的set方法来赋值；

Mybatis在处理{}时，就是把时，就是把{}替换成变量的值。

使用#{}可以有效的防止SQL注入，提高系统安全性。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Mybatis使用场合?
专注于sql本身,是一个足够灵活的dao层解决方案.,对性能的要求很高,或者需求多变的项目,

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Mybatis的优缺点?
Mybaits的优点：

（1）基于SQL语句编程，相当灵活，不会对应用程序或者数据库的现有设计造成任何影响，SQL写在XML里，解除sql与程序代码的耦合，便于统一管理；提供XML标签，支持编写动态SQL语句，并可重用。

（2）与JDBC相比，减少了50%以上的代码量，消除了JDBC大量冗余的代码，不需要手动开关连接；

（3）很好的与各种数据库兼容（因为MyBatis使用JDBC来连接数据库，所以只要JDBC支持的数据库MyBatis都支持）。

（4）能够与Spring很好的集成；

（5）提供映射标签，支持对象与数据库的ORM字段关系映射；提供对象关系映射标签，支持对象关系组件维护。

MyBatis框架的缺点：

（1）SQL语句的编写工作量较大，尤其当字段多、关联表多时，对开发人员编写SQL语句的功底有一定要求。

（2）SQL语句依赖于数据库，导致数据库移植性差，不能随意更换数据库。

MyBatis框架适用场合：

（1）MyBatis专注于SQL本身，是一个足够灵活的DAO层解决方案。

（2）对性能的要求很高，或者需求变化较多的项目，如互联网项目，MyBatis将是不错的选择。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Mybatis？
1）mybatis是一个半ORM框架，它内部封装了JDBC，开发时只需要关乎sql语句本身，不需要花费精力去处理驱动，创建连接，创建1statement等繁复过程。

2）mybatis可以使用xml或注解来配置和映射原生信息。将pijo映射成数据库中的记录，避免了几乎所有的JDBC 代码和手动设置参数以及获取结果集。

3）通过xm文件或注解的方式将要执行的各种statement配置起来,并通java对象和statement中sql的动态参数进行映射生成最终的sql语句,最后由mybatis框架执行sql并将结果映射java对象返回.

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么MongoDB的数据文件很大？
MongoDB采用的预分配空间的方式来防止文件碎片。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何理解MongoDB中的GridFS机制，MongoDB为何使用GridFS来存储文件？
GridFS是一种将大型文件存储在MongoDB中的文件规范。使用GridFS可以将大文件分隔成多个小文档存放，这样我们能够有效的保存大文档，而且解决了BSON对象有限制的问题。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## MongoDB支持存储过程吗？如果支持的话，怎么用？
MongoDB支持存储过程，它是javascript写的，保存在db.system.js表中。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在MongoDB中什么是副本集
在MongoDB中副本集由一组MongoDB实例组成，包括一个主节点多个次节点，MongoDB客户端的所有数据都写入主节点(Primary),副节点从主节点同步写入数据，以保持所有复制集内存储相同的数据，提高数据可用性。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在MongoDb中什么是索引
索引用于高效的执行查询,没有索引的MongoDB将扫描整个集合中的所有文档,这种扫描效率很低,需要处理大量的数据。

索引是一种特殊的数据结构,将一小块数据集合保存为容易遍历的形式.索引能够存储某种特殊字段或字段集的值,并按照索引指定的方式将字段值进行排序。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## "ObjectID"有哪些部分组成
一共有四部分组成:时间戳、客户端ID、客户进程ID、三个字节的增量计数器

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么在MongoDB中使用"Object ID"数据类型
"ObjectID"数据类型用于存储文档id

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么要在MongoDB中用"Regular Expression"数据类型
"Regular Expression"类型用于在文档中存储正则表达式

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么要在MongoDB中用"Code"数据类型
"Code"类型用于在文档中存储 JavaScript 代码。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## MongoDB支持哪些数据类型
* String
* Integer
* Double
* Boolean
* Object
* Object ID
* Arrays
* Min/Max Keys
* Datetime
* Code
* Regular Expression等

*** 
## ⭐️⭐️⭐️⭐️⭐️
## MongoDB支持主键外键关系吗
默认MongoDB不支持主键和外键关系。 用Mongodb本身的API需要硬编码才能实现外键关联，不够直观且难度较大。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么要在MongoDB中使用分析器
mongodb中包括了一个可以显示数据库中每个操作性能特点的数据库分析器.通过这个分析器你可以找到比预期慢的查询(或写操作);利用这一信息,比如,可以确定是否需要添加索引。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## MongoDB中的分片什么意思
分片是将数据水平切分到不同的物理节点。当应用数据越来越大的时候，数据量也会越来越大。当数据量增长时，单台机器有可能无法存储数据或可接受的读取写入吞吐量。利用分片技术可以添加更多的机器来应对数据量增加以及读写操作的要求。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## MongoDB中的命名空间是什么意思?
mongodb存储bson对象在丛集(collection)中，数据库名字和丛集名字以句点连结起来叫做名字空间(namespace)。

一个集合命名空间又有多个数据域(extent)，集合命名空间里存储着集合的元数据，比如集合名称，集合的第一个数据域和最后一个数据域的位置等等。而一个数据域由若干条文档(document)组成，每个数据域都有一个头部，记录着第一条文档和最后一条文档的为知，以及该数据域的一些元数据。extent之间，document之间通过双向链表连接。

索引的存储数据结构是B树，索引命名空间存储着对B树的根节点的指针。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在哪些场景使用MongoDB
* 大数据
* 内容管理系统
* 移动端Apps
* 数据管理

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么用MOngoDB？
* 架构简单
* 没有复杂的连接
* 深度查询能力,MongoDB支持动态查询。
* 容易调试
* 容易扩展
* 不需要转化/映射应用对象到数据库对象
* 使用内部内存作为存储工作区,以便更快的存取数据。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是文档(记录)
文档由一组key value组成。文档是动态模式,这意味着同一集合里的文档不需要有相同的字段和结构。在关系型数据库中table中的每一条记录相当于MongoDB中的一个文档。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是集合(表)？
集合就是一组 MongoDB文档。它相当于关系型数据库（RDBMS）中的表这种概念。集合位于单独的一个数据库中。
一个集合内的多个文档可以有多个不同的字段。一般来说，集合中的文档都有着相同或相关的目的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## MongoDB的优势有哪些
面向文档的存储：以 JSON 格式的文档保存数据。

* 任何属性都可以建立索引。
* 复制以及高可扩展性。
* 自动分片。
* 丰富的查询功能。
* 快速的即时更新。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是MongoDB？
MongoDB是一个文档数据库，提供好的性能，领先的非关系型数据库。采用BSON存储文档数据。

BSON（）是一种类json的一种二进制形式的存储格式，简称Binary JSON

相对于json多了date类型和二进制数组。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Maven依赖冲突
每个显式声明的类包都会依赖于一些其它的隐式类包，这些隐式的类包会被maven间接引入进来，因而可能造成一个我们不想要的类包的载入，严重的甚至会引起类包之间的冲突。

要解决这个问题，首先就是要查看pom.xml显式和隐式的依赖类包，然后通过这个类包树找出我们不想要的依赖类包，手工将其排除在外就可以了。 例如：

```xml
<exclusions>  
    <exclusion>  
        <artifactId>unitils-database</artifactId>  
        <groupId>org.unitils</groupId>  
    </exclusion>  
</exclusions>  
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是 Maven 插件？
Maven 生命周期的每一个阶段的具体实现都是由 Maven 插件实现的。插件通常提供了一个目标的集合，并且可以使用下面的语法执行：`mvn [plugin-name]:[goal-name]`

Maven 提供了下面两种类型的插件：

- Build plugins ：在构建时执行，并在 `pom.xml` 的 元素中配置。
- Reporting plugins ：在网站生成过程中执行，并在 `pom.xml` 的元素中配置。

下面是一些常用插件的列表：

- clean ：构建之后清理目标文件。删除目标目录。
- compiler ：编译 Java 源文件。
- surefile ：运行 JUnit 单元测试。创建测试报告。
- jar ：从当前工程中构建 JAR 文件。
- war ：从当前工程中构建 WAR 文件。
- javadoc ：为工程生成 Javadoc 。
- antrun ：从构建过程的任意一个阶段中运行一个 ant 任务的集合。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何解决 jar 冲突？
遇到冲突的时候第一步，要找到 Maven 加载的到时是什么版本的 jar 包，通过们 `mvn dependency:tree` 查看依赖树，或者使用 [IDEA Maven Helper](https://plugins.jetbrains.com/plugin/7179-maven-helper) 插件。

然后，通过 Maven 的依赖原则来调整坐标在 pom 文件的申明顺序是最好的办法，或者使用将冲突中不想要的 jar 引入的 jar 进行 `<exclusions>` 掉。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Maven 依赖原则？
- 1、赖路径最短优先原则。

  一个项目 Demo 依赖了两个 jar 包，其中 `A-B-C-X(1.0)` ， `A-D-X(2.0)` 。由于 `X(2.0)` 路径最短，所以项目使用的是 `X(2.0)` 。

- 2、pom文 件中申明顺序优先。

  如果 `A-B-X(1.0)` ，`A-C-X(2.0)` 这样的路径长度一样怎么办呢？这样的情况下，Maven 会根据 pom 文件声明的顺序加载，如果先声明了 B ，后声明了 C ，那就最后的依赖就会是 `X(1.0)` 。

- 3、覆写优先

  子 pom 内声明的优先于父 pom 中的依赖。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 对于一个多模块项目，如果管理项目依赖的版本？
- 方式一，通过在父模块中声明 `<dependencyManagement />` 和`<pluginManagement />`， 然后让子模块通过元素指定父模块，这样子模块在定义依赖是就可以只定义 `groupId` 和 `artifactId`，自动使用父模块的 `version` ，这样统一整个项目的依赖的版本。

  继承的方式。

- 方式二，使用 `<dependencie />` 声明 `<scope />` 为 `import` 的依赖，从而引入一个 pom 的`<dependencyManagement />` 的。具体的，可以看看 [《Maven Spring BOM (bill of materials)》](https://www.cnblogs.com/YLsY/p/5711103.html)文章。

  组合的方式。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Maven 版本规则？
Maven 主要是这样定义版本规则的：`<主版本>.<次版本>.<增量版本>` 。比如说 `1.2.3` ，主版本是 1 ，次版本是 2 ，增量版本是 3 。

- 主版本，一般来说代表了项目的重大的架构变更，比如说 Maven 1 和 Maven 2 ，在架构上已经两样了，将来的 Maven 3 和 Maven 2 也会有很大的变化。
- 次版本，一般代表了一些功能的增加或变化，但没有架构的变化，比如说Nexus 1.3 较之于 Nexus 1.2 来说，增加了一系列新的或者改进的功能（仓库镜像支持，改进的仓库管理界面等等），但从大的架构上来说，1.3 和 1.2 没什么区别。
- 增量版本，一般是一些小的 bug fix ，不会有重大的功能变化。

一般来说，在我们发布一次重要的版本之后，随之会开发新的版本。比如说，`myapp-1.1` 发布之后，就着手开发 `myapp-1.2` 了。由于`myapp-1.2` 有新的主要功能的添加和变化，在发布测试前，它会变得不稳定，而 `myapp-1.1` 是一个比较稳定的版本，现在的问题是，我们在`myapp-1.1中` 发现了一些 BUG（当然在 1.2 中也存在），为了能够在一段时间内修复 BUG 并仍然发布稳定的版本，我们就会用到分支(branch)，我们基于 1.1 开启一个分支 1.1.1 ，在这个分支中修复 BUG ，并快速发布。这既保证了版本的稳定，也能够使bug得到快速修复，也不同停止 1.2 的开发。只是，每次修复分支 1.1.1 中的 BUG 后，需要 merge 代码到 1.2 中。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Maven 有哪些优点和缺点
1）优点

- 简化了项目依赖管理。

  当年，多少人被 SSH 整合搞死搞活，很多时候，是因为依赖不完整，或者版本不正确。自从 Maven 出来后，终于可以无痛了~当然，也有一部分功劳是 Spring Boot ，这是后话。

- 易于上手，对于新手可能一个 `mvn clean package` 命令就可能满足我们的工作。

- 便于与持续集成工具(Jenkins)整合。

- 便于项目升级，无论是项目本身升级还是项目使用的依赖升级。

- 有助于多模块项目的开发，一个模块开发好后，发布到仓库，依赖该模块时可以直接从仓库更新，而不用自己去编译。

- Maven 有很多插件，便于功能扩展，比如生产站点，自动发布版本等。

 2）缺点

- Maven 是一个庞大的构建系统，学习难度大。

  这里的学习，更多指的完整学习。如果基本使用，并不会存在该问题。

- Maven 采用约定优于配置的策略(convention over configuration)，虽然上手容易，但是一旦出了问题，难于调试。

  这个确实，略微痛苦。

- 当依赖很多时，m2eclipse 老是搞得 Eclipse 很卡。

  使用 IDEA ，而不是 Eclipse ，完美解决。

- 中国的网络环境差，很多 repository 无法访问，比如 Google Code、 JBoss 仓库无法访问等。

  这个也好解决，在 `<mirrors>` 中增加阿里巴巴的 Maven 私服，具体可以参见 [《提高 Maven 速度 —— Maven 仓库修改成国内阿里巴巴地址》](https://my.oschina.net/af8991/blog/833513) 文章。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Maven 常用命令
- `mvn archetype：create` ：创建 Maven 项目。
- `mvn compile` ：编译源代码。
- `mvn deploy` ：发布项目。
- `mvn test-compile` ：编译测试源代码。
- `mvn test` ：运行应用程序中的单元测试。
- `mvn site` ：生成项目相关信息的网站。
- `mvn clean` ：清除项目目录中的生成结果。
- `mvn package` ：根据项目生成的 jar/war 等。
- `mvn install` ：在本地 Repository 中安装 jar 。
- `mvn eclipse:eclipse` ：生成 Eclipse 项目文件。
- `mvn jetty:run` 启动 Jetty 服务。
- `mvn tomcat:run` ：启动 Tomcat 服务。
- `mvn clean package -Dmaven.test.skip=true` ：清除以前的包后重新打包，跳过测试类。
- 用到最多的命令
  - `mvn eclipse:clean` ：清除 Project 中以前的编译的东西，重新再来。
  - `mvn eclipse:eclipse` ：开始编译 Maven 的 Project 。
  - `mvn clean package` ：清除以前的包后重新打包。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Maven 规约是什么？
- `/src/main/java/` ：Java 源码。
- `/src/main/resource` ：Java 配置文件，资源文件。
- `/src/test/java/` ：Java 测试代码。
- `/src/test/resource` ：Java 测试配置文件，资源文件。
- `/target` ：文件编译过程中生成的 `.class` 文件、jar、war 等等。
- `pom.xml` ：配置文件

Maven 要负责项目的自动化构建，以编译为例，Maven 要想自动进行编译，那么它必须知道 Java 的源文件保存在哪里，这样约定之后，不用我们手动指定位置，Maven 能知道位置，从而帮我们完成自动编译。

遵循**“约定>>>配置>>>编码”**。即能进行配置的不要去编码指定，能事先约定规则的不要去进行配置。这样既减轻了劳动力，也能防止出错。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 你们项目为什么选用 Maven 进行构建？
- 首先，Maven 是一个优秀的项目构建工具。使用maven，可以很方便的对项目进行分模块构建，这样在开发和测试打包部署时，效率会提高很多。
- 其次，Maven 可以进行依赖的管理。使用 Maven ，可以将不同系统的依赖进行统一管理，并且可以进行依赖之间的传递和继承。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Maven的⽣命周期
一个项目的构建过成通常包括清理、编译、测试、打包、集成测试、验证、部署等。

Maven从中抽取了一套完善的、易扩展的生命周期。Maven的生命周期是抽象的，其中的具体任务都交由插件来完成。Maven为大多数构建任务编写并绑定了默认的插件。

Maven定义了三套生命周期：clean、default、site，每个生命周期都包含了一些阶段（phase）。三套生命周期相互独立，但各个生命周期中的阶段却是有顺序的，且后面的夹断依赖于前面的阶段。执行某个阶段时，其前面的阶段会依顺序执行，但不会触发另外两套生命周期中的任何阶段。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Maven的坐标和依赖Maven坐标
-------

坐标是Maven实现依赖管理功能的基础，Maven通过为任何一个构件定义一个唯一的标示来确定该构件的归属及版本。Maven的坐标元素包括groupId、artifactId、version、packaging、classfier。 提供了正确的坐标，maven就能找到对应的构件、首先去你的本地仓库查找，没有的话再去远程仓库下载。如果没有配置远程仓库，会默认从中央仓库地址([http://repo1.maven.org/maven2](http://repo1.maven.org/maven2))下载构件，该中央仓库包含了世界上大部分流行的开源项目构件

**Maven的坐标元素**

groupId：项目的名称  
artifactId：表示项目的模块名称，建议使用项目的名称  
version：项目的版本名称  
packaging：Maven项目打包的方式，使用构件的什么包  
classifier: 该元素用来帮助定义构建输出的一些附件。参考一篇博客：[http://blog.csdn.net/lovingprince/article/details/5894459](http://blog.csdn.net/lovingprince/article/details/5894459)

前三个是必须的，第四个可选，默认是jar；classfier是不能直接定义的，需要结合插件使用。

**根元素project下的dependencies元素详解**

dependencies可以包含一个或者多个dependency元素，以声明一个或多个项目依赖, 其包含的元素：  
groupId、artifactId、version：依赖的基本坐标，上面讲了  
type: 依赖的类型  
scope: 依赖的范围（后面会结合exclusions进行讲解）  
optional: 标记依赖是否可选  
exclusions: 用来排除传递性依赖(后面详解)

传递依赖
----

**依赖范围**

maven在编译项目主代码的时候，需要使用一套classpath，在编译和执行测试的时候，会使用另一套classpath，实际运行maven项目时，又会使用一套classpath。依赖范围就是用来控制依赖于这三种（编译classpath、测试classpath、运行classpath）的关系——摘自《maven实战》5.5节

maven主要的几种依赖范围：  
test：测试范围有效，不会打包，编译打包时不会使用这个依赖；  
compile：范围指的是编译范围有效，在编译和打包时都会将依赖存储进去；  
provide：在编译和测试的过程有效，最后生成war包时不会加入。如：servlet-api，因为servlet-api，tomcat等web服务器已经存在了，如果再打包会冲突  
runtime：运行有依赖，编译不依赖  
system：未做研究  

![image.png](https://i.loli.net/2021/11/14/OPvRFtTi43Cwonq.png)

**依赖调解**

依赖关系A——B——C——X（1.0）;  
A——D——X（2.0）；  
X是A的传递依赖，但是有两个版本X；maven会去解析哪个？  
Maven依赖调解有两个原则：1、路径最近者优先；2、第一声明者优先；  
简单理解：  
上面两条传递依赖，第一条路径长度是3；第二条路径长度是2，所以会优先选择第二条；但是当两条路径一样时，就看pom中，那个依赖先声明，就先用哪个。看，这两条，完全就跟生活一样么：有近路不走远路，先到先得

排除依赖，结合上面的scope和exclusions，我们下篇再见~~
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 使用Maven好处
Maven能提供一种项目的配置，配置好的项目，只需要运行一条简单的命令，就能完成重复的，繁琐的构建动作.

Maven能提供一种项目的依赖配置.可以自动的导入项目依赖的jar,并且自动导入这些jar包依赖的第三方的jar包.

Maven提供了一种标准的项目目录结构，测试命名规则等项目的最佳实践方案，统一了不同项目的学习成本.

## maven的常用命令

* mvn clean : 清理
* mvn compile：编译
* mvn package：打包
* mvn test : 测试，⾃动运⾏所有的测试⽤例
* mvn install : 安装，将项⽬打的包安装到本地仓库，其他项⽬就可以依赖了
* mvn jetty:run : 运⾏jetty插件

*** 
## ⭐️⭐️⭐️⭐️⭐️
## maven是什么？Maven 是一个项目管理和整合工具。Maven项目对象模型(POM)，可以通过一小段描述信息来管理项目的构建，报告和文档的项目管理工具软件。

Maven 为开发者提供了一套完整的构建生命周期框架。开发团队几乎不用花多少时间就能够自动完成工程的基础构建配置，因为 Maven 使用了一个标准的目录结构和一个默认的构建生命周期。

在有多个开发团队环境的情况下，Maven 能够在很短的时间内使得每项工作都按照标准进行。因为大部分的工程配置操作都非常简单并且可复用，在创建报告、检查、构建和测试自动配置时，Maven 可以让开发者的工作变得更简单。

Maven 能够帮助开发者完成以下工作：

*   构建
*   文档生成
*   报告
*   依赖
*   SCMs
*   发布
*   分发
*   邮件列表

Maven 带来的好处：

*   它管理应用程序的整个构建生命周期，从编译、到测试、生成报告、打包、部署等等。、
*   它管理idsanf的jar依赖包，管理多模块项目。
*   通过pom.xml文件来管理项目的构建过程以及依赖信息、团队成员信息。
*   包含很多插件、提供强大的扩展功能。
*   提供了最佳实践开发指南。

总的来说，Maven 简化了工程的构建过程，并对其标准化。它无缝衔接了编译、发布、文档生成、团队合作和其他任务。Maven 提高了重用性，负责了大部分构建相关的任务。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 设置 DNS 需要修改哪个配置文件？
全局的配置，可以在 /etc/resolv.conf 文件中配置。

指定网卡的配置，可以在 /etc/sysconfig/network-scripts/ifcfg-eth0 文件中配置。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何禁止服务器被 ping ？
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 用一条命令显示本机 eth0 网卡的 IP 地址，不显示其它字符？## 方法一
ifconfig eth0|grep inet|awk -F ':' '{print $2}'|awk '{print $1}'

## 方法二
ifconfig eth0|grep "inet addr"|awk -F '[ :]+' '{print $4}' 

##方法三
ifconfig eth0|awk -F '[ :]+' 'NR==2 {print $4}' 

## 方法四
ifconfig eth0|sed -n '2p'|sed 's#^.*addr:##g'|sed 's# Bc.*$##g'

## 方法五

ifconfig eth0|sed -n '2p'|sed -r 's#^.*addr:(.*)  Bc.*$#\1#g'

## 方法六(CENTOS7 也适用)
ip addr|grep eth0|grep inet|awk '{print $2}'|awk -F '/' '{print $1}'

*** 
## ⭐️⭐️⭐️⭐️⭐️
## whereis 命令有哪些常见用法
* 当你不知道某个命令的位置时可以使用 whereis 命令，下面使用 whereis 查找 ls 的位置：whereis ls 。
* 当你想查找某个可执行程序的位置，但这个程序又不在 whereis 的默认目录下，你可以使用 -B 选项，并指定目录作为这个选项的参数。下面的命令在 /tmp 目录下查找 lsmk 命令：whereis -u -B /tmp -f lsmk 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## service 命令有哪些常见用法
* service 命令用于运行 System V init 脚本，这些脚本一般位于 /etc/init.d 文件下，这个命令可以直接运行这个文件夹里面的脚本，而不用加上路径。
* 查看服务状态：service ssh status 。
* 查看所有服务状态：service --status-all 。
* 重启服务：service ssh restart 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## shutdown 命令有哪些常见用法
* 关闭系统并立即关机：shutdown -h now 。
* 10 分钟后关机：shutdown -h +10 。
* 重启：shutdown -r now 。
* 重启期间强制进行系统检查：shutdown -Fr now 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## rpm 命令有哪些常见用法
* 使用 rpm 安装 apache ：rpm -ivh httpd-2.2.3-22.0.1.el5.i386.rpm 。
* 更新 apache ：rpm -uvh httpd-2.2.3-22.0.1.el5.i386.rpm 。
* 卸载/删除 apache ：rpm -ev httpd 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## yum 命令有哪些常见用法
* 使用 yum 安装 apache ：yum install httpd 。
* 更新 apache ：yum update httpd 。
* 卸载/删除 apache ：yum remove httpd 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## export 命令有哪些常见用法
* 输出跟字符串 oracle 匹配的环境变量：export | grep ORCALE 。
* 设置全局环境变量：export ORACLE_HOME=/u01/app/oracle/product/10.2.0 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## unzip 命令有哪些常见用法
* 解压 *.zip 文件：unzip test.zip 。
* 查看 *.zip 文件的内容：unzip -l jasper.zip 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## bzip2 命令有哪些常见用法
* 创建 *.bz2 压缩文件：bzip2 test.txt 。
* 解压 *.bz2 文件：bzip2 -d test.txt.bz2 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## gzip 命令有哪些常见用法
* 创建一个 *.gz 的压缩文件：gzip test.txt 。
* 解压 *.gz 文件：gzip -d test.txt.gz 。
* 显示压缩的比率：gzip -l *.gz 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## tar 命令有哪些常见用法？
* 创建一个新的 tar 文件： tar cvf archive_name.tar dirname/ 。
* 解压 tar 文件：tar xvf archive_name.tar 。
* 查看 tar 文件：tar tvf archive_name.tar 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 把当前目录下所有后缀名为 .txt 的文件的权限修改为 777 ？
* 方式一，使用 xargs 命令：find ./ -type f -name "*.txt" |xargs chmod 777 。
* 方式二，使用 exec 命令：find ./ -type f -name "*.txt" -exec chmod 777 {} 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## xargs 命令有哪些常见用法？
* 将所有图片文件拷贝到外部驱动器：ls *.jpg | xargs -n1 -i cp {} /external-hard-drive/directory 。
* 将系统中所有 jpg 文件压缩打包：find / -name *.jpg -type f -print | xargs tar -cvzf images.tar.gz 。
* 下载文件中列出的所有 url 对应的页面：cat url-list.txt | xargs wget –c 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## sort 命令有哪些常见用法
* 以升序对文件内容排序：sort names.txt 。
* 以降序对文件内容排序：sort -r names.txt 。
* 以第三个字段对 /etc/passwd 的内容排序：sort -t: -k 3n /etc/passwd | more 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## diff 命令有哪些常见用法
比较的时候忽略空白符：diff -w name_list.txt name_list_new.txt 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## vim 命令有哪些常见用法？
* 打开文件并跳到第 10 行：vim +10 filename.txt 。
* 打开文件跳到第一个匹配的行：vim +/search-term filename.txt 。
* 以只读模式打开文件：vim -R /etc/passwd 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 打印 /etc/passwd 的 1 到 3 行？
* 使用 sed 命令：sed -n '1,3p' /etc/passwd
* 使用 awk 命令：awk 'NR>=1&&NR<=3{print $0}' /etc/passwd

*** 
## ⭐️⭐️⭐️⭐️⭐️
## awk 命令有哪些用法
* 删除重复行：$ awk '!($0 in array) { array[$0]; print}' temp 。
* 打印 /etc/passwd 中所有包含同样的 uid 和 gid 的行：awk -F ':' '$3=$4' /etc/passwd 。
* 打印文件中的指定部分的字段：awk '{print $2,$5;}' employee.txt 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 打印 /etc/ssh/sshd_config 的第一百行？```
sed -n '100p' /etc/ssh/sshd_config
```
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 用 sed 命令将指定的路径 /usr/local/http 替换成为 /usr/src/local/http ？```
echo "/usr/local/http/" | sed 's#/usr/local/#/usr/src/local/#'
```
*** 
## ⭐️⭐️⭐️⭐️⭐️
## sed 命令
* 当你将 Dos 系统中的文件复制到 Unix/Linux 后，这个文件每行都会以 \r\n 结尾，sed 可以轻易将其转换为 Unix 格式的文件，使用\n 结尾的文件：sed 's/.$//' filename 。
* 反转文件内容并输出：sed -n '1!G; h; p' filename 。
* 为非空行添加行号：sed '/./=' thegeekstuff.txt | sed 'N; s/\n/ /' 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## grep 命令有哪些用法？
* 在文件中查找字符串(不区分大小写)：grep -i "the" demo_file 。
* 输出成功匹配的行，以及该行之后的三行：grep -A 3 -i "example" demo_text 。
* 在一个文件夹中递归查询包含指定字符串的文件：grep -r "ramesh" * 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## tail 命令有哪些用法
tail 命令默认显示文件最后的 10 行文本：tail filename.txt 。

你可以使用 -n 选项指定要显示的行数：tail -n N filename.txt 。

你也可以使用 -f 选项进行实时查看，这个命令执行后会等待，如果有新行添加到文件尾部，它会继续输出新的行，在查看日志时这个选项会非常有用。你可以通过 CTRL-C 终止命令的执行：tail -f log-file 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## cp 命令有哪些用法
拷贝 file1 到 file2 ，并保持文件的权限、属主和时间戳：cp -p file1 file2 。

拷贝 file1 到 file2 ，如果 file2 存在会提示是否覆盖：cp -i file1 file2 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## mv 命令有哪些用法
将 file1 重命名为 file2 ，如果 file2 存在则提示是否覆盖：mv -i file1 file2 。

-v 会输出重命名的过程，当文件名中包含通配符时，这个选项会非常方便：mv -v file1 file2 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## rm 命令有哪些用法
* 删除文件前先确认：rm -i filename.txt 。
* 在文件名中使用 shell 的元字符会非常有用。删除文件前先打印文件名并进行确认：rm -i file* 。
* 递归删除文件夹下所有文件，并删除该文件夹：rm -r example 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## df 命令有哪些用法？
显示文件系统的磁盘使用情况，默认情况下 df -k 将以字节为单位输出磁盘的使用量。

使用 df -h 选项可以以更符合阅读习惯的方式显示磁盘使用量。

使用 df -T 选项显示文件系统类型。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## ls 命令有哪些用法
* 以易读的方式显示文件大小(显示为 MB,GB…)：ls -lh 。
* 以最后修改时间升序列出文件：ls -ltr 。
* 在文件名后面显示文件类型：ls -F 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在整个目录树下查找文件 “core” ，如发现则无需提示直接删除它们？```
find / -name core -exec rm {} \;
```
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何在 /home 目录下找出 120 天之前被修改过的文件？```
find /home -mtime +120
```
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何在 /var 目录下找出 90 天之内未被访问过的文件？```
find /var \! -atime -90 
```
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何在 /usr 目录下找出大小超过 10MB 的文件?```
find /usr -type f -size +10240k 
```
*** 
## ⭐️⭐️⭐️⭐️⭐️
## find 命令如何使用？
* 查找指定文件名的文件(不区分大小写)：find -iname "MyProgram.c" 。
* 对找到的文件执行某个命令：find -iname "MyProgram.c" -exec md5sum {} \; 。
* 查找 home 目录下的所有空文件：find ~ -empty 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## vim有几种工作模式？
命令模式，行末模式，编辑模式

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Replica Set 和 Replication Controller之间有什么区别？
Replica Set 和 Replication Controller几乎完全相同。它们都确保在任何给定时间运行指定数量的pod副本。不同之处在于复制pod使用的选择器。Replica Set使用基于集合的选择器，而Replication Controller使用基于权限的选择器。

Equity-Based选择器：这种类型的选择器允许按标签键和值进行过滤。因此，在外行术语中，基于Equity的选择器将仅查找与标签具有完全相同短语的pod。 示例：假设您的标签键表示app = nginx，那么，使用此选择器，您只能查找标签应用程序等于nginx的那些pod。

Selector-Based选择器：此类型的选择器允许根据一组值过滤键。因此，换句话说，基于Selector的选择器将查找已在集合中提及其标签的pod。 示例：假设您的标签键在（nginx，NPS，Apache）中显示应用程序。然后，使用此选择器，如果您的应用程序等于任何nginx，NPS或Apache，则选择器将其视为真实结果。



*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Container资源监控？
对于用户而言，了解应用程序的性能和所有不同抽象层的资源利用率非常重要，Kubernetes通过在容器，pod，服务和整个集群等不同级别创建抽象来考虑集群的管理。现在，可以监视每个级别，这只是容器资源监视。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 您对云控制器管理器有何了解？
Cloud Controller Manager负责持久存储，网络路由，从核心Kubernetes特定代码中抽象出特定于云的代码，以及管理与底层云服务的通信。它可能会分成几个不同的容器，具体取决于您运行的是哪个云平台，然后它可以使云供应商和Kubernetes代码在没有任何相互依赖的情况下开发。因此，云供应商开发他们的代码并在运行Kubernetes时与Kubernetes云控制器管理器连接。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Ingress网络，它是如何工作的？
Ingress网络是一组规则，充当Kubernetes集群的入口点。这允许入站连接，可以将其配置为通过可访问的URL，负载平衡流量或通过提供基于名称的虚拟主机从外部提供服务。因此，Ingress是一个API对象，通常通过HTTP管理集群中服务的外部访问，是暴露服务的最有效方式。

现在，让我以一个例子向您解释Ingress网络的工作。

有2个节点具有带有Linux桥接器的pod和根网络命名空间。除此之外，还有一个名为flannel0（网络插件）的新虚拟以太网设备被添加到根网络中。

现在，假设我们希望数据包从pod1流向pod 4。

因此，数据包将pod1的网络保留在eth0，并进入veth0的根网络。

然后它被传递给cbr0，这使得ARP请求找到目的地，并且发现该节点上没有人具有目的地IP地址。

因此，桥接器将数据包发送到flannel0，因为节点的路由表配置了flannel0。

现在，flannel守护程序与Kubernetes的API服务器通信，以了解所有pod IP及其各自的节点，以创建pods IP到节点IP的映射。

网络插件将此数据包封装在UDP数据包中，其中额外的标头将源和目标IP更改为各自的节点，并通过eth0发送此数据包。

现在，由于路由表已经知道如何在节点之间路由流量，因此它将数据包发送到目标节点2。

数据包到达node2的eth0并返回到flannel0以解封装并在根网络命名空间中将其发回。

同样，数据包被转发到Linux网桥以发出ARP请求以找出属于veth1的IP。

数据包最终穿过根网络并到达目标Pod4。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 你对Kubernetes的负载均衡器有什么了解？
负载均衡器是暴露服务的最常见和标准方式之一。根据工作环境使用两种类型的负载均衡器，即内部负载均衡器或外部负载均衡器。内部负载均衡器自动平衡负载并使用所需配置分配容器，而外部负载均衡器将流量从外部负载引导至后端容器。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是etcd？
etcd是用Go编程语言编写的，是一个分布式键值存储，用于协调分布式工作。因此，Etcd存储Kubernetes集群的配置数据，表示在任何给定时间点的集群状态。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 你能简要介绍一下Kubernetes控制管理器吗？
多个控制器进程在主节点上运行，但是一起编译为单个进程运行，即Kubernetes控制器管理器。因此，Controller Manager是一个嵌入控制器并执行命名空间创建和垃圾收集的守护程序。它拥有责任并与API服务器通信以管理端点。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## kube-apiserver和kube-scheduler的作用是什么？
kube -apiserver遵循横向扩展架构，是主节点控制面板的前端。这将公开Kubernetes主节点组件的所有API，并负责在Kubernetes节点和Kubernetes主组件之间建立通信。

kube-scheduler负责工作节点上工作负载的分配和管理。因此，它根据资源需求选择最合适的节点来运行未调度的pod，并跟踪资源利用率。它确保不在已满的节点上调度工作负载。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 您能否介绍一下Kubernetes中主节点的工作情况？
Kubernetes master控制容器存在的节点和节点内部。现在，这些单独的容器包含在容器内部和每个容器内部，您可以根据配置和要求拥有不同数量的容器。因此，如果必须部署pod，则可以使用用户界面或命令行界面部署它们。然后，在节点上调度这些pod，并根据资源需求，将pod分配给这些节点。kube-apiserver确保在Kubernetes节点和主组件之间建立通信。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 你对Kube-proxy有什么了解？
Kube-proxy可以在每个节点上运行，并且可以跨后端网络服务进行简单的TCP / UDP数据包转发。基本上，它是一个网络代理，它反映了每个节点上Kubernetes API中配置的服务。因此，Docker可链接的兼容环境变量提供由代理打开的群集IP和端口。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Kubernetes Architecture的不同组件有哪些？
Kubernetes Architecture主要有两个组件 - 主节点和工作节点。如下图所示，master和worker节点中包含许多内置组件。主节点具有kube-controller-manager，kube-apiserver，kube-scheduler等。而工作节点具有在每个节点上运行的kubelet和kube-proxy。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Kubelet？
这是一个代理服务，它在每个节点上运行，并使从服务器与主服务器通信。因此，Kubelet处理PodSpec中提供给它的容器的描述，并确保PodSpec中描述的容器运行正常。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Kubectl？
Kubectl是一个平台，您可以使用该平台将命令传递给集群。因此，它基本上为CLI提供了针对Kubernetes集群运行命令的方法，以及创建和管理Kubernetes组件的各种方法。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Minikube？
Minikube是一种工具，可以在本地轻松运行Kubernetes。这将在虚拟机中运行单节点Kubernetes群集。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Heapster？
Heapster是由每个节点上运行的Kubelet提供的集群范围的数据聚合器。此容器管理工具在Kubernetes集群上本机支持，并作为pod运行，就像集群中的任何其他pod一样。因此，它基本上发现集群中的所有节点，并通过机上Kubernetes代理查询集群中Kubernetes节点的使用信息。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Google容器引擎？
Google Container Engine（GKE）是Docker容器和集群的开源管理平台。这个基于Kubernetes的引擎仅支持在Google的公共云服务中运行的群集。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Kubernetes如何简化容器化部署？
由于典型应用程序将具有跨多个主机运行的容器集群，因此所有这些容器都需要相互通信。因此，要做到这一点，你需要一些能够负载平衡，扩展和监控容器的东西。由于Kubernetes与云无关并且可以在任何公共/私有提供商上运行，因此必须是您简化容器化部署的选择。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Container Orchestration？
考虑一个应用程序有5-6个微服务的场景。现在，这些微服务被放在单独的容器中，但如果没有容器编排就无法进行通信。因此，由于编排意味着所有乐器在音乐中和谐共处，所以类似的容器编排意味着各个容器中的所有服务协同工作以满足单个服务器的需求。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Kubernetes与Docker有什么关系？
众所周知，Docker提供容器的生命周期管理，Docker镜像构建运行时容器。但是，由于这些单独的容器必须通信，因此使用Kubernetes。因此，我们说Docker构建容器，这些容器通过Kubernetes相互通信。因此，可以使用Kubernetes手动关联和编排在多个主机上运行的容器。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Kubernetes？
Kubernetes是一个开源容器管理工具，负责容器部署，容器扩缩容以及负载平衡。作为Google的创意之作，它提供了出色的社区，并与所有云提供商合作。因此，我们可以说Kubernetes不是一个容器化平台，而是一个多容器管理解决方案。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java Consumer 为什么采用单线程来获取消息?
在回答之前，如果先把这句话说出来，一定会加分:Java Consumer 是双线程的设计。一 个线程是用户主线程，负责获取消息;另一个线程是心跳线程，负责向 Kafka 汇报消费者 存活情况。将心跳单独放入专属的线程，能够有效地规避因消息处理速度慢而被视为下线 的“假死”情况。

单线程获取消息的设计能够避免阻塞式的消息获取方式。单线程轮询方式容易实现异步非阻塞式，这样便于将消费者扩展成支持实时流处理的操作算子。因为很多实时流处理操作算子都不能是阻塞式的。另外一个可能的好处是，可以简化代码的开发。多线程交互的代码是非常容易出错的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Controller 发生网络分区(Network Partitioning)时，Kafka 会怎么样?
这道题目能够诱发我们对分布式系统设计、CAP 理论、一致性等多方面的思考。不过，针 对故障定位和分析的这类问题，我建议你首先言明“实用至上”的观点，即不论怎么进行理论分析，永远都要以实际结果为准。一旦发生 Controller 网络分区，那么，第一要务就是 查看集群是否出现“脑裂”，即同时出现两个甚至是多个 Controller 组件。这可以根据 Broker 端监控指标 ActiveControllerCount 来判断。

现在，我们分析下，一旦出现这种情况，Kafka 会怎么样。

由于 Controller 会给 Broker 发送 3 类请求，即LeaderAndIsrRequest、 StopReplicaRequest 和 UpdateMetadataRequest，因此，一旦出现网络分区，这些请求将不能顺利到达 Broker 端。这将影响主题的创建、修改、删除操作的信息同步，表现为 集群仿佛僵住了一样，无法感知到后面的所有操作。因此，网络分区通常都是非常严重的问 题，要赶快修复。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何调优 Kafka?
回答任何调优问题的第一步，就是确定优化目标，并且定量给出目标!这点特别重要。对于 Kafka 而言，常见的优化目标是吞吐量、延时、持久性和可用性。每一个方向的优化思路都 是不同的，甚至是相反的。

确定了目标之后，还要明确优化的维度。有些调优属于通用的优化思路，比如对操作系统、 JVM 等的优化;有些则是有针对性的，比如要优化 Kafka 的 TPS。我们需要从 3 个方向去考虑

* Producer 端:增加 batch.size、linger.ms，启用压缩，关闭重试等。
* Broker 端:增加 num.replica.fetchers，提升 Follower 同步 TPS，避免 Broker Full GC 等。
* Consumer:增加 fetch.min.bytes 等

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Kafka 的哪些场景中使用了零拷贝(Zero Copy)?
Zero Copy 是特别容易被问到的高阶题目。在 Kafka 中，体现 Zero Copy 使用场景的地方有两处:基于 mmap 的索引和日志文件读写所用的 TransportLayer。

先说第一个。索引都是基于 MappedByteBuffer 的，也就是让用户态和内核态共享内核态 的数据缓冲区，此时，数据不需要复制到用户态空间。不过，mmap 虽然避免了不必要的 拷贝，但不一定就能保证很高的性能。在不同的操作系统下，mmap 的创建和销毁成本可 能是不一样的。很高的创建和销毁开销会抵消 Zero Copy 带来的性能优势。由于这种不确 定性，在 Kafka 中，只有索引应用了 mmap，最核心的日志并未使用 mmap 机制。

再说第二个。TransportLayer 是 Kafka 传输层的接口。它的某个实现类使用了 FileChannel 的 transferTo 方法。该方法底层使用 sendfile 实现了 Zero Copy。对 Kafka 而言，如果 I/O 通道使用普通的 PLAINTEXT，那么，Kafka 就可以利用 Zero Copy 特 性，直接将页缓存中的数据发送到网卡的 Buffer 中，避免中间的多次拷贝。相反，如果 I/O 通道启用了 SSL，那么，Kafka 便无法利用 Zero Copy 特性了。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 分区 Leader 选举策略有几种?
分区的 Leader 副本选举对用户是完全透明的，它是由 Controller 独立完成的。你需要回答的是，在哪些场景下，需要执行分区 Leader 选举。每一种场景对应于一种选举策略。当前，Kafka 有 4 种分区 Leader 选举策略。

* OfflinePartition Leader 选举：每当有分区上线时，就需要执行 Leader 选举。所谓的分区上线，可能是创建了新分区，也可能是之前的下线分区重新上线。这是最常见的分区 Leader 选举场景。

* ReassignPartition Leader 选举：当你手动运行 kafka-reassign-partitions 命令，或者是调用 Admin 的 alterPartitionReassignments 方法执行分区副本重分配时，可能触发此类选举。假设原来的 AR 是[1，2，3]，Leader 是 1，当执行副本重分配后，副本集 合 AR 被设置成[4，5，6]，显然，Leader 必须要变更，此时会发生 Reassign Partition Leader 选举。

* PreferredReplicaPartition Leader 选举：当你手动运行 kafka-preferred-replica- election 命令，或自动触发了 Preferred Leader 选举时，该类策略被激活。所谓的 Preferred Leader，指的是 AR 中的第一个副本。比如 AR 是[3，2，1]，那么， Preferred Leader 就是 3。

* ControlledShutdownPartition Leader 选举：当 Broker 正常关闭时，该 Broker 上 的所有 Leader 副本都会下线，因此，需要为受影响的分区执行相应的 Leader 选举。

这 4 类选举策略的大致思想是类似的，即从 AR 中挑选首个在 ISR 中的副本，作为新 Leader。当然，个别策略有些微小差异。不过，回答到这种程度，应该足以应付面试官 了。毕竟，微小差别对选举 Leader 这件事的影响很小。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## consumer_offsets 是做什么用的?
这是一个内部主题，公开的官网资料很少涉及到。因此，我认为，此题属于面试官炫技一类 的题目。你要小心这里的考点:该主题有 3 个重要的知识点，你一定要全部答出来，才会显得对这块知识非常熟悉。

它是一个内部主题，无需手动干预，由 Kafka 自行管理。当然，我们可以创建该主题。

它的主要作用是负责注册消费者以及保存位移值。可能你对保存位移值的功能很熟悉， 但其实该主题也是保存消费者元数据的地方。千万记得把这一点也回答上。另外，这里 的消费者泛指消费者组和独立消费者，而不仅仅是消费者组。

Kafka 的 GroupCoordinator 组件提供对该主题完整的管理功能，包括该主题的创建、 写入、读取和 Leader 维护等。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Kafka 能手动删除消息吗?
其实，Kafka 不需要用户手动删除消息。它本身提供了留存策略，能够自动删除过期消息。 当然，它是支持手动删除消息的。因此，你最好从这两个维度去回答。

对于设置了 Key 且参数 cleanup.policy=compact 的主题而言，我们可以构造一条 <Key，null> 的消息发送给 Broker，依靠 Log Cleaner 组件提供的功能删除掉该 Key 的消息。
对于普通主题而言，我们可以使用 kafka-delete-records 命令，或编写程序调用 Admin.deleteRecords 方法来删除消息。这两种方法殊途同归，底层都是调用 Admin 的 deleteRecords 方法，通过将分区 Log Start Offset 值抬高的方式间接删除消息。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## LEO、LSO、AR、ISR、HW 都表示什么含义?* LEO:Log End Offset。日志末端位移值或末端偏移量，表示日志下一条待插入消息的 位移值。举个例子，如果日志有 10 条消息，位移值从 0 开始，那么，第 10 条消息的位移值就是 9。此时，LEO = 10。
* LSO:Log Stable Offset。这是 Kafka 事务的概念。如果你没有使用到事务，那么这个值不存在(其实也不是不存在，只是设置成一个无意义的值)。该值控制了事务型消费者能够看到的消息范围。它经常与 Log Start Offset，即日志起始位移值相混淆，因为 有些人将后者缩写成 LSO，这是不对的。在 Kafka 中，LSO 就是指代 Log Stable Offset。
* AR:Assigned Replicas。AR 是主题被创建后，分区创建时被分配的副本集合，副本个数由副本因子决定。
* ISR:In-Sync Replicas。Kafka 中特别重要的概念，指代的是 AR 中那些与 Leader 保持同步的副本集合。在 AR 中的副本可能不在 ISR 中，但 Leader 副本天然就包含在 ISR 中。关于 ISR，还有一个常见的面试题目是如何判断副本是否应该属于 ISR。目前的判断依据是:Follower 副本的 LEO 落后 Leader LEO 的时间，是否超过了 Broker 端参数 replica.lag.time.max.ms 值。如果超过了，副本就会被从 ISR 中移除。
* HW:高水位值(High watermark)。这是控制消费者可读取消息范围的重要字段。一个普通消费者只能“看到”Leader 副本上介于 Log Start Offset 和 HW(不含)之间的所有消息。水位以上的消息是对消费者不可见的。
*** 
## ⭐️⭐️⭐️⭐️⭐️
## Leader 总是 -1，怎么办?
在生产环境中，你一定碰到过“某个主题分区不能工作了”的情形。使用命令行查看状态的 话，会发现 Leader 是 -1，于是，你使用各种命令都无济于事，最后只能用“重启大 法”。

但是，有没有什么办法，可以不重启集群，就能解决此事呢?这就是此题的由来。

我直接给答案:删除 ZooKeeper 节点 /controller，触发 Controller 重选举。 Controller 重选举能够为所有主题分区重刷分区状态，可以有效解决因不一致导致的 Leader 不可用问题。我几乎可以断定，当面试官问出此题时，要么就是他真的不知道怎么 解决在向你寻求答案，要么他就是在等你说出这个答案。所以，千万别一上来就说“来个重 启”之类的话。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何估算 Kafka 集群的机器数量?
这道题目考查的是机器数量和所用资源之间的关联关系。所谓资源，也就是 CPU、内存、磁盘和带宽。

通常来说，CPU 和内存资源的充足是比较容易保证的，因此，你需要从磁盘空间和带宽占用两个维度去评估机器数量。

在预估磁盘的占用时，你一定不要忘记计算副本同步的开销。如果一条消息占用 1KB 的磁 盘空间，那么，在有 3 个副本的主题中，你就需要 3KB 的总空间来保存这条消息。显式地 将这些考虑因素答出来，能够彰显你考虑问题的全面性，是一个难得的加分项。

对于评估带宽来说，常见的带宽有 1Gbps 和 10Gbps，但你要切记，这两个数字仅仅是最大值。因此，你最好和面试官确认一下给定的带宽是多少。然后，明确阐述出当带宽占用接 近总带宽的 90% 时，丢包情形就会发生。这样能显示出你的网络基本功。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Broker 的 Heap Size 如何设置？
如何设置 Heap Size 的问题，其实和 Kafka 关系不大，它是一类非常通用的面试题目。一 旦你应对不当，面试方向很有可能被引到 JVM 和 GC 上去，那样的话，你被问住的几率就 会增大。因此，我建议你简单地介绍一下 Heap Size 的设置方法，并把重点放在 Kafka Broker 堆大小设置的最佳实践上。

比如，你可以这样回复:任何 Java 进程 JVM 堆大小的设置都需要仔细地进行考量和测 试。一个常见的做法是，以默认的初始 JVM 堆大小运行程序，当系统达到稳定状态后，手动触发一次 Full GC，然后通过 JVM 工具查看 GC 后的存活对象大小。之后，将堆大小设 置成存活对象总大小的 1.5~2 倍。对于 Kafka 而言，这个方法也是适用的。不过，业界有 个最佳实践，那就是将 Broker 的 Heap Size 固定为 6GB。经过很多公司的验证，这个大 小是足够且良好的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 监控 Kafka 的框架都有哪些?
面试官其实是在 考察你对监控框架的了解广度，或者说，你是否知道很多能监控 Kafka 的框架或方法。下面这些就是 Kafka 发展历程上比较有名气的监控系统。

* Kafka Manager:应该算是最有名的专属 Kafka 监控框架了，是独立的监控系统。
* Kafka Monitor:LinkedIn 开源的免费框架，支持对集群进行系统测试，并实时监控测试结果。
* CruiseControl:也是 LinkedIn 公司开源的监控框架，用于实时监测资源使用率，以及 提供常用运维操作等。无 UI 界面，只提供 REST API。
* JMX 监控:由于 Kafka 提供的监控指标都是基于 JMX 的，因此，市面上任何能够集成 JMX 的框架都可以使用，比如 Zabbix 和 Prometheus。
* 已有大数据平台自己的监控体系:像 Cloudera 提供的 CDH 这类大数据平台，天然就提 供 Kafka 监控方案。
* JMXTool:社区提供的命令行工具，能够实时监控 JMX 指标。答上这一条，属于绝对 的加分项，因为知道的人很少，而且会给人一种你对 Kafka 工具非常熟悉的感觉。如果 你暂时不了解它的用法，可以在命令行以无参数方式执行一下kafka-run-class.sh kafka.tools.JmxTool，学习下它的用法。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何设置 Kafka 能接收的最大消息的大小?
这道题除了要回答消费者端的参数设置之外，一定要加上 Broker 端的设置，这样才算完整。毕竟，如果 Producer 都不能向 Broker 端发送数据很大的消息，又何来消费一说呢? 因此，你需要同时设置 Broker 端参数和 Consumer 端参数。

Broker 端参数:message.max.bytes、max.message.bytes(主题级别)和 replica.fetch.max.bytes。
Consumer 端参数:fetch.message.max.bytes。
Broker 端的最后一个参数比较容易遗漏。我们必须调整 Follower 副本能够接收的最大消 息的大小，否则，副本同步就会失败。因此，把这个答出来的话，就是一个加分项。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 阐述下 Kafka 中的领导者副本(Leader Replica)和追随者副本 (Follower Replica)的区别。
这道题表面上是考核你对 Leader 和 Follower 区别的理解，但很容易引申到 Kafka 的同步 机制上。因此，我建议你主动出击，一次性地把隐含的考点也答出来，也许能够暂时把面试 官“唬住”，并体现你的专业性。

你可以这么回答:Kafka 副本当前分为领导者副本和追随者副本。只有 Leader 副本才能对外提供读写服务，响应 Clients 端的请求。Follower 副本只是采用拉(PULL)的方式，被动地同步 Leader 副本中的数据，并且在 Leader 副本所在的 Broker 宕机后，随时 准备应聘 Leader 副本。

通常来说，回答到这个程度，其实才只说了 60%，因此，我建议你再回答两个额外的加分 项。

强调 Follower 副本也能对外提供读服务。自 Kafka 2.4 版本开始，社区通过引入新的 Broker 端参数，允许 Follower 副本有限度地提供读服务。

强调 Leader 和 Follower 的消息序列在实际场景中不一致。很多原因都可能造成 Leader 和 Follower 保存的消息序列不一致，比如程序 Bug、网络问题等。这是很严重的错误，必须要完全规避。你可以补充下，之前确保一致性的主要手段是高水位机制， 但高水位值无法保证 Leader 连续变更场景下的数据一致性，因此，社区引入了 Leader Epoch 机制，来修复高水位值的弊端。关于“Leader Epoch 机制”，国内的资料不是 很多，它的普及度远不如高水位，不妨大胆地把这个概念秀出来，力求惊艳一把。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 解释下 Kafka 中位移(offset)的作用。
在 Kafka 中，每个 主题分区下的每条消息都被赋予了一个唯一的 ID 数值，用于标识它在分区中的位置。这个 ID 数值，就被称为位移，或者叫偏移量。一旦消息被写入到分区日志，它的位移值将不能 被修改。

答完这些之后，你还可以把整个面试方向转移到你希望的地方。常见方法有以下 3 种:
* 如果你深谙 Broker 底层日志写入的逻辑，可以强调下消息在日志中的存放格式;
* 如果你明白位移值一旦被确定不能修改，可以强调下“Log Cleaner 组件都不能影响位 移值”这件事情;
* 如果你对消费者的概念还算熟悉，可以再详细说说位移值和消费者位移值之间的区别。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是消费者组?
消费者组是 Kafka 独有的概念，如果面试官问这 个，就说明他对此是有一定了解的。我先给出标准答案：
* 1、定义：即消费者组是 Kafka 提供的可扩展且具有容错性的消费者机制。
* 2、原理：在 Kafka 中，消费者组是一个由多个消费者实例 构成的组。多个实例共同订阅若干个主题，实现共同消费。同一个组下的每个实例都配置有 相同的组 ID，被分配不同的订阅分区。当某个实例挂掉的时候，其他实例会自动地承担起 它负责消费的分区。

此时，又有一个小技巧给到你:消费者组的题目，能够帮你在某种程度上掌控下面的面试方向。

* 如果你擅长位移值原理，就不妨再提一下消费者组的位移提交机制;
* 如果你擅长 Kafka Broker，可以提一下消费者组与 Broker 之间的交互;
* 如果你擅长与消费者组完全不相关的 Producer，那么就可以这么说:“消费者组要消 费的数据完全来自于 Producer 端生产的消息，我对 Producer 还是比较熟悉的。”

*** 
## ⭐️⭐️⭐️⭐️⭐️
## kafka如何实现延迟队列？
Kafka并没有使用JDK自带的Timer或者DelayQueue来实现延迟的功能，而是基于时间轮自定义了一个用于实现延迟功能的定时器（SystemTimer）。JDK的Timer和DelayQueue插入和删除操作的平均时间复杂度为O(nlog(n))，并不能满足Kafka的高性能要求，而基于时间轮可以将插入和删除操作的时间复杂度都降为O(1)。时间轮的应用并非Kafka独有，其应用场景还有很多，在Netty、Akka、Quartz、Zookeeper等组件中都存在时间轮的踪影。

底层使用数组实现，数组中的每个元素可以存放一个TimerTaskList对象。TimerTaskList是一个环形双向链表，在其中的链表项TimerTaskEntry中封装了真正的定时任务TimerTask.

Kafka中到底是怎么推进时间的呢？Kafka中的定时器借助了JDK中的DelayQueue来协助推进时间轮。具体做法是对于每个使用到的TimerTaskList都会加入到DelayQueue中。Kafka中的TimingWheel专门用来执行插入和删除TimerTaskEntry的操作，而DelayQueue专门负责时间推进的任务。再试想一下，DelayQueue中的第一个超时任务列表的expiration为200ms，第二个超时任务为840ms，这里获取DelayQueue的队头只需要O(1)的时间复杂度。如果采用每秒定时推进，那么获取到第一个超时的任务列表时执行的200次推进中有199次属于“空推进”，而获取到第二个超时任务时有需要执行639次“空推进”，这样会无故空耗机器的性能资源，这里采用DelayQueue来辅助以少量空间换时间，从而做到了“精准推进”。Kafka中的定时器真可谓是“知人善用”，用TimingWheel做最擅长的任务添加和删除操作，而用DelayQueue做最擅长的时间推进工作，相辅相成。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Kafka中是怎么体现消息顺序性的？
kafka每个partition中的消息在写入时都是有序的，消费时，每个partition只能被每一个group中的一个消费者消费，保证了消费时也是有序的。

整个topic不保证有序。如果为了保证topic整个有序，那么将partition调整为1。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么Kafka不支持读写分离？
在 Kafka 中，生产者写入消息、消费者读取消息的操作都是与 leader 副本进行交互的，从 而实现的是一种主写主读的生产消费模型。

Kafka 并不支持主写从读，因为主写从读有 2 个很明 显的缺点:

(1)数据一致性问题。数据从主节点转到从节点必然会有一个延时的时间窗口，这个时间 窗口会导致主从节点之间的数据不一致。某一时刻，在主节点和从节点中 A 数据的值都为 X， 之后将主节点中 A 的值修改为 Y，那么在这个变更通知到从节点之前，应用读取从节点中的 A 数据的值并不为最新的 Y，由此便产生了数据不一致的问题。

(2)延时问题。类似 Redis 这种组件，数据从写入主节点到同步至从节点中的过程需要经 历网络→主节点内存→网络→从节点内存这几个阶段，整个过程会耗费一定的时间。而在 Kafka 中，主从同步会比 Redis 更加耗时，它需要经历网络→主节点内存→主节点磁盘→网络→从节 点内存→从节点磁盘这几个阶段。对延时敏感的应用而言，主写从读的功能并不太适用。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Kafka中的消息是否会丢失和重复消费？
要确定Kafka的消息是否丢失或重复，从两个方面分析入手：消息发送和消息消费。

1）消息发送
Kafka消息发送有两种方式：同步（sync）和异步（async），默认是同步方式，可通过producer.type属性进行配置。Kafka通过配置request.required.acks属性来确认消息的生产：

* 0---表示不进行消息接收是否成功的确认；
* 1---表示当Leader接收成功时确认；
* -1---表示Leader和Follower都接收成功时确认；

综上所述，有6种消息生产的情况，下面分情况来分析消息丢失的场景：

（1）acks=0，不和Kafka集群进行消息接收确认，则当网络异常、缓冲区满了等情况时，消息可能丢失；

（2）acks=1、同步模式下，只有Leader确认接收成功后但挂掉了，副本没有同步，数据可能丢失；

2）消息消费

Kafka消息消费有两个consumer接口，Low-level API和High-level API：

* Low-level API：消费者自己维护offset等值，可以实现对Kafka的完全控制；

* High-level API：封装了对parition和offset的管理，使用简单；

如果使用高级接口High-level API，可能存在一个问题就是当消息消费者从集群中把消息取出来、并提交了新的消息offset值后，还没来得及消费就挂掉了，那么下次再消费时之前没消费成功的消息就“诡异”的消失了；

3）解决办法

* 针对消息丢失：同步模式下，确认机制设置为-1，即让消息写入Leader和Follower之后再确认消息发送成功；异步模式下，为防止缓冲区满，可以在配置文件设置不限制阻塞超时时间，当缓冲区满时让生产者一直处于阻塞状态；
* 针对消息重复：将消息的唯一标识保存到外部介质中，每次消费时判断是否处理过即可。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## kafka中consumer group 是什么概念？
同样是逻辑上的概念，是Kafka实现单播和广播两种消息模型的手段。

同一个topic的数据，会广播给不同的group；同一个group中的worker，只有一个worker能拿到这个数据。

换句话说，对于同一个topic，每个group都可以拿到同样的所有数据，但是数据进入group后只能被其中的一个worker消费。group内的worker可以使用多线程或多进程来实现，也可以将进程分散在多台机器上，worker的数量通常不超过partition的数量，且二者最好保持整数倍关系，因为Kafka在设计时假定了一个partition只能被一个worker消费（同一group内）。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## kafka的message格式是什么样的？一个Kafka的Message由一个固定长度的header和一个变长的消息体body组成。

* header部分由一个字节的magic(文件格式)和四个字节的CRC32(用于判断body消息体是否正常)构成。
当magic的值为1的时候，会在magic和crc32之间多一个字节的数据：attributes(保存一些相关属性，比如是否压缩、压缩格式等等)；如果magic的值为0，那么不存在attributes属性。

* body是由N个字节构成的一个消息体，包含了具体的key/value消息。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如果leader crash时，ISR为空怎么办？kafka在Broker端提供了一个配置参数：unclean.leader.election,这个参数有两个值：
* true（默认）：允许不同步副本成为leader，由于不同步副本的消息较为滞后，此时成为leader，可能会出现消息不一致的情况。
* false：不允许不同步副本成为leader，此时如果发生ISR列表为空，会一直等待旧leader恢复，降低了可用性。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## kafka  unclean 配置代表啥？会对 spark streaming 消费有什么影响？unclean.leader.election.enable 为true的话，意味着非ISR集合的broker 也可以参与选举，这样有可能就会丢数据，spark streaming在消费过程中拿到的 end offset 会突然变小，导致 spark streaming job挂掉。如果unclean.leader.election.enable参数设置为true，就有可能发生数据丢失和数据不一致的情况，Kafka的可靠性就会降低；而如果unclean.leader.election.enable参数设置为false，Kafka的可用性就会降低。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## kafka producer 打数据，ack  为 0， 1， -1 的时候代表啥， 设置 -1 的时候，什么情况下，leader 会认为一条消息 commit 了1（默认）：数据发送到Kafka后，经过leader成功接收消息的的确认，就算是发送成功了。在这种情况下，如果leader宕机了，则会丢失数据。

0：生产者将数据发送出去就不管了，不去等待任何返回。这种情况下数据传输效率最高，但是数据可靠性确是最低的。

-1：producer需要等待ISR中的所有follower都确认接收到数据后才算一次发送完成，可靠性最高。当ISR中所有Replica都向Leader发送ACK时，leader才commit，这时候producer才能认为一个请求中的消息都commit了。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## kafka producer如何优化打入速度？* 增加线程
* 提高 batch.size
* 增加更多 producer 实例
* 增加 partition 数
* 设置 acks=-1 时，如果延迟增大：可以增大 num.replica.fetchers（follower 同步数据的线程数）来调解；
* 跨数据中心的传输：增加 socket 缓冲区设置以及 OS tcp 缓冲区设置。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## kafka 为什么那么快？Kafka的消息是保存或缓存在磁盘上的，一般认为在磁盘上读写数据是会降低性能的，因为寻址会比较消耗时间，但是实际上，Kafka的特性之一就是高吞吐率。

即使是普通的服务器，Kafka也可以轻松支持每秒百万级的写入请求，超过了大部分的消息中间件，这种特性也使得Kafka在日志处理等海量数据场景广泛应用。

针对Kafka的基准测试可以参考，Apache Kafka基准测试：每秒写入2百万（在三台廉价机器上）

**下面从数据写入和读取两方面分析，为什么Kafka速度这么快。**

  一、写入数据

Kafka会把收到的消息都写入到硬盘中，它绝对不会丢失数据。为了优化写入速度Kafka采用了两个技术， 顺序写入和MMFile 。

 1、顺序写入

磁盘读写的快慢取决于你怎么使用它，也就是顺序读写或者随机读写。在顺序读写的情况下，磁盘的顺序读写速度和内存持平。

因为硬盘是机械结构，每次读写都会寻址->写入，其中寻址是一个“机械动作”，它是最耗时的。所以硬盘最讨厌随机I/O，最喜欢顺序I/O。为了提高读写硬盘的速度，Kafka就是使用顺序I/O。

而且Linux对于磁盘的读写优化也比较多，包括read-ahead和write-behind，磁盘缓存等。如果在内存做这些操作的时候，一个是JAVA对象的内存开销很大，另一个是随着堆内存数据的增多，JAVA的GC时间会变得很长，使用磁盘操作有以下几个好处：

1、顺序写入磁盘顺序读写速度超过内存随机读写

2、顺序写入JVM的GC效率低，内存占用大。使用磁盘可以避免这一问题

3、顺序写入系统冷启动后，磁盘缓存依然可用

下图就展示了Kafka是如何写入数据的， 每一个Partition其实都是一个文件 ，收到消息后Kafka会把数据插入到文件末尾（虚框部分）：

![640?wx_fmt=png](https://img-blog.csdnimg.cn/img_convert/6697d21d1de35528a43909743a96162c.png)

这种方法有一个缺陷——没有办法删除数据 ，所以Kafka是不会删除数据的，它会把所有的数据都保留下来，每个消费者（Consumer）对每个Topic都有一个offset用来表示读取到了第几条数据 。

![640?wx_fmt=png](https://img-blog.csdnimg.cn/img_convert/1feb716b413929c219eea4c86297de35.png)

两个消费者：

1、顺序写入Consumer1有两个offset分别对应Partition0、Partition1（假设每一个Topic一个Partition）；

2、顺序写入Consumer2有一个offset对应Partition2。

这个offset是由客户端SDK负责保存的，Kafka的Broker完全无视这个东西的存在；一般情况下SDK会把它保存到Zookeeper里面，所以需要给Consumer提供zookeeper的地址。

**如果不删除硬盘肯定会被撑满，所以Kakfa提供了两种策略来删除数据：**

1、顺序写入一是基于时间。

2、顺序写入二是基于partition文件大小。

具体配置可以参看它的配置文档

 2、Memory Mapped Files

即便是顺序写入硬盘，硬盘的访问速度还是不可能追上内存。所以Kafka的数据并不是实时的写入硬盘 ，它充分利用了现代操作系统分页存储来利用内存提高I/O效率。

Memory Mapped Files(后面简称mmap)也被翻译成 内存映射文件 ，在64位操作系统中一般可以表示20G的数据文件，它的工作原理是直接利用操作系统的Page来实现文件到物理内存的直接映射。

完成映射之后你对物理内存的操作会被同步到硬盘上（操作系统在适当的时候）。

通过mmap，进程像读写硬盘一样读写内存（当然是虚拟机内存），也不必关心内存的大小有虚拟内存为我们兜底。

使用这种方式可以获取很大的I/O提升，省去了用户空间到内核空间复制的开销（调用文件的read会把数据先放到内核空间的内存中，然后再复制到用户空间的内存中。）

但也有一个很明显的缺陷——不可靠，写到mmap中的数据并没有被真正的写到硬盘，操作系统会在程序主动调用flush的时候才把数据真正的写到硬盘。

Kafka提供了一个参数——producer.type来控制是不是主动flush，如果Kafka写入到mmap之后就立即flush然后再返回Producer叫 同步 (sync)；写入mmap之后立即返回Producer不调用flush叫异步 (async)。

 二、读取数据

Kafka在读取磁盘时做了哪些优化？

 2、基于sendfile实现Zero Copy

传统模式下，当需要对一个文件进行传输的时候，其具体流程细节如下：

1、基于sendfile实现Zero Copy调用read函数，文件数据被copy到内核缓冲区

2、read函数返回，文件数据从内核缓冲区copy到用户缓冲区

3、write函数调用，将文件数据从用户缓冲区copy到内核与socket相关的缓冲区。

4、数据从socket缓冲区copy到相关协议引擎。

以上细节是传统read/write方式进行网络文件传输的方式，我们可以看到，在这个过程当中，文件数据实际上是经过了四次copy操作：

硬盘—>内核buf—>用户buf—>socket相关缓冲区—>协议引擎

而sendfile系统调用则提供了一种减少以上多次copy，提升文件传输性能的方法。

在内核版本2.1中，引入了sendfile系统调用，以简化网络上和两个本地文件之间的数据传输。sendfile的引入不仅减少了数据复制，还减少了上下文切换。

sendfile(socket, file, len);

运行流程如下：

1、sendfile系统调用，文件数据被copy至内核缓冲区

2、再从内核缓冲区copy至内核中socket相关的缓冲区

3、最后再socket相关的缓冲区copy到协议引擎

相较传统read/write方式，2.1版本内核引进的sendfile已经减少了内核缓冲区到user缓冲区，再由user缓冲区到socket相关缓冲区的文件copy，而在内核版本2.4之后，文件描述符结果被改变，sendfile实现了更简单的方式，再次减少了一次copy操作。

在Apache、Nginx、lighttpd等web服务器当中，都有一项sendfile相关的配置，使用sendfile可以大幅提升文件传输性能。

Kafka把所有的消息都存放在一个一个的文件中，当消费者需要数据的时候Kafka直接把文件发送给消费者，配合mmap作为文件读写方式，直接把它传给sendfile。

 2、批量压缩

在很多情况下，系统的瓶颈不是CPU或磁盘，而是网络IO，对于需要在广域网上的数据中心之间发送消息的数据流水线尤其如此。进行数据压缩会消耗少量的CPU资源,不过对于kafka而言,网络IO更应该需要考虑。

1、如果每个消息都压缩，但是压缩率相对很低，所以Kafka使用了批量压缩，即将多个消息一起压缩而不是单个消息压缩

2、Kafka允许使用递归的消息集合，批量的消息可以通过压缩的形式传输并且在日志中也可以保持压缩格式，直到被消费者解压缩

3、Kafka支持多种压缩协议，包括Gzip和Snappy压缩协议

 三、总结

Kafka速度的秘诀在于，它把所有的消息都变成一个批量的文件，并且进行合理的批量压缩，减少网络IO损耗，通过mmap提高I/O速度，写入数据的时候由于单个Partion是末尾添加所以速度最优；读取数据的时候配合sendfile直接暴力输出。
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么情况下一个 broker 会从 ISR 中被踢出去？leader会维护一个与其基本保持同步的Replica列表，该列表称为ISR(in-sync Replica)，每个Partition都会有一个ISR，而且是由leader动态维护 ，如果一个follower比一个leader落后太多，或者超过一定时间未发起数据复制请求，则leader将其重ISR中移除 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## kafka follower如何与leader同步数据？Kafka的复制机制既不是完全的同步复制，也不是单纯的异步复制。

完全同步复制要求All Alive Follower都复制完，这条消息才会被认为commit，这种复制方式极大的影响了吞吐率。而异步复制方式下，Follower异步的从Leader复制数据，数据只要被Leader写入log就被认为已经commit，这种情况下，如果leader挂掉，会丢失数据，kafka使用ISR的方式很好的均衡了确保数据不丢失以及吞吐率。

Follower可以批量的从Leader复制数据，而且Leader充分利用磁盘顺序读以及send file(zero copy)机制，这样极大的提高复制性能，内部批量写磁盘，大幅减少了Follower与Leader的消息量差。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## kafka中的 zookeeper 起到什么作用？可以不用zookeeper么？zookeeper 是一个分布式的协调组件，早期版本的kafka用zk做meta信息存储，consumer的消费状态，group的管理以及 offset的值。

考虑到zk本身的一些因素以及整个架构较大概率存在单点问题，新版本中逐渐弱化了zookeeper的作用。

新的consumer使用了kafka内部的group coordination协议，也减少了对zookeeper的依赖，但是broker依然依赖于ZK，zookeeper 在kafka中还用来选举controller 和 检测broker是否存活等等。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## kafka中的broker 是干什么的？
broker 是消息的代理，Producers往Brokers里面的指定Topic中写消息，Consumers从Brokers里面拉取指定Topic的消息，然后进行业务处理，broker在中间起到一个代理保存消息的中转站。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Kafka中的ISR、AR又代表什么？ISR的伸缩又指什么？
* ISR:In-Sync Replicas 副本同步队列
* AR:Assigned Replicas 所有副本

ISR是由leader维护，follower从leader同步数据有一些延迟（包括延迟时间replica.lag.time.max.ms和延迟条数replica.lag.max.messages两个维度, 当前最新的版本0.10.x中只支持replica.lag.time.max.ms这个维度），任意一个超过阈值都会把follower剔除出ISR, 存入OSR（Outof-Sync Replicas）列表，新加入的follower也会先存放在OSR中。AR=ISR+OSR。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么要使用 kafka？为什么要使用消息队列？
* 缓冲和削峰：上游数据时有突发流量，下游可能扛不住，或者下游没有足够多的机器来保证冗余，kafka在中间可以起到一个缓冲的作用，把消息暂存在kafka中，下游服务就可以按照自己的节奏进行慢慢处理。
* 解耦和扩展性：项目开始的时候，并不能确定具体需求。消息队列可以作为一个接口层，解耦重要的业务流程。只需要遵守约定，针对数据编程即可获取扩展能力。
* 冗余：可以采用一对多的方式，一个生产者发布消息，可以被多个订阅topic的服务消费到，供多个毫无关联的业务使用。
* 健壮性：消息队列可以堆积请求，所以消费端业务即使短时间死掉，也不会影响主要业务的正常进行。
* 异步通信：很多时候，用户不想也不需要立即处理消息。消息队列提供了异步处理机制，允许用户把一个消息放入队列，但并不立即处理它。想向队列中放入多少消息就放多少，然后在需要的时候再去处理它们。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是jenkinsfile?为什么使用jenkinsfile
Jenkinsfile是一个文本文件，其中包含Jenkins Pipeline的定义，并已签入源代码管理

虽然用于定义管道的脚本语法和jenkinsfile类似，但通常认为在项目中定义管道Jenkinsfile并检查源代码管理是最佳实践。

* 为所有分支和请求自动创建一个管道构建过程。
* 管道上的代码审查/迭代。
* 审核追踪管道

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何通过Jenkins克隆Git存储库？
如果要通过Jenkins克隆Git存储库, 则必须输入Jenkins系统的电子邮件和用户名。切换到作业目录并为此执行” git config”命令。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何在Jenkins中创建备份和复制文件？
如果要创建Jenkins设置的备份, 只需复制将Jenkins的所有设置, 构建工件和日志保存在其主目录中的目录。你还可以复制作业目录以克隆或复制作业或重命名目录。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 可以使用哪些命令手动启动Jenkins？
你可以使用以下任何命令来手动启动Jenkins：

- (Jenkins_url)/ restart：强制重启, 而无需等待构建完成。
- (Jenkin_url)/ safeRestart：允许所有正在运行的构建完成。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Jenkins的优势是什么？
Jenkins的优势包括：

- 在开发环境的早期阶段, 错误跟踪很容易。
- 提供大量的插件支持。
- 对代码的迭代改进。
- 构建失败会在集成阶段进行缓存。
- 对于每个代码提交更改, 都会生成一个自动生成报告通知。
- 为了将构建报告的成功或失败通知开发人员, 它与LDAP邮件服务器集成在一起。
- 实现持续集成的敏捷开发和测试驱动的开发。
- 通过简单的步骤, 即可自动完成maven发布项目。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在Jenkins中, 什么是持续集成？
在软件开发中, 多个开发人员或团队在同一个Web应用程序的不同部分上工作, 因此你必须通过集成所有模块来执行集成测试。为了做到这一点, 每天都要对每段代码进行自动化处理, 以便对所有代码进行测试。此过程称为连续集成。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Jenkins支持哪些SCM工具？
Jenkins支持以下SCM工具：

- AccuRev
- CVS
- 颠覆
- 去
- 水星
- Perforce
- 明箱
- 实时时钟

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Maven, Ant和Jenkins有什么区别？
最基本的区别是：

Maven和Ant是Build Technologies, 而Jenkins是持续集成工具。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Jenkins？
Jenkins是一个用Java编写的开源持续集成工具。它跟踪版本控制系统, 并在发生更改时启动和监视构建系统。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 缓冲区是什么意思？
- Buffer 是一个对象， 它包含一些要写入或者刚读出的数据。在 NIO 中加入 Buffer 对象，体现了新库与原 I/O 的一个重要区别。在面向流的 I/O 中，您将数据直接写入或者将数据直接读到 Stream 对象中
- 在 NIO 库中，所有数据都是用缓冲区处理的。在读取数据时，它是直接读到缓冲区中的。在写入数据时，它是写入到缓冲区中的。任何时候访问 NIO 中的数据，您都是将它放到缓冲区中。
- 缓冲区实质上是一个数组。通常它是一个字节数组，但是也可以使用其他种类的数组。但是一个缓冲区不 仅仅 是一个数组。缓冲区提供了对数据的结构化访问，而且还可以跟踪系统的读/写进程

* ByteBuffer
* CharBuffer
* ShortBuffer
* IntBuffer
* LongBuffer
* FloatBuffer
* DoubleBuffer

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 通道是什么？
- 通道是对原 I/O 包中的流的模拟。到任何目的地(或来自任何地方)的所有数据都必须通过一个 Channel 对象（通道）。一个 Buffer 实质上是一个容器对象。发送给一个通道的所有对象都必须首先放到缓冲区中；同样地，从通道中读取的任何数据都要读到缓冲区中。Channel是一个对象，可以通过它读取和写入数据。拿 NIO 与原来的 I/O 做个比较，通道就像是流。
- 正如前面提到的，所有数据都通过 Buffer 对象来处理。您永远不会将字节直接写入通道中，相反，您是将数据写入包含一个或者多个字节的缓冲区。同样，您不会直接从通道中读取字节，而是将数据从通道读入缓冲区，再从缓冲区获取这个字节。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 同步、异步、阻塞、非堵塞的组合有哪些？
同/异、阻/非堵塞的组合，有四种类型，如下表：

| 组合方式   | 性能分析                                                     |
| ---------- | ------------------------------------------------------------ |
| 同步阻塞   | 最常用的一种用法，使用也是最简单的，但是 I/O 性能一般很差，CPU 大部分在空闲状态。 |
| 同步非阻塞 | 提升 I/O 性能的常用手段，就是将 I/O 的阻塞改成非阻塞方式，尤其在网络 I/O 是长连接，同时传输数据也不是很多的情况下，提升性能非常有效。 这种方式通常能提升 I/O 性能，但是会增加CPU 消耗，要考虑增加的 I/O 性能能不能补偿 CPU 的消耗，也就是系统的瓶颈是在 I/O 还是在 CPU 上。 |
| 异步阻塞   | 这种方式在分布式数据库中经常用到，例如在网一个分布式数据库中写一条记录，通常会有一份是同步阻塞的记录，而还有两至三份是备份记录会写到其它机器上，这些备份记录通常都是采用异步阻塞的方式写 I/O。异步阻塞对网络 I/O 能够提升效率，尤其像上面这种同时写多份相同数据的情况。 |
| 异步非阻塞 | 这种组合方式用起来比较复杂，只有在一些非常复杂的分布式情况下使用，像集群之间的消息同步机制一般用这种 I/O 组合方式。如 Cassandra 的 Gossip 通信机制就是采用异步非阻塞的方式。它适合同时要传多份相同的数据到集群中不同的机器，同时数据的传输量虽然不大，但是却非常频繁。这种网络 I/O 用这个方式性能能达到最高。 |

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 阻塞与非阻塞
阻塞与非阻塞主要是从 CPU 的消耗上来说的，阻塞就是 CPU 停下来等待一个慢的操作完成 CPU 才接着完成其它的事。非阻塞就是在这个慢的操作在执行时 CPU 去干其它别的事，等这个慢的操作完成时，CPU 再接着完成后续的操作。

虽然表面上看非阻塞的方式可以明显的提高 CPU 的利用率，但是也带了另外一种后果就是系统的线程切换增加。增加的 CPU 使用时间能不能补偿系统的切换成本需要好好评估。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 同步与异步
同步就是一个任务的完成需要依赖另外一个任务时，只有等待被依赖的任务完成后，依赖的任务才能算完成，这是一种可靠的任务序列。要么成功都成功，失败都失败，两个任务的状态可以保持一致。

而异步是不需要等待被依赖的任务完成，只是通知被依赖的任务要完成什么工作，依赖的任务也立即执行，只要自己完成了整个任务就算完成了。至于被依赖的任务最终是否真正完成，依赖它的任务无法确定，所以它是不可靠的任务序列。我们可以用打电话和发短信来很好的比喻同步与异步操作。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是AIO
AIO 是 Java 1.7 之后引入的包，是 NIO 的升级版本，提供了异步非堵塞的 IO 操作方式，所以人们叫它 AIO（Asynchronous IO），异步 IO 是基于事件和回调机制实现的，也就是应用操作之后会直接返回，不会堵塞在那里，当后台处理完成，操作系统会通知相应的线程进行后续的操作

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是NIO
是 Java 1.4 引入的 java.nio 包，提供了 Channel、Selector、Buffer 等新的抽象，可以构建多路复用的、同步非阻塞 IO 程序，同时提供了更接近操作系统底层高性能的数据操作方式。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是BIO
BIO 就是传统的 [java.io](http://java.io/) 包，它是基于流模型实现的，交互的方式是同步、阻塞方式，也就是说在读入输入流或者输出流时，在读写动作完成之前，线程会一直阻塞在那里，它们之间的调用时可靠的线性顺序。它的有点就是代码比较简单、直观；缺点就是 IO 的效率和扩展性很低，容易成为应用性能瓶颈。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 流一般需要不需要关闭,如果关闭的话在用什么方法,一般要在那个代码块里面关闭比较好，处理流是怎么关闭的，如果有多个流互相调用传入是怎么关闭的？
1. 流一旦打开就必须关闭，使用close方法

2. 放入finally语句块中（finally 语句一定会执行）

3. 调用的处理流就关闭处理流

4. 多个流互相调用只关闭最外层的流

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是节点流,什么是处理流,它们各有什么用处,处理流的创建有什么特征？
1. 节点流 直接与数据源相连，用于输入或者输出

2. 处理流：在节点流的基础上对之进行加工，进行一些功能的扩展

3. 处理流的构造器必须要 传入节点流的子类

*** 
## ⭐️⭐️⭐️⭐️⭐️
## PrintStream、BufferedWriter、PrintWriter的比较?
1. PrintStream类的输出功能非常强大，通常如果需要输出文本内容，都应该将输出流包装成PrintStream后进行输出。它还提供其他两项功能。与其他输出流不同，PrintStream 永远不会抛出 IOException；而是，异常情况仅设置可通过 checkError 方法测试的内部标志。另外，为了自动刷新，可以创建一个 PrintStream

2. BufferedWriter:将文本写入字符输出流，缓冲各个字符从而提供单个字符，数组和字符串的高效写入。通过write()方法可以将获取到的字符输出，然后通过newLine()进行换行操作。BufferedWriter中的字符流必须通过调用flush方法才能将其刷出去。并且BufferedWriter只能对字符流进行操作。如果要对字节流操作，则使用BufferedInputStream

3. PrintWriter的println方法自动添加换行，不会抛异常，若关心异常，需要调用checkError方法看是否有异常发生，PrintWriter构造方法可指定参数，实现自动刷新缓存（autoflush）

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 字节流和字符流的区别？
字节流读取的时候，读到一个字节就返回一个字节；字符流使用了字节流读到一个或多个字节（中文对应的字节数是两个，在 UTF-8 码表中是 3 个字节）时。先去查指定的编码表，将查到的字符返回。

字节流可以处理所有类型数据，如：图片，MP3，AVI视频文件，而字符流只能处理字符数据。只要是处理纯文本数据，就要优先考虑使用字符流，除此之外都用字节流。

字节流主要是操作 byte 类型数据，以 byte 数组为准，主要操作类就是 OutputStream、InputStream字符流处理的单元为 2 个字节的 Unicode 字符，分别操作字符、字符数组或字符串，而字节流处理单元为 1 个字节，操作字节和字节数组。所以字符流是由 Java 虚拟机将字节转化为 2 个字节的 Unicode 字符为单位的字符而成的，所以它对多国语言支持性比较好！如果是音频文件、图片、歌曲，就用字节流好点，如果是关系到中文（文本）的，用字符流好点。在程序中一个字符等于两个字节，java 提供了 Reader、Writer 两个专门操作字符流的类。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何实现 java 序列化？
序列化的实现，将需要被序列化的类实现Serializable 接口，该接口没有需要实现的方法，implements Serializable 只是为了标注该对象是可被序列化的，然后使用一个输出流(如：File Output Stream)来构造一个 Object Output Stream(对象流)对象，接着，使用 Object Output Stream 对象的 write Object(Object obj)方法就可以将参数为 obj 的对象写出(即保存其状态)，要恢复的话则用输入流。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是 java序列化？
序列化就是一种用来处理对象流的机制，所谓对象流也就是将对象的内容进行流化。可以对流化后的对象进行读写操作，也可将流化后的对象传输于网络之间。序列化是为了解决在对对象流进行读写操作时所引发的问题

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java 中有几种类型的流？
（1）按照流的方向：输入流（inputStream）和输出流（outputStream）；

（2）按照实现功能分：节点流（可以从或向一个特定的地方（节点）读写数据。如 FileReader）和处理流（是对一个已存在的流的连接和封装，通过所封装的流的功能调用实现数据读写。如 BufferedReader。处理流的构造方法总是要带一个其他的流对象做参数。一个流对象经过其他流的多次包装，称为流的链接）；

（3）按照处理数据的单位： 字节流和字符流。字节流继承于 InputStream 和 OutputStrea，字符流继承于InputStreamReader 和 OutputStreamWriter 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Comparable和Comparator接口有何区别？
Comparable和Comparator接口被用来对对象集合或者数组进行排序。Comparable接口被用来提供对象的自然排序，我们可以使用它来提供基于单个逻辑的排序。

Comparator接口被用来提供不同的排序算法，我们可以选择需要使用的Comparator来对给定的对象集合进行排序。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## Collections类是什么？
Java.util.Collections是一个工具类仅包含静态方法，它们操作或返回集合。它包含操作集合的多态算法，返回一个由指定集合支持的新集合和其它一些内容。这个类包含集合框架算法的方法，比如折半搜索、排序、混编和逆序等。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 队列和栈是什么，列出它们的区别？
栈和队列两者都被用来预存储数据。java.util.Queue是一个接口，它的实现类在Java并发包中。队列允许先进先出（FIFO）检索元素，但并非总是这样。Deque接口允许从两端检索元素。

栈与队列很相似，但它允许对元素进行后进先出（LIFO）进行检索。

Stack是一个扩展自Vector的类，而Queue是一个接口。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## BlockingQueue是什么？`Java.util.concurrent.BlockingQueue`是一个队列，在进行检索或移除一个元素的时候，它会等待队列变为非空；当在添加一个元素时，它会等待队列中的可用空间。BlockingQueue接口是Java集合框架的一部分，主要用于实现生产者-消费者模式。我们不需要担心等待生产者有可用的空间，或消费者有可用的对象，因为它都在BlockingQueue的实现类中被处理了。Java提供了集中BlockingQueue的实现，比如ArrayBlockingQueue、LinkedBlockingQueue、PriorityBlockingQueue,、SynchronousQueue等。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 哪些集合类提供对元素的随机访问？
 ArrayList、HashMap、TreeMap和HashTable类提供对元素的随机访问。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何决定选用HashMap还是TreeMap？
对于在Map中插入、删除和定位元素这类操作，HashMap是最好的选择。然而，假如你需要对一个有序的key集合进行遍历，TreeMap是更好的选择。基于你的collection的大小，也许向HashMap中添加元素会更快，将map换为TreeMap进行有序key的遍历。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 我们能否使用任何类作为Map的key？
我们可以使用任何类作为Map的key，然而在使用它们之前，需要考虑以下几点：

（1）如果类重写了equals()方法，它也应该重写hashCode()方法。

（2）类的所有实例需要遵循与equals()和hashCode()相关的规则。请参考之前提到的这些规则。

（3）如果一个类没有使用equals()，你不应该在hashCode()中使用它。

（4）用户自定义key类的最佳实践是使之为不可变的，这样，hashCode()值可以被缓存起来，拥有更好的性能。不可变的类也可以确保hashCode()和equals()在未来不会改变，这样就会解决与可变相关的问题了。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## hashCode()和equals()方法有何重要性？HashMap使用Key对象的hashCode()和equals()方法去决定key-value对的索引。当我们试着从HashMap中获取值的时候，这些方法也会被用到。如果这些方法没有被正确地实现，在这种情况下，两个不同Key也许会产生相同的hashCode()和equals()输出，HashMap将会认为它们是相同的，然后覆盖它们，而非把它们存储到不同的地方。同样的，所有不允许存储重复数据的集合类都使用hashCode()和equals()去查找重复，所以正确实现它们非常重要。equals()和hashCode()的实现应该遵循以下规则：

（1）如果o1.equals(o2)，那么o1.hashCode() == o2.hashCode()总是为true的。

（2）如果o1.hashCode() == o2.hashCode()，并不意味着o1.equals(o2)会为true。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## fail-fast与fail-safe有什么区别？Iterator的fail-fast属性与当前的集合共同起作用，因此它不会受到集合中任何改动的影响。Java.util包中的所有集合类都被设计为fail-fast的，而java.util.concurrent中的集合类都为fail-safe的。Fail-fast迭代器抛出ConcurrentModificationException，而fail-safe迭代器从不抛出ConcurrentModificationException。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Iterater和ListIterator之间有什么区别？
（1）我们可以使用Iterator来遍历Set和List集合，而ListIterator只能遍历List。

（2）Iterator只可以向前遍历，而LIstIterator可以双向遍历。

（3）ListIterator从Iterator接口继承，然后添加了一些额外的功能，比如添加一个元素、替换一个元素、获取前面或后面元素的索引位置。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Enumeration和Iterator接口的区别？Enumeration的速度是Iterator的两倍，也使用更少的内存。Enumeration是非常基础的，也满足了基础的需要。但是，与Enumeration相比，Iterator更加安全，因为当一个集合正在被遍历的时候，它会阻止其它线程去修改集合。

迭代器取代了Java集合框架中的Enumeration。迭代器允许调用者从集合中移除元素，而Enumeration不能做到。为了使它的功能更加清晰，迭代器方法名已经经过改善。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Iterator是什么？Iterator接口提供遍历任何Collection的接口。我们可以从一个Collection中使用迭代器方法来获取迭代器实例。迭代器取代了Java集合框架中的Enumeration。迭代器允许调用者在迭代过程中移除元素。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为何Map接口不继承Collection接口？尽管Map接口和它的实现也是集合框架的一部分，但Map不是集合，集合也不是Map。因此，Map继承Collection毫无意义，反之亦然。

如果Map继承Collection接口，那么元素去哪儿？Map包含key-value对，它提供抽取key或value列表集合的方法，但是它不适合“一组对象”规范。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为何Collection不从Cloneable和Serializable接口继承？Collection接口指定一组对象，对象即为它的元素。如何维护这些元素由Collection的具体实现决定。例如，一些如List的Collection实现允许重复的元素，而其它的如Set就不允许。很多Collection实现有一个公有的clone方法。然而，把它放到集合的所有实现中也是没有意义的。这是因为Collection是一个抽象表现。重要的是实现。

当与具体实现打交道的时候，克隆或序列化的语义和含义才发挥作用。所以，具体实现应该决定如何对它进行克隆或序列化，或它是否可以被克隆或序列化。

在所有的实现中授权克隆和序列化，最终导致更少的灵活性和更多的限制。特定的实现应该决定它是否可以被克隆和序列化。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 集合框架中的泛型有什么优点？Java1.5引入了泛型，所有的集合接口和实现都大量地使用它。泛型允许我们为集合提供一个可以容纳的对象类型，因此，如果你添加其它类型的任何元素，它会在编译时报错。这避免了在运行时出现ClassCastException，因为你将会在编译时得到报错信息。泛型也使得代码整洁，我们不需要使用显式转换和instanceOf操作符。它也给运行时带来好处，因为不会产生类型检查的字节码指令。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java集合框架是什么？说出一些集合框架的优点？每种编程语言中都有集合，最初的Java版本包含几种集合类：Vector、Stack、HashTable和Array。随着集合的广泛使用，Java1.2提出了囊括所有集合接口、实现和算法的集合框架。在保证线程安全的情况下使用泛型和并发集合类，Java已经经历了很久。它还包括在Java并发包中，阻塞接口以及它们的实现。集合框架的部分优点如下：

（1）使用核心集合类降低开发成本，而非实现我们自己的集合类。

（2）随着使用经过严格测试的集合框架类，代码质量会得到提高。

（3）通过使用JDK附带的集合类，可以降低代码维护成本。

（4）复用性和可操作性。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 谈谈对HashMap 构造方法中初始容量、加载因子的理解初始容量代表了哈希表中桶的初始数量，即 Entry< K,V>[] table 数组的初始长度。

加载因子是哈希表在其容量自动增加之前可以达到多满的一种饱和度百分比，其衡量了一个散列表的空间的使用程度，负载因子越大表示散列表的装填程度越高，反之愈小。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## HashMap 默认的初始化长度是多少？
在JDK中默认长度是16，并且默认长度和扩容后的长度都必须是 2 的幂。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## ArrayList和LinkedList的区别？
LinkedList基于链表的数据结构；ArrayList基于动态数组的数据结构

LinkedList 在插入和删除数据时效率更高，ArrayList 查询效率更高；

*** 
## ⭐️⭐️⭐️⭐️⭐️
## ArrayList 和 Vector 的区别？
Vector 是线程安全的，ArrayList 是线程不安全的。

Vector在数据满时增长为原来的两倍，而 ArrayList在数据量达到容量的一半时,增长为原容量的1.5倍。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## ConcurrentHashMap实现原理JDK1.7 : 【数组（Segment） + 数组（HashEntry） + 链表（HashEntry节点）】
ConcurrentHashMap（分段锁） 对整个桶数组进行了分割分段(Segment)，每一把锁只锁容器其中一部分数据，多线程访问容器里不同数据段的数据，就不会存在锁竞争，提高并发访问率。
Segment是一种可重入锁ReentrantLock，在ConcurrentHashMap里扮演锁的角色，HashEntry则用于存储键值对数据。

JDK1.8 : Node数组+链表 / 红黑树
利用CAS+Synchronized来保证并发更新的安全，底层依然采用数组+链表+红黑树的存储结构。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## ConcurrentHashMap和Hashtable的区别？ConcurrentHashMap 结合了 HashMap 和 HashTable 二者的优势。HashMap 没有考虑同步，HashTable 考虑了同步的问题。但是 HashTable 在每次同步执行时都要锁住整个结构。 ConcurrentHashMap 锁的方式是稍微细粒度的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## HashMap与HashTable的区别？* HashMap没有考虑同步，是线程不安全的；Hashtable使用了synchronized关键字，是线程安全的；
* HashMap允许K/V都为null；后者K/V都不允许为null；

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 常见的集合底层实现* ArrayList底层是数组。
* LinkedList底层是双向链表。
* HashMap底层与HashTable原理相同，Java 8版本以后如果同一位置哈希冲突大于8则链表变成红黑树。
* HashTable底层是链地址法组成的哈希表（即数组+单项链表组成）。
* HashSet底层是HashMap。
* LinkedHashMap底层修改自HashMap，包含一个维护插入顺序的双向链表。
* TreeMap底层是红黑树。
* LinkedHashSet底层是LinkedHashMap。
* TreeSet底层是TreeMap。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 常见的集合有哪些？**Map接口和Collection接口是所有集合框架的父接口**

1.  Collection接口的子接口包括：Set接口和List接口。Set中不能包含重复的元素。List是一个有序的集合，可以包含重复的元素，提供了按索引访问的方式。
2.  Map接口的实现类主要有：HashMap、Hashtable、ConcurrentHashMap以及TreeMap等。Map不能包含重复的key，但是可以包含相同的value。根据键得到值，对map集合遍历时先得到键的set集合，对set集合进行遍历，得到相应的值。
3.  Set接口的实现类主要有：HashSet、TreeSet、LinkedHashSet等
4.  List接口的实现类主要有：ArrayList、LinkedList、Stack以及Vector等
5.  Iterator，所有的集合类，都实现了Iterator接口，这是一个用于遍历集合中元素的接口，主要包含以下三种方法：  
    hasNext()是否还有下一个元素  
    next()返回下一个元素  
    remove()删除当前元素

![在这里插入图片描述](https://img-blog.csdnimg.cn/20181025231543126.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2JhaWR1XzM0MTIyMzI0,size_27,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/2018102523155144.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2JhaWR1XzM0MTIyMzI0,size_27,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20181025231613150.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2JhaWR1XzM0MTIyMzI0,size_27,color_FFFFFF,t_70)
*** 
## ⭐️⭐️⭐️⭐️⭐️
## ConcurrentHashMap是怎么实现的？hashmap是线程不安全的，而hashtable性能低下，所以concurrentHashMap应运而生。

这个类设计的主要目标是维持并发访问时的可读性，将更新冲突减小到最少。第二个目标是保持和hashmap相同或者更低的空间消耗，多线程环境中支持在一个空表中有一个更高的插入比例。

`jdk1.7`的`concurrentHashMap`是有锁的，使用的分段锁。

`Java 8`的`concurrenthashMap`用无锁操作，基于CAS原子指令。

下面分析下`Java 8`的ConcurrentHashMap的源码：  

首先是Node节点，和hashmap的差不多，用于储存key-value。提供了判断相等以及查找的方法。  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20181107164250395.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xqejIwMTY=,size_16,color_FFFFFF,t_70)

     static class Node<K,V> implements Map.Entry<K,V> {
            final int hash;
            final K key;
            volatile V val;
            volatile Node<K,V> next;
    
            Node(int hash, K key, V val, Node<K,V> next) {
                this.hash = hash;
                this.key = key;
                this.val = val;
                this.next = next;
            }
    
            public final K getKey()       { return key; }
            public final V getValue()     { return val; }
            public final int hashCode()   { return key.hashCode() ^ val.hashCode(); }
            public final String toString(){ return key + "=" + val; }
            public final V setValue(V value) {
                throw new UnsupportedOperationException();
            }
    
            public final boolean equals(Object o) {
                Object k, v, u; Map.Entry<?,?> e;
                return ((o instanceof Map.Entry) &&
                        (k = (e = (Map.Entry<?,?>)o).getKey()) != null &&
                        (v = e.getValue()) != null &&
                        (k == key || k.equals(key)) &&
                        (v == (u = val) || v.equals(u)));
            }
    
            /**
             * Virtualized support for map.get(); overridden in subclasses.
             */
            Node<K,V> find(int h, Object k) {
                Node<K,V> e = this;
                if (k != null) {
                    do {
                        K ek;
                        if (e.hash == h &&
                            ((ek = e.key) == k || (ek != null && k.equals(ek))))
                            return e;
                    } while ((e = e.next) != null);
                }
                return null;
            }
        }
    

下面这个方法是通过位运算改变哈希值，高位不变只是首位 强制转换为0。  
因为浮点数的哈希值可能发生大量聚集，比如 Float a=3.4f;  
Float b=3.9f;他们的哈希值对16取余数，都是10，那么这两个key就会发生碰撞，如果使用了下面的位传播算法，就能降低这个冲突。

& HASH_BITS这个运算，是为了把最高位置为0

    static final int spread(int h) {
            return (h ^ (h >>> 16)) & HASH_BITS;
        }
    

ASHIFT，记录左移的位数。

参数i是元素在数组tab中的索引。这个方法是查找在数组tab中，索引i处的元素。ABASE表示基础偏移距，i << ASHIFT表示第i个元素相对于基础偏移距以外的偏移距。  
get操作是无锁的。

    static final <K,V> Node<K,V> tabAt(Node<K,V>[] tab, int i) {
            return (Node<K,V>)U.getObjectVolatile(tab, ((long)i << ASHIFT) + ABASE);
        }
    

查找到e这一步是原子性的，但是后续在e这个链表上查找时，不是原子的。

    public V get(Object key) {
            Node<K,V>[] tab; Node<K,V> e, p; int n, eh; K ek;
            int h = spread(key.hashCode());
            if ((tab = table) != null && (n = tab.length) > 0 &&
                (e = tabAt(tab, (n - 1) & h)) != null) {
                if ((eh = e.hash) == h) {
                    if ((ek = e.key) == key || (ek != null && key.equals(ek)))
                        return e.val;
                }
                else if (eh < 0)
                    return (p = e.find(h, key)) != null ? p.val : null;
                while ((e = e.next) != null) {
                    if (e.hash == h &&
                        ((ek = e.key) == key || (ek != null && key.equals(ek))))
                        return e.val;
                }
            }
            return null;
        }
    

* * *

put操作：  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20181108094359777.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xqejIwMTY=,size_16,color_FFFFFF,t_70)

    final V putVal(K key, V value, boolean onlyIfAbsent) {
            if (key == null || value == null) throw new NullPointerException();
            int hash = spread(key.hashCode());
            int binCount = 0;
            for (Node<K,V>[] tab = table;;) {
                Node<K,V> f; int n, i, fh;
                if (tab == null || (n = tab.length) == 0)
                    tab = initTable();
                else if ((f = tabAt(tab, i = (n - 1) & hash)) == null) {
                    if (casTabAt(tab, i, null,
                                 new Node<K,V>(hash, key, value, null)))
                        break;                   // no lock when adding to empty bin
                }
                else if ((fh = f.hash) == MOVED)
                    tab = helpTransfer(tab, f);
                else {
                    V oldVal = null;
                    synchronized (f) {
                        if (tabAt(tab, i) == f) {
                            if (fh >= 0) {
                                binCount = 1;
                                for (Node<K,V> e = f;; ++binCount) {
                                    K ek;
                                    if (e.hash == hash &&
                                        ((ek = e.key) == key ||
                                         (ek != null && key.equals(ek)))) {
                                        oldVal = e.val;
                                        if (!onlyIfAbsent)
                                            e.val = value;
                                        break;
                                    }
                                    Node<K,V> pred = e;
                                    if ((e = e.next) == null) {
                                        pred.next = new Node<K,V>(hash, key,
                                                                  value, null);
                                        break;
                                    }
                                }
                            }
                            else if (f instanceof TreeBin) {
                                Node<K,V> p;
                                binCount = 2;
                                if ((p = ((TreeBin<K,V>)f).putTreeVal(hash, key,
                                                               value)) != null) {
                                    oldVal = p.val;
                                    if (!onlyIfAbsent)
                                        p.val = value;
                                }
                            }
                        }
                    }
                    if (binCount != 0) {
                        if (binCount >= TREEIFY_THRESHOLD)
                            treeifyBin(tab, i);
                        if (oldVal != null)
                            return oldVal;
                        break;
                    }
                }
            }
            addCount(1L, binCount);
            return null;
        }
    

刚开始插入第一个元素时，表肯定还是空 的，所以先看看initTable方法。  
sizeCtl是表的初始容量，默认是16，也可以通过构造函数指定。

这个方法也是线程安全的，它没有加锁，但是通过sizeCtl的值来控制，初始化前修改sizeCtl为-1，初始化完成后再把sizeCtl的值修改回原来值的一半。

    private final Node<K,V>[] initTable() {
            Node<K,V>[] tab; int sc;
            while ((tab = table) == null || tab.length == 0) {
                if ((sc = sizeCtl) < 0)
                    Thread.yield(); // lost initialization race; just spin
                else if (U.compareAndSwapInt(this, SIZECTL, sc, -1)) {
                    try {
                        if ((tab = table) == null || tab.length == 0) {
                            int n = (sc > 0) ? sc : DEFAULT_CAPACITY;
                            @SuppressWarnings("unchecked")
                            Node<K,V>[] nt = (Node<K,V>[])new Node<?,?>[n];
                            table = tab = nt;
                            sc = n - (n >>> 2);
                        }
                    } finally {
                        sizeCtl = sc;
                    }
                    break;
                }
            }
            return tab;
        }
    
    

* * *

每次新增一个元素，都会调用addCount  
baseCount的初始值为0  
counterCells一开始也是null.counterCells的长度最大值是CPU的最大线程并行数（真并行，比如4核8线程，那么长度最大值就是8），这个用于计数，统计当前Map中共有多少个元素，如果只用Basecount计数，那要么加锁，要么cas竞争激烈，不管哪一种情况，效率都比较低，使用counterCells可以更好的利用多核计算机的性能，又不需要加锁。

有流程图可以看出，如果在单线程或者并发低的情况下，总数只由basecount计数，但是在竞争激烈的情况下，由foundcount方法增加计数。

第一次调用时的执行：  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20181108104707380.png)![在这里插入图片描述](https://img-blog.csdnimg.cn/20181108113544329.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xqejIwMTY=,size_16,color_FFFFFF,t_70)

    private final void addCount(long x, int check) {
            CounterCell[] as; long b, s;
            if ((as = counterCells) != null ||
                !U.compareAndSwapLong(this, BASECOUNT, b = baseCount, s = b + x)) {
                CounterCell a; long v; int m;
                boolean uncontended = true;
                if (as == null || (m = as.length - 1) < 0 ||
                    (a = as[ThreadLocalRandom.getProbe() & m]) == null ||
                    !(uncontended =
                      U.compareAndSwapLong(a, CELLVALUE, v = a.value, v + x))) {
                    fullAddCount(x, uncontended);
                    return;
                }
                if (check <= 1)
                    return;
                s = sumCount();
            }
            if (check >= 0) {
                Node<K,V>[] tab, nt; int n, sc;
                while (s >= (long)(sc = sizeCtl) && (tab = table) != null &&
                       (n = tab.length) < MAXIMUM_CAPACITY) {
                    int rs = resizeStamp(n);
                    if (sc < 0) {
                        if ((sc >>> RESIZE_STAMP_SHIFT) != rs || sc == rs + 1 ||
                            sc == rs + MAX_RESIZERS || (nt = nextTable) == null ||
                            transferIndex <= 0)
                            break;
                        if (U.compareAndSwapInt(this, SIZECTL, sc, sc + 1))
                            transfer(tab, nt);
                    }
                    else if (U.compareAndSwapInt(this, SIZECTL, sc,
                                                 (rs << RESIZE_STAMP_SHIFT) + 2))
                        transfer(tab, null);
                    s = sumCount();
                }
            }
        }
    

fullAddCount流程图:  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20181108165033945.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xqejIwMTY=,size_16,color_FFFFFF,t_70)

     private final void fullAddCount(long x, boolean wasUncontended) {
            int h;
            if ((h = ThreadLocalRandom.getProbe()) == 0) {
                ThreadLocalRandom.localInit();      // force initialization
                h = ThreadLocalRandom.getProbe();
                wasUncontended = true;
            }
            boolean collide = false;                // True if last slot nonempty
            for (;;) {
                CounterCell[] as; CounterCell a; int n; long v;
                if ((as = counterCells) != null && (n = as.length) > 0) {
                    if ((a = as[(n - 1) & h]) == null) {
                        if (cellsBusy == 0) {            // Try to attach new Cell
                            CounterCell r = new CounterCell(x); // Optimistic create
                            if (cellsBusy == 0 &&
                                U.compareAndSwapInt(this, CELLSBUSY, 0, 1)) {
                                boolean created = false;
                                try {               // Recheck under lock
                                    CounterCell[] rs; int m, j;
                                    if ((rs = counterCells) != null &&
                                        (m = rs.length) > 0 &&
                                        rs[j = (m - 1) & h] == null) {
                                        rs[j] = r;
                                        created = true;
                                    }
                                } finally {
                                    cellsBusy = 0;
                                }
                                if (created)
                                    break;
                                continue;           // Slot is now non-empty
                            }
                        }
                        collide = false;
                    }
                    else if (!wasUncontended)       // CAS already known to fail
                        wasUncontended = true;      // Continue after rehash
                    else if (U.compareAndSwapLong(a, CELLVALUE, v = a.value, v + x))
                        break;
                    else if (counterCells != as || n >= NCPU)
                        collide = false;            // At max size or stale
                    else if (!collide)
                        collide = true;
                    else if (cellsBusy == 0 &&
                             U.compareAndSwapInt(this, CELLSBUSY, 0, 1)) {
                        try {
                            if (counterCells == as) {// Expand table unless stale
                                CounterCell[] rs = new CounterCell[n << 1];
                                for (int i = 0; i < n; ++i)
                                    rs[i] = as[i];
                                counterCells = rs;
                            }
                        } finally {
                            cellsBusy = 0;
                        }
                        collide = false;
                        continue;                   // Retry with expanded table
                    }
                    h = ThreadLocalRandom.advanceProbe(h);
                }
                else if (cellsBusy == 0 && counterCells == as &&
                         U.compareAndSwapInt(this, CELLSBUSY, 0, 1)) {
                    boolean init = false;
                    try {                           // Initialize table
                        if (counterCells == as) {
                            CounterCell[] rs = new CounterCell[2];
                            rs[h & 1] = new CounterCell(x);
                            counterCells = rs;
                            init = true;
                        }
                    } finally {
                        cellsBusy = 0;
                    }
                    if (init)
                        break;
                }
                else if (U.compareAndSwapLong(this, BASECOUNT, v = baseCount, v + x))
                    break;                          // Fall back on using base
            }
        }
    
    

* * *

remove方法：

    public V remove(Object key) {
            return replaceNode(key, null, null);
        }
    

value是新的值,cv是旧的值。  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20181109111200386.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xqejIwMTY=,size_16,color_FFFFFF,t_70)

    final V replaceNode(Object key, V value, Object cv) {
            int hash = spread(key.hashCode());
            for (Node<K,V>[] tab = table;;) {
                Node<K,V> f; int n, i, fh;
                if (tab == null || (n = tab.length) == 0 ||
                    (f = tabAt(tab, i = (n - 1) & hash)) == null)
                    break;
                else if ((fh = f.hash) == MOVED)
                    tab = helpTransfer(tab, f);
                else {
                    V oldVal = null;
                    boolean validated = false;
                    synchronized (f) {
                        if (tabAt(tab, i) == f) {
                            if (fh >= 0) {
                                validated = true;
                                for (Node<K,V> e = f, pred = null;;) {
                                    K ek;
                                    if (e.hash == hash &&
                                        ((ek = e.key) == key ||
                                         (ek != null && key.equals(ek)))) {
                                        V ev = e.val;
                                        if (cv == null || cv == ev ||
                                            (ev != null && cv.equals(ev))) {
                                            oldVal = ev;
                                            if (value != null)
                                                e.val = value;
                                            else if (pred != null)
                                                pred.next = e.next;
                                            else
                                                setTabAt(tab, i, e.next);
                                        }
                                        break;
                                    }
                                    pred = e;
                                    if ((e = e.next) == null)
                                        break;
                                }
                            }
                            else if (f instanceof TreeBin) {
                                validated = true;
                                TreeBin<K,V> t = (TreeBin<K,V>)f;
                                TreeNode<K,V> r, p;
                                if ((r = t.root) != null &&
                                    (p = r.findTreeNode(hash, key, null)) != null) {
                                    V pv = p.val;
                                    if (cv == null || cv == pv ||
                                        (pv != null && cv.equals(pv))) {
                                        oldVal = pv;
                                        if (value != null)
                                            p.val = value;
                                        else if (t.removeTreeNode(p))
                                            setTabAt(tab, i, untreeify(t.first));
                                    }
                                }
                            }
                        }
                    }
                    if (validated) {
                        if (oldVal != null) {
                            if (value == null)
                                addCount(-1L, -1);
                            return oldVal;
                        }
                        break;
                    }
                }
            }
            return null;
      }
    

* * *

get操作，没加锁，找到指定key的索引，然后遍历一遍。

    public V get(Object key) {
        Node<K,V>[] tab; Node<K,V> e, p; int n, eh; K ek;
        int h = spread(key.hashCode());
        if ((tab = table) != null && (n = tab.length) > 0 &&
            (e = tabAt(tab, (n - 1) & h)) != null) {
            if ((eh = e.hash) == h) {
                if ((ek = e.key) == key || (ek != null && key.equals(ek)))
                    return e.val;
            }
            else if (eh < 0)
                return (p = e.find(h, key)) != null ? p.val : null;
            while ((e = e.next) != null) {
                if (e.hash == h &&
                    ((ek = e.key) == key || (ek != null && key.equals(ek))))
                    return e.val;
            }
        }
        return null;
    }
*** 
## ⭐️⭐️⭐️⭐️⭐️
## HashMap有时候会死循环，你知道是什么原因吗？### 问题

如果是在单线程下使用HashMap，自然是没有问题的，如果后期由于代码优化，这段逻辑引入了多线程并发执行，在一个未知的时间点，会发现CPU占用100%，居高不下，通过查看堆栈，你会惊讶的发现，线程都Hang在hashMap的get()方法上，服务重启之后，问题消失，过段时间可能又复现了。

这是为什么？

### 原因分析

在了解来龙去脉之前，我们先看看HashMap的数据结构。

在内部，HashMap使用一个Entry数组保存key、value数据，当一对key、value被加入时，会通过一个hash算法得到数组的下标index，算法很简单，根据key的hash值，对数组的大小取模 hash & (length-1)，并把结果插入数组该位置，如果该位置上已经有元素了，就说明存在hash冲突，这样会在index位置生成链表。

如果存在hash冲突，最惨的情况，就是所有元素都定位到同一个位置，形成一个长长的链表，这样get一个值时，最坏情况需要遍历所有节点，性能变成了O(n)，所以元素的hash值算法和HashMap的初始化大小很重要。

当插入一个新的节点时，如果不存在相同的key，则会判断当前内部元素是否已经达到阈值（默认是数组大小的0.75），如果已经达到阈值，会对数组进行扩容，也会对链表中的元素进行rehash。

### 实现

HashMap的put方法实现：

1、判断key是否已经存在

```java
public V put(K key, V value) {
    if (key == null)
        return putForNullKey(value);
    int hash = hash(key);
    int i = indexFor(hash, table.length);
    // 如果key已经存在，则替换value，并返回旧值
    for (Entry<K,V> e = table[i]; e != null; e = e.next) {
        Object k;
        if (e.hash == hash && ((k = e.key) == key || key.equals(k))) {
            V oldValue = e.value;
            e.value = value;
            e.recordAccess(this);
            return oldValue;
        }
    }
 
    modCount++;
    // key不存在，则插入新的元素
    addEntry(hash, key, value, i);
    return null;
}
```

2、检查容量是否达到阈值threshold

```java
void addEntry(int hash, K key, V value, int bucketIndex) {
    if ((size >= threshold) && (null != table[bucketIndex])) {
        resize(2 * table.length);
        hash = (null != key) ? hash(key) : 0;
        bucketIndex = indexFor(hash, table.length);
    }
 
    createEntry(hash, key, value, bucketIndex);
}
```

如果元素个数已经达到阈值，则扩容，并把原来的元素移动过去。

3、扩容实现

```java
void resize(int newCapacity) {
    Entry[] oldTable = table;
    int oldCapacity = oldTable.length;
    ...
 
    Entry[] newTable = new Entry[newCapacity];
    ...
    transfer(newTable, rehash);
    table = newTable;
    threshold = (int)Math.min(newCapacity * loadFactor, MAXIMUM_CAPACITY + 1);
}
```

这里会新建一个更大的数组，并通过transfer方法，移动元素。

```java
void transfer(Entry[] newTable, boolean rehash) {
    int newCapacity = newTable.length;
    for (Entry<K,V> e : table) {
        while(null != e) {
            Entry<K,V> next = e.next;
            if (rehash) {
                e.hash = null == e.key ? 0 : hash(e.key);
            }
            int i = indexFor(e.hash, newCapacity);
            e.next = newTable[i];
            newTable[i] = e;
            e = next;
        }
    }
}
```

移动的逻辑也很清晰，遍历原来table中每个位置的链表，并对每个元素进行重新hash，在新的newTable找到归宿，并插入。

### 案例分析

假设HashMap初始化大小为4，插入个3节点，不巧的是，这3个节点都hash到同一个位置，如果按照默认的负载因子的话，插入第3个节点就会扩容，为了验证效果，假设负载因子是1.

```java
void transfer(Entry[] newTable, boolean rehash) {
    int newCapacity = newTable.length;
    for (Entry<K,V> e : table) {
        while(null != e) {
            Entry<K,V> next = e.next;
            if (rehash) {
                e.hash = null == e.key ? 0 : hash(e.key);
            }
            int i = indexFor(e.hash, newCapacity);
            e.next = newTable[i];
            newTable[i] = e;
            e = next;
        }
    }
}
```

以上是节点移动的相关逻辑。

![image.png](https://i.loli.net/2021/11/14/BSiXnL6vyHUowK4.png)

插入第4个节点时，发生rehash，假设现在有两个线程同时进行，线程1和线程2，两个线程都会新建新的数组。

![image.png](https://i.loli.net/2021/11/14/bY5sM4EaGVOhcZf.png)

假设 **线程2** 在执行到`Entry<K,V> next = e.next;`之后，cpu时间片用完了，这时变量e指向节点a，变量next指向节点b。

**线程1**继续执行，很不巧，a、b、c节点rehash之后又是在同一个位置7，开始移动节点

第一步，移动节点a

![image.png](https://i.loli.net/2021/11/14/AfPFwxgJ5eTMG4L.png)

第二步，移动节点b

![image.png](https://i.loli.net/2021/11/14/cNkh5QlCHq3oUIf.png)

注意，这里的顺序是反过来的，继续移动节点c

![image.png](https://i.loli.net/2021/11/14/p6MhF5tGKIQlvHw.png)

这个时候 **线程1** 的时间片用完，内部的table还没有设置成新的newTable， **线程2** 开始执行，这时内部的引用关系如下：

![image.png](https://i.loli.net/2021/11/14/JmK9itLqIDsWSFA.png)

这时，在 **线程2** 中，变量e指向节点a，变量next指向节点b，开始执行循环体的剩余逻辑。

```java
Entry<K,V> next = e.next;
int i = indexFor(e.hash, newCapacity);
e.next = newTable[i];
newTable[i] = e;
e = next;
```

执行之后的引用关系如下图

![image.png](https://i.loli.net/2021/11/14/1R9LomcyTerCkiI.png)

执行后，变量e指向节点b，因为e不是null，则继续执行循环体，执行后的引用关系

![image.png](https://i.loli.net/2021/11/14/bhMH6PIrV3xnFt5.png)

变量e又重新指回节点a，只能继续执行循环体，这里仔细分析下：  
```
1、执行完`Entry<K,V> next = e.next;`，目前节点a没有next，所以变量next指向null；  
2、`e.next = newTable[i];` 其中 newTable\[i\] 指向节点b，那就是把a的next指向了节点b，这样a和b就相互引用了，形成了一个环；  
3、`newTable[i] = e` 把节点a放到了数组i位置；  
4、`e = next;` 把变量e赋值为null，因为第一步中变量next就是指向null；
```

所以最终的引用关系是这样的：

![image.png](https://i.loli.net/2021/11/14/G7KWrv5uVm14eXQ.png)

节点a和b互相引用，形成了一个环，当在数组该位置get寻找对应的key时，就发生了死循环。

另外，如果线程2把newTable设置成到内部的table，节点c的数据就丢了，看来还有数据遗失的问题。

### 总结

所以在并发的情况，发生扩容时，可能会产生循环链表，在执行get的时候，会触发死循环，引起CPU的100%问题，所以一定要避免在并发环境下使用HashMap，并发环境下要使用ConcurrentHashmap。
*** 
## ⭐️⭐️⭐️⭐️⭐️
## HashMap在Java7和Java8中的实现有什么不同？不同点：
----

**（1）JDK1.7用的是头插法，而JDK1.8及之后使用的都是尾插法，那么他们为什么要这样做呢？因为JDK1.7是用单链表进行的纵向延伸，当采用头插法时会容易出现逆序且环形链表死循环问题。但是在JDK1.8之后是因为加入了红黑树使用尾插法，能够避免出现逆序且链表死循环的问题。**

**（2）扩容后数据存储位置的计算方式也不一样：1. 在JDK1.7的时候是直接用hash值和需要扩容的二进制数进行&（这里就是为什么扩容的时候为啥一定必须是2的多少次幂的原因所在，因为如果只有2的n次幂的情况时最后一位二进制数才一定是1，这样能最大程度减少hash碰撞）（hash值 & length-1）**

**（3）在JDK1.7的时候是先扩容后插入的，这样就会导致无论这一次插入是不是发生hash冲突都需要进行扩容，如果这次插入的并没有发生Hash冲突的话，那么就会造成一次无效扩容，但是在1.8的时候是先插入再扩容的，优点其实是因为为了减少这一次无效的扩容，原因就是如果这次插入没有发生Hash冲突的话，那么其实就不会造成扩容，但是在1.7的时候就会急造成扩容**

**（4）而在JDK1.8的时候直接用了JDK1.7的时候计算的规律，也就是扩容前的原始位置+扩容的大小值=JDK1.8的计算方式，而不再是JDK1.7的那种异或的方法。但是这种方式就相当于只需要判断Hash值的新增参与运算的位是0还是1就直接迅速计算出了扩容后的储存方式。**

> 在计算hash值的时候，JDK1.7用了9次扰动处理=4次位运算+5次异或，而JDK1.8只用了2次扰动处理=1次位运算+1次异或。	
    
**扩容流程对比图：**  

![image.png](https://i.loli.net/2021/11/14/15i7eoJ2lA3qXBb.png)

**（3）JDK1.7的时候使用的是数组+ 单链表的数据结构。但是在JDK1.8及之后时，使用的是数组+链表+红黑树的数据结构（当链表的深度达到8的时候，也就是默认阈值，就会自动扩容把链表转成红黑树的数据结构来把时间复杂度从O（n）变成O（logN）提高了效率）**

![image.png](https://i.loli.net/2021/11/14/ATNPI6GHkdjWOrq.png)

**这里在重新进行补充两个问题：**

**（1）为什么在JDK1.7的时候是先进行扩容后进行插入，而在JDK1.8的时候则是先插入后进行扩容的呢？**

```
    //其实就是当这个Map中实际插入的键值对的值的大小如果大于这个默认的阈值的时候（初始是16*0.75=12）的时候才会触发扩容，
    //这个是在JDK1.8中的先插入后扩容
    if (++size > threshold)
                resize();
 ```

*   其实这个问题也是JDK8对HashMap中，主要是因为对链表转为红黑树进行的优化，因为你插入这个节点的时候有可能是普通链表节点，也有可能是红黑树节点，但是为什么1.8之后HashMap变为先插入后扩容的原因，我也有点不是很理解？欢迎来讨论这个问题？
*   但是在JDK1.7中的话，是先进行扩容后进行插入的，就是当你发现你插入的桶是不是为空，如果不为空说明存在值就发生了hash冲突，那么就必须得扩容，但是如果不发生Hash冲突的话，说明当前桶是空的（后面并没有挂有链表），那就等到下一次发生Hash冲突的时候在进行扩容，但是当如果以后都没有发生hash冲突产生，那么就不会进行扩容了，减少了一次无用扩容，也减少了内存的使用

```java
    void addEntry(int hash, K key, V value, int bucketIndex) {
    		//这里当钱数组如果大于等于12（假如）阈值的话，并且当前的数组的Entry数组还不能为空的时候就扩容
        　　if ((size >= threshold) && (null != table[bucketIndex])) {
    　　　　　　 //扩容数组，比较耗时
           　　 resize(2 * table.length);
            　　hash = (null != key) ? hash(key) : 0;
            　　bucketIndex = indexFor(hash, table.length);
        　　}
    
        　　createEntry(hash, key, value, bucketIndex);
    　　}
    
     void createEntry(int hash, K key, V value, int bucketIndex) {
        　　Entry<K,V> e = table[bucketIndex];
    　　　　//把新加的放在原先在的前面，原先的是e，现在的是new，next指向e
       　　 table[bucketIndex] = new Entry<>(hash, key, value, e);//假设现在是new
        　　size++;
    　　}
```

**（2）为什么在JDK1.8中进行对HashMap优化的时候，把链表转化为红黑树的阈值是8,而不是7或者不是20呢（面试蘑菇街问过）？**

*   如果选择6和8（如果链表小于等于6树还原转为链表，大于等于8转为树），中间有个差值7可以有效防止链表和树频繁转换。假设一下，如果设计成链表个数超过8则链表转换成树结构，链表个数小于8则树结构转换成链表，如果一个HashMap不停的插入、删除元素，链表个数在8左右徘徊，就会频繁的发生树转链表、链表转树，效率会很低。
*   还有一点重要的就是由于treenodes的大小大约是常规节点的两倍，因此我们仅在容器包含足够的节点以保证使用时才使用它们，当它们变得太小（由于移除或调整大小）时，它们会被转换回普通的node节点，容器中节点分布在hash桶中的频率遵循泊松分布，桶的长度超过8的概率非常非常小。所以作者应该是根据概率统计而选择了8作为阀值

```java
    	//Java中解释的原因
       * Because TreeNodes are about twice the size of regular nodes, we
         * use them only when bins contain enough nodes to warrant use
         * (see TREEIFY_THRESHOLD). And when they become too small (due to
         * removal or resizing) they are converted back to plain bins.  In
         * usages with well-distributed user hashCodes, tree bins are
         * rarely used.  Ideally, under random hashCodes, the frequency of
         * nodes in bins follows a Poisson distribution
         * (http://en.wikipedia.org/wiki/Poisson_distribution) with a
         * parameter of about 0.5 on average for the default resizing
         * threshold of 0.75, although with a large variance because of
         * resizing granularity. Ignoring variance, the expected
         * occurrences of list size k are (exp(-0.5) * pow(0.5, k) /
         * factorial(k)). The first values are:
         *
         * 0:    0.60653066
         * 1:    0.30326533
         * 2:    0.07581633
         * 3:    0.01263606
         * 4:    0.00157952
         * 5:    0.00015795
         * 6:    0.00001316
         * 7:    0.00000094
         * 8:    0.00000006
         * more: less than 1 in ten million
```

（二）哈希表如何解决Hash冲突？
-----------------

![image.png](https://i.loli.net/2021/11/14/eDbzTvqcpstaAJR.png)

（三）为什么HashMap具备下述特点：键-值（key-value）都允许为空、线程不安全、不保证有序、存储位置随时间变化
-------------------------------------------------------------

![image.png](https://i.loli.net/2021/11/14/E6x4i8FAqoVRZXP.png)

（四）为什么 HashMap 中 String、Integer 这样的包装类适合作为 key 键
------------------------------------------------

![image.png](https://i.loli.net/2021/11/14/KNXaGEhpgWfqOkS.png)

（五）HashMap 中的 key若 Object类型， 则需实现哪些方法？
--------------------------------------

![image.png](https://i.loli.net/2021/11/14/kUYE9gfSJmLKtCZ.png)
*** 
## ⭐️⭐️⭐️⭐️⭐️
## HashMap是怎么实现的？> 哈希表（hash table）  
> 也叫散列表，是一种非常重要的数据结构，应用场景及其丰富，许多缓存技术（比如memcached）的核心其实就是在内存中维护一张大的哈希表，本文会对java集合框架中HashMap的实现原理进行讲解，并对JDK7的HashMap源码进行分析。

**一、什么是哈希表**

在讨论哈希表之前，我们先大概了解下其他数据结构在新增，查找等基础操作执行性能

**数组**：采用一段连续的存储单元来存储数据。对于指定下标的查找，时间复杂度为O(1)；通过给定值进行查找，需要遍历数组，逐一比对给定关键字和数组元素，时间复杂度为O(n)，当然，对于有序数组，则可采用二分查找，插值查找，斐波那契查找等方式，可将查找复杂度提高为O(logn)；对于一般的插入删除操作，涉及到数组元素的移动，其平均复杂度也为O(n)

**线性链表**：对于链表的新增，删除等操作（在找到指定操作位置后），仅需处理结点间的引用即可，时间复杂度为O(1)，而查找操作需要遍历链表逐一进行比对，复杂度为O(n)

**二叉树**：对一棵相对平衡的有序二叉树，对其进行插入，查找，删除等操作，平均复杂度均为O(logn)。

**哈希表**：相比上述几种数据结构，在哈希表中进行添加，删除，查找等操作，性能十分之高，不考虑哈希冲突的情况下（后面会探讨下哈希冲突的情况），仅需一次定位即可完成，时间复杂度为O(1)，接下来我们就来看看哈希表是如何实现达到惊艳的常数阶O(1)的。

我们知道，数据结构的物理存储结构只有两种：**顺序存储结构**和**链式存储结构**（像栈，队列，树，图等是从逻辑结构去抽象的，映射到内存中，也这两种物理组织形式），而在上面我们提到过，在数组中根据下标查找某个元素，一次定位就可以达到，哈希表利用了这种特性，**哈希表的主干就是数组**。

**比如我们要新增或查找某个元素，我们通过把当前元素的关键字 通过某个函数映射到数组中的某个位置，通过数组下标一次定位就可完成操作。**  
　　  
这个函数可以简单描述为：**存储位置 = f(关键字)** ，这个函数f一般称为哈希函数，这个函数的设计好坏会直接影响到哈希表的优劣。举个例子，比如我们要在哈希表中执行插入操作：  
插入过程如下图所示  
![哈希表数据插入过程](https://img-blog.csdnimg.cn/2018110221063296.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dvc2hpbWF4aWFvMQ==,size_16,color_FFFFFF,t_70)

查找操作同理，先通过哈希函数计算出实际存储地址，然后从数组中对应地址取出即可。

**哈希冲突**

然而万事无完美，**如果两个不同的元素，通过哈希函数得出的实际存储地址相同怎么办**？也就是说，当我们对某个元素进行哈希运算，得到一个存储地址，然后要进行插入的时候，发现已经被其他元素占用了，其实这就是所谓的**哈希冲突**，也叫**哈希碰撞**。前面我们提到过，哈希函数的设计至关重要，好的哈希函数会尽可能地保证 计算简单和散列地址分布均匀,但是，我们需要清楚的是，数组是一块连续的固定长度的内存空间，再好的哈希函数也不能保证得到的存储地址绝对不发生冲突。那么哈希冲突如何解决呢？哈希冲突的解决方案有多种:开放定址法（发生冲突，继续寻找下一块未被占用的存储地址），再散列函数法，链地址法，而HashMap即是采用了**链地址法**，也就是**数组+链表**的方式。

二、HashMap的实现原理

HashMap的主干是一个Entry数组。Entry是HashMap的基本组成单元，每一个Entry包含一个key-value键值对。（其实所谓Map其实就是保存了两个对象之间的映射关系的一种集合）

```java
//HashMap的主干数组，可以看到就是一个Entry数组，初始值为空数组{}，主干数组的长度一定是2的次幂。
//至于为什么这么做，后面会有详细分析。
transient Entry<K,V>[] table = (Entry<K,V>[]) EMPTY_TABLE;
```

Entry是HashMap中的一个静态内部类。代码如下

```java
static class Entry<K,V> implements Map.Entry<K,V> {
  final K key;
  V value;
  Entry<K,V> next;//存储指向下一个Entry的引用，单链表结构
  int hash;//对key的hashcode值进行hash运算后得到的值，存储在Entry，避免重复计算

  /**
   * Creates new entry.
   */
  Entry(int h, K k, V v, Entry<K,V> n) {
    value = v;
    next = n;
    key = k;
    hash = h;
  } 
```

所以，HashMap的总体结构如下：  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20181102221702492.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dvc2hpbWF4aWFvMQ==,size_16,color_FFFFFF,t_70)

简单来说，**HashMap由数组+链表组成的**，数组是HashMap的主体，链表则是主要为了解决哈希冲突而存在的，如果定位到的数组位置不含链表（当前entry的next指向null）,那么查找，添加等操作很快，仅需一次寻址即可；如果定位到的数组包含链表，对于添加操作，其时间复杂度为O(n)，首先遍历链表，存在即覆盖，否则新增；对于查找操作来讲，仍需遍历链表，然后通过key对象的equals方法逐一比对查找。所以，性能考虑，**HashMap中的链表出现越少，性能才会越好。**

其他几个重要字段

111java
    /**实际存储的key-value键值对的个数*/
    transient int size;
    
    /**阈值，当table == {}时，该值为初始容量（初始容量默认为16）；当table被填充了，也就是为table分配内存空间后，
    threshold一般为 capacity*loadFactory。HashMap在进行扩容时需要参考threshold，后面会详细谈到*/
    int threshold;
    
    /**负载因子，代表了table的填充度有多少，默认是0.75
    加载因子存在的原因，还是因为减缓哈希冲突，如果初始桶为16，等到满16个元素才扩容，某些桶里可能就有不止一个元素了。
    所以加载因子默认为0.75，也就是说大小为16的HashMap，到了第13个元素，就会扩容成32。
    */
    final float loadFactor;
    
    /**HashMap被改变的次数，由于HashMap非线程安全，在对HashMap进行迭代时，
    如果期间其他线程的参与导致HashMap的结构发生变化了（比如put，remove等操作），
    需要抛出异常ConcurrentModificationException*/
    transient int modCount;
```

HashMap有4个构造器，其他构造器如果用户没有传入initialCapacity 和loadFactor这两个参数，会使用默认值

initialCapacity默认为16，loadFactory默认为0.75

我们看下其中一个

```java
    public HashMap(int initialCapacity, float loadFactor) {
    　　　　　//此处对传入的初始容量进行校验，最大不能超过MAXIMUM_CAPACITY = 1<<30(230)
            if (initialCapacity < 0)
                throw new IllegalArgumentException("Illegal initial capacity: " +
                                                   initialCapacity);
            if (initialCapacity > MAXIMUM_CAPACITY)
                initialCapacity = MAXIMUM_CAPACITY;
            if (loadFactor <= 0 || Float.isNaN(loadFactor))
                throw new IllegalArgumentException("Illegal load factor: " +
                                                   loadFactor);
    
            this.loadFactor = loadFactor;
            threshold = initialCapacity;
    　　　　　
            init();//init方法在HashMap中没有实际实现，不过在其子类如 linkedHashMap中就会有对应实现
        }
```

从上面这段代码我们可以看出，在常规构造器中，没有为数组table分配内存空间（有一个入参为指定Map的构造器例外），**而是在执行put操作的时候才真正构建table数组**

OK,接下来我们来看看put操作的实现

```java
    public V put(K key, V value) {
            //如果table数组为空数组{}，进行数组填充（为table分配实际内存空间），入参为threshold，
            //此时threshold为initialCapacity 默认是1<<4(24=16)
            if (table == EMPTY_TABLE) {
                inflateTable(threshold);
            }
           //如果key为null，存储位置为table[0]或table[0]的冲突链上
            if (key == null)
                return putForNullKey(value);
            int hash = hash(key);//对key的hashcode进一步计算，确保散列均匀
            int i = indexFor(hash, table.length);//获取在table中的实际位置
            for (Entry<K,V> e = table[i]; e != null; e = e.next) {
            //如果该对应数据已存在，执行覆盖操作。用新value替换旧value，并返回旧value
                Object k;
                if (e.hash == hash && ((k = e.key) == key || key.equals(k))) {
                    V oldValue = e.value;
                    e.value = value;
                    e.recordAccess(this);
                    return oldValue;
                }
            }
            modCount++;//保证并发访问时，若HashMap内部结构发生变化，快速响应失败
            addEntry(hash, key, value, i);//新增一个entry
            return null;
        }
```

inflateTable这个方法用于为主干数组table在内存中分配存储空间，通过roundUpToPowerOf2(toSize)可以确保capacity为大于或等于toSize的最接近toSize的二次幂，比如toSize=13,则capacity=16;to\_size=16,capacity=16;to\_size=17,capacity=32.

```java
    private void inflateTable(int toSize) {
            int capacity = roundUpToPowerOf2(toSize);//capacity一定是2的次幂
            /**此处为threshold赋值，取capacity*loadFactor和MAXIMUM_CAPACITY+1的最小值，
            capaticy一定不会超过MAXIMUM_CAPACITY，除非loadFactor大于1 */
            threshold = (int) Math.min(capacity * loadFactor, MAXIMUM_CAPACITY + 1);
            table = new Entry[capacity];
            initHashSeedAsNeeded(capacity);
        }
```

roundUpToPowerOf2中的这段处理使得数组长度一定为2的次幂，Integer.highestOneBit是用来获取最左边的bit（其他bit位为0）所代表的数值.

```java
     private static int roundUpToPowerOf2(int number) {
            // assert number >= 0 : "number must be non-negative";
            return number >= MAXIMUM_CAPACITY
                    ? MAXIMUM_CAPACITY
                    : (number > 1) ? Integer.highestOneBit((number - 1) << 1) : 1;
        }
```
    

hash函数

```java
    /**这是一个神奇的函数，用了很多的异或，移位等运算
    对key的hashcode进一步进行计算以及二进制位的调整等来保证最终获取的存储位置尽量分布均匀*/
    final int hash(Object k) {
            int h = hashSeed;
            if (0 != h && k instanceof String) {
                return sun.misc.Hashing.stringHash32((String) k);
            }
    
            h ^= k.hashCode();
    
            h ^= (h >>> 20) ^ (h >>> 12);
            return h ^ (h >>> 7) ^ (h >>> 4);
        }
```

以上hash函数计算出的值，通过indexFor进一步处理来获取实际的存储位置

```java
    /**
         * 返回数组下标
         */
        static int indexFor(int h, int length) {
            return h & (length-1);
        }
```

h&（length-1）保证获取的index一定在数组范围内，举个例子，默认容量16，length-1=15，h=18,转换成二进制计算为index=2。位运算对计算机来说，性能更高一些（HashMap中有大量位运算）

所以最终存储位置的确定流程是这样的：  
![HashMap如何确定元素位置](https://img-blog.csdnimg.cn/20181102214046362.png)

再来看看addEntry的实现：

```java
    void addEntry(int hash, K key, V value, int bucketIndex) {
            if ((size >= threshold) && (null != table[bucketIndex])) {
                resize(2 * table.length);//当size超过临界阈值threshold，并且即将发生哈希冲突时进行扩容
                hash = (null != key) ? hash(key) : 0;
                bucketIndex = indexFor(hash, table.length);
            }
    
            createEntry(hash, key, value, bucketIndex);
        }
```

通过以上代码能够得知，**当发生哈希冲突并且size大于阈值的时候，需要进行数组扩容，扩容时，需要新建一个长度为之前数组2倍的新的数组，然后将当前的Entry数组中的元素全部传输过去，扩容后的新数组长度为之前的2倍，所以扩容相对来说是个耗资源的操作。**

**三、为何HashMap的数组长度一定是2的次幂？**

我们来继续看上面提到的resize方法

```java
    void resize(int newCapacity) {
            Entry[] oldTable = table;
            int oldCapacity = oldTable.length;
            if (oldCapacity == MAXIMUM_CAPACITY) {
                threshold = Integer.MAX_VALUE;
                return;
            }
    
            Entry[] newTable = new Entry[newCapacity];
            transfer(newTable, initHashSeedAsNeeded(newCapacity));
            table = newTable;
            threshold = (int)Math.min(newCapacity * loadFactor, MAXIMUM_CAPACITY + 1);
        }
```

如果数组进行扩容，数组长度发生变化，而存储位置 index = h&(length-1),index也可能会发生变化，需要重新计算index，我们先来看看transfer这个方法

```java
    void transfer(Entry[] newTable, boolean rehash) {
            int newCapacity = newTable.length;
    　　　　　//for循环中的代码，逐个遍历链表，重新计算索引位置，将老数组数据复制到新数组中去（数组不存储实际数据，所以仅仅是拷贝引用而已）
            for (Entry<K,V> e : table) {
                while(null != e) {
                    Entry<K,V> next = e.next;
                    if (rehash) {
                        e.hash = null == e.key ? 0 : hash(e.key);
                    }
                    int i = indexFor(e.hash, newCapacity);
                    //将当前entry的next链指向新的索引位置,newTable[i]有可能为空，有可能也是个entry链，如果是entry链，直接在链表头部插入。
                    e.next = newTable[i];
                    newTable[i] = e;
                    e = next;
                }
            }
        }
```

这个方法将老数组中的数据逐个链表地遍历，扔到新的扩容后的数组中，我们的数组索引位置的计算是通过 对key值的hashcode进行hash扰乱运算后，再通过和 length-1进行位运算得到最终数组索引位置。

HashMap的数组长度一定保持2的次幂，比如16的二进制表示为 10000，那么length-1就是15，二进制为01111，同理扩容后的数组长度为32，二进制表示为100000，length-1为31，二进制表示为011111。从下图可以我们也能看到这样会保证低位全为1，而扩容后只有一位差异，也就是多出了最左位的1，这样在通过 h&(length-1)的时候，只要h对应的最左边的那一个差异位为0，就能保证得到的新的数组索引和老数组索引一致(大大减少了之前已经散列良好的老数组的数据位置重新调换)，个人理解。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20181102223343298.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dvc2hpbWF4aWFvMQ==,size_16,color_FFFFFF,t_70)

还有，数组长度保持2的次幂，length-1的低位都为1，会使得获得的数组索引index更加均匀

![在这里插入图片描述](https://img-blog.csdnimg.cn/20181102223421180.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dvc2hpbWF4aWFvMQ==,size_16,color_FFFFFF,t_70)  
我们看到，上面的&运算，高位是不会对结果产生影响的（hash函数采用各种位运算可能也是为了使得低位更加散列），我们只关注低位bit，如果低位全部为1，那么对于h低位部分来说，任何一位的变化都会对结果产生影响，也就是说，要得到index=21这个存储位置，h的低位只有这一种组合。这也是数组长度设计为必须为2的次幂的原因。  
![在这里插入图片描述](https://img-blog.csdnimg.cn/2018110222343145.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dvc2hpbWF4aWFvMQ==,size_16,color_FFFFFF,t_70)  
如果不是2的次幂，也就是低位不是全为1此时，要使得index=21，h的低位部分不再具有唯一性了，哈希冲突的几率会变的更大，同时，index对应的这个bit位无论如何不会等于1了，而对应的那些数组位置也就被白白浪费了。

**get方法**：

```java
     public V get(Object key) {
    　　　　 //如果key为null,则直接去table[0]处去检索即可。
            if (key == null)
                return getForNullKey();
            Entry<K,V> entry = getEntry(key);
            return null == entry ? null : entry.getValue();
     }
```

get方法通过key值返回对应value，如果key为null，直接去table\[0\]处检索。我们再看一下getEntry这个方法

```java
    final Entry<K,V> getEntry(Object key) {
                
            if (size == 0) {
                return null;
            }
            //通过key的hashcode值计算hash值
            int hash = (key == null) ? 0 : hash(key);
            //indexFor (hash&length-1) 获取最终数组索引，然后遍历链表，通过equals方法比对找出对应记录
            for (Entry<K,V> e = table[indexFor(hash, table.length)];
                 e != null;
                 e = e.next) {
                Object k;
                if (e.hash == hash && 
                    ((k = e.key) == key || (key != null && key.equals(k))))
                    return e;
            }
            return null;
        }    
```

可以看出，get方法的实现相对简单，key(hashcode)–>hash–>indexFor–>最终索引位置，找到对应位置table\[i\]，再查看是否有链表，遍历链表，通过key的equals方法比对查找对应的记录。要注意的是，有人觉得上面在定位到数组位置之后然后遍历链表的时候，e.hash == hash这个判断没必要，仅通过equals判断就可以。其实不然，试想一下，如果传入的key对象重写了equals方法却没有重写hashCode，而恰巧此对象定位到这个数组位置，如果仅仅用equals判断可能是相等的，但其hashCode和当前对象不一致，这种情况，根据Object的hashCode的约定，不能返回当前对象，而应该返回null，后面的例子会做出进一步解释。

**四、重写equals方法需同时重写hashCode方法**

最后我们再聊聊老生常谈的一个问题，各种资料上都会提到，“重写equals时也要同时覆盖hashcode”，我们举个小例子来看看，如果重写了equals而不重写hashcode会发生什么样的问题

```java
    public class MyTest {
        private static class Person{
            int idCard;
            String name;
    
            public Person(int idCard, String name) {
                this.idCard = idCard;
                this.name = name;
            }
            @Override
            public boolean equals(Object o) {
                if (this == o) {
                    return true;
                }
                if (o == null || getClass() != o.getClass()){
                    return false;
                }
                Person person = (Person) o;
                //两个对象是否等值，通过idCard来确定
                return this.idCard == person.idCard;
            }
    
        }
        public static void main(String []args){
            HashMap<Person,String> map = new HashMap<Person, String>();
            Person person = new Person(1234,"乔峰");
            //put到hashmap中去
            map.put(person,"天龙八部");
            //get取出，从逻辑上讲应该能输出“天龙八部”
            System.out.println("结果:"+map.get(new Person(1234,"萧峰")));
        }
    }
    
    实际输出结果：null
```

如果我们已经对HashMap的原理有了一定了解，这个结果就不难理解了。尽管我们在进行get和put操作的时候，使用的key从逻辑上讲是等值的（通过equals比较是相等的），但由于没有重写hashCode方法，所以put操作时，key(hashcode1)–>hash–>indexFor–>最终索引位置 ，而通过key取出value的时候 key(hashcode1)–>hash–>indexFor–>最终索引位置，由于hashcode1不等于hashcode2，导致没有定位到一个数组位置而返回逻辑上错误的值null（也有可能碰巧定位到一个数组位置，但是也会判断其entry的hash值是否相等，上面get方法中有提到。）

所以，在重写equals的方法的时候，必须注意重写hashCode方法，同时还要保证通过equals判断相等的两个对象，调用hashCode方法要返回同样的整数值。而如果equals判断不相等的两个对象，其hashCode可以相同（只不过会发生哈希冲突，应尽量避免）。

**五、JDK1.8中HashMap的性能优化**

假如一个数组槽位上链上数据过多（即拉链过长的情况）导致性能下降该怎么办？  
JDK1.8在JDK1.7的基础上针对增加了红黑树来进行优化。即当链表超过8时，链表就转换为红黑树，利用红黑树快速增删改查的特点提高HashMap的性能，其中会用到红黑树的插入、删除、查找等算法。  

**附：HashMap put方法逻辑图（JDK1.8）**  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20181105181728652.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dvc2hpbWF4aWFvMQ==,size_16,color_FFFFFF,t_70)
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说说你对Java里的阻塞队列的理解
### 7个阻塞队列。分别是

* ArrayBlockingQueue ：一个由数组结构组成的有界阻塞队列。
* LinkedBlockingQueue ：一个由链表结构组成的有界阻塞队列。
* PriorityBlockingQueue ：一个支持优先级排序的无界阻塞队列。
* DelayQueue：一个使用优先级队列实现的无界阻塞队列。
* SynchronousQueue：一个不存储元素的阻塞队列。
* LinkedTransferQueue：一个由链表结构组成的无界阻塞队列。
* LinkedBlockingDeque：一个由链表结构组成的双向阻塞队列。

### 添加元素

Java中的阻塞队列接口BlockingQueue继承自Queue接口。BlockingQueue接口提供了3个添加元素方法。
* add：添加元素到队列里，添加成功返回true，由于容量满了添加失败会抛出IllegalStateException异常
* offer：添加元素到队列里，添加成功返回true，添加失败返回false
* put：添加元素到队列里，如果容量满了会阻塞直到容量不满

### 删除方法

3个删除方法
* poll：删除队列头部元素，如果队列为空，返回null。否则返回元素。
* remove：基于对象找到对应的元素，并删除。删除成功返回true，否则返回false
* take：删除队列头部元素，如果队列为空，一直阻塞到队列有元素并删除

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 对AQS的理解在Java多线程编程中，重入锁(ReentrantLock) 和信号量(Semaphore)是两个极其重要的并发控制工具。相信大部分读者都应该比较熟悉它们的使用(如果不清楚的小伙伴，赶快拿出书本翻阅一下)。

但是不知道大家是不是有了解过重入锁和信号量的实现细节? 我就带大家看一看它们的具体实现。

首先，先上一张重要的类图，来说明一下三者之间的关系：

![](https://img-blog.csdnimg.cn/img_convert/360294ed54b639b19cca9dcc40ba17d1.png)

可以看到， 重入锁和信号量都在自己内部，实现了一个AbstractQueuedSynchronizer的子类，子类的名字都是Sync。而这个Sync类，也正是重入锁和信号量的核心实现。子类Sync中的代码也比较少，其核心算法都由AbstractQueuedSynchronizer提供。因此，可以说，只要大家了解了AbstractQueuedSynchronizer，就清楚得知道重入锁和信号量的实现原理了。

### 了解AbstractQueuedSynchronizer你必须知道的

在正是进入AbstractQueuedSynchronizer之前，还有一些基础知识需要大家了解，这样才能更好的理解AbstractQueuedSynchronizer的实现。

#### 基于许可的多线程控制

为了控制多个线程访问共享资源 ，我们需要为每个访问共享区间的线程派发一个许可。拿到一个许可的线程才能进入共享区间活动。当线程完成工作后，离开共享区间时，必须要归还许可，以确保后续的线程可以正常取得许可。如果许可用完了，那么线程进入共享区间时，就必须等待，这就是控制多线程并行的基本思想。

打个比方，一大群孩子去游乐场玩摩天轮，摩天轮上只能坐20个孩子。但是却来了100个小孩。那么许可以的个数就是20。也就说一次只有20个小孩可以上摩天轮玩，其他的孩子必须排队等待。只有等摩天轮上的孩子离开控制一个位置时，才能有其他小孩上去玩。

因此，使用许可控制线程行为和排队玩摩天轮差不多就是一个意思了。

#### 排他锁和共享锁

第二个重要的概念就是排他锁(exclusive)和共享锁(shared)。顾名思义，在排他模式上，只有一个线程可以访问共享变量，而共享模式则允许多个线程同时访问。简单地说，重入锁是排他的；信号量是共享的。

用摩天轮的话来说，排他锁就是虽然我这里有20个位置，但是小朋友也只能一个一个上哦，多出来的位置怎么办呢，可以空着，也可以让摩天轮上唯一的小孩换着做，他想坐哪儿就坐哪儿，1分钟换个位置，都没有关系。而共享锁，就是玩耍摩天轮正常的打开方式了。

#### LockSupport

LockSupport可以理解为一个工具类。它的作用很简单，就是挂起和继续执行线程。它的常用的API如下：

*   public static void park() : 如果没有可用许可，则挂起当前线程
*   public static void unpark(Thread thread)：给thread一个可用的许可，让它得以继续执行

因为单词park的意思就是停车，因此这里park()函数就表示让线程暂停。反之，unpark()则表示让线程继续执行。

需要注意的是，LockSupport本身也是基于许可的实现，如何理解这句话呢，请看下面的代码：

```java
    LockSupport.unpark(Thread.currentThread());
    LockSupport.park();
```

大家可以猜一下，park()之后，当前线程是停止，还是 可以继续执行呢？

答案是：可以继续执行。那是因为在park()之前，先执行了unpark()，进而释放了一个许可，也就是说当前线程有一个可用的许可。而park()在有可用许可的情况下，是不会阻塞线程的。

综上所述，park()和unpark()的执行效果和它调用的先后顺序没有关系。这一点相当重要，因为在一个多线程的环境中，我们往往很难保证函数调用的先后顺序(都在不同的线程中并发执行)，因此，这种基于许可的做法能够最大限度保证程序不出错。

与park()和unpark()相比， 一个典型的反面教材就是Thread.resume()和Thread.suspend()。

看下面的代码：

```java
    Thread.currentThread().resume();
    Thread.currentThread().suspend();
```

首先让线程继续执行，接着在挂起线程。这个写法和上面的park()的示例非常接近，但是运行结果却是截然不同的。在这里，当前线程就是卡死。

因此，使用park()和unpark()才是我们的首选。而在AbstractQueuedSynchronizer中，也正是使用了LockSupport的park()和unpark()操作来控制线程的运行状态的。

AbstractQueuedSynchronizer内部数据结构
--------------------------------

好了，基础的部分就介绍到这里。下面，让我们切入正题：首先来看一下AbstractQueuedSynchronizer的内部数据结构。

在AbstractQueuedSynchronizer内部，有一个队列，我们把它叫做**同步等待队列**。它的作用是保存等待在这个锁上的线程(由于lock()操作引起的等待）。此外，为了维护等待在条件变量上的等待线程，AbstractQueuedSynchronizer又需要再维护一个**条件变量等待队列**，也就是那些由Condition.await()引起阻塞的线程。

由于一个重入锁可以生成多个条件变量对象，因此，一个重入锁就可能有多个条件变量等待队列。实际上，每个条件变量对象内部都维护了一个等待列表。其逻辑结构如下所示：

![](https://img-blog.csdnimg.cn/img_convert/da0f1ce6f5ffb6cb413aa807b9785408.png)

下面的类图展示了代码层面的具体实现：

![](https://img-blog.csdnimg.cn/img_convert/f0a97b873a7b8204050ed732f049e8cb.png)

可以看到，无论是同步等待队列，还是条件变量等待队列，都使用同一个Node类作为链表的节点。对于同步等待队列，Node中包括链表的上一个元素prev，下一个元素next和线程对象thread。对于条件变量等待队列，还使用nextWaiter表示下一个等待在条件变量队列中的节点。

Node节点另外一个重要的成员是waitStatus，它表示节点等待在队列中的状态：

*   CANCELLED：表示线程取消了等待。如果取得锁的过程中发生了一些异常，则可能出现取消的情况，比如等待过程中出现了中断异常或者出现了timeout。
*   SIGNAL：表示后续节点需要被唤醒。
*   CONDITION：线程等待在条件变量队列中。
*   PROPAGATE：在共享模式下，无条件传播releaseShared状态。早期的JDK并没有这个状态，咋看之下，这个状态是多余的。引入这个状态是为了解决共享锁并发释放引起线程挂起的bug 6801020。（随着JDK的不断完善，它的代码也越来越难懂了 😦，就和我们自己的工程代码一样，bug修多了，细节就显得越来越晦涩）
*   0： 初始状态

其中CANCELLED=1，SIGNAL=-1，CONDITION=-2，PROPAGATE=-3 。在具体的实现中，就可以简单的通过waitStatus释放小于等于0，来判断是否是CANCELLED状态。

### 排他锁

了解了AbstractQueuedSynchronizer的基本实现思路和数据结构，接下来一起看一下它的实现细节吧。首先，来看一下排他锁的实现。重入锁是一种 典型的排他锁。

### 请求锁

下面是排他锁获得请求许可的代码：

```java
    public final void acquire(int arg) {
        //尝试获得许可， arg为许可的个数。对于重入锁来说，每次请求1个。
        if (!tryAcquire(arg) &&
        // 如果tryAcquire 失败，则先使用addWaiter()将当前线程加入同步等待队列
        // 然后继续尝试获得锁
        acquireQueued(addWaiter(Node.EXCLUSIVE), arg))
        selfInterrupt();
    }
```

进入一步看一下tryAcquire()函数。该函数的作用是尝试获得一个许可。对于AbstractQueuedSynchronizer来说，这是一个未实现的抽象函数。

具体实现在子类中。在重入锁，读写锁，信号量等实现中， 都有各自的实现。

如果tryAcquire()成功，则acquire()直接返回成功。如果失败，就用addWaiter()将当前线程加入同步等待队列。

![](https://img-blog.csdnimg.cn/img_convert/3cbb5219cb3ebe003b5ea1de4064e2f5.png)

接着， 对已经在队列中的线程请求锁，使用acquireQueued()函数，从函数名字上可以看到，其参数node，必须是一个已经在队列中等待的节点。它的功能就是为已经在队列中的Node请求一个许可。

这个函数大家要好好看看，因为无论是普通的lock()方法，还是条件变量的await()都会使用这个方法。

![](https://img-blog.csdnimg.cn/img_convert/2e2f750f5a92df8db78551211b6c4f64.png)

### 条件变量等待

如果调用Condition.await()，那么线程也会进入等待，下面来看实现：

![](https://img-blog.csdnimg.cn/img_convert/736432faf5295deee09b220bdf1fd518.png)

### Condition对象的signal()通知

signal()通知的时候，是在条件等待队列中，按照FIFO进行，首先从第一个节点下手：

![](https://img-blog.csdnimg.cn/img_convert/da52e20eb42571badb2825c45ef08b99.png)

### release()释放锁

释放排他锁很简单

```java
    public final boolean release(int arg) {
        //tryRelease()是一个抽象方法，在子类中有具体实现和tryAcquire()一样
        if (tryRelease(arg)) {
            Node h = head;
            if (h != null && h.waitStatus != 0)
                // 从队列中唤醒一个等待中的线程（遇到CANCEL的直接跳过）
                unparkSuccessor(h);
                return true;
        }
        return false;
    }
```

### 共享锁

与排他锁相比，共享锁的实现略微复杂一点。这也很好理解。因为排他锁的场景很简单，单进单出，而共享锁就不一样了。可能是N进M出，处理起来要麻烦一些。但是，他们的核心思想还是一致的。共享锁的几个典型应用有：信号量，读写锁中的写锁。

#### 获得共享锁

为了实现共享锁，在AbstractQueuedSynchronizer中，专门有一套针对共享锁的方法。

获得共享锁使用acquireShared()方法：

![](https://img-blog.csdnimg.cn/img_convert/600c661ae0968e10ac41708431972b8d.png)

#### 释放共享锁

释放共享锁的代码如下：

```java
    public final boolean releaseShared(int arg) {
        //tryReleaseShared()尝试释放许可，这是一个抽象方法，需要在子类中实现
        if (tryReleaseShared(arg)) {
            //上述代码中已经出现这个函数了，就是唤醒线程，设置传播状态
            doReleaseShared();
            return true;
        }
        return false;
    }
```
    
*** 
## ⭐️⭐️⭐️⭐️⭐️
## CopyOnWriteArrayList是什么？
CopyOnWriteArrayList : 写时加锁，当添加一个元素的时候，将原来的容器进行copy，复制出一个新的容器，然后在新的容器里面写，写完之后再将原容器的引用指向新的容器，而读的时候是读旧容器的数据，所以可以进行并发的读，但这是一种弱一致性的策略。

使用场景：CopyOnWriteArrayList适合使用在读操作远远大于写操作的场景里，比如缓存。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Nginx多进程模型是如何实现高并发的？进程数与并发数不存在很直接的关系。这取决取server采用的工作方式。

如果一个server采用一个进程负责一个request的方式，那么进程数就是并发数。那么显而易见的，就是会有很多进程在等待中。等什么？最多的应该是等待网络传输。其缺点题主应该也感觉到了，此处不述。

而nginx 的异步非阻塞工作方式正是利用了这点等待的时间。在需要等待的时候，这些进程就空闲出来待命了。因此表现为少数几个进程就解决了大量的并发问题。

nginx是如何利用的呢，简单来说：同样的4个进程，如果采用一个进程负责一个request的方式，那么，同时进来4个request之后，每个进程就负责其中一个，直至会话关闭。期间，如果有第5个request进来了。就无法及时反应了，因为4个进程都没干完活呢，因此，一般有个调度进程，每当新进来了一个request，就新开个进程来处理。

nginx不这样，每进来一个request，会有一个worker进程去处理。但不是全程的处理，处理到什么程度呢？处理到可能发生阻塞的地方，比如向上游（后端）服务器转发request，并等待请求返回。那么，这个处理的worker不会这么傻等着，他会在发送完请求后，注册一个事件：“如果upstream返回了，告诉我一声，我再接着干”。于是他就休息去了。此时，如果再有request 进来，他就可以很快再按这种方式处理。而一旦上游服务器返回了，就会触发这个事件，worker才会来接手，这个request才会接着往下走。

由于web server的工作性质决定了每个request的大部份生命都是在网络传输中，实际上花费在server机器上的时间片不多。这是几个进程就解决高并发的秘密所在。
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 常见的同步工具类？* CountDownLatch：递减计数器闭锁，直到达到某个条件时才放行，多线程可以调用await方法一直阻塞，直到计数器递减为零。比如我们连接zookeeper，由于连接操作是异步的，所以可以使用countDownLatch创建一个计数器为1的锁，连接挂起，当异步连接成功时，调用countDown通知挂起线程；再比如5V5游戏竞技，只有房间人满了才可以开始游戏。
* FutureTask：带有计算结果的任务，在计算完成时才能获取结果，如果计算尚未完成，则阻塞 get 方法。FutureTask将计算结果从执行线程传递到获取这个结果的线程。
* Semaphore：信号量，用来控制同时访问某个特定资源的数量，只有获取到许可acquire，才能够正常执行，并在完成后释放许可，acquire会一致阻塞到有许可或中断超时。使用信号量可以轻松实现一个阻塞队列。
* CyclicBarrier：类似于闭锁，它可以阻塞一组线程，只有所有线程全部到达以后，才能够继续执行，so线程必须相互等待。这在并行计算中是很有用的，将一个问题拆分为多个独立的子问题，当线程到达栅栏时，调用await等待，一直阻塞到所有参与线程全部到达，再执行下一步任务。



*** 
## ⭐️⭐️⭐️⭐️⭐️
## 常见的并发容器？* ConcurrentHashMap：使用了分段锁，锁的粒度变得更小，多线程访问时，可能都不存在锁的竞争，所以大大提高了吞吐量。简单对比来看，就好比数据库上用行锁来取代表锁，行锁无疑带来更大的并发。
* CopyOnWriteArrayList：写入时复制，多线程访问时，彼此不会互相干扰或被修改的线程所干扰，当然copy时有开销的，尤其时列表元素庞大，且写入操作频繁时，所以仅当迭代操作远远大于修改操作时，才应该考虑使用。
* BlockingQueue：阻塞队列提供了可阻塞的put和take方法，当队列已经满了，那么put操作将阻塞到队列可用，当队列为空时，take操作会阻塞到队列里有数据。有界的队列是一种强大的资源管理器，可以在程序负荷过载时保护应用，可作为一种服务降级的策略。阻塞队列还提供offer操作，当数据无法加入队列时，返回失败状态，给应用主动处理负荷过载带来更多灵活性。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 死锁的避免与诊断？如果一个线程最多只能获取一个锁，那么就不会发生锁顺序死锁了。如果确实需要获取多个锁，锁的顺序可以按照某种规约，比如两个资源的id值，程序按规约保证获取锁的顺序一致。或者可以使用显式的锁Lock，获取锁的时候设置超时时间，超时后可以重新发起，以避免发生死锁。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是锁顺序死锁？
两个线程试图以不同的顺序获得相同的锁，那么可能发发生死锁。比如转账问题，由from账户向to账户转账，假设每次我们先同步from对象，再同步to账户，然后执行转账操作，貌似没什么问题。如果这时候to账户同时向from账户转账，那么两个线程可能要永久等待了。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 数据库死锁？
在执行一个事务时可能要获取多个锁，一直持有锁到事务提交，如果A事务需要获取的锁在另一个事务B中，且B事务也在等待A事务所持有的锁，那么两个事务之间就会发生死锁。但数据库死锁比较少见，数据库会加以干涉死锁问题，牺牲一个事务使得其他事务正常执行。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是线程调度器(Thread Scheduler)和时间分片(Time Slicing)？线程调度器是一个操作系统服务，它负责为Runnable状态的线程分配CPU时间。一旦我们创建一个线程并启动它，它的执行便依赖于线程调度器的实现。

时间分片是指将可用的CPU时间分配给可用的Runnable线程的过程。分配CPU时间可以基于线程优先级或者线程等待的时间。线程调度并不受到Java虚拟机控制，所以由应用程序来控制它是更好的选择（即最好不要让你的程序依赖于线程的优先级）。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 有三个线程T1，T2，T3，怎么确保它们按顺序执行？
在多线程中有多种方法让线程按特定顺序执行，你可以用线程类的join()方法在一个线程中启动另一个线程，另外一个线程完成该线程继续执行。为了确保三个线程的顺序你应该先启动最后一个(T3调用T2，T2调用T1)，这样T1就会先完成而T3最后完成。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何测试并发量？
可以使用apache提供的ab工具测试。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java中Unsafe类详解unsafe可以帮我们直接去操作硬件资源,当然了是借助java的jit来进行的,官方不推荐使用,因为不安全,例如你使用unsafe创建一个超级大的数组,但是这个数组jvm是不管理的,只能你自己操作,容易oom,也不利于资源的回收.

1.获取unsafe

```java
//1.最简单的使用方式是基于反射获取Unsafe实例
Field f = Unsafe.class.getDeclaredField("theUnsafe");
f.setAccessible(true);
Unsafe unsafe = (Unsafe) f.get(null);
```

2.获取unsafe

```java
private static Unsafe unsafe = null;
private static Field getUnsafe = null; 
static {    
	try {        
    	getUnsafe = Unsafe.class.getDeclaredField("theUnsafe");        
        getUnsafe.setAccessible(true);        
        unsafe = (Unsafe) getUnsafe.get(null);    
    } catch (NoSuchFieldException e) {        
    	e.printStackTrace();    
    } catch (IllegalAccessException e) {        
    	e.printStackTrace();    
    }
}
```

随便只要你高兴,都可以获取到unfase,因为涉及到unfase 的权限问题,所以,我们只能使用这种方式获取,不然就是权限异常,

操作方法:

```java
/** 
 * 操作数组: 
 * 可以获取数组的在内容中的基本偏移量（arrayBaseOffset），获取数组内元素的间隔（比例）， 
 * 根据数组对象和偏移量获取元素值（getObject），设置数组元素值（putObject），示例如下。 
 */
String[] strings = new String[]{"1", "2", "3"};
long i = unsafe.arrayBaseOffset(String[].class);
System.out.println("string[] base offset is :" + i); 

//every index scale
long scale = unsafe.arrayIndexScale(String[].class);
System.out.println("string[] index scale is " + scale); 

//print first string in strings[]
System.out.println("first element is :" + unsafe.getObject(strings, i)); 

//set 100 to first string
unsafe.putObject(strings, i + scale * 0, "100"); 

//print first string in strings[] again
System.out.println("after set ,first element is :" + unsafe.getObject(strings, i + scale * 0));
```

```java
/** 
 * 对象操作 
 * 实例化Data 
 * 
 * 可以通过类的class对象创建类对象（allocateInstance），获取对象属性的偏移量（objectFieldOffset） 
 * ，通过偏移量设置对象的值（putObject） 
 * 
 * 对象的反序列化 
 * 当使用框架反序列化或者构建对象时，会假设从已存在的对象中重建，你期望使用反射来调用类的设置函数， 
 * 或者更准确一点是能直接设置内部字段甚至是final字段的函数。问题是你想创建一个对象的实例， 
 * 但你实际上又不需要构造函数，因为它可能会使问题更加困难而且会有副作用。 
 * 
 */
 
//调用allocateInstance函数避免了在我们不需要构造函数的时候却调用它
Data data = (Data) unsafe.allocateInstance(Data.class);
data.setId(1L);
data.setName("unsafe");
System.out.println(data); 

//返回成员属性在内存中的地址相对于对象内存地址的偏移量
Field nameField = Data.class.getDeclaredField("name");
long fieldOffset = unsafe.objectFieldOffset(nameField);
//putLong，putInt，putDouble，putChar，putObject等方法，直接修改内存数据（可以越过访问权限）unsafe.putObject(data,fieldOffset,"这是新的值");
System.out.println(data.getName());  

/** 
 * 我们可以在运行时创建一个类，比如从已编译的.class文件中。将类内容读取为字节数组， 
 * 并正确地传递给defineClass方法；当你必须动态创建类，而现有代码中有一些代理， 这是很有用的 
 */
File file = new File("C:\\workspace\\idea2\\disruptor\\target\\classes\\com\\onyx\\distruptor\\test\\Data.class");
FileInputStream input = new FileInputStream(file);
byte[] content = new byte[(int)file.length()];
input.read(content);
Class c = unsafe.defineClass(null, content, 0, content.length,null,null);
c.getMethod("getId").invoke(c.newInstance(), null);   

/** 
 * 内存操作 
 * 可以在Java内存区域中分配内存（allocateMemory），设置内存（setMemory，用于初始化）， 
 * 在指定的内存位置中设置值（putInt\putBoolean\putDouble等基本类型） 
 */
//分配一个8byte的内存
long address = unsafe.allocateMemory(8L);
//初始化内存填充1
unsafe.setMemory(address, 8L, (byte) 1);
//测试输出
System.out.println("add byte to memory:" + unsafe.getInt(address));
//设置0-3 4个byte为0x7fffffff
unsafe.putInt(address, 0x7fffffff);
//设置4-7 4个byte为0x80000000
unsafe.putInt(address + 4, 0x80000000);
//int占用4byte
System.out.println("add byte to memory:" + unsafe.getInt(address));
System.out.println("add byte to memory:" + unsafe.getInt(address + 4));
```
```java
/** 
 * CAS操作 
 * Compare And Swap（比较并交换），当需要改变的值为期望的值时，那么就替换它为新的值，是原子 
 * （不可在分割）的操作。很多并发框架底层都用到了CAS操作，CAS操作优势是无锁，可以减少线程切换耗费 
 * 的时间，但CAS经常失败运行容易引起性能问题，也存在ABA问题。在Unsafe中包含compareAndSwapObject、 
 * compareAndSwapInt、compareAndSwapLong三个方法，compareAndSwapInt的简单示例如下。 
 */
Data data = new Data();
data.setId(1L);
Field id = data.getClass().getDeclaredField("id");
long l = unsafe.objectFieldOffset(id);
id.setAccessible(true);

//比较并交换，比如id的值如果是所期望的值1，那么就替换为2，否则不做处理unsafe.compareAndSwapLong(data,1L,1L,2L);System.out.println(data.getId());
```

```java
/** 
 * 常量获取 
 * 
 * 可以获取地址大小（addressSize），页大小（pageSize），基本类型数组的偏移量 
 * （Unsafe.ARRAY_INT_BASE_OFFSET\Unsafe.ARRAY_BOOLEAN_BASE_OFFSET等）、 
 * 基本类型数组内元素的间隔（Unsafe.ARRAY_INT_INDEX_SCALE\Unsafe.ARRAY_BOOLEAN_INDEX_SCALE等） 
 */
 
//get os address size
System.out.println("address size is :" + unsafe.addressSize());//get os page 
sizeSystem.out.println("page size is :" + unsafe.pageSize());//int array base 
offsetSystem.out.println("unsafe array int base offset:" + Unsafe.ARRAY_INT_BASE_OFFSET);

/** 
 * 线程许可 
 * 许可线程通过（park），或者让线程等待许可(unpark)， 
 */

Thread packThread = new Thread(() -> {    
	long startTime = System.currentTimeMillis();    //纳秒，相对时间park    
    unsafe.park(false,3000000000L);    //毫秒，绝对时间park    
    //unsafe.park(true,System.currentTimeMillis()+3000);     
    
    System.out.println("main thread end,cost :"+(System.currentTimeMillis()-startTime)+"ms");
});
packThread.start();TimeUnit.SECONDS.sleep(1);
//注释掉下一行后，线程3秒数后进行输出,否则在1秒后输出
unsafe.unpark(packThread);

/** 
 * Java数组大小的最大值为Integer.MAX_VALUE。使用直接内存分配，我们创建的数组大小受限于堆大小； 
 * 实际上，这是堆外内存（off-heap memory）技术，在java.nio包中部分可用； 
 * 
 * 这种方式的内存分配不在堆上，且不受GC管理，所以必须小心Unsafe.freeMemory()的使用。 
 * 它也不执行任何边界检查，所以任何非法访问可能会导致JVM崩溃 
 */
public class SuperArray {     
	private static Unsafe unsafe = null;    
   	private static Field getUnsafe = null;     
    
    static {        
    	try {            
        	getUnsafe = Unsafe.class.getDeclaredField("theUnsafe");    
            getUnsafe.setAccessible(true);            
            unsafe = (Unsafe) getUnsafe.get(null);        
        } catch (NoSuchFieldException e) {            
        	e.printStackTrace();        
        } catch (IllegalAccessException e) {            
        	e.printStackTrace();        
        }    
    }      
    
    private final static int BYTE = 1;     
    private long size;    
    private long address;     
    public SuperArray(long size) {        
    	this.size = size;        
        address = unsafe.allocateMemory(size * BYTE);    
    }     
    
    public void set(long i, byte value) {        
    	unsafe.putByte(address + i * BYTE, value);    
    }     
    
    public int get(long idx) {        
    	return unsafe.getByte(address + idx * BYTE);    
    }     
    
    public long size() {        
    	return size;    
    }      
    
    public static void main(String[] args) {        
    	long SUPER_SIZE = (long)Integer.MAX_VALUE * 2;        
        SuperArray array = new SuperArray(SUPER_SIZE);        
        System.out.println("Array size:" + array.size()); // 4294967294        
        int sum=0;        
        for (int i = 0; i < 100; i++) {            
        	array.set((long)Integer.MAX_VALUE + i, (byte)3);            
            sum += array.get((long)Integer.MAX_VALUE + i);        
        }        
        System.out.println(sum);    
    }   
}
```
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 进程调度算法
**实时系统**：FIFO(First Input First Output，先进先出算法)，SJF(Shortest Job First，最短作业优先算法)，SRTF(Shortest Remaining Time First，最短剩余时间优先算法）。

**交互式系统**：RR(Round Robin，时间片轮转算法)，HPF(Highest Priority First，最高优先级算法)，多级队列，最短进程优先，保证调度，彩票调度，公平分享调度。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 同步和异步有何不同，在什么情况下分别使用它们？举例说明如果数据将在线程间共享。例如：正在写的数据以后可能会被另一个线程读到，或者正在读的数据可能已经被另一个线程写过了，那么这些数据就是共享数据，必须进行同步存取

当应用程序在对象上调用了一个需要花费很长时间来执行的方法，并且不希望让程序等待方法的返回时，就应该使用异步编程，在很多情况下采用异步途径往往更有效。

* 同步交互：指发送一个请求，需要等待返回，然后才能发送下一个请求，有个等待的过程
* 异步交互：指发送一个请求，不需要等待返回，随时可以再发送下一个请求，即不需要等待。

区别：一个需要等待，一个不需要等待

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 线程间如何通讯
## 锁机制

包括互斥锁、条件变量、读写锁

* 互斥锁提供了以排他方式防止数据结构被并发修改的方法
* 读写锁允许多个线程同时读共享数据，而对写操作是互斥的
* 条件变量可以以原子的方式阻塞进程，直到某个特定条件为真为止。对条件的测试是在互斥锁的保护下进行的。条件变量始终与互斥锁一起使用。

## 信号量机制

包括无名线程信号量和命名线程信号量

## 信号机制

类似进程间的信号处理

线程间的通信目的只要是用于新陈同步，所以线程没有像进程通信中的用于数据交换的通信机制。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 进程间如何通讯## 管道(pipe)

管道是一种半双工的通信方式，数据只能单向流动，而且只能在具有亲缘关系的进程间使用。进程的亲缘关系通常是指父子进程关系

## 有名管道(namedpipe)

有名管道也是半双工的通信方式，但是它云溪无亲缘关系进程间的通信。

## 信号量(semaphore)

信号量是一个计数器，可以用来控制多个进程对共享资源的访问。它常作为一种锁机制，防止某进程正在访问共享资源时，其他进程也访问该资源。因此，主要作为进程间以及同一进程内不同线程之间的同步手段。

## 消息队列（messagequeue）

消息队列里有消息的链表，存放在内核中并由消息队列标识符标识。消息队列克服了信号传递消息少、管道只能承载无格式字节流以及缓冲区大小受限等缺点

## 信号（signal）

信号是一种比较复杂的通信方式，用于通知接收进程某个事件已经发生

## 共享内存（shared memory）

共享内存就是映射一段能被其他进程所访问的内存，这段共享内存由一个进程创建，但多个进程都可以访问。共享内存是最快的IPC方式，它是针对其他进程间通信方式运行效率低而专门设计的。它往往与其他通信机制，如信号量配合使用，来实现进程间的同步和通信。

## 套接字（socket）

套接口也是一种进程间通信机制，以其他通信机制不同的是，它可用于不同进程间的通信

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是线程
进程是表示自愿分配的基本单位。而线程则是进程中执行运算的最小单位，即执行处理机调度的基本单位。通俗来讲：一个程序有一个进程，而一个进程可以有多个线程。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是进程
进程是指运行中的应用程序，每个进程都有自己独立的地址空间（内存空间）。
比如用户点击桌面的IE浏览器，就启动了一个进程，操作系统就会为该进程分配独立的地址空间。当用户再次点击左边的IE浏览器，又启动了一个进程，操作系统将为新的进程分配新的独立的地址空间。目前操作系统都支持多进程。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 是什么使Java SE 8优于其他？
Java SE 8具有以下功能，使其优于其他功能：

它编写并行代码。它提供了更多可用的代码。它具有改进的性能应用程序。它具有更易读和简洁的代码。它支持编写包含促销的数据库。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Java8中的MetaSpace？它与PermGen Space有何不同？
使用JDK8时，permGen空间已被删除。那么现在将元数据信息存储在哪里？此元数据现在存储在本机内存中，称为“MetaSpace”。该内存不是连续的Java堆内存。它允许通过垃圾收集，自动调整，元数据并发解除分配来改进PermGen空间。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Lambda函数的优点：
直到Java 8列表和集合通常由客户端代码从集合中获取迭代器来处理，然后使用它迭代其元素并依次处理每个元素。如果要并行处理不同的元素，那么客户代码而不是集合的责任就是组织它。 通过Java 8，可以更轻松地在多个线程上分发集合的处理。 集合现在可以在内部组织自己的迭代，将并行化的责任从客户端代码转移到库代码中。

更少的代码行。如上所述，用户必须仅以声明方式声明要执行的操作。 n > System.out.println（“Hello World”+ n）; 所以用户必须键入减少的代码量。

使用Java 8 Lambda表达式可以实现更高的效率。通过使用具有多核的CPU，用户可以通过使用lambda并行处理集合来利用多核CPU。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Lambda表达式？
Lambda Expression可以定义为允许用户将方法作为参数传递的匿名函数。这有助于删除大量的样板代码。Lambda函数没有访问修饰符（私有，公共或受保护），没有返回类型声明和没有名称。

Lambda表达式允许用户将“函数”传递给代码。所以，与以前需要一整套的接口/抽象类想必，我们可以更容易地编写代码。例如，假设我们的代码具有一些复杂的循环/条件逻辑或工作流程。使用lambda表达式，在那些有难度的地方，可以得到很好的解决。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 解释Java 8-中间操作与终端操作？
流操作可以分为两部分：

中间操作 -返回另一个Stream的中间操作，允许操作以查询的形式连接。

终端操作 -产生非流，结果如原始值，集合或根本没有值。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## hashMap原理，java8做的改变
从结构实现来讲，HashMap是数组+链表+红黑树（JDK1.8增加了红黑树部分）实现的。HashMap最多只允许一条记录的键为null，允许多条记录的值为null。HashMap非线程安全。ConcurrentHashMap线程安全。解决碰撞：当出现冲突时，运用拉链法，将关键词为同义词的结点链接在一个单链表中，散列表长m，则定义一个由m个头指针组成的指针数组T，地址为i的结点插入以T(i)为头指针的单链表中。Java8中，冲突的元素超过限制（8），用红黑树替换链表。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java 8中的可选项是什么？
Java 8引入了一个新的容器类java.util.Optional 。如果该值可用，它将包装一个值。如果该值不可用，则应返回空的可选项。因此它代表空值，缺失值。这个类有各种实用方法，如isPresent（），它可以帮助用户避免使用空值检查。由于不直接返回值，而是返回包装器对象，所以用户可以避免空指针异常。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java8支持函数编程是什么意思？
在Java 8之前，所有东西都是面向对象的。除了原语之外，java中的 所有内容都作为对象存在。对方法/函数的所有调用都是使用对象或类引用进行的。

方法/功能本身并不是独立存在的。

使用Java 8，引入了函数式编程。所以我们可以使用匿名函数。Java是一种一流的面向对象语言。除了原始数据类型之外，Java中的所有内容都是一个对象。即使是一个数组也是一个对象。每个类都创建对象的实例。没有办法只定义一个独立于Java的函数/方法。无法将方法作为参数传递或返回该实例的方法体。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## java8中的 抽象类 和 接口 有哪些异同？
```
抽象类：含有 abstract 修饰符的 class 就算 抽象类；它既可以有抽象方法，也可以有 普通方法，构造方法，静态方法，但是不能有抽象构造方法 和 抽象静态方法。且如果其子类没有实现其所有的 抽象方法，那么该 子类 也必须是 抽象类；
接口：他可以看成是 抽象类的 一个特例，使用 interface 修饰符；
内部结构：
    jdk7：接口只有常量和抽象方法，无构造器
    jdk8：接口增加了 默认方法 和 静态方法，无构造器
    jdk9：接口允许 以 private 修饰的方法，无构造器
共同点：
    不能实例化；
    多态方式的一种使用；
不同点：
    抽象类是单继承的，而接口可以多继承（实现）；

```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java 8 新特性简介有哪些
```
1. 代码更少（增加了新语法：Lambda 表达式）
2. 强大的 Stream API（集合数据的操作）
3. 最大化的减少空指针 异常：Optional 类 的使用
4. 接口的新特性
5. 注解的新特性
6. 集合的底层 源码实现
7. 新日期时间的 api
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何监控 Elasticsearch 集群状态？
Marvel 让你可以很简单的通过 Kibana 监控 Elasticsearch。你可以实时查看你的集群健康状态和性能，也可以分析过去的集群、索引和节点指标。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在并发情况下，Elasticsearch 如果保证读写一致？
* 可以通过版本号使用乐观并发控制，以确保新版本不会被旧版本覆盖，由应用层来处理具体的冲突；
* 另外对于写操作，一致性级别支持 quorum/one/all，默认为 quorum，即只有当大多数分片可用时才允许写操作。但即使大多数可用，也可能存在因为网络等原因导致写入副本失败，这样该副本被认为故障，分片将会在一个不同的节点上重建。
* 对于读操作，可以设置 replication 为 sync(默认)，这使得操作在主分片和副本分片都完成后才会返回；如果设置 replication 为 async 时，也可以通过设置搜索请求参数_preference 为 primary 来查询主分片，确保文档是最新版本。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 对于 GC 方面，在使用 Elasticsearch 时要注意什么？* 倒排词典的索引需要常驻内存，无法 GC，需要监控 data node 上 segmentmemory 增长趋势。
* 各类缓存，field cache, filter cache, indexing cache, bulk queue 等等，要设置合理的大小，并且要应该根据最坏的情况来看 heap 是否够用，也就是各类缓存全部占满的时候，还有 heap 空间可以分配给其他任务吗？避免采用 clear cache等“自欺欺人”的方式来释放内存。
* 避免返回大量结果集的搜索与聚合。确实需要大量拉取数据的场景，可以采用scan & scroll api 来实现。
* cluster stats 驻留内存并无法水平扩展，超大规模集群可以考虑分拆成多个集群通过 tribe node 连接。
* 想知道 heap 够不够，必须结合实际应用场景，并对集群的 heap 使用情况做持续的监控。
* 根据监控数据理解内存需求，合理配置各类circuit breaker，将内存溢出风险降低到最低

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在 Elasticsearch 中，是怎么根据一个词找到对应的倒排索引的？
（1）Lucene的索引过程，就是按照全文检索的基本过程，将倒排表写成此文件格式的过程。
（2）Lucene的搜索过程，就是按照此文件格式将索引进去的信息读出来，然后计算每篇文档打分(score)的过程。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 客户端在和集群连接时，如何选择特定的节点执行请求？
TransportClient 利用 transport 模块远程连接一个 elasticsearch 集群。它并不加入到集群中，只是简单的获得一个或者多个初始化的 transport 地址，并以 轮询 的方式与这些地址进行通信。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Elasticsearch 在部署时，对 Linux 的设置有哪些优化方法？* 64 GB 内存的机器是非常理想的， 但是 32 GB 和 16 GB 机器也是很常见的。少于 8 GB 会适得其反。
* 如果你要在更快的 CPUs 和更多的核心之间选择，选择更多的核心更好。多个内核提供的额外并发远胜过稍微快一点点的时钟频率。
* 如果你负担得起 SSD，它将远远超出任何旋转介质。 基于 SSD 的节点，查询和索引性能都有提升。如果你负担得起，SSD 是一个好的选择。
* 即使数据中心们近在咫尺，也要避免集群跨越多个数据中心。绝对要避免集群跨越大的地理距离。
* 请确保运行你应用程序的 JVM 和服务器的 JVM 是完全一样的。 在Elasticsearch 的几个地方，使用 Java 的本地序列化。
* 通过设置 gateway.recover_after_nodes、gateway.expected_nodes、gateway.recover_after_time 可以在集群重启的时候避免过多的分片交换，这可能会让数据恢复从数个小时缩短为几秒钟。
* Elasticsearch 默认被配置为使用单播发现，以防止节点无意中加入集群。只有在同一台机器上运行的节点才会自动组成集群。最好使用单播代替组播。
* 不要随意修改垃圾回收器（CMS）和各个线程池的大小。
* 把你的内存的（少于）一半给 Lucene（但不要超过 32 GB！），通过ES_HEAP_SIZE 环境变量设置。
* 内存交换到磁盘对服务器性能来说是致命的。如果内存交换到磁盘上，一个100 微秒的操作可能变成 10 毫秒。 再想想那么多 10 微秒的操作时延累加起来。 不难看出 swapping 对于性能是多么可怕。
* Lucene 使用了大 量 的文件。同时，Elasticsearch 在节点和 HTTP 客户端之间进行通信也使用了大量的套接字。 所有这一切都需要足够的文件描述符。你应该增加你的文件描述符，设置一个很大的值，如 64,000。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说说Elasticsearch常用的调优手段？
设计阶段调优
（1）根据业务增量需求，采取基于日期模板创建索引，通过 roll over API 滚动索引；
（2）使用别名进行索引管理；
（3）每天凌晨定时对索引做 force_merge 操作，以释放空间；
（4）采取冷热分离机制，热数据存储到 SSD，提高检索效率；冷数据定期进行 shrink操作，以缩减存储；
（5）采取 curator 进行索引的生命周期管理；
（6）仅针对需要分词的字段，合理的设置分词器；
（7）Mapping 阶段充分结合各个字段的属性，是否需要检索、是否需要存储等。……..

写入调优
（1）写入前副本数设置为 0；
（2）写入前关闭 refresh_interval 设置为-1，禁用刷新机制；
（3）写入过程中：采取 bulk 批量写入；
（4）写入后恢复副本数和刷新间隔；
（5）尽量使用自动生成的 id。

查询调优
（1）禁用 wildcard；
（2）禁用批量 terms（成百上千的场景）；
（3）充分利用倒排索引机制，能 keyword 类型尽量 keyword；
（4）数据量大时候，可以先基于时间敲定索引再检索；
（5）设置合理的路由机制。

其他调优
部署调优，业务调优等。
上面的提及一部分，面试者就基本对你之前的实践或者运维经验有所评估了。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## Elasticsearch中的分析器是什么？
在ElasticSearch中索引数据时，数据由为索引定义的Analyzer在内部进行转换。 分析器由一个Tokenizer和零个或多个TokenFilter组成。编译器可以在一个或多个CharFilter之前。分析模块允许您在逻辑名称下注册分析器，然后可以在映射定义或某些API中引用它们。

Elasticsearch附带了许多可以随时使用的预建分析器。或者，您可以组合内置的字符过滤器，编译器和过滤器器来创建自定义分析器。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Elasticsearch中的倒排索引是什么？
倒排索引是搜索引擎的核心。搜索引擎的主要目标是在查找发生搜索条件的文档时提供快速搜索。倒排索引是一种像数据结构一样的散列图，可将用户从单词导向文档或网页。它是搜索引擎的核心。其主要目标是快速搜索从数百万文件中查找数据。 

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是ElasticSearch？Elasticsearch是一个基于Lucene的搜索引擎。它提供了具有HTTP Web界面和无架构JSON文档的分布式，多租户能力的全文搜索引擎。Elasticsearch是用Java开发的，根据Apache许可条款作为开源发布。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## ElasticSearch中的分片是什么?在大多数环境中，每个节点都在单独的盒子或虚拟机上运行。

* 索引 - 在Elasticsearch中，索引是文档的集合。
* 分片 -因为Elasticsearch是一个分布式搜索引擎，所以索引通常被分割成分布在多个节点上的被称为分片的元素。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## ElasticSearch中的集群、节点、索引、文档、类型是什么？
群集是一个或多个节点（服务器）的集合，它们共同保存您的整个数据，并提供跨所有节点的联合索引和搜索功能。群集由唯一名称标识，默认情况下为“elasticsearch”。此名称很重要，因为如果节点设置为按名称加入群集，则该节点只能是群集的一部分。

节点是属于集群一部分的单个服务器。它存储数据并参与群集索引和搜索功能。

索引就像关系数据库中的“数据库”。它有一个定义多种类型的映射。索引是逻辑名称空间，映射到一个或多个主分片，并且可以有零个或多个副本分片。 MySQL =>数据库，ElasticSearch =>索引。

文档类似于关系数据库中的一行。不同之处在于索引中的每个文档可以具有不同的结构（字段），但是对于通用字段应该具有相同的数据类型。 MySQL => Databases =>Tables => Columns / Rows， ElasticSearch => Indices => Types =>具有属性的文档。

类型是索引的逻辑类别/分区，其语义完全取决于用户。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在并发情况下，Elasticsearch如果保证读写一致？可以通过版本号使用乐观并发控制，以确保新版本不会被旧版本覆盖，由应用层来处理具体的冲突；

另外对于写操作，一致性级别支持quorum/one/all，默认为quorum，即只有当大多数分片可用时才允许写操作。但即使大多数可用，也可能存在因为网络等原因导致写入副本失败，这样该副本被认为故障，分片将会在一个不同的节点上重建。

对于读操作，可以设置replication为sync(默认)，这使得操作在主分片和副本分片都完成后才会返回；如果设置replication为async时，也可以通过设置搜索请求参数_preference为primary来查询主分片，确保文档是最新版本。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Elasticsearch对于大数据量（上亿量级）的聚合如何实现？Elasticsearch 提供的首个近似聚合是cardinality 度量。

它提供一个字段的基数，即该字段的distinct或者unique值的数目。它是基于HLL算法的。HLL 会先对我们的输入作哈希运算，然后根据哈希运算的结果中的 bits 做概率估算从而得到基数。

其特点是：可配置的精度，用来控制内存的使用（更精确 ＝ 更多内存）；小的数据集精度是非常高的；我们可以通过配置参数，来设置去重需要的固定内存使用量。无论数千还是数十亿的唯一值，内存使用量只与你配置的精确度相关 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 详细描述一下Elasticsearch搜索的过程搜索被执行成一个两阶段过程，我们称之为 Query Then Fetch；

在初始查询阶段时，查询会广播到索引中每一个分片拷贝（主分片或者副本分片）。 每个分片在本地执行搜索并构建一个匹配文档的大小为 from + size 的优先队列。PS：在搜索的时候是会查询Filesystem Cache的，但是有部分数据还在Memory Buffer，所以搜索是近实时的。

每个分片返回各自优先队列中 所有文档的 ID 和排序值 给协调节点，它合并这些值到自己的优先队列中来产生一个全局排序后的结果列表。

接下来就是 取回阶段，协调节点辨别出哪些文档需要被取回并向相关的分片提交多个 GET 请求。每个分片加载并 丰富 文档，如果有需要的话，接着返回文档给协调节点。一旦所有的文档都被取回了，协调节点返回结果给客户端。

补充：Query Then Fetch的搜索类型在文档相关性打分的时候参考的是本分片的数据，这样在文档数量较少的时候可能不够准确，DFS Query Then Fetch增加了一个预查询的处理，询问Term和Document frequency，这个评分更准确，但是性能会变差。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 详细描述一下Elasticsearch更新和删除文档的过程删除和更新也都是写操作，但是Elasticsearch中的文档是不可变的，因此不能被删除或者改动以展示其变更；

磁盘上的每个段都有一个相应的.del文件。当删除请求发送后，文档并没有真的被删除，而是在.del文件中被标记为删除。该文档依然能匹配查询，但是会在结果中被过滤掉。当段合并时，在.del文件中被标记为删除的文档将不会被写入新段。

在新的文档被创建时，Elasticsearch会为该文档指定一个版本号，当执行更新时，旧版本的文档在.del文件中被标记为删除，新版本的文档被索引到一个新段。旧版本的文档依然能匹配查询，但是会在结果中被过滤掉。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 详细描述一下Elasticsearch索引文档的过程。* 当分片所在的节点接收到来自协调节点的请求后，会将请求写入到 MemoryBuffer，然后定时（默认是每隔 1 秒）写入到 Filesystem Cache，这个从 MomeryBuffer 到 Filesystem Cache 的过程就叫做 refresh；
* 当然在某些情况下，存在 Momery Buffer 和 Filesystem Cache 的数据可能会丢失，ES 是通过 translog 的机制来保证数据的可靠性的。其实现机制是接收到请求后，同时也会写入到 translog 中，当 Filesystem cache 中的数据写入到磁盘中时，才会清除掉，这个过程叫做 flush；
* 在 flush 过程中，内存中的缓冲将被清除，内容被写入一个新段，段的 fsync将创建一个新的提交点，并将内容刷新到磁盘，旧的 translog 将被删除并开始一个新的 translog。
* flush 触发的时机是定时触发（默认 30 分钟）或者 translog 变得太大（默认为 512M）时；
*** 
## ⭐️⭐️⭐️⭐️⭐️
## Elasticsearch中的节点（比如共20个），其中的10个选了一个master，另外10个选了另一个master，怎么办？* 当集群master候选数量不小于3个时，可以通过设置最少投票通过数量（discovery.zen.minimum_master_nodes）超过所有候选节点一半以上来解决脑裂问题；
* 当候选数量为两个时，只能修改为唯一的一个master候选，其他作为data节点，避免脑裂问题。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Elasticsearch是如何实现Master选举的？Elasticsearch的选主是ZenDiscovery模块负责的，主要包含Ping（节点之间通过这个RPC来发现彼此）和Unicast（单播模块包含一个主机列表以控制哪些节点需要ping通）这两部分；

* 对所有可以成为master的节点（node.master: true）根据nodeId字典排序，每次选举每个节点都把自己所知道节点排一次序，然后选出第一个（第0位）节点，暂且认为它是master节点。
* 如果对某个节点的投票数达到一定的值（可以成为master节点数n/2+1）并且该节点自己也选举自己，那这个节点就是master。否则重新选举一直到满足上述条件。

补充：master节点的职责主要包括集群、节点和索引的管理，不负责文档级别的管理；data节点可以关闭http功能。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么要使用Elasticsearch?
因为在我们的数据，将来会非常多，所以采用以往的模糊查询，模糊查询前置配置，会放弃索引，导致商品查询是全表扫面，在百万级别的数据库中，效率非常低下，而我们使用ES做一个全文索引，我们将经常查询的商品的某些字段，比如说商品名，描述、价格还有id这些字段我们放入我们索引库里，可以提高查询速度。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说说 Dubbo 服务暴露的过程。
Dubbo 会在 Spring 实例化完 bean 之后，在刷新容器最后一步发布 ContextRefreshEvent 事件的时候，通知实现了 ApplicationListener 的 ServiceBean 类进行回调 onApplicationEvent 事件方法，Dubbo 会在这个方法中调用 ServiceBean 父类 ServiceConfig 的 export 方法，而该方法真正实现了服务的（异步或者非异步）发布。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## Dubbo的管理控制台能做什么？
管理控制台主要包含：路由规则，动态配置，服务降级，访问控制，权重调整，负载均衡，等管理功能。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Dubbo必须依赖的包有哪些？
Dubbo 必须依赖 JDK，其他为可选。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 服务读写推荐的容错策略是怎样的？
读操作建议使用 Failover 失败自动切换，默认重试两次其他服务器。

写操作建议使用 Failfast 快速失败，发一次调用失败就立即报错。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何解决服务调用链过长的问题？
Dubbo 可以使用 Pinpoint 和 Apache Skywalking(Incubator) 实现分布式服务追踪，当然还有其他很多方案。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 服务提供者能实现失效踢出是什么原理？
服务失效踢出基于 Zookeeper 的临时节点原理。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Dubbo如何优雅停机？
Dubbo 是通过 JDK 的 ShutdownHook 来完成优雅停机的，所以如果使用 kill -9 PID 等强制关闭指令，是不会执行优雅停机的，只有通过 kill PID 时，才会执行。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Dubbo支持服务降级吗？
Dubbo 2.2.0 以上版本支持。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Dubbo支持分布式事务吗？
目前暂时不支持，后续可能采用基于 JTA/XA 规范实现。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Dubbo服务之间的调用是阻塞的吗？
默认是同步等待结果阻塞的，支持异步调用。

Dubbo 是基于 NIO 的非阻塞实现并行调用，客户端不需要启动多线程即可完成并行调用多个远程服务，相对多线程开销较小，异步调用会返回一个 Future 对象。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Dubbo可以对结果进行缓存吗？
可以，Dubbo 提供了声明式缓存，用于加速热门数据的访问速度，以减少用户加缓存的工作量。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 服务上线怎么兼容旧版本？
可以用版本号（version）过渡，多个不同版本的服务注册到注册中心，版本号不同的服务相互间不引用。这个和服务分组的概念有一点类似。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 当一个服务接口有多种实现时怎么做？
当一个接口有多种实现时，可以用 group 属性来分组，服务提供方和消费方都指定同一个 group 即可。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Dubbo支持服务多协议吗？
Dubbo 允许配置多协议，在不同服务上支持不同协议或者同一服务上同时支持多种协议。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 注册了多个同一样的服务，如果测试指定的某一个服务呢？
可以配置环境点对点直连，绕过注册中心，将以服务接口为单位，忽略注册中心的提供者列表。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Dubbo默认使用的是什么通信框架，还有别的选择吗？
Dubbo 默认使用 Netty 框架，也是推荐的选择，另外内容还集成有Mina、Grizzly。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Dubbo推荐使用什么序列化框架，你知道的还有哪些？
推荐使用Hessian序列化，还有Duddo、FastJson、Java自带序列化。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Dubbo启动时如果依赖的服务不可用会怎样？
Dubbo 缺省会在启动时检查依赖的服务是否可用，不可用时会抛出异常，阻止 Spring 初始化完成，默认 check="true"，可以通过 check="false" 关闭检查。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在 Provider 上可以配置的 Consumer 端的属性有哪些？
1）timeout：方法调用超时
2）retries：失败重试次数，默认重试 2 次
3）loadbalance：负载均衡算法，默认随机
4）actives 消费者端，最大并发调用限制

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Dubbo有哪几种配置方式？
1）Spring 配置方式
2）Java API 配置方式

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Dubbo默认使用什么注册中心，还有别的选择吗？
推荐使用 Zookeeper 作为注册中心，还有 Redis、Multicast、Simple 注册中心，但不推荐。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Dubbo内置了哪几种服务容器？
Spring Container

Jetty Container

Log4j Container

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Dubbo是什么？
Dubbo是阿里巴巴开源的基于 Java 的高性能 RPC 分布式服务框架，现已成为 Apache 基金会孵化项目。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在使用 Docker 技术的产品中如何监控其运行
Docker 在产品中提供如 运行统计和 Docker 事件的工具。可以通过这些工具命令获取 Docker 运行状况的统计信息或报告。

Docker stats ： 通过指定的容器 id 获取其运行统计信息，可获得容器对 CPU，内存使用情况等的统计信息，类似 Linux 系统中的 top 命令。
Docker events ：Docker 事件是一个命令，用于观察显示运行中的 Docker 一系列的行为活动。
一般的 Docker 事件有：attach（关联），commit（提交），die（僵死），detach（取消关联），rename（改名），destory（销毁）等。也可使用多个选项对事件记录筛选找到想要的事件信息。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Docker 群（Swarm）是什么
Docker Swarm -- Docker 群 -- 是原生的 Docker 集群服务工具。它将一群 Docker 主机集成为单一一个虚拟 Docker 主机。利用一个 Docker 守护进程，通过标准的 Docker API 和任何完善的通讯工具，Docker Swarm 提供透明地将 Docker 主机扩散到多台主机上的服务。

群（swarm）是一个运行了docker并加入到簇（cluster）的设备集合。在集群之后，我们任然可以像以前那样执行docker命令，只不过现在命令的执行交个群管理器（swarm manager）来执行。刚才我们提到的设备可以是实际存在的物理机也可以是虚拟机，此时每个设备我们称为节点（node）。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何清理批量后台停止的容器？
使用docker rm $（sudo docker ps -a -q）

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何停止所有正在运行的容器？
使用docker kill $(sudo docker ps -q)

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Docker Image 和 Docker Layer (层) 有什么不同
Image ：一个 Docker Image 是由一系列 Docker 只读层（read-only Layer） 创建出来的。
Layer： 在 Dockerfile 配置文件中完成的一条配置指令，即表示一个 Docker 层（Layer）。
如下 Dockerfile 文件包含 4 条指令，每条指令创建一个层（Layer）。

```
FROM ubuntu:15.04
COPY . /app
RUN make /app
CMD python /app/app.py
```

重点，每层只对其前一层进行一（某）些进化。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 有什么方法确定一个 Docker 容器运行状态
使用如下命令行命令确定一个 Docker 容器的运行状态

```
$ docker ps –a
```

这将列表形式输出运行在主机上的所有 Docker 容器及其运行状态。从这个列表中很容易找到想要的容器及其运行状态。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何使用 Docker 技术创建与环境无关的容器系统？
Docker 技术有三中主要的技术途径辅助完成此需求：

- 存储卷（Volumes）
- 环境变量（Environment variable）注入
- 只读（Read-only）文件系统

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Service Mesh了解过吗？什么是service mesh
===============

       根据Linkerd CEO William Morgan定义，Service Mesh是用于处理服务间通信的基础设施层，用于在云原生应用复杂的服务拓扑中实现可靠的请求传递。在实践中，Service Mesh通常是一组与应用一起部署，但对应用透明的轻量级网络代理。

基本结构图如下：

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9ncnN0YXRpYy5vc3MtY24tc2hhbmdoYWkuYWxpeXVuY3MuY29tL2ltYWdlcy9hcnRpY2xlL3doYXQtaXMtc2VydmljZS1tZXNoLTEucG5n)

        在实践中，Service Mesh基本来说是一组轻量级的服务代理和应用逻辑的服务在一起，同生共死，并且对于应用服务是透明的。具体的部署方式类似下面这样。

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9ncnN0YXRpYy5vc3MtY24tc2hhbmdoYWkuYWxpeXVuY3MuY29tL2ltYWdlcy9hcnRpY2xlL3doYXQtaXMtc2VydmljZS1tZXNoLTIucG5n)

       如何理解sidecar呢？可以参考下面的图，边上的人可以专注的做自己的事情，而sidercar负责处理开车相关的事情，实现业务和通用功能的分离。

![](https://imgconvert.csdnimg.cn/aHR0cDovL3d4MS5zaW5haW1nLmNuL2xhcmdlL2FkNWZiZjY1bHkxZzE4emhub2g3NmoyMGR3MGR3NzUyLmpwZw)

为什么要这么设计呢？是因为在当前的微服务发展中，有几个问题逐渐暴露出来：

1.  业务服务的代码和微服务的SDK强耦合在一起导致业务升级和微服务SDK的升级强绑定在了一起。
2.  对于异构的系统，需要开发多语言的SDK，维护成本很高。

Service Mesh如何解决上述问题呢？Service Mesh会抽离微服务中的通用功能，比如服务注册发现，负载均衡，熔断降级，限流扩容，监控等功能，把这些功能放到sidercar中，通过代理的方式于业务服务进行通信，从而解决上面的问题。

istlo介绍
=======

Istio是Google、IBM和Lyft联合开源的微服务Service Mesh框架，旨在解决大量微服务的发现、连接、管理、监控以及安全等问题。

Istio是对Service Mesh的产品化实践，帮助微服务实现了分层解耦，此时的sidecar具有一下功能：

_（1）服务发现(discovery)_

_（2）负载均衡(load balancing)_

_（3）故障恢复(failure recovery)_

_（4）服务度量(metrics)_

_（5）服务监控(monitoring)_

_（6）A/B测试(A/B testing)_

_（7）灰度发布(canary rollouts)_

_（8）限流限速(rate limiting)_

_（9）访问控制(access control)_

_（10）身份认证(end-to-end authentication)_

架构图如下：

![](https://img-blog.csdnimg.cn/20190729110311255.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2h1d2VpMDUxOA==,size_16,color_FFFFFF,t_70)

逻辑上Istio分为数据平面(data pane)和控制平面(control pane)：

*   数据平面用于有一些智能代理组成，微服务之间的网络通信，
*   控制平面负责对智能代理进行管理和配置。

**主要由以下组件构成**
-------------

**数据平面，有一个核心组件：**

**Envoy (proxy)**

Envoy的核心职责是高效转发，更具体的，它具备这样一些能力：

_（1）服务发现_

_（2）负载均衡_

_（3）安全传输_

_（4）多协议支持，例如HTTP/2，gRPC_

_（5）断路器(Circuit breakers)_

_（6）健康检查_

_（7）百分比分流路由_

_（8）故障注入(Fault injection)_

_（9）系统度量_

**控制平面，有四个核心组件：**

**Mixer**

Mixer的一些核心能力是：

（1）跨平台，作为其他组件的adapter，实现Istio跨平台的能力；

（2）和Envoy通讯，实时各种策略

（3）和Envoy通讯，收集各种数据

Mixer的设计核心在于“插件化”，这种模型使得Istio能够适配各种复杂的主机环境，以及后端基础设施。

**Pilot**

Pilot作为非常重要的控制平面组件，其核心能力是：

（1）为Envoy提供服务发现能力；

（2）为Envoy提供各种智能路由管理能力，例如A/B测试，灰度发布；

（3）为Envoy提供各种弹性管理能力，例如超时，重试，断路策略；

Pilot的设计核心在于“标准化”，它会将各种流控的控制命令转化为Envoy能够识别的配置，并在运行时，将这些指令扩散到所有的Envoy。Pilot将这些能力抽象成通用配置的好处是，所有符合这种标准的Envoy都能够接入到Pilot来。

潜台词是，任何第三方可以实现自己的proxy，只要符合相关的API标准，都可以和Pilot集成。

**Citadel**

Citadel组件，它提供终端用户身份认证，以及服务到服务的访问控制。总之，这是一个和安全相关的组件。

**Galley**

Gally组件，它是一个配置获取、校验、处理、分发的组件，它的设计核心在于“解耦”，它将“从底层平台（例如：K8S）获取用户配置”与Istio解耦开来。
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 作为注册中心，Zookeeper和Eureka有什么区别？**1\. 前言**  

=============

服务注册中心，给客户端提供可供调用的服务列表，客户端在进行远程服务调用时，根据服务列表然后选择服务提供方的服务地址进行服务调用。服务注册中心在分布式系统中大量应用，是分布式系统中不可或缺的组件，例如rocketmq的name server，hdfs中的namenode，dubbo中的zk注册中心，spring cloud中的服务注册中心eureka。

在spring cloud中，除了可以使用eureka作为注册中心外，还可以通过配置的方式使用zookeeper作为注册中心。既然这样，我们该如何选择注册中心的实现呢？

著名的CAP理论指出，一个分布式系统不可能同时满足C(一致性)、A(可用性)和P(分区容错性)。由于分区容错性在是分布式系统中必须要保证的，因此我们只能在A和C之间进行权衡。在此Zookeeper保证的是CP, 而Eureka则是AP。

**2\. Zookeeper保证CP**
=====================

当向注册中心查询服务列表时，我们可以容忍注册中心返回的是几分钟以前的注册信息，但不能接受服务直接down掉不可用。也就是说，服务注册功能对可用性的要求要高于一致性。但是zk会出现这样一种情况，当master节点因为网络故障与其他节点失去联系时，剩余节点会重新进行leader选举。问题在于，选举leader的时间太长，30 ~ 120s, 且选举期间整个zk集群都是不可用的，这就导致在选举期间注册服务瘫痪。在云部署的环境下，因网络问题使得zk集群失去master节点是较大概率会发生的事，虽然服务能够最终恢复，但是漫长的选举时间导致的注册长期不可用是不能容忍的。

**3\. Eureka保证AP**
==================

Eureka看明白了这一点，因此在设计时就优先保证可用性。Eureka各个节点都是平等的，几个节点挂掉不会影响正常节点的工作，剩余的节点依然可以提供注册和查询服务。而Eureka的客户端在向某个Eureka注册或如果发现连接失败，则会自动切换至其它节点，只要有一台Eureka还在，就能保证注册服务可用(保证可用性)，只不过查到的信息可能不是最新的(不保证强一致性)。除此之外，Eureka还有一种自我保护机制，如果在15分钟内超过85%的节点都没有正常的心跳，那么Eureka就认为客户端与注册中心出现了网络故障，此时会出现以下几种情况：   
1\. Eureka不再从注册列表中移除因为长时间没收到心跳而应该过期的服务   
2\. Eureka仍然能够接受新服务的注册和查询请求，但是不会被同步到其它节点上(即保证当前节点依然可用)   
3\. 当网络稳定时，当前实例新的注册信息会被同步到其它节点中

因此， Eureka可以很好的应对因网络故障导致部分节点失去联系的情况，而不会像zookeeper那样使整个注册服务瘫痪。

**4\. 更深入的探讨**
==============

下面转发一篇更深入探讨zookeeper与eureka作为注册中心区别的问题，文章转发自

http://dockone.io/article/78 ，该文翻译了国外的一篇文章。

**4.1 为什么不应该使用ZooKeeper做服务发现**
------------------------------

【编者的话】本文作者通过ZooKeeper与Eureka作为Service发现服务（注：WebServices体系中的UDDI就是个发现服务）的优劣对比，分享了Knewton在云计算平台部署服务的经验。本文虽然略显偏激，但是看得出Knewton在云平台方面是非常有经验的，这篇文章从实践角度出发分别从云平台特点、CAP原理以及运维三个方面对比了ZooKeeper与Eureka两个系统作为发布服务的优劣，并提出了在云平台构建发现服务的方法论。

**4.2 背景**
----------

很多公司选择使用ZooKeeper作为Service发现服务（Service Discovery），但是在构建Knewton（Knewton是一个提供个性化教育平台的公司、学校和出版商可以通过Knewton平台为学生提供自适应的学习材料）平台时，我们发现这是个根本性的错误。在这边文章中，我们将用我们在实践中遇到的问题来说明，为什么使用ZooKeeper做Service发现服务是个错误。

**4.3 请留意服务部署环境**
-----------------

让我们从头开始梳理。我们在部署服务的时候，应该首先考虑服务部署的平台（平台环境），然后才能考虑平台上跑的软件系统或者如何在选定的平台上自己构建一套系统。例如，对于云部署平台来说，平台在硬件层面的伸缩（注：作者应该指的是系统的冗余性设计，即系统遇到单点失效问题，能够快速切换到其他节点完成任务）与如何应对网络故障是首先要考虑的。当你的服务运行在大量服务器构建的集群之上时（注：原话为大量可替换设备），则肯定会出现单点故障的问题。对于knewton来说，我们虽然是部署在AWS上的，但是在过往的运维中，我们也遇到过形形色色的故障；所以，你应该把系统设计成“故障开放型”（expecting failure）的。其实有很多同样使用AWS的公司跟我们遇到了（同时有很多书是介绍这方面的）相似的问题。你必须能够提前预料到平台可能会出现的问题如：意外故障（注：原文为box failure，只能意会到作者指的是意外弹出的错误提示框），高延迟与网络分割问题（注：原文为network partitions。意思是当网络交换机出故障会导致不同子网间通讯中断）——同时我们要能构建足够弹性的系统来应对它们的发生。

永远不要期望你部署服务的平台跟其他人是一样的！当然，如果你在独自运维一个数据中心，你可能会花很多时间与钱来避免硬件故障与网络分割问题，这是另一种情况了；但是在云计算平台中，如AWS，会产生不同的问题以及不同的解决方式。当你实际使用时你就会明白，但是，你最好提前应对它们（注：指的是上一节说的意外故障、高延迟与网络分割问题）的发生。

**4.4 ZooKeeper作为发现服务的问题**
--------------------------

ZooKeeper（注：ZooKeeper是著名Hadoop的一个子项目，旨在解决大规模分布式应用场景下，服务协调同步（Coordinate Service）的问题；它可以为同在一个分布式系统中的其他服务提供：统一命名服务、配置管理、分布式锁服务、集群管理等功能）是个伟大的开源项目，它很成熟，有相当大的社区来支持它的发展，而且在生产环境得到了广泛的使用；但是用它来做Service发现服务解决方案则是个错误。

在分布式系统领域有个著名的CAP定理（C-数据一致性；A-服务可用性；P-服务对网络分区故障的容错性，这三个特性在任何分布式系统中不能同时满足，最多同时满足两个）；ZooKeeper是个CP的，即任何时刻对ZooKeeper的访问请求能得到一致的数据结果，同时系统对网络分割具备容错性；但是它不能保证每次服务请求的可用性（注：也就是在极端环境下，ZooKeeper可能会丢弃一些请求，消费者程序需要重新请求才能获得结果）。但是别忘了，ZooKeeper是分布式协调服务，它的职责是保证数据（注：配置数据，状态数据）在其管辖下的所有服务之间保持同步、一致；所以就不难理解为什么ZooKeeper被设计成CP而不是AP特性的了，如果是AP的，那么将会带来恐怖的后果（注：ZooKeeper就像交叉路口的信号灯一样，你能想象在交通要道突然信号灯失灵的情况吗？）。而且，作为ZooKeeper的核心实现算法Zab，就是解决了分布式系统下数据如何在多个服务之间保持同步问题的。

作为一个分布式协同服务，ZooKeeper非常好，但是对于Service发现服务来说就不合适了；因为对于Service发现服务来说就算是返回了包含不实的信息的结果也比什么都不返回要好；再者，对于Service发现服务而言，宁可返回某服务5分钟之前在哪几个服务器上可用的信息，也不能因为暂时的网络故障而找不到可用的服务器，而不返回任何结果。所以说，用ZooKeeper来做Service发现服务是肯定错误的，如果你这么用就惨了！

而且更何况，如果被用作Service发现服务，ZooKeeper本身并没有正确的处理网络分割的问题；而在云端，网络分割问题跟其他类型的故障一样的确会发生；所以最好提前对这个问题做好100%的准备。就像Jepsen在ZooKeeper网站上发布的博客中所说：在ZooKeeper中，如果在同一个网络分区（partition）的节点数（nodes）数达不到ZooKeeper选取Leader节点的“法定人数”时，它们就会从ZooKeeper中断开，当然同时也就不能提供Service发现服务了。

如果给ZooKeeper加上客户端缓存（注：给ZooKeeper节点配上本地缓存）或者其他类似技术的话可以缓解ZooKeeper因为网络故障造成节点同步信息错误的问题。Pinterest与Airbnb公司就使用了这个方法来防止ZooKeeper故障发生。这种方式可以从表面上解决这个问题，具体地说，当部分或者所有节点跟ZooKeeper断开的情况下，每个节点还可以从本地缓存中获取到数据；但是，即便如此，ZooKeeper下所有节点不可能保证任何时候都能缓存所有的服务注册信息。如果ZooKeeper下所有节点都断开了，或者集群中出现了网络分割的故障（注：由于交换机故障导致交换机底下的子网间不能互访）；那么ZooKeeper会将它们都从自己管理范围中剔除出去，外界就不能访问到这些节点了，即便这些节点本身是“健康”的，可以正常提供服务的；所以导致到达这些节点的服务请求被丢失了。（注：这也是为什么ZooKeeper不满足CAP中A的原因）

更深层次的原因是，ZooKeeper是按照CP原则构建的，也就是说它能保证每个节点的数据保持一致，而为ZooKeeper加上缓存的做法的目的是为了让ZooKeeper变得更加可靠（available）；但是，ZooKeeper设计的本意是保持节点的数据一致，也就是CP。所以，这样一来，你可能既得不到一个数据一致的（CP）也得不到一个高可用的（AP）的Service发现服务了；因为，这相当于你在一个已有的CP系统上强制栓了一个AP的系统，这在本质上就行不通的！一个Service发现服务应该从一开始就被设计成高可用的才行！

如果抛开CAP原理不管，正确的设置与维护ZooKeeper服务就非常的困难；错误会经常发生，导致很多工程被建立只是为了减轻维护ZooKeeper的难度。这些错误不仅存在与客户端而且还存在于ZooKeeper服务器本身。Knewton平台很多故障就是由于ZooKeeper使用不当而导致的。那些看似简单的操作，如：正确的重建观察者（reestablishing watcher）、客户端Session与异常的处理与在ZK窗口中管理内存都是非常容易导致ZooKeeper出错的。同时，我们确实也遇到过ZooKeeper的一些经典bug：ZooKeeper-1159 与ZooKeeper-1576；我们甚至在生产环境中遇到过ZooKeeper选举Leader节点失败的情况。这些问题之所以会出现，在于ZooKeeper需要管理与保障所管辖服务群的Session与网络连接资源（注：这些资源的管理在分布式系统环境下是极其困难的）；但是它不负责管理服务的发现，所以使用ZooKeeper当Service发现服务得不偿失。

**4.5 做出正确的选择：Eureka的成功**
-------------------------

我们把Service发现服务从ZooKeeper切换到了Eureka平台，它是一个开源的服务发现解决方案，由Netflix公司开发。（注：Eureka由两个组件组成：Eureka服务器和Eureka客户端。Eureka服务器用作服务注册服务器。Eureka客户端是一个java客户端，用来简化与服务器的交互、作为轮询负载均衡器，并提供服务的故障切换支持。）Eureka一开始就被设计成高可用与可伸缩的Service发现服务，这两个特点也是Netflix公司开发所有平台的两个特色。（他们都在讨论Eureka）。自从切换工作开始到现在，我们实现了在生产环境中所有依赖于Eureka的产品没有下线维护的记录。我们也被告知过，在云平台做服务迁移注定要遇到失败；但是我们从这个例子中得到的经验是，一个优秀的Service发现服务在其中发挥了至关重要的作用！

首先，在Eureka平台中，如果某台服务器宕机，Eureka不会有类似于ZooKeeper的选举leader的过程；客户端请求会自动切换到新的Eureka节点；当宕机的服务器重新恢复后，Eureka会再次将其纳入到服务器集群管理之中；而对于它来说，所有要做的无非是同步一些新的服务注册信息而已。所以，再也不用担心有“掉队”的服务器恢复以后，会从Eureka服务器集群中剔除出去的风险了。Eureka甚至被设计用来应付范围更广的网络分割故障，并实现“0”宕机维护需求。当网络分割故障发生时，每个Eureka节点，会持续的对外提供服务（注：ZooKeeper不会）：接收新的服务注册同时将它们提供给下游的服务发现请求。这样一来，就可以实现在同一个子网中（same side of partition），新发布的服务仍然可以被发现与访问。

但是，Eureka做到的不止这些。正常配置下，Eureka内置了心跳服务，用于淘汰一些“濒死”的服务器；如果在Eureka中注册的服务，它的“心跳”变得迟缓时，Eureka会将其整个剔除出管理范围（这点有点像ZooKeeper的做法）。这是个很好的功能，但是当网络分割故障发生时，这也是非常危险的；因为，那些因为网络问题（注：心跳慢被剔除了）而被剔除出去的服务器本身是很”健康“的，只是因为网络分割故障把Eureka集群分割成了独立的子网而不能互访而已。

幸运的是，Netflix考虑到了这个缺陷。如果Eureka服务节点在短时间里丢失了大量的心跳连接（注：可能发生了网络故障），那么这个Eureka节点会进入”自我保护模式“，同时保留那些“心跳死亡“的服务注册信息不过期。此时，这个Eureka节点对于新的服务还能提供注册服务，对于”死亡“的仍然保留，以防还有客户端向其发起请求。当网络故障恢复后，这个Eureka节点会退出”自我保护模式“。所以Eureka的哲学是，同时保留”好数据“与”坏数据“总比丢掉任何”好数据“要更好，所以这种模式在实践中非常有效。

最后，Eureka还有客户端缓存功能（注：Eureka分为客户端程序与服务器端程序两个部分，客户端程序负责向外提供注册与发现服务接口）。所以即便Eureka集群中所有节点都失效，或者发生网络分割故障导致客户端不能访问任何一台Eureka服务器；Eureka服务的消费者仍然可以通过Eureka客户端缓存来获取现有的服务注册信息。甚至最极端的环境下，所有正常的Eureka节点都不对请求产生相应，也没有更好的服务器解决方案来解决这种问题时；得益于Eureka的客户端缓存技术，消费者服务仍然可以通过Eureka客户端查询与获取注册服务信息，这点很重要。

Eureka的构架保证了它能够成为Service发现服务。它相对与ZooKeeper来说剔除了Leader节点的选取或者事务日志机制，这样做有利于减少使用者维护的难度也保证了Eureka的在运行时的健壮性。而且Eureka就是为发现服务所设计的，它有独立的客户端程序库，同时提供心跳服务、服务健康监测、自动发布服务与自动刷新缓存的功能。但是，如果使用ZooKeeper你必须自己来实现这些功能。Eureka的所有库都是开源的，所有人都能看到与使用这些源代码，这比那些只有一两个人能看或者维护的客户端库要好。

维护Eureka服务器也非常的简单，比如，切换一个节点只需要在现有EIP下移除一个现有的节点然后添加一个新的就行。Eureka提供了一个web-based的图形化的运维界面，在这个界面中可以查看Eureka所管理的注册服务的运行状态信息：是否健康，运行日志等。Eureka甚至提供了Restful-API接口，方便第三方程序集成Eureka的功能。

**4.6 结论**
----------

关于Service发现服务通过本文我们想说明两点：1、留意服务运行的硬件平台；2、时刻关注你要解决的问题，然后决定使用什么平台。Knewton就是从这两个方面考虑使用Eureka替换ZooKeeper来作为service发现服务的。云部署平台是充满不可靠性的，Eureka可以应对这些缺陷；同时Service发现服务必须同时具备高可靠性与高弹性，Eureke就是我们想要的！
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是代理模式？什么是动态代理？Java中动态代理有哪些实现方式？**摘要：**

　　代理根据代理类的产生方式和时机分为静态代理和动态代理两种。代理类不仅可以有效的将具体的实现与调用方进行解耦，通过面向接口进行编码完全将具体的实现隐藏在内部，而且还可以在符合开闭原则的前提下，对目标类进行进一步的增强。典型地，Spring AOP 是对JDK动态代理的经典应用。

一. 代理与代理模式
----------

**1). 代理**

　　代理模式其实很常见，比如买火车票这件小事：黄牛相当于是我们本人的的代理，我们可以通过黄牛买票。通过黄牛买票，我们可以避免与火车站的直接交互，可以省很多事，并且还能享受到黄牛更好的服务(如果钱给够的话)。在软件开发中，代理也具有类似的作用，并且一般可以分为静态代理和动态代理两种，上述的这个黄牛买票的例子就是静态代理。

　　那么，静态代理与动态代理的区别是什么呢？所谓静态代理，其实质是自己手写(或者用工具生成)代理类，也就是在程序运行前就已经存在的编译好的代理类。但是，如果我们需要很多的代理，每一个都这么去创建实属浪费时间，而且会有大量的重复代码，此时我们就可以采用动态代理，动态代理可以在程序运行期间根据需要动态的创建代理类及其实例来完成具体的功能。**总的来说，根据代理类的创建时机和创建方式的不同，我们可以将代理分为静态代理和动态代理两种形式。**

　　就像我们也可以自己直接去买票一样，在软件开发中，方法直接调用就可以完成功能，为什么非要通过代理呢？原因是采用代理模式可以有效的将具体的实现(买票过程)与调用方(买票者)进行解耦，通过面向接口进行编码完全将具体的实现(买票过程)隐藏在内部(黄牛)。此外，代理类不仅仅是一个隔离客户端和目标类的中介，我们还可以借助代理来在增加一些功能，而不需要修改原有代码，是开闭原则的典型应用。代理类主要负责为目标类预处理消息、过滤消息、把消息转发给目标类，以及事后处理消息等。代理类与目标类之间通常会存在关联关系，一个代理类的对象与一个目标类的对象关联，代理类的对象本身并不真正实现服务，而是通过调用目标类的对象的相关方法，来提供特定的服务。总的来说，

*   代理对象存在的价值主要用于拦截对真实业务对象的访问(我们不需要直接与火车站打交道，而是把这个任务委托给黄牛)；
    
*   代理对象应该具有和目标对象(真实业务对象)相同的方法，即实现共同的接口或继承于同一个类；
    
*   代理对象应该是目标对象的增强，否则我们就没有必要使用代理了。
    

**事实上，真正的业务功能还是由目标类来实现，代理类只是用于扩展、增强目标类的行为。**例如，在项目开发中我们没有加入缓冲、日志这些功能而后期需要加入，我们就可以使用代理来实现，而没有必要去直接修改已经封装好的目标类。

* * *

**2). 代理模式**

　　代理模式是较常见的模式之一，在许多框架中经常见到，比如Spring的面向切面的编程，MyBatis中缓存机制对PooledConnection的管理等。代理模式使得客户端在使用目标对象的时候间接通过操作代理对象进行，代理对象是对目标对象的增强，代理模式的UML示意图如下：

![image.png](https://i.loli.net/2021/11/14/4wHlkvSWJy8KTP2.png)

代理模式包含如下几个角色：

*   客户端：客户端面向接口编程，使用代理角色完成某项功能。
    
*   抽象主题：一般实现为接口，是对(被代理对象的)行为的抽象。
    
*   被代理角色(目标类)：直接实现上述接口，是抽象主题的具体实现。
    
*   代理角色(代理类)：实现上述接口，是对被代理角色的增强。
    

**代理模式的使用本质上是对开闭原则(Open for Extension, Close for Modification)的直接支持。**

* * *

二. 静态代理
-------

　　静态代理的实现模式一般是：首先创建一个接口（JDK代理都是面向接口的），然后创建具体实现类来实现这个接口，然后再创建一个代理类同样实现这个接口，不同之处在于，具体实现类的方法中需要将接口中定义的方法的业务逻辑功能实现，而代理类中的方法只要调用具体类中的对应方法即可，这样我们在需要使用接口中的某个方法的功能时直接调用代理类的方法即可，将具体的实现类隐藏在底层。下面通过例子来了解静态代理：

　　我们平常去电影院看电影的时候，在电影开始的阶段是不是经常会放广告呢？

　　电影是电影公司委托给影院进行播放的，但是影院可以在播放电影的时候，产生一些自己的经济收益，比如卖爆米花、可乐等，然后在影片开始结束时播放一些广告，现在用代码来进行模拟。

* * *

1). 抽象主题(接口)

　　首先得有一个接口，通用的接口是代理模式实现的基础。这个接口我们命名为Movie，代表电影这个主题。

```java
    package com.frank.test;
    
    public interface Movie {
        void play();
    }
```
* * *

2). 被代理角色(目标类)与代理角色(代理类)

　　然后，我们要有一个真正的实现这个 Movie 接口的类和一个只是实现接口的代理类。
  
```java
    package com.frank.test;
    public class RealMovie implements Movie {
        @Override
        public void play() {
            // TODO Auto-generated method stub
            System.out.println("您正在观看电影 《肖申克的救赎》");
        }
    }
```

　　这个表示真正的影片。它实现了 Movie 接口，play()方法调用时，影片就开始播放。那么代理类呢？

```java
    package com.frank.test;
    
    public class Cinema implements Movie {
    
        RealMovie movie;
        public Cinema(RealMovie movie) {
            super();
            this.movie = movie;
        }
    
        @Override
        public void play() {
            guanggao(true);    // 代理类的增强处理
            movie.play();     // 代理类把具体业务委托给目标类，并没有直接实现
            guanggao(false);    // 代理类的增强处理
        }
    
        public void guanggao(boolean isStart){
            if ( isStart ) {
                System.out.println("电影马上开始了，爆米花、可乐、口香糖9.8折，快来买啊！");
            } else {
                System.out.println("电影马上结束了，爆米花、可乐、口香糖9.8折，买回家吃吧！");
            }
        }
    }
```

　　Cinema 就是代理对象，它有一个 play() 方法。不过调用 play() 方法时，它进行了一些相关利益的处理，那就是广告。也就是说，Cinema(代理类) 与 RealMovie(目标类) 都可以播放电影，但是除此之外，Cinema(代理类)还对“播放电影”这个行为进行进一步增强，即增加了额外的处理，同时不影响RealMovie(目标类)的实现。

* * *

3). 客户端

```java
    package com.frank.test;
    public class ProxyTest {
        public static void main(String[] args) {
            RealMovie realmovie = new RealMovie();
            Movie movie = new Cinema(realmovie);
            movie.play();
        }
    }/** Output
            电影马上开始了，爆米花、可乐、口香糖9.8折，快来买啊！
            您正在观看电影 《肖申克的救赎》
            电影马上结束了，爆米花、可乐、口香糖9.8折，买回家吃吧！
     **/
```

　　现在可以看到，代理模式可以在不修改被代理对象的基础上(符合开闭原则)，通过扩展代理类，进行一些功能的附加与增强。值得注意的是，代理类和被代理类应该共同实现一个接口，或者是共同继承某个类。如前所述，由于Cinema(代理类)是事先编写、编译好的，而不是在程序运行过程中动态生成的，因此这个例子是一个静态代理的应用。

* * *

三. 动态代理
-------

　　在第一节我们已经提到，动态代理可以在程序运行期间根据需要动态的创建代理类及其实例来完成具体的功能，下面我们结合具体实例来介绍JDK动态代理。

* * *

1). 抽象主题(接口)

　　同样地，首先得有一个接口，通用的接口是代理模式实现的基础。

```java
    package cn.inter;
    
    public interface Subject {
        public void doSomething();
    }
```
* * *

2). 被代理角色(目标类)

　　然后，我们要有一个真正的实现这个 Subject 接口的类，以便代理。
```java
    package cn.impl;
    
    import cn.inter.Subject;
    
    public class RealSubject implements Subject {
        public void doSomething() {
            System.out.println("call doSomething()");
        }
    }
```
* * *

3). 代理角色(代理类)与客户端

　　在动态代理中，代理类及其实例是程序自动生成的，因此我们不需要手动去创建代理类。在Java的动态代理机制中，InvocationHandler(Interface)接口和Proxy(Class)类是实现我们动态代理所必须用到的。事实上，Proxy通过使用InvocationHandler对象生成具体的代理代理对象，下面我们看一下对InvocationHandler接口的实现：

```java
    package cn.handler;
    
    import java.lang.reflect.InvocationHandler;
    import java.lang.reflect.Method;
    /**
     * Title: InvocationHandler 的实现 
     * Description: 每个代理的实例都有一个与之关联的 InvocationHandler
     * 实现类，如果代理的方法被调用，那么代理便会通知和转发给内部的 InvocationHandler 实现类，由它调用invoke()去处理。
     * 
     * @author rico
     * @created 2017年7月3日 下午3:08:55
     */
    public class ProxyHandler implements InvocationHandler {
    
        private Object proxied;   // 被代理对象
    
        public ProxyHandler(Object proxied) {
            this.proxied = proxied;
        }
    
        public Object invoke(Object proxy, Method method, Object[] args)
                throws Throwable {
    
            // 在转调具体目标对象之前，可以执行一些功能处理
            System.out.println("前置增强处理： yoyoyo...");
    
            // 转调具体目标对象的方法(三要素：实例对象 + 实例方法 + 实例方法的参数)
            Object obj = method.invoke(proxied, args);
    
            // 在转调具体目标对象之后，可以执行一些功能处理
            System.out.println("后置增强处理：hahaha...");
    
            return obj;
        }
    }
```
* * *

　　在实现了InvocationHandler接口后，我们就可以创建代理对象了。在Java的动态代理机制中，我们使用Proxy类的静态方法newProxyInstance创建代理对象，如下：
```java
    package cn.client;
    
    import java.lang.reflect.Proxy;
    
    import cn.handler.ProxyHandler;
    import cn.impl.RealSubject;
    import cn.inter.Subject;
    
    public class Test {
        public static void main(String args[]) {
    
            // 真实对象real
            Subject real = new RealSubject();
    
            // 生成real的代理对象
            Subject proxySubject = (Subject) Proxy.newProxyInstance(
                    Subject.class.getClassLoader(), new Class[] { Subject.class },
                    new ProxyHandler(real));
    
            proxySubject.doSomething();
            System.out.println("代理对象的类型 ： " + proxySubject.getClass().getName());
            System.out.println("代理对象所在类的父类型 ： " + proxySubject.getClass().getGenericSuperclass());
        }
    }
    /** Output
            前置增强处理： yoyoyo...
            call doSomething()
            后置增强处理：hahaha...
            代理对象的类型 ： com.sun.proxy.$Proxy0
            代理对象所在类的父类型 ： class java.lang.reflect.Proxy
     **/
```
　　到此为止，我们给出了完整的基于JDK动态代理机制的代理模式的实现。我们从上面的实例中可以看到，代理对象proxySubject的类型为”com.sun.proxy.$Proxy0”，这恰好印证了proxySubject对象是一个代理对象。除此之外，**我们还发现代理对象proxySubject所对应的类继承自java.lang.reflect.Proxy类，这也正是JDK动态代理机制无法实现对class的动态代理的原因：Java只允许单继承。**

* * *

4). JDK中InvocationHandler接口与Proxy类

**(1). InvocationHandler接口**

　　InvocationHandler 是一个接口，官方文档解释说：**每个代理的实例都有一个与之关联的 InvocationHandler 实现类，如果代理的方法被调用，那么代理便会通知和转发给内部的 InvocationHandler 实现类，由它决定处理。**

```java
    public interface InvocationHandler {
        public Object invoke(Object proxy, Method method, Object[] args)
            throws Throwable;
    }

　　InvocationHandler中的invoke() 方法决定了怎么样处理代理传递过来的方法调用。
```
* * *

**(2). Proxy类**

　　JDK通过 Proxy 的静态方法 newProxyInstance 动态地创建代理，该方法在Java中的声明如下：
```java
        /**     
         * @description 
         * @author rico       
         * @created 2017年7月3日 下午3:16:49     
         * @param loader 类加载器
         * @param interfaces 目标类所实现的接口
         * @param h  InvocationHandler 实例
         * @return     
         */
        public static Object newProxyInstance(ClassLoader loader,
                Class<?>[] interfaces,
                InvocationHandler h)
```
　　事实上，Proxy 动态产生的代理对象调用目标方法时，代理对象会调用 InvocationHandler 实现类，所以 InvocationHandler 是实际执行者。

* * *

五. Spring AOP 与 动态代理
--------------------

　　AOP 专门用于处理系统中分布于各个模块（不同方法）中的交叉关注点的问题，在 Java EE 应用中，常常通过 AOP 来处理一些具有横切性质的系统级服务，如事务管理、安全检查、缓存、对象池管理等，AOP 已经成为一种非常常用的解决方案。

　　AOP机制是 Spring 所提供的核心功能之一，其既是Java动态代理机制的经典应用，也是动态AOP实现的代表。Spring AOP默认使用Java动态代理来创建AOP代理，具体通过以下几个步骤来完成：

1.  Spring IOC 容器创建Bean(目标类对象)；
    
2.  Bean创建完成后，Bean后处理器(BeanPostProcessor)根据具体的切面逻辑及Bean本身使用Java动态代理技术生成代理对象；
    
3.  应用程序使用上述生成的代理对象替代原对象来完成业务逻辑，从而达到增强处理的目的。
    
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 计算机的补码解决了什么问题？人类在制造出晶体管后，利用晶体管制造出了与非门，然后又利用与非门制造出了加法器。加法器解决了加法运算问题。只有加法器是不够的，还需要解决减法的计算问题，但是与加法器相比，设计减法器硬件更为复杂，增加了计算的时间，能不能用加法器实现减法器的功能？这个实现的过程就用到了补码。  

计算机为什么使用补码？**采用补码可以简化计算机硬件电路设计的复杂度**。

对于有符号数，内存要区分符号位和数值位，要是能把符号位和数值位等同起来，让它们一起参与运算，不再加以区分，只用加法器就可以同时实现加法和减法运算，这样硬件电路就变得简单了。

8 - 3 等价于 8 + (-3)，12 - (-9) 等价于 10 + 9。

简化硬件电路的代价就是有符号数在存储和读取时都要进行转化。这个转换过程就涉及到我们熟悉的原码、反码、补码。

原码
--

将一个整数转换成二进制形式，就是其原码。例如short a = 5;，a 的原码就是0000 0000 0000 0101；更改 a 的值a = -19;，此时 a 的原码就是1000 0000 0001 0011。

通俗的理解，原码就是一个整数本来的二进制形式。

反码
--

正数与负数的反码不一样。

对于正数，它的反码就是其原码（原码和反码相同）；**负数的反码是将原码中除符号位以外的所有位（数值位）取反**，也就是 0 变成 1，1 变成 0。例如 short a = 5;，a 的原码和反码都是 0000 0000 0000 0101；更改 a 的值 a = -19;，此时 a 的反码是 1111 1111 1110 1100。

为什么需要反码，**反码的作用就相当于数学中的负数，有了负数，才可以实现减法与加法运算统一成加法运算**。

补码
--

### 有了反码为什么还需要补码

因为 “0” 这个特殊数字的存在。

将减法运算按加法运算处理，负数需要用反码表示，那么用 8 位二进制反码表示的正数范围：+0 —— +127；负数范围：-127 —— -0。但是，其中有两个特殊的编码会出现：

\[0_0000000\]=+0 （反码）

\[1_1111111\]=-0 （反码）

+0 和 -0 代表的都是 0。这样一来，“0” 这个数字在计算机中的编码就不是唯一的了。对于计算机来说，这是绝对不行的，因为任何数字都只能有 1 个编码。

我们知道 0 既不是正数也不是负数，为了解决这个编码不唯一的问题，把 0 当成正数，也即 +0，这样 0 的编码就变成：0\_0000000。那 8 位二进制表示的正数范围仍然是：+0 —— +127。负数整体向后“挪动1位”，反码 +1，{1\_1111111}编码就不再表示 -0，而变成了 -1。顺着推，最小的编码{1_0000000}就是 -128，8 位二进制表示的负数范围从：-127 —— -0 变成：-128 —— -1，就能成功解决问题。

这种操作好像是在反码上打了“补丁”，进行了一下修正,所以称之为补码,补码定义如下：

1.正数的补码保持原码不变：5 = 0_000 0000 0000 0101

2.负数先求反码，然后再加1：-19 = 1\_111 1111 1110 1100 + 1 = 1\_111 1111 1110 1101

![](https://img-blog.csdnimg.cn/img_convert/8781f76d42ebd1ab70a4ffcc06e58b3d.png)

5 - 19 的计算过程:

0\_000 0000 0000 0101 + 1\_111 1111 1110 1101 = 1_111 1111 1111 0010;

将补码转换为原码也很简单：先减去 1，再将数值位取反即可。

1_111 1111 1111 0010 逆向转换原码是：1000 0000 0000 1110 = -14

**采用补码成功解决了数字 0 在计算机中非唯一编码的问题，也实现了减法变加法**。

总结
--

补码是为了解决负数在计算机中的表示问题，最终是为了解决计算机的减法运算问题。计算机中采用了补码的根本原因是，"设计硬件简单！"

*   不浪费编码个数;
    
*   省去计算机判断符号位或者说判断+/-运算的麻烦。
    
*   有了补码，对加减运算，硬件上，只有一种加法器就行了;
    
*   有了加减运算，用程序就可以实现乘除运算，不用额外增加硬件;
    
*   有了加减乘除运算，用程序就可以实现"所有"算术运算了，不用额外增加硬件。
    
*** 
## ⭐️⭐️⭐️⭐️⭐️
## TCP为什么要四次挥手_tcp的连接时全双工的，因此每个方向都必须单独关闭。一方A发送完数据后，发送一个FIN请求断开与对方B的连接，B收到FIN表示不会再从A收到数据了，但是这个TCP连接中还是可以发送数据的，直到B发送完数据，也发送FIN，最终释放连接。_

一、四次挥手：

![](https://img-blog.csdnimg.cn/20190818173848350.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDAxMjkwOQ==,size_16,color_FFFFFF,t_70)

> **第一次挥手**：C-->S，client发送一个FIN=1,seq=u,用来关闭c-->s的数据传送，client进入FIN-WAIT 1 状态；
> 
> **第二次挥手**：S-->C，sever收到FIN后，发送ACK=1,seq=v，ack=u+1给client（与SYN相同，一个FIN占用一个序号），sever进入CLOSE-WAIT状态；当client收到这确认报文后进入FIN-WAIT 2 状态；
> 
> **第三次挥手**：S-->C，当sever发送完数据后，发送FIN=1，ACK=1，seq=w,ack=u+1，用来关闭s-->c的数据传送，sever进入LAST-ACK状态。
> 
> **第四次挥手**：C-->S，当client收到FIN后，client进入TIME-WAIT状态（2msl最大报文生存时间后进入CLOSED状态），接着发送ACK=1,seq=u+1,ack=w+1，sever进入CLOSDE状态。

二、为什么TCP的挥手需要四次：

> 参照三次握手机制，挥手最少需要三次，如果只有三次，客户端发送完数据请求断开连接，而服务端不一定也同样发送完数据，若同时回ACK和FIN给客户端，断开连接，可能造成数据的损坏；若先发送ACK，再等B的数据发送完了再发送FIN和ACK，就可以保证传输数据的完整性。
> 
> tcp是全双工模式，接收到FIN意味着将没有数据再发来，但是还是可以继续发送数据。

三、为什么TIME-WAIT状态需要经过2msl（最大报文生存时间）才能返回CLOSE状态：

虽然四个报文都发送完毕，可以进入CLOSE状态，但是网络可能会存在不可靠假象，有可能最后一个ACK丢失，TIME-WAIT状态就是用来重新发送可能丢失的报文。

> 等待2msl的意义：可靠的终止TCP连接、保证迟来的TCP报文有足够的时间被识别并丢弃；
> 
> 1、保证A发送的ACK能够顺利到达B，这个报文可能丢失，处在LAST-ACK的B收不到对自己以发送的FIN和ACK报文的确认，B会超时重传FIN和ACK报文，那么在2msl时间内收到这个重传的FIN+ACK报文，接着A重传一次；
> 
> 2、在这个期间，定义这个连接的插口（客户的IP地址和端口号，服务器的IP地址和端口号）不能再被使用，这个连接只能在2msl结束后才能被使用；
> 
> 3、为了使旧的数据包在网络中因过期而消失，每个具体的TCP必须选择一个报文最大生存时间MSL，它是任何报文字段被丢弃前在网络内的最长时间。
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说一说TCP/IP四层模型
TCP/IP协议族体系结构以及主要协议
===================

TCP/IP协议族是一个四层协议系统，自底而上分别是数据链路层、网络层、传输层和应用层。每一层完成不同  
的功能，且通过若干协议来实现，上层协议使用下层协议提供的服务。  

![image.png](https://i.loli.net/2021/11/14/WwuPC2bBKfYlHkd.png)

数据链路层
=====

**数据链路层实现了网卡接口的网络驱动程序，以处理数据在物理媒介（比如以太网、令牌环等）上的传输。**

**数据链路层两个常用的协议是ARP协议（Address Resolve Protocol，地址解析协议）和RARP协议**（ReverseAddress Resolve Protocol，逆地址解析协议）。它们实现了IP地址和机器物理地址（通常是MAC地址，以太网、令牌环和802.11无线网络都使用MAC地址）之间的相互转换。

网络层使用IP地址寻址一台机器，而数据链路层使用物理地址寻址一台机器，因此网络层必须先将目标机器的IP地址转化成其物理地址，才能使用数据链路层提供的服务，**这就是ARP协议的用途。**

RARP协议仅用于网络上的某些无盘工作站。因为缺乏存储设备，无盘工作站无法记住自己的IP地址，但它们可以利用网卡上的物理地址来向网  
络管理者（服务器或网络管理软件）查询自身的IP地址。运行RARP服务的网络管理者通常存有该网络上所有机器的物理地址到IP地址的映射。

网络层
===

**网络层实现数据包的选路和转发。**  
WAN（Wide Area Network，广域网）通常使用众多分级的路由器来连接分散的主机或LAN（Local Area Network，局域网），因此，通信的两台主机一般不是直接相连的，而是通过多个中间节点（路由器）连接的。网络层的任务就是选择这些中间节点，以确定两台主机之间的通信路径。同时，网络层对上层协议隐藏了网络拓扑连接的细节，使得在传输层和网络应用程序看来，通信的双方是直接相连的。

网络层最核心的协议是IP协议（Internet Protocol，因特网协议）。IP协议根据数据包的目的IP地址来决定如何投递它。如果数据包不能直接发送给目标主机，那么IP协议就为它寻找一个合适的下一跳（next hop）路由器，并将数据包交付给该路由器来转发。多次重复这一过程，数据包最终到达目标主机，或者由于发送失败而被丢弃。可见，IP协议使用逐跳（hop by hop）的方式确定通信路径。

网络层另外一个重要的协议是ICMP协议（Internet Control Message Protocol，因特网控制报文协议）。它是IP协议的重要补充，主要用于检测网络连接。  

![image.png](https://i.loli.net/2021/11/14/ZXdF6l15PkJIcRY.png)

8位类型字段用于区分报文类型。它将**ICMP报文分为两大类**  
**差错报文**，这类报文主要用来回应网络错误，比如目标不可到达（类型值为3）和重定向（类型值为5）；  
**查询报文**，这类报文用来查询网络信息，比如ping程序就是使用ICMP报文查看目标是否可到达（类型值为8）的。  
有的ICMP报文还使用8位代码字段来进一步细分不同的条件。比如重定向报文使用代码值0表示对网络重定向，代码值1表示对主机重定向。  
ICMP报文使用16位校验和字段对整个报文（包括头部和内容部分）进行循环冗余校验（Cyclic Redundancy Check，CRC），以检验报文在传输过程中是否损坏。不同的ICMP报文类型具有不同的正文内容。

传输层
===

**传输层为两台主机上的应用程序提供端到端（end to end）的通信。与网络层使用的逐跳通信方式不同，传输层只关心通信的起始端和目的端，而不在乎数据包的中转过程。**

![image.png](https://i.loli.net/2021/11/14/OAdmnMb5G4swjXu.png)

垂直的实线箭头表示TCP/IP协议族各层之间的实体通信（数据包确实是沿着这些线路传递的），而水平的虚线箭头表示逻辑通信线路。该图中还附带描述了不同物理网络的连接方法。可见，  
**数据链路层（驱动程序）封装了物理网络的电气细节；网络层封装了网络连接的细节；传输层则为应用程序封装了一条端到端的逻辑通信链路，它负责数据的收发、链路的超时重连等。**

传输层协议：TCP协议、UDP协议。

*   TCP协议（Transmission Control Protocol，传输控制协议）为应用层提供可靠的、面向连接的和基于流（stream）的服务。TCP协议使用超时重传、数据确认等方式来确保数据包被正确地发送至目的端，因此TCP服务是可靠的。使用TCP协议通信的双方必须先建立TCP连接，并在内核中为该连接维持一些必要的数据结构，比如连接的状态、读写缓冲区，以及诸多定时器等。当通信结束时，双方必须关闭连接以释放这些内核数据。TCP服务是基于流的。基于流的数据没有边界（长度）限制，它源源不断地从通信的一端流入另一端。发送端可以逐个字节地向数据流中写入数据，接收端也可以逐个字节地将它们读出。
    
*   UDP协议（User Datagram Protocol，用户数据报协议）则与TCP协议完全相反，它为应用层提供不可靠、无连接和基于数据报的服务。“不可靠”意味着UDP协议无法保证数据从发送端正确地传送到目的端。如果数据在中途丢失，或者目的端通过数据校验发现数据错误而将其丢弃，则UDP协议只是单地通知应用程序发送失败。因此，使用UDP协议的应用程序通常要自己处理数据确认、超时重传等逻辑。UDP协议是无连接的，即通信双方不保持一个长久的联系，因此应用程序每次发送数据都要明确指定接收端的地址（IP地址等信息）。基于数据报的服务，是相对基于流的服务而言的。每个UDP数据报都有一个长度，接收端必须以该长度为最小单位将其所有内容一次性读出，否则数据将被截断。
    

应用层
===

**应用层负责处理应用程序的逻辑。**  
数据链路层、网络层和传输层负责处理网络通信细节，这部分必须既稳定又高效，因此它们都在内核空间中实现。而应用层则在用户空间实现，因为它负责处理众多逻辑，比如文件传输、名称查询和网络管理等。如果应用层也在内核中实现，则会使内核变得非常庞大。当然，也有少数服务器程序是在内核中实现的，这样代码就无须在用户空间和内核空间来回切换（主要是数据的复制），极大地提高了工作效率。不过这种代码实现起来较复杂，不够灵活，且不便于移植。

ping是应用程序，而不是协议，前面说过它利用ICMP报文检测网络连接，是调试网络环境的必备工具。

telnet协议是一种远程登录协议，它使我们能在本地完成远程任务。

OSPF（Open Shortest Path First，开放最短路径优先）协议是一种动态路由更新协议，用于路由器之间的通信，以告知对方各自的路由信息。

DNS（Domain Name Service，域名服务）协议提供机器域名到IP地址的转换。

应用层协议（或程序）可能跳过传输层直接使用网络层提供的服务，比如ping程序和OSPF协议。应用层协议（或程序）通常既可以使用TCP服务，又可以使用UDP服务，比如DNS协议。我们可以通过/etc/services文件查看所有知名的应用层协议，以及它们都能使用哪些传输层服务。

五层协议背后的思想：上层屏蔽下层细节，只使用其提供的服务。**高内聚低耦合，每一层专注于其功能，各层之间的关系依赖不大。**

数据包在每层有不同的格式，从上到下依次叫段，数据报，帧，数据从应用层通过协议栈向下传递，每经过一层加上对应层协议的报头，最后封装成帧发送到传输介质上，到达路由器或者目的主机剥掉头部，交付给上层需要者。**这一过程称为封装，传输，分离，分用。**
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 知道什么是Gossip协议吗？背景
--

gossip 协议（gossip protocol）又称 epidemic 协议（epidemic protocol），是基于流行病传播方式的节点或者进程之间信息交换的协议，在分布式系统中被广泛使用，比如我们可以使用 gossip 协议来确保网络中所有节点的数据一样。

Gossip protocol 最早是在 1987 年发表在 ACM 上的论文 《Epidemic Algorithms for Replicated Database Maintenance》中被提出。主要用在分布式数据库系统中各个副本节点同步数据之用，这种场景的一个最大特点就是组成的网络的节点都是对等节点，是非结构化网络，这区别于用于结构化网络中的 DHT 算法 Kadmelia。很多知名的 P2P 网络或区块链项目，比如 IPFS，Ethereum 等，都使用了 Kadmelia 算法，而大名鼎鼎的 Bitcoin 则是使用了 Gossip 协议来传播交易和区块信息。实际上，Ethereum 使用 DHT 算法并不是很合理，因为它使用节点保存整个链数据，不像 IPFS 那样分片保存数据，因此 Ethereum 真正适合的协议应该像 Bitcoin 那样，是 Gossip 协议。

从 gossip 单词就可以看到，其中文意思是八卦、流言等意思，我们可以想象下绯闻的传播（或者流行病的传播）；gossip 协议的工作原理就类似于这个。gossip 协议利用一种随机的方式将信息传播到整个网络中，并在一定时间内使得系统内的所有节点数据一致。Gossip 其实是一种去中心化思路的分布式协议，解决状态在集群中的传播和状态一致性的保证两个问题。

优势
--

**可扩展性（Scalable）**

gossip 协议是可扩展的，一般需要 O(logN) 轮就可以将信息传播到所有的节点，其中 N 代表节点的个数。每个节点仅发送固定数量的消息，并且与网络中节点数目无法。在数据传送的时候，节点并不会等待消息的 ack，所以消息传送失败也没有关系，因为可以通过其他节点将消息传递给之前传送失败的节点。系统可以轻松扩展到数百万个进程。

**容错（Fault-tolerance）**

网络中任何节点的重启或者宕机都不会影响 gossip 协议的运行。

**健壮性（Robust）**

gossip 协议是去中心化的协议，所以集群中的所有节点都是对等的，没有特殊的节点，所以任何节点出现问题都不会阻止其他节点继续发送消息。任何节点都可以随时加入或离开，而不会影响系统的整体服务质量（QOS）

**最终一致性（Convergent consistency）**

Gossip 协议实现信息指数级的快速传播，因此在有新信息需要传播时，消息可以快速地发送到全局节点，在有限的时间内能够做到所有节点都拥有最新的数据。

**简单（Simplicity）**

Gossip 协议实现过程简单，没有太多复杂性。

劣势
--

分布式网络中，没有一种完美的解决方案，Gossip 协议跟其他协议一样，也有一些不可避免的缺陷，主要是两个：

1）消息的延迟

由于 Gossip 协议中，节点只会随机向少数几个节点发送消息，消息最终是通过多个轮次的散播而到达全网的，因此使用 Gossip 协议会造成不可避免的消息延迟。不适合用在对实时性要求较高的场景下。

2）消息冗余

Gossip 协议规定，节点会定期随机选择周围节点发送消息，而收到消息的节点也会重复该步骤，因此就不可避免的存在消息重复发送给同一节点的情况，造成了消息的冗余，同时也增加了收到消息的节点的处理压力。而且，由于是定期发送，因此，即使收到了消息的节点还会反复收到重复消息，加重了消息的冗余。

协议类型
----

gossip 协议的类型。目前主要有两种方法：

*   Anti-Entropy（反熵）：以固定的概率传播所有的数据
*   Rumor-Mongering（谣言传播）：仅传播新到达的数据

### Anti-Entropy

Anti-Entropy 的主要工作方式是：每个节点周期性地随机选择其他节点，然后通过互相交换自己的**所有**数据来消除两者之间的差异。Anti-Entropy 这种方法非常可靠，但是每次节点两两交换自己的所有数据会带来非常大的通信负担，以此不会频繁使用。

Anti-Entropy 使用“simple epidemics”的方式，所以其包含两种状态：susceptible 和 infective，这种模型也称为 **SI model**。处于 infective 状态的节点代表其有数据更新，并且会将这个数据分享给其他节点；处于 susceptible 状态的节点代表其并没有收到来自其他节点的更新。

### Rumor-Mongering

Rumor-Mongering 的主要工作方式是：当一个节点有了新的信息后，这个节点变成活跃状态，并周期性地联系其他节点向其发送新信息。直到所有的节点都知道该新信息。因为节点之间只是交换新信息，所有大大减少了通信的负担。

Rumor-Mongering 使用“complex epidemics”方法，相比 Anti-Entropy 多了一种状态：removed，这种模型也称为 **SIR model**。处于 removed 状态的节点说明其已经接收到来自其他节点的更新，但是其并不会将这个更新分享给其他节点。因为 Rumor 消息会在某个时间标记为 removed，然后不会发送给其他节点，所以 Rumor-Mongering 类型的 gossip 协议有极小概率使得更新不会达到所有节点。一般来说，为了在通信代价和可靠性之间取得折中，需要将这两种方法结合使用。

通信方式
----

不管是 Anti-Entropy 还是 Rumor-Mongering 都涉及到节点间的数据交互方式，节点间的交互方式主要有三种：Push、Pull 以及 Push&Pull。

*   **Push**：发起信息交换的节点 A 随机选择联系节点 B，并向其发送自己的信息（key,value,version），节点 B 在收到信息后更新比自己新的数据，一般拥有新信息的节点才会作为发起节点。
*   **Pull**：发起信息交换的节点 A 随机选择联系节点 B，发送自己的(key,version) 信息给B，B将比A新的信息(key,value,version) 发送给A，A更新本地数据。一般无新信息的节点才会作为发起节点。
*   **Push&Pull**：在Push和Pull的基础上，A再将比B新的信息(key,value,version)发送给B，B收到后更新本地数据，从而分别从对方获取数据，并更新自己的本地数据。

如果把两个节点数据同步一次定义为一个周期，则在一个周期内，Push 需通信 1 次，Pull 需 2 次，Push/Pull 则需 3 次。虽然消息数增加了，但从效果上来讲，Push/Pull 最好，理论上一个周期内可以使两个节点完全一致。直观上，Push/Pull 的收敛速度也是最快的。

收敛分析
----

流行病传染最基本的模型仅作如下几个假设：

1.  (n+1)个人均匀的分布在一起
2.  每一对人群之间的传染概率是β，显然0<β<1.
3.  任意时刻，某个人要么处于infected的状态要么处于uninfected的状态.
4.  一旦某个人从uninfected状态转变成为infected状态，其一直停留在infected状态。

有了以上假设，我们可以进一步分析流行病的传染情况。我们记t时刻处于infected状态的人数为yt，处于uninfected状态的人为xt，那么初始状态 y0=1, x0=n，并且在任何时候xt+yt=n+1.

考虑连续的时间，可知：

dxdt=−βxy

解的：

x=n(n+1)n+eβ(n+1)ty=n+11+ne−β(n+1)t

明显，当t→∞时，x→0,y→(n+1)，即经过足够的时间，所有的人都将被传染。

上述流行病传染模型为分析Gossip的性能提供了基础。在Gossip性能中，可以认为: β=b/n（因为对每个节点而言，被其他节点选中的概率就是b/n)。我们令t=clog(n)，可以得到:

y≈(n+1)−1ncb−2

这表明，仅需要O(log(n))个回合，gossip协议即可将信息传递到所有的节点。 根据分析可得，Gossip协议具有以下的特点:

1.  低延迟。仅仅需要O(log(n))个回合的传递时间。
2.  非常可靠。仅有1ncb−2个节点不会收到信息。
3.  轻量级。每个节点传送了cblog(n)次信息。

于此同时，Gossip协议的容错性比较高，例如，50的丢包率等价于使用b/2带代替b进行分析；50的节点错误等价于使用n/2来代替n，同时使用b/2来代替b进行分析，其分析结果不用带来数量级上的变化。

应用
--

gossip 协议可以支持以下需求：

*   Database replication
*   消息传播
*   Cluster membership
*   Failure 检测
*   Overlay Networks
*   Aggregations (比如计算平均值、最大值以及总和)
*** 
## ⭐️⭐️⭐️⭐️⭐️
## Zookeeper的Zab协议了解过吗？**什么是Zab协议？**
-------------

Zab协议 的全称是 **Zookeeper Atomic Broadcast** （Zookeeper原子广播）。  
**Zookeeper 是通过 Zab 协议来保证分布式事务的最终一致性**。

1.  Zab协议是为分布式协调服务Zookeeper专门设计的一种 **支持崩溃恢复** 的 **原子广播协议** ，是Zookeeper保证数据一致性的核心算法。Zab借鉴了Paxos算法，但又不像Paxos那样，是一种通用的分布式一致性算法。**它是特别为Zookeeper设计的支持崩溃恢复的原子广播协议**。
    
2.  在Zookeeper中主要依赖Zab协议来实现数据一致性，基于该协议，zk实现了一种主备模型（即Leader和Follower模型）的系统架构来保证集群中各个副本之间数据的一致性。  
    这里的主备系统架构模型，就是指只有一台客户端（Leader）负责处理外部的写事务请求，然后Leader客户端将数据同步到其他Follower节点。
    

Zookeeper 客户端会随机的链接到 zookeeper 集群中的一个节点，如果是读请求，就直接从当前节点中读取数据；如果是写请求，那么节点就会向 Leader 提交事务，Leader 接收到事务提交，会广播该事务，只要超过半数节点写入成功，该事务就会被提交。

**Zab 协议的特性**：  
1）Zab 协议需要确保那些**已经在 Leader 服务器上提交（Commit）的事务最终被所有的服务器提交**。  
2）Zab 协议需要确保**丢弃那些只在 Leader 上被提出而没有被提交的事务**。

![](https://img-blog.csdnimg.cn/img_convert/8bbb6569ac9ec9d0ec33b09cc0dc4213.webp?x-oss-process=image/format,png)

模型图

* * *

Zab 协议实现的作用
-----------

1）**使用一个单一的主进程（Leader）来接收并处理客户端的事务请求**（也就是写请求），并采用了Zab的原子广播协议，将服务器数据的状态变更以 **事务proposal** （事务提议）的形式广播到所有的副本（Follower）进程上去。  
 

2）**保证一个全局的变更序列被顺序引用**。  
Zookeeper是一个树形结构，很多操作都要先检查才能确定是否可以执行，比如P1的事务t1可能是创建节点"/a"，t2可能是创建节点"/a/bb"，只有先创建了父节点"/a"，才能创建子节点"/a/b"。

为了保证这一点，Zab要保证同一个Leader发起的事务要按顺序被apply，同时还要保证只有先前Leader的事务被apply之后，新选举出来的Leader才能再次发起事务。  
 

3）**当主进程出现异常的时候，整个zk集群依旧能正常工作**。

* * *

Zab协议原理
-------

Zab协议要求每个 Leader 都要经历三个阶段：**发现，同步，广播**。

*   **发现**：要求zookeeper集群必须选举出一个 Leader 进程，同时 Leader 会维护一个 Follower 可用客户端列表。将来客户端可以和这些 Follower节点进行通信。
    
*   **同步**：Leader 要负责将本身的数据与 Follower 完成同步，做到多副本存储。这样也是提现了CAP中的高可用和分区容错。Follower将队列中未处理完的请求消费完成后，写入本地事务日志中。
    
*   **广播**：Leader 可以接受客户端新的事务Proposal请求，将新的Proposal请求广播给所有的 Follower。
    

* * *

Zab协议核心
-------

Zab协议的核心：**定义了事务请求的处理方式**

1）所有的事务请求必须由一个全局唯一的服务器来协调处理，这样的服务器被叫做 **Leader服务器**。其他剩余的服务器则是 **Follower服务器**。

2）Leader服务器 负责将一个客户端事务请求，转换成一个 **事务Proposal**，并将该 Proposal 分发给集群中所有的 Follower 服务器，也就是向所有 Follower 节点发送数据广播请求（或数据复制）

3）分发之后Leader服务器需要等待所有Follower服务器的反馈（Ack请求），**在Zab协议中，只要超过半数的Follower服务器进行了正确的反馈**后（也就是收到半数以上的Follower的Ack请求），那么 Leader 就会再次向所有的 Follower服务器发送 Commit 消息，要求其将上一个 事务proposal 进行提交。

![](https://img-blog.csdnimg.cn/img_convert/a69984b0cc8d06e5664880291f202a03.webp?x-oss-process=image/format,png)

事务请求处理

* * *

Zab协议内容
-------

Zab 协议包括两种基本的模式：**崩溃恢复** 和 **消息广播**

协议过程

当整个集群启动过程中，或者当 Leader 服务器出现网络中弄断、崩溃退出或重启等异常时，Zab协议就会 **进入崩溃恢复模式**，选举产生新的Leader。

当选举产生了新的 Leader，同时集群中有过半的机器与该 Leader 服务器完成了状态同步（即数据同步）之后，Zab协议就会退出崩溃恢复模式，**进入消息广播模式**。

这时，如果有一台遵守Zab协议的服务器加入集群，因为此时集群中已经存在一个Leader服务器在广播消息，那么该新加入的服务器自动进入恢复模式：找到Leader服务器，并且完成数据同步。同步完成后，作为新的Follower一起参与到消息广播流程中。  
 

协议状态切换

当Leader出现崩溃退出或者机器重启，亦或是集群中不存在超过半数的服务器与Leader保存正常通信，Zab就会再一次进入崩溃恢复，发起新一轮Leader选举并实现数据同步。同步完成后又会进入消息广播模式，接收事务请求。  
 

保证消息有序

在整个消息广播中，Leader会将每一个事务请求转换成对应的 proposal 来进行广播，并且在广播 事务Proposal 之前，Leader服务器会首先为这个事务Proposal分配一个全局单递增的唯一ID，称之为事务ID（即zxid），由于Zab协议需要保证每一个消息的严格的顺序关系，因此必须将每一个proposal按照其zxid的先后顺序进行排序和处理。

* * *

消息广播
----

1）在zookeeper集群中，数据副本的传递策略就是采用消息广播模式。zookeeper中农数据副本的同步方式与二段提交相似，但是却又不同。二段提交要求协调者必须等到所有的参与者全部反馈ACK确认消息后，再发送commit消息。要求所有的参与者要么全部成功，要么全部失败。二段提交会产生严重的阻塞问题。

2）Zab协议中 Leader 等待 Follower 的ACK反馈消息是指“只要半数以上的Follower成功反馈即可，不需要收到全部Follower反馈”

![](https://img-blog.csdnimg.cn/img_convert/ecda78479a4fd130d7d7351852b7182b.webp?x-oss-process=image/format,png)

消息广播流程图

  
 

消息广播具体步骤

1）客户端发起一个写操作请求。

2）Leader 服务器将客户端的请求转化为事务 Proposal 提案，同时为每个 Proposal 分配一个全局的ID，即zxid。

3）Leader 服务器为每个 Follower 服务器分配一个单独的队列，然后将需要广播的 Proposal 依次放到队列中取，并且根据 FIFO 策略进行消息发送。

4）Follower 接收到 Proposal 后，会首先将其以事务日志的方式写入本地磁盘中，写入成功后向 Leader 反馈一个 Ack 响应消息。

5）Leader 接收到超过半数以上 Follower 的 Ack 响应消息后，即认为消息发送成功，可以发送 commit 消息。

6）Leader 向所有 Follower 广播 commit 消息，同时自身也会完成事务提交。Follower 接收到 commit 消息后，会将上一条事务提交。

**zookeeper 采用 Zab 协议的核心，就是只要有一台服务器提交了 Proposal，就要确保所有的服务器最终都能正确提交 Proposal。这也是 CAP/BASE 实现最终一致性的一个体现。**

**Leader 服务器与每一个 Follower 服务器之间都维护了一个单独的 FIFO 消息队列进行收发消息，使用队列消息可以做到异步解耦。 Leader 和 Follower 之间只需要往队列中发消息即可。如果使用同步的方式会引起阻塞，性能要下降很多。**

* * *

崩溃恢复
----

**一旦 Leader 服务器出现崩溃或者由于网络原因导致 Leader 服务器失去了与过半 Follower 的联系，那么就会进入崩溃恢复模式。**

在 Zab 协议中，为了保证程序的正确运行，整个恢复过程结束后需要选举出一个新的 Leader 服务器。因此 Zab 协议需要一个高效且可靠的 Leader 选举算法，从而确保能够快速选举出新的 Leader 。

Leader 选举算法不仅仅需要让 Leader 自己知道自己已经被选举为 Leader ，同时还需要让集群中的所有其他机器也能够快速感知到选举产生的新 Leader 服务器。

崩溃恢复主要包括两部分：**Leader选举** 和 **数据恢复**

Zab 协议如何保证数据一致性

假设两种异常情况：  
1、一个事务在 Leader 上提交了，并且过半的 Folower 都响应 Ack 了，但是 Leader 在 Commit 消息发出之前挂了。  
2、假设一个事务在 Leader 提出之后，Leader 挂了。

要确保如果发生上述两种情况，数据还能保持一致性，那么 Zab 协议选举算法必须满足以下要求：

**Zab 协议崩溃恢复要求满足以下两个要求**：  
1）**确保已经被 Leader 提交的 Proposal 必须最终被所有的 Follower 服务器提交**。  
2）**确保丢弃已经被 Leader 提出的但是没有被提交的 Proposal**。

根据上述要求  
Zab协议需要保证选举出来的Leader需要满足以下条件：  
1）**新选举出来的 Leader 不能包含未提交的 Proposal** 。  
即新选举的 Leader 必须都是已经提交了 Proposal 的 Follower 服务器节点。  
2）**新选举的 Leader 节点中含有最大的 zxid** 。  
这样做的好处是可以避免 Leader 服务器检查 Proposal 的提交和丢弃工作。  
 

Zab 如何数据同步

1）完成 Leader 选举后（新的 Leader 具有最高的zxid），在正式开始工作之前（接收事务请求，然后提出新的 Proposal），Leader 服务器会首先确认事务日志中的所有的 Proposal 是否已经被集群中过半的服务器 Commit。

2）Leader 服务器需要确保所有的 Follower 服务器能够接收到每一条事务的 Proposal ，并且能将所有已经提交的事务 Proposal 应用到内存数据中。等到 Follower 将所有尚未同步的事务 Proposal 都从 Leader 服务器上同步过啦并且应用到内存数据中以后，Leader 才会把该 Follower 加入到真正可用的 Follower 列表中。  
 

Zab 数据同步过程中，如何处理需要丢弃的 Proposal

在 Zab 的事务编号 zxid 设计中，zxid是一个64位的数字。

其中低32位可以看成一个简单的单增计数器，针对客户端每一个事务请求，Leader 在产生新的 Proposal 事务时，都会对该计数器加1。而高32位则代表了 Leader 周期的 epoch 编号。

> epoch 编号可以理解为当前集群所处的年代，或者周期。每次Leader变更之后都会在 epoch 的基础上加1，这样旧的 Leader 崩溃恢复之后，其他Follower 也不会听它的了，因为 Follower 只服从epoch最高的 Leader 命令。

每当选举产生一个新的 Leader ，就会从这个 Leader 服务器上取出本地事务日志充最大编号 Proposal 的 zxid，并从 zxid 中解析得到对应的 epoch 编号，然后再对其加1，之后该编号就作为新的 epoch 值，并将低32位数字归零，由0开始重新生成zxid。

**Zab 协议通过 epoch 编号来区分 Leader 变化周期**，能够有效避免不同的 Leader 错误的使用了相同的 zxid 编号提出了不一样的 Proposal 的异常情况。

基于以上策略  
**当一个包含了上一个 Leader 周期中尚未提交过的事务 Proposal 的服务器启动时，当这台机器加入集群中，以 Follower 角色连上 Leader 服务器后，Leader 服务器会根据自己服务器上最后提交的 Proposal 来和 Follower 服务器的 Proposal 进行比对，比对的结果肯定是 Leader 要求 Follower 进行一个回退操作，回退到一个确实已经被集群中过半机器 Commit 的最新 Proposal**。

* * *

实现原理
----

**Zab 节点有三种状态**：

*   Following：当前节点是跟随者，服从 Leader 节点的命令。
*   Leading：当前节点是 Leader，负责协调事务。
*   Election/Looking：节点处于选举状态，正在寻找 Leader。

代码实现中，多了一种状态：Observing 状态  
这是 Zookeeper 引入 Observer 之后加入的，Observer 不参与选举，是只读节点，跟 Zab 协议没有关系。

**节点的持久状态**：

*   history：当前节点接收到事务 Proposal 的Log
*   acceptedEpoch：Follower 已经接受的 Leader 更改 epoch 的 newEpoch 提议。
*   currentEpoch：当前所处的 Leader 年代
*   lastZxid：history 中最近接收到的Proposal 的 zxid（最大zxid）  
     

Zab 的四个阶段

**1、选举阶段（Leader Election）**  
节点在一开始都处于选举节点，只要有一个节点得到超过半数节点的票数，它就可以当选准 Leader，只有到达第三个阶段（也就是同步阶段），这个准 Leader 才会成为真正的 Leader。

**Zookeeper 规定所有有效的投票都必须在同一个 轮次 中，每个服务器在开始新一轮投票时，都会对自己维护的 logicalClock 进行自增操作**。

每个服务器在广播自己的选票前，会将自己的投票箱（recvset）清空。该投票箱记录了所受到的选票。  
例如：Server\_2 投票给 Server\_3，Server\_3 投票给 Server\_1，则Server_1的投票箱为(2,3)、(3,1)、(1,1)。（每个服务器都会默认给自己投票）

前一个数字表示投票者，后一个数字表示被选举者。票箱中只会记录每一个投票者的最后一次投票记录，如果投票者更新自己的选票，则其他服务器收到该新选票后会在自己的票箱中更新该服务器的选票。

**这一阶段的目的就是为了选出一个准 Leader ，然后进入下一个阶段。**  
协议并没有规定详细的选举算法，后面会提到实现中使用的 Fast Leader Election。

![](https://img-blog.csdnimg.cn/img_convert/825b10a09607e37b7fac04f75d4580a3.webp?x-oss-process=image/format,png)

选举流程

  
 

**2、发现阶段（Descovery）**  
在这个阶段，Followers 和上一轮选举出的准 Leader 进行通信，同步 Followers 最近接收的事务 Proposal 。  
一个 Follower 只会连接一个 Leader，如果一个 Follower 节点认为另一个 Follower 节点，则会在尝试连接时被拒绝。被拒绝之后，该节点就会进入 Leader Election阶段。

**这个阶段的主要目的是发现当前大多数节点接收的最新 Proposal，并且准 Leader 生成新的 epoch ，让 Followers 接收，更新它们的 acceptedEpoch**。

![](https://img-blog.csdnimg.cn/img_convert/937b6cb405ea377e317913ab3223668b.webp?x-oss-process=image/format,png)

发现流程

  
 

**3、同步阶段（Synchronization）**  
**同步阶段主要是利用 Leader 前一阶段获得的最新 Proposal 历史，同步集群中所有的副本**。  
只有当 quorum（超过半数的节点） 都同步完成，准 Leader 才会成为真正的 Leader。Follower 只会接收 zxid 比自己 lastZxid 大的 Proposal。

![](https://img-blog.csdnimg.cn/img_convert/f179f84ddf4c21056abd15024542dfd1.png)

同步流程

  
 

**4、广播阶段（Broadcast）**  
到了这个阶段，Zookeeper 集群才能正式对外提供事务服务，并且 Leader 可以进行消息广播。同时，如果有新的节点加入，还需要对新节点进行同步。  
需要注意的是，Zab 提交事务并不像 2PC 一样需要全部 Follower 都 Ack，只需要得到 quorum（超过半数的节点）的Ack 就可以。

![](https://img-blog.csdnimg.cn/img_convert/a575aff8560a9b94bb75ef9c3f62e790.png)

广播流程

* * *

协议实现
----

协议的 Java 版本实现跟上面的定义略有不同，选举阶段使用的是 Fast Leader Election（FLE），它包含了步骤1的发现指责。因为FLE会选举拥有最新提议的历史节点作为 Leader，这样就省去了发现最新提议的步骤。

实际的实现将发现和同步阶段合并为 Recovery Phase（恢复阶段），所以，Zab 的实现实际上有三个阶段。

Zab协议三个阶段：

1）**选举（Fast Leader Election）**  
2）**恢复（Recovery Phase）**  
3）**广播（Broadcast Phase）**

**Fast Leader Election（快速选举）**  
前面提到的 FLE 会选举拥有最新Proposal history （lastZxid最大）的节点作为 Leader，这样就省去了发现最新提议的步骤。**这是基于拥有最新提议的节点也拥有最新的提交记录**

*   **成为 Leader 的条件：**  
    1）选 epoch 最大的  
    2）若 epoch 相等，选 zxid 最大的  
    3）若 epoch 和 zxid 相等，选择 server_id 最大的（zoo.cfg中的myid）

节点在选举开始时，都默认投票给自己，当接收其他节点的选票时，会根据上面的 **Leader条件** 判断并且更改自己的选票，然后重新发送选票给其他节点。**当有一个节点的得票超过半数，该节点会设置自己的状态为 Leading ，其他节点会设置自己的状态为 Following**。

![](https://img-blog.csdnimg.cn/img_convert/667db36fc93f0b97fd4a428f72a3cdfd.webp?x-oss-process=image/format,png)

选举过程

  
 

**Recovery Phase（恢复阶段）**  
这一阶段 Follower 发送他们的 lastZxid 给 Leader，Leader 根据 lastZxid 决定如何同步数据。这里的实现跟前面的 Phase 2 有所不同：Follower 收到 TRUNC 指令会终止 L.lastCommitedZxid 之后的 Proposal ，收到 DIFF 指令会接收新的 Proposal。

> history.lastCommitedZxid：最近被提交的 Proposal zxid  
> history.oldThreshold：被认为已经太旧的已经提交的 Proposal zxid
> 
>  
> 
> ![](https://img-blog.csdnimg.cn/img_convert/621a4e5260d84b1214fda80dae62e6bb.webp?x-oss-process=image/format,png)
> 
> 恢复阶段

* * *

什么情况下zab协议会进入崩溃恢复模式？
====================

*   1、当服务器启动时
    
*   2、当leader 服务器出现网络中断，崩溃或者重启的情况
    
*   3、当集群中已经不存在过半的服务器与Leader服务器保持正常通信。
    

* * *

zab协议进入崩溃恢复模式会做什么？
==================

1、当leader出现问题，zab协议进入崩溃恢复模式，并且选举出新的leader。当新的leader选举出来以后，如果集群中已经有过半机器完成了leader服务器的状态同（数据同步），退出崩溃恢复，进入消息广播模式。

2、当新的机器加入到集群中的时候，如果已经存在leader服务器，那么新加入的服务器就会自觉进入崩溃恢复模式，找到leader进行数据同步。

特殊情况下需要解决的两个问题：
===============

### 问题一：已经被处理的事务请求（proposal）不能丢（commit的）

> 当 leader 收到合法数量 follower 的 ACKs 后，就向各个 follower 广播 COMMIT 命令，同时也会在本地执行 COMMIT 并向连接的客户端返回「成功」。但是如果在各个 follower 在收到 COMMIT 命令前 leader 就挂了，导致剩下的服务器并没有执行都这条消息。

*   如何解决 _已经被处理的事务请求（proposal）不能丢（commit的）_ 呢？

1、选举拥有 proposal 最大值（即 zxid 最大） 的节点作为新的 leader。

> 由于所有提案被 COMMIT 之前必须有合法数量的 follower ACK，即必须有合法数量的服务器的事务日志上有该提案的 proposal，因此，zxid最大也就是数据最新的节点保存了所有被 COMMIT 消息的 proposal 状态。

2、新的 leader 将自己事务日志中 proposal 但未 COMMIT 的消息处理。

3、新的 leader 与 follower 建立先进先出的队列， 先将自身有而 follower 没有的 proposal 发送给 follower，再将这些 proposal 的 COMMIT 命令发送给 follower，以保证所有的 follower 都保存了所有的 proposal、所有的 follower 都处理了所有的消息。通过以上策略，能保证已经被处理的消息不会丢。

### 问题二：没被处理的事务请求（proposal）不能再次出现什么时候会出现事务请求被丢失呢？

> 当 leader 接收到消息请求生成 proposal 后就挂了，其他 follower 并没有收到此 proposal，因此经过恢复模式重新选了 leader 后，这条消息是被跳过的。 此时，之前挂了的 leader 重新启动并注册成了 follower，他保留了被跳过消息的 proposal 状态，与整个系统的状态是不一致的，需要将其删除。

*   如果解决呢？

Zab 通过巧妙的设计 zxid 来实现这一目的。

一个 zxid 是64位，高 32 是纪元（epoch）编号，每经过一次 leader 选举产生一个新的 leader，新 leader 会将 epoch 号 +1。低 32 位是消息计数器，每接收到一条消息这个值 +1，新 leader 选举后这个值重置为 0。

这样设计的好处是旧的 leader 挂了后重启，它不会被选举为 leader，因为此时它的 zxid 肯定小于当前的新 leader。当旧的 leader 作为 follower 接入新的 leader 后，新的 leader 会让它将所有的拥有旧的 epoch 号的未被 COMMIT 的 proposal 清除。
*** 
## ⭐️⭐️⭐️⭐️⭐️
## Paxos算法了解过吗？Paxos
=====

目标：复制日志
-------

![](https://img-blog.csdnimg.cn/20190518193359501.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlc3Ricm9va2xpdQ==,size_16,color_FFFFFF,t_70)

*   复制日志 =\> 复制状态机
    *   所有服务器按照相同的顺序执行相同的命令
*   一致性模型确保正确的日志复制
*   只要大部分服务器是运行的系统就能工作
*   失败的模型：失败-停止(非拜占庭)，延迟/丢失信息

Basic Paxos
-----------

*   Proposers：
    *   活动的：提出特定的值被选中
    *   处理客户请求
*   Acceptors：
    *   被动的：响应消息给proposers
    *   回应达成共识的投票
    *   保存选中的值
    *   想知道哪个值被选中
*   每个服务器都包含proposer和acceptor

### 一个Acceptor

![](https://img-blog.csdnimg.cn/20190518193426471.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlc3Ricm9va2xpdQ==,size_16,color_FFFFFF,t_70)

*   Q：如果acceptor挂掉了怎么办？
*   A：多个acceptors，选中被大多数acceptors的值

### 问题：平分投票

![](https://img-blog.csdnimg.cn/20190518193451161.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlc3Ricm9va2xpdQ==,size_16,color_FFFFFF,t_70)

*   Q：Acceptor只接受第一个到达的值？
*   A：如果同时提出提案，不会选中任何值，所以Acceptors必须可以选择多个不同的值

### 问题：选择冲突

*   Q：Acceptor接受所有到达的值？
*   A：可能会导致选择多个值(如下图中的S3)，所以一旦一个值被选中，以后的提案必须提出/选择一样的值(两阶段提交)  
    ![](https://img-blog.csdnimg.cn/20190518194809355.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlc3Ricm9va2xpdQ==,size_16,color_FFFFFF,t_70)

### 仍然有选择冲突

下图的流程：

1.  s1看到此时其他服务器没有接受某个值，之后提出red值
2.  s5当时也看到此时没有其他服务器没有接受某个值，就提出blue值
3.  blue很快就被s3、s4、s5接受，而s3之后也会接受red值  
    ![](https://img-blog.csdnimg.cn/20190518194858922.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlc3Ricm9va2xpdQ==,size_16,color_FFFFFF,t_70)

*   s1的提案必须被终止(s3必须拒绝它)
*   因此提案必须有序，拒绝旧的提案

### 提案值

*   每个提案有一个唯一的值
    *   大的优先级高
    *   提案者必须选择一个比之前见过的还大的提案值
*   一个简单的方法：
    *   一个提案值包括 轮值+服务器ID
    *   每个服务器保存 maxRound
    *   为产生一个新的提案值：
        *   递增 maxRound
        *   与服务器ID关联
    *   提案者必须将 maxRound 持久化到磁盘，防止提案值在机器宕机重启后重用

### 两阶段方法

*   阶段一：Prepare RPCs
    *   找到已经被选中的值
    *   阻止旧的提案
*   阶段二：Accept RPCs
    *   请求acceptors接受值

### 流程

![](https://img-blog.csdnimg.cn/20190518215222453.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlc3Ricm9va2xpdQ==,size_16,color_FFFFFF,t_70)

### 例子

在之后提出一个提案有三种可能：

1.  之前的值已经被选中了
    
    *   新的Proposer会发现它并使用它  
        ![](https://img-blog.csdnimg.cn/20190518215828101.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlc3Ricm9va2xpdQ==,size_16,color_FFFFFF,t_70)
    *   先说明一下方框内写的是什么意思，P表示Prepare，A表示Accept，  
        3.1中的3表示 Round Number，1表示由s1提出，X为acceptedValue
    *   可以看到之后的提案了解到X已经被选中，s3、s4、s5也会选中同样的值
2.  之前没有值被选中，但已经被接受
    
    *   新的Proposer会发现它并使用它
    *   与前一种情况类似  
        ![](https://img-blog.csdnimg.cn/20190518220442791.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlc3Ricm9va2xpdQ==,size_16,color_FFFFFF,t_70)
3.  之前没有值被选中，也没看到值被接受
    
    *   后来的Proposer会使用自己的值
    *   旧的值会被拒绝  
        ![](https://img-blog.csdnimg.cn/20190518220851962.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlc3Ricm9va2xpdQ==,size_16,color_FFFFFF,t_70)

### 活锁

![](https://img-blog.csdnimg.cn/2019051822145557.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlc3Ricm9va2xpdQ==,size_16,color_FFFFFF,t_70)

### 其它

*   只有 proposer 知道哪个值被选中了，acceptor是不知道的
*   如果其它服务器想知道，就必须运行paxos

Multi-Paxos
-----------

*   用日志项将 Basic Paxos 分成每一轮
    *   添加 index 参数到 Prepare 和 Accept  
        ![](https://img-blog.csdnimg.cn/20190519085213173.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlc3Ricm9va2xpdQ==,size_16,color_FFFFFF,t_70)

### 概述

*   怎么选择哪个日志项来存放给定的客户请求？
*   性能优化：
    *   使用 leader 减少 proposer 冲突
    *   消除大部分 Prepare 请求
*   复制的完整型
*   客户协议
*   配置变更

### 选择日志项

*   当客户传来请求：
    *   找到第一个没有被选中的日志项
    *   运行 Basic Paxos，在这个 index， propose 客户命令
    *   Prepare 返回 acceptedValue？
        *   Yes，结束选中 acceptedValue
        *   No，选中客户命令

![](https://img-blog.csdnimg.cn/2019051909092591.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlc3Ricm9va2xpdQ==,size_16,color_FFFFFF,t_70)

*   当接收到请求时，服务器 S1 上的记录可能处于不同的状态，服务器知道有些记录已经被选定（1-mov，2-add，6-ret），在后面我会介绍服务器是如何知道这些记录已经被选定的。服务器上也有一些其他的记录（3-cmp），但此时它还不知道这条记录已经被选定。在这个例子中，我们可以看到，实际上记录（3-cmp）已经被选定了，因为在服务器 S3 上也有相同的记录，只是 S1 和 S3 还不知道。还有空白记录（4-，5-）没有接受任何值，不过其他服务器上相应的记录可能已经有值了。
    
*   当 jmp 请求到达 S1 后，它会找到第一个没有被选定的记录（3-cmp），然后它会试图让 jmp 作为该记录的选定值。为了让这个例子更具体一些，我们假设服务器 S3 已经下线。所以 Paxos 协议在服务器 S1 和 S2 上运行，服务器 S1 会尝试让记录 3 接受 jmp 值，它正好发现记录 3 内已经有值（3-cmp），这时它会结束选择并进行比较，S1 会向 S2 发送接受（3-cmp）的请求，S2 会接受 S1 上已经接受的 3-cmp 并完成选定。这时（3-cmp）变成粗体，不过还没能完成客户端的请求，所以我们返回到第一步，重新进行选择。找到当前还没有被选定的记录（这次是记录 4-），这时 S1 会发现 S2 相应记录上已经存在接受值（4-sub），所以它会再次放弃 jmp ，并将 sub 值作为它 4- 记录的选定值。所以此时 S1 会再次返回到第一步，重新进行选择，当前未被选定的记录是 5- ，这次它会成功的选定 5-jmp ，因为 S1 没有发现其他服务器上有接受值。
    

注意事项：

*   在这种方式下，单个服务器可以同时处理多个客户端请求，也就是说前一个客户端请求会找到记录 3- ，下一个客户端请求就会找到记录 4- ，只要我们为不同的请求使用不同的记录，它们都能以并行的方式独立运行。
*   不过，当进入到状态机后，就必须以一定的顺序来执行命令，命令必须与它们在日志内的顺序一致，也就是说只有当记录 3- 完成执行后，才能执行记录 4- 。

### 提高效率

*   Basic Paxos 是低效的
    1.  多个 proposers 冲突问题
    2.  对于选中一个值需要两轮RPCs(Prepare、Accept)
*   解决：
    1.  选一个 leader
        *   在一个时刻，只有一个 Proposer
    2.  消除大部分 Prepare RPCs
        *   一轮 Prepare 完整的日志，而不是单条记录。
        *   一旦完成了 Prepare，它就可以通过 Accept 请求，同时创建多条记录。这样就不需要多次使用 Prepare 阶段。这样就能减少一半的 RPCs。

### 领导选举

选举领导者的方式有很多，这里只介绍一种由 Leslie Lamport 建议的简单方式。

*   让有 **最高 ID** 的服务器作为领导者
*   可以通过每个服务器定期（每 T ms）向其他服务器 **发送心跳消息** 的方式来实现。这些消息包含发送服务器的 ID
*   如果它们没有能收到某一具有高 ID 的服务器的心跳消息，这个间隔（通常是 2T ms）需要设置的足够长，让消息有足够的通信传递时间。所以，如果这些服务器没有能接收到高 ID 的服务器消息，然后它们会自己选举成为领导者。
*   也就是说，首先它会从客户端接受到请求，其次在 Paxos 协议中，它会 **同时扮演 proposer 和 acceptor**
*   如果机器能够接收到来自高 ID 的服务器的心跳消息，它就不会作为 leader，如果它接收到客户端的请求，那么它会 **拒绝** 这个请求，并告知客户端与 leader 进行通信。
*   非 leader 服务器不会作为 proposer，**只会作为 acceptor**
*   这个机制的优势在于，它不太可能出现两个 leader 同时工作的情况，即使这样，如果出现了两个 leader，Paxos 协议还是能正常工作，只是不是那么高效而已。
*   应该注意的是，实际上大多数系统都不会采用这种选举方式，它们会采用基于 **租约** 的方式（lease based approach），这比上述介绍的机制要复杂的多，不过也有其优势。

### 减少 Prepare 的 RPC 请求

*   为什么需要 Prepare？
    *   需要使用提议序号来 **阻止** 旧的提议
    *   使用 Prepare 阶段来检查已经被接受的值，这样就可以使用这些值来替代原本自己希望接受的值。

1.  第一个问题是阻止所有的提议，我们可以通过改变提议序号的含义来解决这个问题， **将提议序号全局化，代表完整的日志** ，而不是为每个日志记录都保留独立的提议序号。这么做要求我们在完成一轮准备请求后，当然我们知道这样做会锁住整个日志，所以后续的日志记录不需要其他的准备请求。
    
2.  第二个问题有点讨巧。因为在不同接受者的不同日志记录里有很多接受值，为了处理这些值，我们扩展了准备请求的返回信息。和之前一样，准备请求仍然返回 acceptor 所接受的最高 ID 的提议，它只对当前记录这么做，不过除了这个， acceptor 会查看当前请求的后续日志记录，**如果后续的日志里没有接受值** ，它还会返回这些记录的标志位 **noMoreAccepted** 。
    
3.  使用了这种领导者选举的机制，领导者会达到一个状态，每个 acceptor 都返回 noMoreAccepted ，领导者知道所有它已接受的记录。所以一旦达到这个状态，对于单个 acceptor 我们不需要再向这些 acceptor 发送准备请求，因为它们已经知道了日志的状态。
    
4.  不仅如此，一旦从集群 **大多数 acceptor 那获得 noMoreAccepted 返回值** ，我们就 **不需要发送准备的 RPC 请求** 。也就是说， leader 可以简单地发送 Accept 请求，只需要一轮的 RPC 请求。这个过程会一直执行下去，唯一能改变的就是有其他的服务器被选举成了 leader ，当前 leader 的 Accept 请求会被拒绝，整个过程会重新开始。
    

### 复制的完整性

*   之前的复制是不完整的
    *   日志项只需要复制到大多数，我们需要复制到 **全部**
    *   只有 proposer 知道某个日志项被选中了，我们需要所有服务器都知道哪些日志项被选中了

解决办法：

1.  在后台持续尝试 Accept RPCs 直到所有 acceptors 返回
2.  追踪被选中的日志项
    *   让acceptedProposal\[i\] = 无穷大，这样这个日志项就不可以被覆盖，也就是说被选中了
    *   每个服务器还会保持一个 firstUnchosenIndex：表示未被标识选定的最小下标值
3.  proposer 告诉 acceptors 已经被选中的日志项
    *   Proposer 在 Accept RPCs 中包含它的 firstUnchosenIndex
    *   Acceptor 将选中第i个日志项，如果：
        *   i < request.firstUnchosenIndex
        *   acceptedProposal\[i\] == request.proposal
    *   结果：acceptors知道大多数被选中的日志项

![](https://img-blog.csdnimg.cn/2019051912223475.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlc3Ricm9va2xpdQ==,size_16,color_FFFFFF,t_70)

该 acceptor 在 accept 之前的第6个日志项的提议序号为 3.4 ，  
这时它收到一个提议序号也为 3.4 的 accepte 请求，并且 请求的 firstUnchosenIndex = 7，大于之前 3.4 所在的 6，所以将选中第6个日志项，同时该请求的 index = 8，将 3.4 的请求放到第8个日志项

这个机制无法解决所有的问题。问题在于 acceptor 可能会接收到来自于不同 proposer 的某些日志记录，这里记录 4 可能来自于之前轮次的服务器 S5 ，不幸的是这种情况下， acceptor 是无法知道该记录是否已被选定。它也可能是一个已失效过时的值。

我们知道它已经被 proposer 选定，但是它可能应该被另外一个值所取代。所以还需要多做一步。

4.  旧 leader 的日志项
    *   Acceptor 返回它的 fristUnchosenIndex 在 Accept回答中
    *   如果 proposer 的 firstUnchosenIndex > acceptor回答的 firstUnchosenIndex(说明 acceptor 中的某些状态不确定)，proposer就会在后台发送 **Success RPC**
    *   Success(index, v):通知 acceptor 该日志项被选中了
        *   acceptedValue\[index\] = v
        *   acceptedProposal\[index\] = 无穷大
        *   return firstUnchosenIndex
        *   如果需要(可能存在多个不确定的状态)，Proposer 发送额外的Success RPC

### 客户端协议

*   发送命令给 leader
    *   如果不知道哪个是 leader，随便选择一个服务器
    *   如果该服务不是 leader，**重定向** 给 leader
*   leader 直到日志项被选中并且被 leader 的状态机执行才回应客户
*   如果请求超时(leader 挂了)
    *   客户重新发送命令给其他服务器
    *   最终重定向给新 leader
    *   给新 leader 重试请求

#### 问题

*   如果 laeder 在执行完命令但在回应之前挂掉
    
    *   该命令不能执行两次
*   解决：客户端需要为每条命令提供一个 **唯一的 id**
    
    *   服务器会将该 id 存入日志项中
    *   状态机会记录每个客户最近执行的命令，即 **最高 id 序号**
    *   在执行命令之前，状态机会检查该命令如否被执行过，如果执行过：
        *   忽略
        *   返回之前执行的结果
*   结果：只要客户端不崩溃，就能获得 **exactly once** 的保证，每个客户端命令仅被集群执行一次。如果客户端出现崩溃，就处于 **at most once** 的情况，也就是说客户端的命令可能执行，也可能没有执行。但是如果客户端是活着的，这些命令只会执行一次
    

### 配置变更

同一时刻不可以出现两个不重叠的多数派  
![](https://img-blog.csdnimg.cn/20190519131524470.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlc3Ricm9va2xpdQ==,size_16,color_FFFFFF,t_70)

解决办法：

*   Leslie Lamport 建议的 Paxos 配置变更方案是用 **日志** 来管理这些变更，当前的配置作为日志的一条记录存储，并与其他的日志记录一同被复制同步。
*   所以下图中 1-C1、3-C2 表示两个配置信息，其他的用来存储普通的命令。这里有趣的是，配置所使用每条记录是由它的更早的记录所决定的。
*   这里有一个系统参数 å 来决定这个更早是多早，假设 å 为 3，我们这里有两个配置相关的记录，C1 存于记录 1 中，C2 存于记录 3 中，这也意味着 C1 在 3 条记录内不会生效，也就是说，C1 从记录 4 开始才会生效。C2 从记录 6 开始才会生效。所以当我们选择记录 1、2、3 时，生效的配置会是 C1 之前的那条配置，这里我们将其标记为 C0 。
*   这里的 å 是在系统启动时配置好的参数，这个参数可以用来限制同时使用的配置信息，也就是说，我们是无法在 i+å 之前选择使用记录 i 中的配置的。因为我们无法知道哪些服务器使用哪些配置，也无法知道大多数所代表的服务器数量。所以如果 å 的值很小时，整个过程是序列化的，每条记录选择的配置都是不同的，如果 å 为 3 ，也就意味着同时有三条记录可以使用相同的配置，如果 å 大很多时，事情会变得更复杂，我们需要长时间的等待，让新的配置生效。也就是说如果 å 的值是 1000 时，我们需要在 1000 个记录之后才能等到这个配置生效。

![](https://img-blog.csdnimg.cn/20190519131721110.png)

总结
--

*   Basic Paxos：
    *   Prepare 阶段
    *   Acceptor 阶段
*   Multi-Paxos：
    *   Choosing log entries
    *   Leader election
    *   Eliminting most Prepare requests
    *   Full infomation propagation
*   客户协议
*   配置变更
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 分布式id如何生成？#### **一、为什么要用分布式ID？**

在说分布式ID的具体实现之前，我们来简单分析一下为什么用分布式ID？分布式ID应该满足哪些特征？

###### 1、什么是分布式ID？

拿MySQL数据库举个栗子：

在我们业务数据量不大的时候，单库单表完全可以支撑现有业务，数据再大一点搞个MySQL主从同步读写分离也能对付。

但随着数据日渐增长，主从同步也扛不住了，就需要对数据库进行分库分表，但分库分表后需要有一个唯一ID来标识一条数据，数据库的自增ID显然不能满足需求；特别一点的如订单、优惠券也都需要有`唯一ID`做标识。此时一个能够生成`全局唯一ID`的系统是非常必要的。那么这个`全局唯一ID`就叫`分布式ID`。

###### 2、那么分布式ID需要满足那些条件？

*   全局唯一：必须保证ID是全局性唯一的，基本要求
    
*   高性能：高可用低延时，ID生成响应要块，否则反倒会成为业务瓶颈
    
*   高可用：100%的可用性是骗人的，但是也要无限接近于100%的可用性
    
*   好接入：要秉着拿来即用的设计原则，在系统设计和实现上要尽可能的简单
    
*   趋势递增：最好趋势递增，这个要求就得看具体业务场景了，一般不严格要求
    

#### **二、 分布式ID都有哪些生成方式？**

今天主要分析一下以下9种，分布式ID生成器方式以及优缺点：

*   UUID
    
*   数据库自增ID
    
*   数据库多主模式
    
*   号段模式
    
*   Redis
    
*   雪花算法（SnowFlake）
    
*   滴滴出品（TinyID）
    
*   百度 （Uidgenerator）
    
*   美团（Leaf）
    

那么它们都是如何实现？以及各自有什么优缺点？我们往下看  

![image.png](https://i.loli.net/2021/11/14/KLiBSd4wQnkjDyZ.png)

##### 1、基于UUID

在Java的世界里，想要得到一个具有唯一性的ID，首先被想到可能就是`UUID`，毕竟它有着全球唯一的特性。那么`UUID`可以做`分布式ID`吗？**答案是可以的，但是并不推荐！**

```java
public static void main(String[] args) {        
	String uuid = UUID.randomUUID().toString().replaceAll("-","");       
    System.out.println(uuid); 
}
```

`UUID`的生成简单到只有一行代码，输出结果 `c2b8c2b9e46c47e3b30dca3b0d447718`，但UUID却并不适用于实际的业务需求。像用作订单号`UUID`这样的字符串没有丝毫的意义，看不出和订单相关的有用信息；而对于数据库来说用作业务`主键ID`，它不仅是太长还是字符串，存储性能差查询也很耗时，所以不推荐用作`分布式ID`。

**优点：**

*   生成足够简单，本地生成无网络消耗，具有唯一性
    

**缺点：**

*   无序的字符串，不具备趋势自增特性
    
*   没有具体的业务含义
    
*   长度过长16 字节128位，36位长度的字符串，存储以及查询对MySQL的性能消耗较大，MySQL官方明确建议主键要尽量越短越好，作为数据库主键 `UUID` 的无序性会导致数据位置频繁变动，严重影响性能。
    

##### 2、基于数据库自增ID

基于数据库的`auto_increment`自增ID完全可以充当`分布式ID`，具体实现：需要一个单独的MySQL实例用来生成ID，建表结构如下：

```sql
CREATE DATABASE `SEQ_ID`;
CREATE TABLE SEQID.SEQUENCE_ID (    
	id bigint(20) unsigned NOT NULL auto_increment,     
	value char(10) NOT NULL default '',    
    PRIMARY KEY (id),
) ENGINE=MyISAM;

insert into SEQUENCE_ID(value)  VALUES ('values');
```

当我们需要一个ID的时候，向表中插入一条记录返回`主键ID`，但这种方式有一个比较致命的缺点，访问量激增时MySQL本身就是系统的瓶颈，用它来实现分布式服务风险比较大，不推荐！

**优点：**

*   实现简单，ID单调自增，数值类型查询速度快
    

**缺点：**

*   DB单点存在宕机风险，无法扛住高并发场景
    

##### 3、基于数据库集群模式

前边说了单点数据库方式不可取，那对上边的方式做一些高可用优化，换成主从模式集群。害怕一个主节点挂掉没法用，那就做双主模式集群，也就是两个Mysql实例都能单独的生产自增ID。

那这样还会有个问题，两个MySQL实例的自增ID都从1开始，**会生成重复的ID怎么办？**

**解决方案**：设置`起始值`和`自增步长`

MySQL_1 配置：

```
set @@auto_increment_offset = 1;     -- 起始值set 
@@auto_increment_increment = 2;  -- 步长
```

MySQL_2 配置：

```
set @@auto_increment_offset = 2;     -- 起始值
set @@auto_increment_increment = 2;  -- 步长
```

这样两个MySQL实例的自增ID分别就是：

> 1、3、5、7、9   
> 2、4、6、8、10

那如果集群后的性能还是扛不住高并发咋办？就要进行MySQL扩容增加节点，这是一个比较麻烦的事。

![image.png](https://i.loli.net/2021/11/14/u7BGVRzQHFJ3f4k.png)
  
从上图可以看出，水平扩展的数据库集群，有利于解决数据库单点压力的问题，同时为了ID生成特性，将自增步长按照机器数量来设置。

  

增加第三台`MySQL`实例需要人工修改一、二两台`MySQL实例`的起始值和步长，把`第三台机器的ID`起始生成位置设定在比现有`最大自增ID`的位置远一些，但必须在一、二两台`MySQL实例`ID还没有增长到`第三台MySQL实例`的`起始ID`值的时候，否则`自增ID`就要出现重复了，**必要时可能还需要停机修改**。

**优点：**

*   解决DB单点问题
    

**缺点：**

*   不利于后续扩容，而且实际上单个数据库自身压力还是大，依旧无法满足高并发场景。
    

##### 4、基于数据库的号段模式

号段模式是当下分布式ID生成器的主流实现方式之一，号段模式可以理解为从数据库批量的获取自增ID，每次从数据库取出一个号段范围，例如 (1,1000\] 代表1000个ID，具体的业务服务将本号段，生成1~1000的自增ID并加载到内存。表结构如下：

```java
CREATE TABLE id_generator (  
	id int(10) NOT NULL,  
    max_id bigint(20) NOT NULL COMMENT '当前最大id',  
    step int(20) NOT NULL COMMENT '号段的布长',  
    biz_type    int(20) NOT NULL COMMENT '业务类型',  
    version int(20) NOT NULL COMMENT '版本号',  
    PRIMARY KEY (`id`)
) 
```

* biz_type ：代表不同业务类型
* max_id ：当前最大的可用id
* step ：代表号段的长度
* version ：是一个乐观锁，每次都更新version，保证并发时数据的正确性

| id | biz_type | max_id | step | version |
| -- | -- | -- | -- | -- | 
| 1 | 101 | 1000 | 2000 | 0 |

等这批号段ID用完，再次向数据库申请新号段，对`max_id`字段做一次`update`操作，`update max_id= max_id + step`，update成功则说明新号段获取成功，新的号段范围是`(max_id ,max_id +step]`。

```sql
update id_generator set max_id = #{max_id+step}, version = version + 1 where version = # {version} and biz_type = XXX
```

由于多业务端可能同时操作，所以采用版本号`version`乐观锁方式更新，这种`分布式ID`生成方式不强依赖于数据库，不会频繁的访问数据库，对数据库的压力小很多。

##### 5、基于Redis模式

`Redis`也同样可以实现，原理就是利用`redis`的 `incr`命令实现ID的原子性自增。

```
127.0.0.1:6379> set seq_id 1     // 初始化自增ID为1
OK
127.0.0.1:6379> incr seq_id      // 增加1，并返回递增后的数值
(integer) 2
```

用`redis`实现需要注意一点，要考虑到redis持久化的问题。`redis`有两种持久化方式`RDB`和`AOF`

*   `RDB`会定时打一个快照进行持久化，假如连续自增但`redis`没及时持久化，而这会Redis挂掉了，重启Redis后会出现ID重复的情况。
    
*   `AOF`会对每条写命令进行持久化，即使`Redis`挂掉了也不会出现ID重复的情况，但由于incr命令的特殊性，会导致`Redis`重启恢复的数据时间过长。
    

##### 6、基于雪花算法（Snowflake）模式

雪花算法（Snowflake）是twitter公司内部分布式项目采用的ID生成算法，开源后广受国内大厂的好评，在该算法影响下各大公司相继开发出各具特色的分布式生成器。

![image.png](https://i.loli.net/2021/11/14/NLwdDc4k291aCBm.png)

`Snowflake`生成的是Long类型的ID，一个Long类型占8个字节，每个字节占8比特，也就是说一个Long类型占64个比特。

Snowflake ID组成结构：`正数位`（占1比特）+ `时间戳`（占41比特）+ `机器ID`（占5比特）+ `数据中心`（占5比特）+ `自增值`（占12比特），总共64比特组成的一个Long类型。

*   第一个bit位（1bit）：Java中long的最高位是符号位代表正负，正数是0，负数是1，一般生成ID都为正数，所以默认为0。
    
*   时间戳部分（41bit）：毫秒级的时间，不建议存当前时间戳，而是用（当前时间戳 - 固定开始时间戳）的差值，可以使产生的ID从更小的值开始；41位的时间戳可以使用69年，(1L << 41) / (1000L * 60 * 60 * 24 * 365) = 69年
    
*   工作机器id（10bit）：也被叫做`workId`，这个可以灵活配置，机房或者机器号组合都可以。
    
*   序列号部分（12bit），自增值支持同一毫秒内同一个节点可以生成4096个ID
    

根据这个算法的逻辑，只需要将这个算法用Java语言实现出来，封装为一个工具方法，那么各个业务应用可以直接使用该工具方法来获取分布式ID，只需保证每个业务应用有自己的工作机器id即可，而不需要单独去搭建一个获取分布式ID的应用。

** Java版本的`Snowflake`算法实现：**

```java
/** 
 * Twitter的SnowFlake算法,使用SnowFlake算法生成一个整数，然后转化为62进制变成一个短地址URL 
 * 
 * https://github.com/beyondfengyu/SnowFlake 
 */
 
public class SnowFlakeShortUrl {    
	/**     
     * 起始的时间戳     
     */    
    private final static long START_TIMESTAMP = 1480166465631L;    
    
    /**     
     * 每一部分占用的位数     
     */    
    private final static long SEQUENCE_BIT = 12;   //序列号占用的位数    
    private final static long MACHINE_BIT = 5;     //机器标识占用的位数    
    private final static long DATA_CENTER_BIT = 5; //数据中心占用的位数    
    
    /**     
     * 每一部分的最大值     
     */    
    private final static long MAX_SEQUENCE = -1L ^ (-1L << SEQUENCE_BIT);    
    private final static long MAX_MACHINE_NUM = -1L ^ (-1L << MACHINE_BIT);    
    private final static long MAX_DATA_CENTER_NUM = -1L ^ (-1L << DATA_CENTER_BIT);    
    
    /**     
     * 每一部分向左的位移     
     */    
    private final static long MACHINE_LEFT = SEQUENCE_BIT;    
    private final static long DATA_CENTER_LEFT = SEQUENCE_BIT + MACHINE_BIT;    
    private final static long TIMESTAMP_LEFT = DATA_CENTER_LEFT + DATA_CENTER_BIT;    
    
    private long dataCenterId;  //数据中心    
    private long machineId;     //机器标识    
    private long sequence = 0L; //序列号    
    private long lastTimeStamp = -1L;  //上一次时间戳    
    
    private long getNextMill() {        
    	long mill = getNewTimeStamp();        
        while (mill <= lastTimeStamp) {            
        	mill = getNewTimeStamp();        
        }        
        return mill;    
    }    
    
    private long getNewTimeStamp() {        
    	return System.currentTimeMillis();    
    }    
    
    /**     
     * 根据指定的数据中心ID和机器标志ID生成指定的序列号     
     *     
     * @param dataCenterId 数据中心ID     
     * @param machineId    机器标志ID     
     */    
     
    public SnowFlakeShortUrl(long dataCenterId, long machineId) {        
    	if (dataCenterId > MAX_DATA_CENTER_NUM || dataCenterId < 0) {            
        	throw new IllegalArgumentException("DtaCenterId can't be greater than MAX_DATA_CENTER_NUM or less than 0！");        
        }        
        
        if (machineId > MAX_MACHINE_NUM || machineId < 0) {            
        	throw new IllegalArgumentException("MachineId can't be greater than MAX_MACHINE_NUM or less than 0！");        
        }        
        
        this.dataCenterId = dataCenterId;        
        this.machineId = machineId;    
    }    
    
    /**     
     * 产生下一个ID     
  	 *     
  	 * @return     
  	 */    
     public synchronized long nextId() {        
     long currTimeStamp = getNewTimeStamp();   
     
     if (currTimeStamp < lastTimeStamp) {            
     	throw new RuntimeException("Clock moved backwards.  Refusing to generate id");        
     }    
     
     if (currTimeStamp == lastTimeStamp) {            
     	//相同毫秒内，序列号自增            
        sequence = (sequence + 1) & MAX_SEQUENCE;            
        
        //同一毫秒的序列数已经达到最大            
        if (sequence == 0L) {                
        	currTimeStamp = getNextMill();            
       	}        
     } else {            
     	//不同毫秒内，序列号置为0            
        sequence = 0L;        
     }        
     
     lastTimeStamp = currTimeStamp;        
     
     return (currTimeStamp - START_TIMESTAMP) << TIMESTAMP_LEFT //时间戳部分                
     		| dataCenterId << DATA_CENTER_LEFT       //数据中心部分                
            | machineId << MACHINE_LEFT             //机器标识部分                
            | sequence;                             //序列号部分    
	}    
            
    public static void main(String[] args) {        
        SnowFlakeShortUrl snowFlake = new SnowFlakeShortUrl(2, 3);        

        for (int i = 0; i < (1 << 4); i++) {            
            //10进制            
            System.out.println(snowFlake.nextId());        
        }    
    }
}

##### 7、百度（uid-generator）

`uid-generator`是由百度技术部开发，项目GitHub地址 https://github.com/baidu/uid-generator

`uid-generator`是基于`Snowflake`算法实现的，与原始的`snowflake`算法不同在于，`uid-generator`支持自`定义时间戳`、`工作机器ID`和 `序列号` 等各部分的位数，而且`uid-generator`中采用用户自定义`workId`的生成策略。

`uid-generator`需要与数据库配合使用，需要新增一个`WORKER_NODE`表。当应用启动时会向数据库表中去插入一条数据，插入成功后返回的自增ID就是该机器的`workId`数据由host，port组成。

**对于`uid-generator` ID组成结构**：

`workId`，占用了22个bit位，时间占用了28个bit位，序列化占用了13个bit位，需要注意的是，和原始的`snowflake`不太一样，时间的单位是秒，而不是毫秒，`workId`也不一样，而且同一应用每次重启就会消费一个`workId`。

##### 8、美团（Leaf）

`Leaf`由美团开发，github地址：https://github.com/Meituan-Dianping/Leaf

`Leaf`同时支持号段模式和`snowflake`算法模式，可以切换使用。

##### 号段模式

先导入源码，再建一张表`leaf_alloc`

```
DROP TABLE IF EXISTS `leaf_alloc`;

CREATE TABLE `leaf_alloc` (  
	`biz_tag` varchar(128)  NOT NULL DEFAULT '' COMMENT '业务key',  
    `max_id` bigint(20) NOT NULL DEFAULT '1' COMMENT '当前已经分配了的最大id',  
    `step` int(11) NOT NULL COMMENT '初始步长，也是动态调整的最小步长',  
    `description` varchar(256)  DEFAULT NULL COMMENT '业务key的描述',  
    `update_time` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '数据库维护的更新时间',  
    PRIMARY KEY (`biz_tag`)
) ENGINE=InnoDB;

然后在项目中开启`号段模式`，配置对应的数据库信息，并关闭`snowflake`模式

```
leaf.name=com.sankuai.leaf.opensource.test
leaf.segment.enable=true
leaf.jdbc.url=jdbc:mysql://localhost:3306/leaf_test?useUnicode=true&characterEncoding=utf8&characterSetResults=utf8leaf.jdbc.username=rootleaf.jdbc.password=root

leaf.snowflake.enable=false
#leaf.snowflake.zk.address=
#leaf.snowflake.port=
```

启动`leaf-server` 模块的 `LeafServerApplication`项目就跑起来了

号段模式获取分布式自增ID的测试url ：http：//localhost：8080/api/segment/get/leaf-segment-test

监控号段模式：http://localhost:8080/cache

##### snowflake模式

`Leaf`的snowflake模式依赖于`ZooKeeper`，不同于`原始snowflake`算法也主要是在`workId`的生成上，`Leaf`中`workId`是基于`ZooKeeper`的顺序Id来生成的，每个应用在使用`Leaf-snowflake`时，启动时都会都在`Zookeeper`中生成一个顺序Id，相当于一台机器对应一个顺序节点，也就是一个`workId`。

```
leaf.snowflake.enable=true
leaf.snowflake.zk.address=127.0.0.1
leaf.snowflake.port=2181
```

snowflake模式获取分布式自增ID的测试url：http://localhost:8080/api/snowflake/get/test

##### 9、滴滴（Tinyid）

`Tinyid`由滴滴开发，Github地址：https://github.com/didi/tinyid。

`Tinyid`是基于号段模式原理实现的与`Leaf`如出一辙，每个服务获取一个号段（1000,2000\]、（2000,3000\]、（3000,4000\]

![image.png](https://i.loli.net/2021/11/14/dpiqjIXMcuH6Dzk.png)
  
`Tinyid`提供`http`和`tinyid-client`两种方式接入

##### Http方式接入

（1）导入Tinyid源码：

git clone https://github.com/didi/tinyid.git

（2）创建数据表：

```
CREATE TABLE `tiny_id_info` (  
	`id` bigint(20) unsigned NOT NULL AUTO_INCREMENT COMMENT '自增主键',  
    `biz_type` varchar(63) NOT NULL DEFAULT '' COMMENT '业务类型，唯一',  
    `begin_id` bigint(20) NOT NULL DEFAULT '0' COMMENT '开始id，仅记录初始值，无其他含义。初始化时begin_id和max_id应相同',  
    `max_id` bigint(20) NOT NULL DEFAULT '0' COMMENT '当前最大id',  
    `step` int(11) DEFAULT '0' COMMENT '步长',  
    `delta` int(11) NOT NULL DEFAULT '1' COMMENT '每次id增量',  
    `remainder` int(11) NOT NULL DEFAULT '0' COMMENT '余数',  
    `create_time` timestamp NOT NULL DEFAULT '2010-01-01 00:00:00' COMMENT '创建时间',  
    `update_time` timestamp NOT NULL DEFAULT '2010-01-01 00:00:00' COMMENT '更新时间',  
    `version` bigint(20) NOT NULL DEFAULT '0' COMMENT '版本号',  
    PRIMARY KEY (`id`),  
    UNIQUE KEY `uniq_biz_type` (`biz_type`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8 COMMENT 'id信息表';
    
CREATE TABLE `tiny_id_token` (  
	`id` int(11) unsigned NOT NULL AUTO_INCREMENT COMMENT '自增id',  
    `token` varchar(255) NOT NULL DEFAULT '' COMMENT 'token',  
    `biz_type` varchar(63) NOT NULL DEFAULT '' COMMENT '此token可访问的业务类型标识',  
    `remark` varchar(255) NOT NULL DEFAULT '' COMMENT '备注',  
    `create_time` timestamp NOT NULL DEFAULT '2010-01-01 00:00:00' COMMENT '创建时间',  
    `update_time` timestamp NOT NULL DEFAULT '2010-01-01 00:00:00' COMMENT '更新时间',  
    PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8 COMMENT 'token信息表';

INSERT INTO `tiny_id_info` (`id`, `biz_type`, `begin_id`, `max_id`, `step`, `delta`, `remainder`, `create_time`, `update_time`, `version`)
VALUES    
	(1, 'test', 1, 1, 100000, 1, 0, '2018-07-21 23:52:58', '2018-07-22 23:19:27', 1);
    
INSERT INTO `tiny_id_info` (`id`, `biz_type`, `begin_id`, `max_id`, `step`, `delta`, `remainder`, `create_time`, `update_time`, `version`)VALUES    (2, 'test_odd', 1, 1, 100000, 2, 1, '2018-07-21 23:52:58', '2018-07-23 00:39:24', 3);
 
INSERT INTO `tiny_id_token` (`id`, `token`, `biz_type`, `remark`, `create_time`, `update_time`)VALUES    (1, '0f673adf80504e2eaa552f5d791b644c', 'test', '1', '2017-12-14 16:36:46', '2017-12-14 16:36:48');INSERT INTO `tiny_id_token` (`id`, `token`, `biz_type`, `remark`, `create_time`, `update_time`)VALUES    (2, '0f673adf80504e2eaa552f5d791b644c', 'test_odd', '1', '2017-12-14 16:36:46', '2017-12-14 16:36:48');
```

（3）配置数据库：

```
datasource.tinyid.names=primary
datasource.tinyid.primary.driver-class-name=com.mysql.jdbc.Driver
datasource.tinyid.primary.url=jdbc:mysql://ip:port/databaseName?autoReconnect=true&useUnicode=true&characterEncoding=UTF-8
datasource.tinyid.primary.username=root
datasource.tinyid.primary.password=123456
```

（4）启动`tinyid-server`后测试

```
获取分布式自增ID: http://localhost:9999/tinyid/id/nextIdSimple?bizType=test&token=0f673adf80504e2eaa552f5d791b644c'
返回结果: 3

批量获取分布式自增ID:http://localhost:9999/tinyid/id/nextIdSimple?bizType=test&token=0f673adf80504e2eaa552f5d791b644c&batchSize=10'
返回结果:  4,5,6,7,8,9,10,11,12,13
```

##### Java客户端方式接入

重复Http方式的（2）（3）操作

引入依赖

```
<dependency>            
	<groupId>com.xiaoju.uemc.tinyid</groupId>            
    <artifactId>tinyid-client</artifactId>            
    <version>${tinyid.version}</version>        
</dependency>
```

配置文件

```
tinyid.server =localhost:9999
tinyid.token =0f673adf80504e2eaa552f5d791b644c
```

`test` 、`tinyid.token`是在数据库表中预先插入的数据，`test` 是具体业务类型，`tinyid.token`表示可访问的业务类型

```
// 获取单个分布式自增ID
Long id =  TinyId . nextId( " test " );

// 按需批量分布式自增ID
List< Long > ids =  TinyId . nextId( " test " , 10 );
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说一下你对volatile的理解？`volatile` 这个关键字可能很多朋友都听说过，或许也都用过。在 `Java 5` 之前，它是一个备受争议的关键字，因为在程序中使用它往往会导致出人意料的结果。在 `Java 5` 之后，`volatile` 关键字才得以重获生机。

## 一.内存模型的相关概念

大家都知道，计算机在执行程序时，每条指令都是在 CPU 中执行的，而执行指令过程中，势必涉及到数据的读取和写入。由于程序运行过程中的临时数据是存放在主存（物理内存）当中的，这时就存在一个问题，由于 CPU 执行速度很快，而从内存读取数据和向内存写入数据的过程跟 CPU 执行指令的速度比起来要慢的多，因此如果任何时候对数据的操作都要通过和内存的交互来进行，会大大降低指令执行的速度。因此在 CPU 里面就有了高速缓存。

也就是，当程序在运行过程中，会将运算需要的数据从主存复制一份到 CPU 的高速缓存当中，那么 CPU 进行计算时就可以直接从它的高速缓存读取数据和向其中写入数据，当运算结束之后，再将高速缓存中的数据刷新到主存当中。举个简单的例子，比如下面的这段代码：

```java
i = i + 1;
```

当线程执行这个语句时，会先从主存当中读取 i 的值，然后复制一份到高速缓存当中，然后 CPU 执行指令对 i 进行加 1 操作，然后将数据写入高速缓存，最后将高速缓存中 i 最新的值刷新到主存当中。

这个代码在单线程中运行是没有任何问题的，但是在多线程中运行就会有问题了。在多核 CPU 中，每条线程可能运行于不同的 CPU 中，因此每个线程运行时有自己的高速缓存（对单核 CPU 来说，其实也会出现这种问题，只不过是以线程调度的形式来分别执行的）。本文我们以多核 CPU 为例。

比如同时有 2 个线程执行这段代码，假如初始时 i 的值为 0，那么我们希望两个线程执行完之后 i 的值变为 2。但是事实会是这样吗？

可能存在下面一种情况：初始时，两个线程分别读取 i 的值存入各自所在的 CPU 的高速缓存当中，然后线程 1 进行加 1 操作，然后把 i 的最新值 1 写入到内存。此时线程 2 的高速缓存当中 i 的值还是 0，进行加 1 操作之后，i 的值为 1，然后线程 2 把 i 的值写入内存。

最终结果 i 的值是 1，而不是 2。这就是著名的缓存一致性问题。通常称这种被多个线程访问的变量为共享变量。

也就是说，如果一个变量在多个 CPU 中都存在缓存（一般在多线程编程时才会出现），那么就可能存在缓存不一致的问题。

为了解决缓存不一致性问题，通常来说有以下 2 种解决方法：

1）通过在总线加 LOCK#锁的方式

2）通过缓存一致性协议

这 2 种方式都是硬件层面上提供的方式。

在早期的 CPU 当中，是通过在总线上加 LOCK#锁 的形式来解决缓存不一致的问题。因为 CPU 和其他部件进行通信都是通过总线来进行的，如果对总线加 LOCK#锁 的话，也就是说阻塞了其他 CPU 对其他部件访问（如内存），从而使得只能有一个 CPU 能使用这个变量的内存。比如上面例子中 如果一个线程在执行 `i = i +1`，如果在执行这段代码的过程中，在总线上发出了 LCOK#锁的信号，那么只有等待这段代码完全执行完毕之后，其他 CPU 才能从变量 i 所在的内存读取变量，然后进行相应的操作。这样就解决了缓存不一致的问题。

但是上面的方式会有一个问题，由于在锁住总线期间，其他 CPU 无法访问内存，导致效率低下。

所以就出现了缓存一致性协议。最出名的就是 Intel 的 MESI 协议，MESI 协议保证了每个缓存中使用的共享变量的副本是一致的。它核心的思想是：当 CPU 写数据时，如果发现操作的变量是共享变量，即在其他 CPU 中也存在该变量的副本，会发出信号通知其他 CPU 将该变量的缓存行置为无效状态，因此当其他 CPU 需要读取这个变量时，发现自己缓存中缓存该变量的缓存行是无效的，那么它就会从内存重新读取。

![image.png](https://i.loli.net/2021/11/14/7DYctpR2aikSHXE.png)

## 二.并发编程中的三个概念

在并发编程中，我们通常会遇到以下三个问题：原子性问题，可见性问题，有序性问题。我们先看具体看一下这三个概念：

### 原子性

原子性：即一个操作或者多个操作，要么全部执行并且执行的过程不会被任何因素打断，要么就都不执行。

一个很经典的例子就是银行账户转账问题：

比如从账户 A 向账户 B 转 1000 元，那么必然包括 2 个操作：从账户 A 减去 1000 元，往账户 B 加上 1000 元。

试想一下，如果这 2 个操作不具备原子性，会造成什么样的后果。假如从账户 A 减去 1000 元之后，操作突然中止。然后又从 B 取出了 500 元，取出 500 元之后，再执行 往账户 B 加上 1000 元 的操作。这样就会导致账户 A 虽然减去了 1000 元，但是账户 B 没有收到这个转过来的 1000 元。

所以这 2 个操作必须要具备原子性才能保证不出现一些意外的问题。

同样地反映到并发编程中会出现什么结果呢？

举个最简单的例子，大家想一下假如为一个 32 位的变量赋值过程不具备原子性的话，会发生什么后果？

```java
    i = 9;
```

假若一个线程执行到这个语句时，我暂且假设为一个 32 位的变量赋值包括两个过程：为低 16 位赋值，为高 16 位赋值。

那么就可能发生一种情况：当将低 16 位数值写入之后，突然被中断，而此时又有一个线程去读取 i 的值，那么读取到的就是错误的数据。

### 可见性

可见性是指当多个线程访问同一个变量时，一个线程修改了这个变量的值，其他线程能够立即看得到修改的值。

举个简单的例子，看下面这段代码：

```java
//线程1执行的代码
int i = 0;
i = 10; 

//线程2执行的代码
j = i;
```

假若执行线程 1 的是 CPU1，执行线程 2 的是 CPU2。由上面的分析可知，当线程 1 执行 i =10 这句时，会先把 i 的初始值加载到 CPU1 的高速缓存中，然后赋值为 10，那么在 CPU1 的高速缓存当中 i 的值变为 10 了，却没有立即写入到主存当中。

此时线程 2 执行 j = i，它会先去主存读取 i 的值并加载到 CPU2 的缓存当中，注意此时内存当中 i 的值还是 0，那么就会使得 j 的值为 0，而不是 10.

这就是可见性问题，线程 1 对变量 i 修改了之后，线程 2 没有立即看到线程 1 修改的值。

### 有序性

有序性：即程序执行的顺序按照代码的先后顺序执行。举个简单的例子，看下面这段代码：

```java
int i = 0;               
boolean flag = false;
i = 1;                //语句1   
flag = true;          //语句2
```

上面代码定义了一个 int 型变量，定义了一个 boolean 类型变量，然后分别对两个变量进行赋值操作。从代码顺序上看，语句 1 是在语句 2 前面的，那么 JVM 在真正执行这段代码的时候会保证语句 1 一定会在语句 2 前面执行吗？不一定，为什么呢？这里可能会发生指令重排序（Instruction Reorder）。

下面解释一下什么是指令重排序，一般来说，处理器为了提高程序运行效率，可能会对输入代码进行优化，它不保证程序中各个语句的执行先后顺序同代码中的顺序一致，但是它会保证程序最终执行结果和代码顺序执行的结果是一致的。

比如上面的代码中，语句 1 和语句 2 谁先执行对最终的程序结果并没有影响，那么就有可能在执行过程中，语句 2 先执行而语句 1 后执行。

但是要注意，虽然处理器会对指令进行重排序，但是它会保证程序最终结果会和代码顺序执行结果相同，那么它靠什么保证的呢？再看下面一个例子：

```java
int a = 10;    //语句1
int r = 2;    //语句2
a = a + 3;    //语句3
r = a*a;	 //语句4
```

这段代码有 4 个语句，那么可能的一个执行顺序是：

![image.png](https://i.loli.net/2021/11/14/4onhBSUlwjV67Qt.png)

那么可不可能是这个执行顺序呢： 语句 2   语句 1    语句 4   语句 3

不可能，因为处理器在进行重排序时是会考虑指令之间的数据依赖性，如果一个指令 Instruction 2 必须用到 Instruction 1 的结果，那么处理器会保证 Instruction 1 会在 Instruction 2 之前执行。

虽然重排序不会影响单个线程内程序执行的结果，但是多线程呢？下面看一个例子：

```java
//线程1:
context = loadContext();   //语句1
inited = true;             //语句2 

//线程2:
while(!inited ){  
	sleep() 
}

doSomethingwithconfig(context);
```

上面代码中，由于语句 1 和语句 2 没有数据依赖性，因此可能会被重排序。假如发生了重排序，在线程 1 执行过程中先执行语句 2，而此是线程 2 会以为初始化工作已经完成，那么就会跳出 while 循环，去执行 doSomethingwithconfig(context)方法，而此时 context 并没有被初始化，就会导致程序出错。

从上面可以看出，指令重排序不会影响单个线程的执行，但是会影响到线程并发执行的正确性。

也就是说，要想并发程序正确地执行，必须要保证原子性、可见性以及有序性。只要有一个没有被保证，就有可能会导致程序运行不正确。

## 三.Java 内存模型

在前面谈到了一些关于内存模型以及并发编程中可能会出现的一些问题。下面我们来看一下 Java 内存模型，研究一下 Java 内存模型为我们提供了哪些保证以及在 java 中提供了哪些方法和机制来让我们在进行多线程编程时能够保证程序执行的正确性。

在 Java 虚拟机规范中试图定义一种 Java 内存模型（Java Memory Model，JMM）来屏蔽各个硬件平台和操作系统的内存访问差异，以实现让 Java 程序在各种平台下都能达到一致的内存访问效果。那么 Java 内存模型规定了哪些东西呢，它定义了程序中变量的访问规则，往大一点说是定义了程序执行的次序。注意，为了获得较好的执行性能，Java 内存模型并没有限制执行引擎使用处理器的寄存器或者高速缓存来提升指令执行速度，也没有限制编译器对指令进行重排序。也就是说，在 java 内存模型中，也会存在缓存一致性问题和指令重排序的问题。

Java 内存模型规定所有的变量都是存在主存当中（类似于前面说的物理内存），每个线程都有自己的工作内存（类似于前面的高速缓存）。线程对变量的所有操作都必须在工作内存中进行，而不能直接对主存进行操作。并且每个线程不能访问其他线程的工作内存。

举个简单的例子：在 java 中，执行下面这个语句：

```java
i  = 10;
```

执行线程必须先在自己的工作线程中对变量 i 所在的缓存行进行赋值操作，然后再写入主存当中。而不是直接将数值 10 写入主存当中。

那么 Java 语言 本身对 原子性、可见性以及有序性提供了哪些保证呢？

### 原子性

在 Java 中，对基本数据类型的变量的读取和赋值操作是原子性操作，即这些操作是不可被中断的，要么执行，要么不执行。

上面一句话虽然看起来简单，但是理解起来并不是那么容易。看下面一个例子 i：

请分析以下哪些操作是原子性操作：

```java
x = 10;         //语句1
y = x;         //语句2
x++;           //语句3
x = x + 1;     //语句4
```

咋一看，有些朋友可能会说上面的 4 个语句中的操作都是原子性操作。其实只有语句 1 是原子性操作，其他三个语句都不是原子性操作。

语句 1 是直接将数值 10 赋值给 x，也就是说线程执行这个语句的会直接将数值 10 写入到工作内存中。

语句 2 实际上包含 2 个操作，它先要去读取 x 的值，再将 x 的值写入工作内存，虽然读取 x 的值以及 将 x 的值写入工作内存 这 2 个操作都是原子性操作，但是合起来就不是原子性操作了。

同样的，x++和 x = x+1 包括 3 个操作：读取 x 的值，进行加 1 操作，写入新的值。

所以上面 4 个语句只有语句 1 的操作具备原子性。

也就是说，只有简单的读取、赋值（而且必须是将数字赋值给某个变量，变量之间的相互赋值不是原子操作）才是原子操作。

不过这里有一点需要注意：在 32 位平台下，对 64 位数据的读取和赋值是需要通过两个操作来完成的，不能保证其原子性。但是好像在最新的 JDK 中，JVM 已经保证对 64 位数据的读取和赋值也是原子性操作了。

从上面可以看出，Java 内存模型只保证了基本读取和赋值是原子性操作，如果要实现更大范围操作的原子性，可以通过 synchronized 和 Lock 来实现。由于 synchronized 和 Lock 能够保证任一时刻只有一个线程执行该代码块，那么自然就不存在原子性问题了，从而保证了原子性。

### 可见性

对于可见性，Java 提供了 volatile 关键字来保证可见性。

当一个共享变量被 volatile 修饰时，它会保证修改的值会立即被更新到主存，当有其他线程需要读取时，它会去内存中读取新值。

而普通的共享变量不能保证可见性，因为普通共享变量被修改之后，什么时候被写入主存是不确定的，当其他线程去读取时，此时内存中可能还是原来的旧值，因此无法保证可见性。

另外，通过 synchronized 和 Lock 也能够保证可见性，synchronized 和 Lock 能保证同一时刻只有一个线程获取锁然后执行同步代码，并且在释放锁之前会将对变量的修改刷新到主存当中。因此可以保证可见性。

### 有序性

在 Java 内存模型中，允许编译器和处理器对指令进行重排序，但是重排序过程不会影响到单线程程序的执行，却会影响到多线程并发执行的正确性。

在 Java 里面，可以通过 volatile 关键字来保证一定的“有序性”（具体原理在下一节讲述）。另外可以通过 synchronized 和 Lock 来保证有序性，很显然，synchronized 和 Lock 保证每个时刻是有一个线程执行同步代码，相当于是让线程顺序执行同步代码，自然就保证了有序性。

另外，Java 内存模型具备一些先天的“有序性”，即不需要通过任何手段就能够得到保证的有序性，这个通常也称为 happens-before 原则。如果两个操作的执行次序无法从 happens-before 原则推导出来，那么它们就不能保证它们的有序性，虚拟机可以随意地对它们进行重排序。

下面就来具体介绍下 happens-before 原则（先行发生原则）：

- 程序次序规则：一个线程内，按照代码顺序，书写在前面的操作先行发生于书写在后面的操作
- 锁定规则：一个 unLock 操作先行发生于后面对同一个锁额 lock 操作
- volatile 变量规则：对一个变量的写操作先行发生于后面对这个变量的读操作
- 传递规则：如果操作 A 先行发生于操作 B，而操作 B 又先行发生于操作 C，则可以得出操作 A 先行发生于操作 C
- 线程启动规则：Thread 对象的 start()方法先行发生于此线程的每个一个动作
- 线程中断规则：对线程 interrupt()方法的调用先行发生于被中断线程的代码检测到中断事件的发生
- 线程终结规则：线程中所有的操作都先行发生于线程的终止检测，我们可以通过 Thread.join()方法结束、Thread.isAlive()的返回值手段检测到线程已经终止执行
- 对象终结规则：一个对象的初始化完成先行发生于他的 finalize()方法的开始

这 8 条原则摘自《深入理解 Java 虚拟机》。

这 8 条规则中，前 4 条规则是比较重要的，后 4 条规则都是显而易见的。

下面我们来解释一下前 4 条规则：

对于程序次序规则来说，我的理解就是一段程序代码的执行在单个线程中看起来是有序的。注意，虽然这条规则中提到“书写在前面的操作先行发生于书写在后面的操作”，这个应该是程序看起来执行的顺序是按照代码顺序执行的，因为虚拟机可能会对程序代码进行指令重排序。虽然进行重排序，但是最终执行的结果是与程序顺序执行的结果一致的，它只会对不存在数据依赖性的指令进行重排序。因此，在单个线程中，程序执行看起来是有序执行的，这一点要注意理解。事实上，这个规则是用来保证程序在单线程中执行结果的正确性，但无法保证程序在多线程中执行的正确性。

第二条规则也比较容易理解，也就是说无论在单线程中还是多线程中，同一个锁如果出于被锁定的状态，那么必须先对锁进行了释放操作，后面才能继续进行 lock 操作。

第三条规则是一条比较重要的规则，也是后文将要重点讲述的内容。直观地解释就是，如果一个线程先去写一个变量，然后一个线程去进行读取，那么写入操作肯定会先行发生于读操作。

第四条规则实际上就是体现 happens-before 原则具备传递性。

## 四.深入剖析 volatile 关键字

在前面讲述了很多东西，其实都是为讲述 volatile 关键字作铺垫，那么接下来我们就进入主题。

### volatile 关键字的两层语义

一旦一个共享变量（类的成员变量、类的静态成员变量）被 volatile 修饰之后，那么就具备了两层语义：

1）保证了不同线程对这个变量进行操作时的可见性，即一个线程修改了某个变量的值，这新值对其他线程来说是立即可见的。

2）禁止进行指令重排序。

先看一段代码，假如线程 1 先执行，线程 2 后执行：

```java
//线程1
boolean stop = false;
while(!stop){	
	doSomething();
} 

//线程2
stop = true;
```

这段代码是很典型的一段代码，很多人在中断线程时可能都会采用这种标记办法。但是事实上，这段代码会完全运行正确么？即一定会将线程中断么？不一定，也许在大多数时候，这个代码能够把线程中断，但是也有可能会导致无法中断线程（虽然这个可能性很小，但是只要一旦发生这种情况就会造成死循环了）。

下面解释一下这段代码为何有可能导致无法中断线程。在前面已经解释过，每个线程在运行过程中都有自己的工作内存，那么线程 1 在运行的时候，会将 stop 变量的值拷贝一份放在自己的工作内存当中。

那么当线程 2 更改了 stop 变量的值之后，但是还没来得及写入主存当中，线程 2 转去做其他事情了，那么线程 1 由于不知道线程 2 对 stop 变量的更改，因此还会一直循环下去。

但是用 volatile 修饰之后就变得不一样了：

第一：使用 volatile 关键字会强制将修改的值立即写入主存；

第二：使用 volatile 关键字的话，当线程 2 进行修改时，会导致线程 1 的工作内存中缓存变量 stop 的缓存行无效（反映到硬件层的话，就是 CPU 的 L1 或者 L2 缓存中对应的缓存行无效）；

第三：由于线程 1 的工作内存中缓存变量 stop 的缓存行无效，所以线程 1 再次读取变量 stop 的值时会去主存读取。

那么在线程 2 修改 stop 值时（当然这里包括 2 个操作，修改线程 2 工作内存中的值，然后将修改后的值写入内存），会使得线程 1 的工作内存中缓存变量 stop 的缓存行无效，然后线程 1 读取时，发现自己的缓存行无效，它会等待缓存行对应的主存地址被更新之后，然后去对应的主存读取最新的值。

那么线程 1 读取到的就是最新的正确的值。

### volatile 保证原子性吗？

从上面知道 volatile 关键字保证了操作的可见性，但是 volatile 能保证对变量的操作是原子性吗？

下面看一个例子：

```java
public class Test {
	public volatile int inc = 0;		
    
    public void increase() {		
    	inc++;	
    }		
    public static void main(String[] args) {		
    	final Test test = new Test();		
        for(int i=0;i<10;i++){			
        	new Thread(){				
            	public void run() {					
                	for(int j=0;j<1000;j++)						
                    	test.increase();				
                };			
            }.start();		    
        }				
        while(Thread.activeCount()>1)  //保证前面的线程都执行完			
        	Thread.yield();		
        System.out.println(test.inc);	
    }
}
```

大家想一下这段程序的输出结果是多少？也许有些朋友认为是 10000。但是事实上运行它会发现每次运行结果都不一致，都是一个小于 10000 的数字。

可能有的朋友就会有疑问，不对啊，上面是对变量 inc 进行自增操作，由于 volatile 保证了可见性，那么在每个线程中对 inc 自增完之后，在其他线程中都能看到修改后的值啊，所以有 10 个线程分别进行了 1000 次操作，那么最终 inc 的值应该是 1000 * 10=10000。

这里面就有一个误区了，volatile 关键字能保证可见性没有错，但是上面的程序错在没能保证原子性。可见性只能保证每次读取的是最新的值，但是 volatile 没办法保证对变量的操作的原子性。

在前面已经提到过，自增操作是不具备原子性的，它包括读取变量的原始值、进行加 1 操作、写入工作内存。那么就是说自增操作的三个子操作可能会分割开执行，就有可能导致下面这种情况出现：

假如某个时刻变量 inc 的值为 10，

线程 1 对变量进行自增操作，线程 1 先读取了变量 inc 的原始值，然后线程 1 被阻塞了；

然后线程 2 对变量进行自增操作，线程 2 也去读取变量 inc 的原始值，由于线程 1 只是对变量 inc 进行读取操作，而没有对变量进行修改操作，所以不会导致线程 2 的工作内存中缓存变量 inc 的缓存行无效，所以线程 2 会直接去主存读取 inc 的值，发现 inc 的值时 10，然后进行加 1 操作，并把 11 写入工作内存，最后写入主存。

然后线程 1 接着进行加 1 操作，由于已经读取了 inc 的值，注意此时在线程 1 的工作内存中 inc 的值仍然为 10，所以线程 1 对 inc 进行加 1 操作后 inc 的值为 11，然后将 11 写入工作内存，最后写入主存。

那么两个线程分别进行了一次自增操作后，inc 只增加了 1。

解释到这里，可能有朋友会有疑问，不对啊，前面不是保证一个变量在修改 volatile 变量时，会让缓存行无效吗？然后其他线程去读就会读到新的值，对，这个没错。这个就是上面的 happens-before 规则中的 volatile 变量规则，但是要注意，线程 1 对变量进行读取操作之后，被阻塞了的话，并没有对 inc 值进行修改。然后虽然 volatile 能保证线程 2 对变量 inc 的值读取是从内存中读取的，但是线程 1 没有进行修改，所以线程 2 根本就不会看到修改的值。

根源就在这里，自增操作不是原子性操作，而且 volatile 也无法保证对变量的任何操作都是原子性的。

在 java 1.5 的 `java.util.concurrent.atomic` 包下提供了一些原子操作类，即对基本数据类型的 自增（加 1 操作），自减（减 1 操作）、以及加法操作（加一个数），减法操作（减一个数）进行了封装，保证这些操作是原子性操作。atomic 是利用 CAS 来实现原子性操作的（Compare And Swap），CAS 实际上是利用处理器提供的 CMPXCHG 指令实现的，而处理器执行 CMPXCHG 指令是一个原子性操作。

### volatile 能保证有序性吗？

在前面提到 volatile 关键字能禁止指令重排序，所以 volatile 能在一定程度上保证有序性。

volatile 关键字禁止指令重排序有两层意思：

1）当程序执行到 volatile 变量的读操作或者写操作时，在其前面的操作的更改肯定全部已经进行，且结果已经对后面的操作可见；在其后面的操作肯定还没有进行；

2）在进行指令优化时，不能将在对 volatile 变量访问的语句放在其后面执行，也不能把 volatile 变量后面的语句放到其前面执行。

可能上面说的比较绕，举个简单的例子：

```java
//x、y为非volatile变量
//flag为volatile变量 

x = 2;        //语句1
y = 0;        //语句2
flag = true;  //语句3
x = 4;        //语句4
y = -1;       //语句5
```

由于 flag 变量为 volatile 变量，那么在进行指令重排序的过程的时候，不会将语句 3 放到语句 1、语句 2 前面，也不会讲语句 3 放到语句 4、语句 5 后面。但是要注意语句 1 和语句 2 的顺序、语句 4 和语句 5 的顺序是不作任何保证的。

并且 volatile 关键字能保证，执行到语句 3 时，语句 1 和语句 2 必定是执行完毕了的，且语句 1 和语句 2 的执行结果对语句 3、语句 4、语句 5 是可见的。

那么我们回到前面举的一个例子：

```java
//线程1:
context = loadContext();   //语句1
inited = true;             //语句2 

//线程2:
while(!inited ){  
	sleep() 
}
doSomethingwithconfig(context);
```

前面举这个例子的时候，提到有可能语句 2 会在语句 1 之前执行，那么久可能导致 context 还没被初始化，而线程 2 中就使用未初始化的 context 去进行操作，导致程序出错。

这里如果用 volatile 关键字对 inited 变量进行修饰，就不会出现这种问题了，因为当执行到语句 2 时，必定能保证 context 已经初始化完毕。

### volatile 的原理和实现机制

前面讲述了源于 volatile 关键字的一些使用，下面我们来探讨一下 volatile 到底如何保证可见性和禁止指令重排序的。

下面这段话摘自《深入理解 Java 虚拟机》：

“观察加入 volatile 关键字和没有加入 volatile 关键字时所生成的汇编代码发现，加入 volatile 关键字时，会多出一个 lock 前缀指令”

lock 前缀指令实际上相当于一个内存屏障（也成内存栅栏），内存屏障会提供 3 个功能：

1）它确保指令重排序时不会把其后面的指令排到内存屏障之前的位置，也不会把前面的指令排到内存屏障的后面；即在执行到内存屏障这句指令时，在它前面的操作已经全部完成；

2）它会强制将对缓存的修改操作立即写入主存；

3）如果是写操作，它会导致其他 CPU 中对应的缓存行无效。

## 五.使用 volatile 关键字的场景

synchronized 关键字是防止多个线程同时执行一段代码，那么就会很影响程序执行效率，而 volatile 关键字在某些情况下性能要优于 synchronized，但是要注意 volatile 关键字是无法替代 synchronized 关键字的，因为 volatile 关键字无法保证操作的原子性。通常来说，使用 volatile 必须具备以下 2 个条件：

1）对变量的写操作不依赖于当前值

2）该变量没有包含在具有其他变量的不变式中

实际上，这些条件表明，可以被写入 volatile 变量的这些有效值独立于任何程序的状态，包括变量的当前状态。

事实上，我的理解就是上面的 2 个条件需要保证操作是原子性操作，才能保证使用 volatile 关键字的程序在并发时能够正确执行。

下面列举几个 Java 中使用 volatile 的几个场景。

1.状态标记量

```java
volatile boolean flag = false; 

while(!flag){	
	doSomething();
} 

public void setFlag() {	
	flag = true;
}



volatile boolean inited = false;
//线程1:
context = loadContext();   
inited = true;              

//线程2:while(!inited ){
	sleep() 
}
doSomethingwithconfig(context);
```

2.double check

```java
class Singleton{	
	private volatile static Singleton instance = null;		
    
    private Singleton() {			
    
    }		
    
    public static Singleton getInstance() {		
    	if(instance==null) {			
        	synchronized (Singleton.class) {				
            	if(instance==null)					
                	instance = new Singleton();			
            }		
        }		
     	return instance;	
      	}
    }
}
```


*** 
## ⭐️⭐️⭐️⭐️⭐️
## Dubbo需要 Web 容器吗？
不需要，如果硬要用 Web 容器，只会增加复杂性，也浪费资源。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## dubbo都支持什么协议，推荐用哪种？
dubbo://（推荐）

rmi://

hessian://

http://

webservice://

thrift://

memcached://

redis://

rest://

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Dubbo 和 Dubbox 有什么区别？
Dubbox 是继 Dubbo 停止维护后，当当网基于 Dubbo 做的一个扩展项目，如加了服务可 Restful 调用，更新了开源组件等。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么要用Dubbo？
因为是阿里开源项目，国内很多互联网公司都在用，已经经过很多线上考验。内部使用了 Netty、Zookeeper，保证了高性能高可用性。

使用 Dubbo 可以将核心业务抽取出来，作为独立的服务，逐渐形成稳定的服务中心，可用于提高业务复用灵活扩展，使前端应用能更快速的响应多变的市场需求。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是孤儿卷及如何删除它？
孤儿卷是未与任何容器关联的卷。在 Docker v。1.9 之前的版本中，删除这些孤儿卷存在很大问题。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在 Windows 系统上可以运行原生的 Docker 容器吗？
在 'Windows Server 2016' 系统上， 你可以运行 Windows 的原生容器， 微软推出其映像是 'Windows Nano Server' ， 一个轻量级的运行在容器中的 Windows 原生系统。 您可以在其中布署基于 .NET 的应用。

译注： 结合 Docker 的基本技术原理，参考后面的 问题 26 和 问题 27， 可推测， 微软在系统内核上开发了对 Docker 的支持， 支持其闭源系统的容器化虚拟技术。但译者认为， Windows 系统本就是闭源紧耦合的系统， 好像你在本机上不装 .NET 组件，各应用能很好运行似的。何必再弄个容器，浪费资源。这只是译者自己之孔见，想喷就喷！ 另： Windows Server 2016 版本之后的都可支持这种原生 Docker 技术，如 Windows Server 2018 版。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 怎么停止一个运行中的线程？## 核心思想
使用interrupt()来通知，而不是强制。

## 代码演示

### 场景1：run()方法中没有sleep()/wait()等会响应中断的方法。

* 线程未处理中断：

```java
/**
 * 正确停止线程---run()方法内没有sleep()或者wait()方法-未处理中断信号
 *
 * @author futao
 * @date 2020/6/6
 */
public class StopThreadWithoutSleepWait implements Runnable {
 
    @Override
    public void run() {
        unHandleInterrupt();
    }
 
    /**
     * 未处理中断
     */
    public void unHandleInterrupt() {
        int num = 0;
        //打印最大整数一半的范围内10000的倍数
        while (num <= Integer.MAX_VALUE / 2) {
            if (num % 10000 == 0) {
                System.out.println(num + "是10000倍数");
            }
            ++num;
        }
        System.out.println("任务执行完毕");
    }
 
    public static void main(String[] args) throws InterruptedException {
        Thread thread = new Thread(new StopThreadWithoutSleepWait());
        //启动线程
        thread.start();
        //增加子线程处于运行状态的可能性
        Thread.sleep(500L);
        //尝试中断子线程
        thread.interrupt();
    }
}
```

**期望**：子线程在执行500毫秒之后停下来。

**结果**：线程并没有停下来。原因是：我们并未处理线程的中断信号。

* 对程序进行改进：响应中断。

在while循环条件中判断当前线程是否被中断(`Thread.currentThread().isInterrupted()`)，如果未被中断才继续执行，被中断则跳出while循环。

```java
/**
 * 正确停止线程---run()方法内没有sleep()或者wait()方法
 *
 * @author futao
 * @date 2020/6/6
 */
public class StopThreadWithoutSleepWait implements Runnable {
 
    @Override
    public void run() {
        handleInterrupt();
    }
 
    /**
     * 响应中断
     */
    public void handleInterrupt() {
        int num = 0;
        //加入线程未被中断的条件
        while (!Thread.currentThread().isInterrupted() && num <= Integer.MAX_VALUE / 2) {
            if (num % 10000 == 0) {
                System.out.println(num + "是10000倍数");
            }
            ++num;
        }
        System.out.println("任务执行完毕");
    }
 
    public static void main(String[] args) throws InterruptedException {
        Thread thread = new Thread(new StopThreadWithoutSleepWait());
        //启动线程
        thread.start();
        //增加子线程处于运行状态的可能性
        Thread.sleep(500L);
        //尝试中断子线程
        thread.interrupt();
    }
}
```

**期望**：线程在500毫秒之后响应中断，停下来。
**结果**：线程成功响应中断，提前结束。

总结可得出：线程调用者可以向线程发出中断请求，但是线程中断的权利控制在线程代码的编写者是否响应了你的中断请求。线程代码的编写者比调用者更加了解线程应不应该被停止，何时停止。

### 场景2：run()方法中存在sleep()/wait()等会响应中断的方法。(响应中断的方法会抛出InterruptedException)

* sleep()在while循环外

```java
/**
 * 中断线程-run()方法中有sleep()或者wait()方法
 *
 * @author futao
 * @date 2020/6/6
 */
public class StopThreadWithSleep {
    public static void main(String[] args) throws InterruptedException {
        Thread thread = new Thread(() -> {
            int num = 0;
            while (!Thread.currentThread().isInterrupted() && num <= 300) {
                if (num % 100 == 0) {
                    System.out.println(num + "是100的整数倍");
                }
                ++num;
            }
            try {
                //sleep()方法会响应中断，且响应中断的方式为抛出InterruptException异常--- sleep interrupted
                Thread.sleep(1000L);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("线程执行完毕");
        });
        //启动线程
        thread.start();
        //等待while循环执行完毕
        Thread.sleep(200L);
        //当线程处于sleep()状态时进行中断
        thread.interrupt();
    }
}
```

**预期**：程序执行完while循环之后，阻塞在sleep()方法，此时进行中断，sleep()方法响应该中断，抛出InterruptedException，打印异常堆栈。

**测试**：符合预期。

* 无法停止的线程：sleep()方法在while循环内。

你预期下面代码的执行结果是怎样的？

```java
/**
 * 3. 无法停止的线程
 *
 * @author futao
 * @date 2020/6/6
 */
public class CantStopThread {
 
    public static void main(String[] args) throws InterruptedException {
        Thread thread = new Thread(() -> {
            int num = 1;
            while (num <= 1000 && !Thread.currentThread().isInterrupted()) {
                if (num % 2 == 0) {
                    System.out.println(num + "是2的整数倍");
                }
                ++num;
                try {
                    Thread.sleep(1000L);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
            System.out.println("线程执行完毕");
        });
 
        //启动线程
        thread.start();
        //主线程休眠500毫秒
        Thread.sleep(500L);
        //中断线程
        thread.interrupt();
    }
}
```

**预期**：线程在第一次进入while循环时，进入休眠1000毫秒状态，在500毫秒时主线程向子线程发出中断信号，sleep()方法响应中断，打印异常堆栈，下次再进入while循环时，因为线程被设置成了中断状态，所以while中条件不成立，不应该继续执行。 但是实际上是这样吗？

**结果**：slee()响应了中断，打印了异常堆栈。但是线程并没有停下来，而是继续执行。就像什么都没有发生一样。

**原因**：sleep()在响应了中断之后，清除了线程的中断状态。那么while判断时不知道线程被中断了。

查看sleep()方法的描述：当InterruptedException异常被抛出后，线程的中断状态将被清除。

类似的会响应中断的方法还有那些？

```
响应中断的方法总结：
Object.wait()/wait(long)/wait(long,int)
Thread.sleep(long)/sleep(long,int)
Thread.join()/join(long)/join(long,int)
juc.BlockingQueue.take()/put(E)
juc.Lock.lockInterruptibly()
juc.CountDownLatch.await()
juc.CyclicBarrier.await()
juc.Exchanger.exchange(V)
jio.InterruptibleChannel相关方法
jio.Selector相关方法
```

那么，线程响应中断后应该怎么处理。

## 线程中断的最佳实践：

* 传递中断
* 不想或无法传递：恢复中断
* 核心思想：不应屏蔽中断

### 传递中断：在方法签名中将中断异常抛出，而不是生吞，交给调用者处理。

```java
/**
 * 正确停止线程的方式1-抛出中断
 * 优先在方法签名中抛出该异常
 *
 * @author futao
 * @date 2020/6/6
 */
public class RightWayToStopThread implements Runnable {
 
    @Override
    public void run() {
        while (true) {
            System.out.println("running...");
            try {
                throwInMethod();
            } catch (InterruptedException e) {
                e.printStackTrace();
                System.out.println("响应中断，跳出循环，停止线程");
                break;
            }
        }
    }
 
    /**
     * 业务方法应该将中断异常抛出，将异常传递给上层--传递中断
     *
     * @throws InterruptedException
     */
    private void throwInMethod() throws InterruptedException {
        System.out.println("业务执行中.....");
        Thread.sleep(2000L);
    }
 
    public static void main(String[] args) throws InterruptedException {
        Thread thread = new Thread(new RightWayToStopThread());
        thread.start();
        Thread.sleep(1000L);
        thread.interrupt();
    }
}
```

### 不想或无法传递时：应该恢复中断(`Thread.currentThread().interrupt()`)

```java
/**
 * 正确停止线程的方式2
 * 恢复中断
 *
 * @author futao
 * @date 2020/6/6
 */
public class RightWayToStopThreadReInterrupt implements Runnable {
    @Override
    public void run() {
        while (!Thread.currentThread().isInterrupted()) {
            System.out.println("running...");
            throwInMethod();
        }
        System.out.println("线程任务执行完毕");
    }
 
    private void throwInMethod() {
        try {
            Thread.sleep(2000L);
        } catch (InterruptedException e) {
            System.out.println("感知到中断请求。");
            System.out.println("重新设置中断信号");
            //尝试恢复中断
            Thread.currentThread().interrupt();
        }
    }
 
    public static void main(String[] args) throws InterruptedException {
        Thread thread = new Thread(new RightWayToStopThreadReInterrupt());
        thread.start();
        Thread.sleep(1000L);
        thread.interrupt();
    }
}
```

## 线程中断的相关方法

预期下面代码的执行结果？

```java
/**
 * 线程中断的相关方法
 *
 * @author futao
 * @date 2020/6/7
 */
public class InterruptMethod {
    public static void main(String[] args) {
        Thread thread = new Thread(() -> {
            System.out.println("线程任务执行中...");
            while (true) {
            }
        });
 
        //启动线程
        thread.start();
        System.out.println(thread.isInterrupted());
        //向线程发送中断信号
        thread.interrupt();
        System.out.println(thread.isInterrupted());
        System.out.println(thread.isInterrupted());
        System.out.println(Thread.interrupted());
        System.out.println(thread.isInterrupted());
        System.out.println(thread.interrupted());
        System.out.println(thread.isInterrupted());
    }
}
```

结果：

```
false
true
true
false
true
false
true
```

### 分析：

* 线程处于运行状态，且没有程序给线程发送中断信号。所以非中断状态。
* 调用了中断方法，所以线程状态状态为true。
* 由于thread.isInterrupted()并不会清除线程的中断状态，所以多次调用，返回的结果一样，依旧为已中断。
* Thread.interrupted()判断的是执行这行代码的线程的中断状态。这里是主线程，所以为未中断。且该方法调用之后，会将执行该方法的线程的中断状态清除。
* 因为Thread.interrupted()清除的是执行代码的线程的中断状态，所以不印象子线程的中断状态，所以子线程的中断状态仍然为true。
* 如果子线程对象直接调用静态方法interrupted()，返回的也是执行这段代码的线程的中断状态。此时为主线程，状态为未中断。
* 子线程对象直接调用静态方法interrupted()并不会清除调用对象的线程中断状态，而是清除执行这段代码的线程的中断状态。所以子线程的中断状态不影响。

为什么通过子线程对象来执行静态方法·static boolean interrupted()·清除的是执行者的中断状态呢?

查看源码发现，静态方法static boolean interrupted()会先获取到当前执行这段代码的线程，清除其中断状态，并返回中断状态。

### 总结:

* thread.interrupt() 给线程发送中断信号，设置线程thread的中断状态为true。
* thread.isInterrupted() 判断线程thread是否被中断。且不改变线程的中断状态
* Thread.interrupted()/thread.interrupted() 判断执行这行代码的线程的中断状态，并且清除其中断状态。
* private native boolean isInterrupted(boolean ClearInterrupted); native方法，真正判断线程中断状态和清除中断状态的代码。thread.isInterrupted()和Thread.interrupted()/thread.interrupted()最终调用的都是这个方法。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## InheritableThreadLocal原理知道吗？## 前言

复习下 ThreadLocal 的原理，因为会对 InheritableThreadLocal 的理解 有重大的帮助：

* 每个线程都有一个 ThreadLocalMap 类型的 threadLocals 属性。
* ThreadLocalMap 类相当于一个Map，key 是 ThreadLocal 本身，value 就是我们的值。
* 当我们通过 `threadLocal.set(new Integer(123));` ，我们就会在这个线程中的 threadLocals 属性中放入一个键值对，key 是 这个 `threadLocal.set(new Integer(123));` 的 threadlocal，value 就是值。
* 当我们通过 `threadlocal.get()` 方法的时候，首先会根据这个线程得到这个线程的 threadLocals 属性，然后由于这个属性放的是键值对，我们就可以根据键 threadlocal 拿到值。 注意，这时候这个键 threadlocal 和 我们 set 方法的时候的那个键 threadlocal 是一样的，所以我们能够拿到相同的值。

## InheritableThreadLocal 概念

从上面的介绍我们可以知道，我们其实是根据 Thread.currentThread()，拿到该线程的 threadlocals，从而进一步得到我们之前预先 set 好的值。那么如果我们新开一个线程，这个时候，由于 Thread.currentThread() 已经变了，从而导致获得的 threadlocals 不一样，我们之前并没有在这个新的线程的 threadlocals 中放入值，那么我就再通过 threadlocal.get()方法 是不可能拿到值的。例如如下代码：

```java
public class Test {
 
    public static ThreadLocal<Integer> threadLocal = new ThreadLocal<Integer>();
 
    public static void main(String args[]){
        threadLocal.set(new Integer(123));
 
        Thread thread = new MyThread();
        thread.start();
 
        System.out.println("main = " + threadLocal.get());
    }
 
    static class MyThread extends Thread{
        @Override
        public void run(){
            System.out.println("MyThread = " + threadLocal.get());
        }
    }
}
```

输出是：

```
main = 123
MyThread = null
```

那么这个时候怎么解决？ InheritableThreadLocal 就可以解决这个问题。 先看一个官方对它的介绍：

```
 * This class extends <tt>ThreadLocal</tt> to provide inheritance of values
 * from parent thread to child thread: when a child thread is created, the
 * child receives initial values for all inheritable thread-local variables
 * for which the parent has values.  Normally the child's values will be
 * identical to the parent's; however, the child's value can be made an
 * arbitrary function of the parent's by overriding the <tt>childValue</tt>
 * method in this class.
```

也就是说，我们把上面的

```java
public static ThreadLocal<Integer> threadLocal = new ThreadLocal<Integer>();
```

改成

```java
public static ThreadLocal<Integer> threadLocal = new InheritableThreadLocal<Integer>();

```

再运行，就会有结果：

```
main = 123
MyThread = 123
```

也就是子线程或者说新开的线程拿到了该值。那么，这个究竟是怎么实现的呢，key 都变了，为什么还可以拿到呢？

## InheritableThreadLocal 原理

我们可以首先可以浏览下 InheritableThreadLocal 类中有什么东西：

```java
public class InheritableThreadLocal<T> extends ThreadLocal<T> {
    protected T childValue(T parentValue) {
        return parentValue;
    }
    ThreadLocalMap getMap(Thread t) {
       return t.inheritableThreadLocals;
    }
    void createMap(Thread t, T firstValue) {
        t.inheritableThreadLocals = new ThreadLocalMap(this, firstValue);
    }
}
```

其实就是重写了3个方法。

首先，当我们调用 get 方法的时候，由于子类没有重写，所以我们调用了父类的 get 方法：

```java
public T get() {
    Thread t = Thread.currentThread();
    ThreadLocalMap map = getMap(t);
    if (map != null) {
        ThreadLocalMap.Entry e = map.getEntry(this);
        if (e != null) {
            @SuppressWarnings("unchecked")
            T result = (T)e.value;
            return result;
        }
    }
    return setInitialValue();
}
```

这里会有一个Thread.currentThread() ， getMap(t) 方法，所以就会得到这个线程 threadlocals。 但是，由于子类 InheritableThreadLocal 重写了 getMap()方法，再看上述代码，我们可以看到：

其实不是得到 threadlocals，而是得到 inheritableThreadLocals。 inheritableThreadLocals 之前一直没提及过，其实它也是 Thread 类的一个 ThreadLocalMap 类型的 属性，如下 Thread 类的部分代码：

```java
ThreadLocal.ThreadLocalMap threadLocals = null;
ThreadLocal.ThreadLocalMap inheritableThreadLocals = null;
```

那么，这里看 InheritableThreadLocal 重写的方法，感觉 inheritableThreadLocals 和 threadLocals 几乎是一模一样的作用，只是换了个名字而且，那么究竟 为什么在新的 线程中通过 threadlocal.get() 方法还能得到值呢？

这时候要注意 childValue 方法，我们可以看下它的官方说明：

```
 * Computes the child's initial value for this inheritable thread-local
 * variable as a function of the parent's value at the time the child
 * thread is created.  This method is called from within the parent
 * thread before the child is started.
 * 
```

这个时候，你明白了，是不是在 创建线程的时候做了手脚，做了一些值的传递，或者这里利用上了 inheritableThreadLocals 之类的。

其实，关键在于 `Thread thread = new MyThread();`

这不是一个简简单单的 new 操作。当我们 new 一个 线程的时候：

```java
public Thread() {
    init(null, null, "Thread-" + nextThreadNum(), 0);
}
```

然后：

```java
private void init(ThreadGroup g, Runnable target, String name,
                      long stackSize) {
    init(g, target, name, stackSize, null);
}
```

然后：
```java
private void init(ThreadGroup g, Runnable target, String name,
                      long stackSize, AccessControlContext acc) {
     ......
    if (parent.inheritableThreadLocals != null)
        this.inheritableThreadLocals =
            ThreadLocal.createInheritedMap(parent.inheritableThreadLocals);
        /* Stash the specified stack size in case the VM cares */
        this.stackSize = stackSize;
    ......
    }

```

这时候有一句`ThreadLocal.createInheritedMap(parent.inheritableThreadLocals);` ，然后

```java
static ThreadLocalMap createInheritedMap(ThreadLocalMap parentMap) {
    return new ThreadLocalMap(parentMap);
}
```

继续跟踪：

```java
private ThreadLocalMap(ThreadLocalMap parentMap) {
    Entry[] parentTable = parentMap.table;
    int len = parentTable.length;
    setThreshold(len);
    table = new Entry[len];
 
    for (int j = 0; j < len; j++) {
        Entry e = parentTable[j];
        if (e != null) {
            @SuppressWarnings("unchecked")
            ThreadLocal<Object> key = (ThreadLocal<Object>) e.get();
            if (key != null) {
                Object value = key.childValue(e.value);
                Entry c = new Entry(key, value);
                int h = key.threadLocalHashCode & (len - 1);
                while (table[h] != null)
                    h = nextIndex(h, len);
                    table[h] = c;
                    size++;
                }
            }
        }
    }
```

当我们创建一个新的线程的时候X，X线程就会有 ThreadLocalMap 类型的 inheritableThreadLocals ，因为它是 Thread 类的一个属性。

然后

先得到当前线程存储的这些值，例如 Entry[] parentTable = parentMap.table; 。再通过一个 for 循环，不断的把当前线程的这些值复制到我们新创建的线程X 的inheritableThreadLocals 中。就这样，就ok了。

那么这样会有一个什么结果呢？

结果就是我们创建的新线程X 的inheritableThreadLocals 变量中已经有了值了。那么我在新的线程X中调用threadlocal.get() 方法，首先会得到新线程X的inheritableThreadLocals，然后，再根据threadlocal.get()中的 threadlocal，就能够得到这个值。

这样就避免了 新线程中得到的 threadlocals 没有东西。之前就是因为没有东西，所以才拿不到值。

所以说 整个 InheritableThreadLocal 的实现原理就是这样的。

## 总结

首先要理解为什么在新线程中得不到值，是因为我们其实是根据 Thread.currentThread()，拿到该线程的 threadlocals，从而进一步得到我们之前预先 set 好的值。那么如果我们新开一个线程，这个时候，由于 Thread.currentThread() 已经变了，从而导致获得的 threadlocals 不一样，我们之前并没有在这个新的线程的 threadlocals 中放入值，那么我就再通过 threadlocal.get()方法是不可能拿到值的。

那么解决办法就是 我们在新线程中，要把父线程的 threadlocals 的值 给复制到 新线程中的 threadlocals 中来。这样，我们在新线程中得到的 threadlocals 才会有东西，再通过 threadlocal.get() 中的 threadlocal，就会得到值。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## ThreadLocal实现原理## 使用场景

ThreadLocal 适用于每个线程需要自己独立的实例且该实例需要在多个方法中被使用，也就是变量在线程间隔离，而在同一线程共享的场景。例如管理Connection，我们希望每个线程只使用一个Connection实例，这个时候用ThreadLocal就很合适。

```java
public class ThreadLocalDemo {
    private static final ThreadLocal<Object> threadLocal = new ThreadLocal<>();

    public static void main(String[] args) {
        threadLocal.set(new Object());
        someMethod();
    }

    static void someMethod() {
        // 获取在threadLocal中存储的对象
        threadLocal.get();
        
        // 清除ThreadLocal中数据
        threadLocal.remove();
    }
}
```

## 原理

在我们了解了如何使用之后，来看下 ThreadLocal 是如何实现的

* ThreadLocal.get()

我们从get方法来分析，可以看到方法中获取当前线程，并通过当前线程得到一个 ThreadLocalMap，我们可以暂时把这个ThreadLocalMap 理解为我们熟悉的HashMap，然后通过 this（当前ThreadLocal对象）作为key，从Map中获取Entry

![image.png](https://i.loli.net/2021/11/08/TxYDJV8IuthcijQ.png)

我们再来看下，ThreadLocalMap 以及ThreadLocalMap.Entry 中的核心成员变量，ThreadLocalMap 中实现了一个简单的hash表

![image.png](https://i.loli.net/2021/11/08/dpBLOaYy4Ek9g6c.png)

看到这里你可能还不是很清晰，结合下面这张图理解一下，每个线程（Thread对象）中有一个ThreadLocalMap，使线程之间的数据天然隔离，ThreadLocalMap 有一张hash表 Entry[]，每个 Entry 中对应存储着一个ThreadLocal实例 - value，这样使得不同的ThreadLocal 对象之间也形成了隔离

![image.png](https://i.loli.net/2021/11/08/J1jomd9OUIMCtwz.png)

* ThreadLocalMap 中的hash表

我们通过 ThreadLocalMap.set() 来了解下内部的hash表是如何实现的

![image.png](https://i.loli.net/2021/11/08/svi26tOeBlZMR7n.png)

线性探测是指当发生hash冲突时，利用固定的算法寻找一定步长的下个位置（ThreadLocal中发生hash冲突时，index+1），依次判断，直至找到能够存放的位置

> 如果线程中操作了大量的 ThreadLocal 对象，势必会造成hash冲突，这是没有必要的性能开销，如果可以的话，我们可以只保留一个ThreadLocal对象

## 关于 ThreadLocal 的一些思考

* 为什么要使用弱引用

图3中，我们看到hash表中会出现 key == null的Entry，这是因为 ThreadLocalMap.Entry 的key （Entry 对ThreadLocal设置了弱引用，可以回顾一下图2）

弱引用的对象拥有更短暂的生命周期。在GC时，一旦发现了对象只具有弱引用，这个对象一定被回收
这么做的原因：如果ThreadLocal 对象需要被回收时（此时并没有调用ThreadLocal.remove），线程中的ThreadLocalMap 一直强引用着 ThreadLocal对象，这会让 ThreadLocal对象 以及对应的value对象内存无法释放，导致内存泄漏。这算是ThreadLocal的一种容错机制，这样做使得了ThreadLocal对象得到了回收，但是value的内存并没有释放，所以ThreadLocalMap 的get、set方法中都会去尝试清理ThreadLocal已经被回收的entry。

* 使用过后不及时remove会怎么样

很多博客中都强调了，ThreadLocal.remove的重要性。举个例子，我们新启了一个线程在这个线程中使用了ThreadLocal，我们并没有调用remove，这会导致存储的value对象一直没有办法被回收，直到线程被销毁

* 线程池中也需要remove吗

以web线程池为例，如果每次都在过滤器中操作同一个ThreadLocal.set，然后业务代码中get，似乎没什么问题。计算出的hash值都是一样的，槽位也是一样的会覆盖上一次的值。确实业务不会有问题，但是还是推荐大家在使用完之后remove，因为这样会让无用的value对象早点被回收，在很多java源码中都会看到，对一些不再使用的对象进行如下的help GC操作

```java
object = null // help GC
```

所以我们也需要让无用的对象失去引用，帮助GC

* 综上所述

ThreadLocal 使用过后要及时remove，帮助JVM释放内存



*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何临时退出一个正在交互的容器的终端，而不终止它？
按Ctrl+p，后按Ctrl+q，如果按Ctrl+c会使容器内的应用进程终止，进而会使容器终止。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java线程池实现原理## 前言

线程是稀缺资源，如果被无限制的创建，不仅会消耗系统资源，还会降低系统的稳定性，合理的使用线程池对线程进行统一分配、调优和监控，有以下好处：

* 降低资源消耗。线程是操作系统十分宝贵的资源，当多个人同时开发一个项目时，在互不知情的情况下，都自己在代码中创建了线程，这样就会导致线程数过多，而且线程的创建和销毁，在操作系统层面，需要由用户态切换到内核态，这是一个费时费力的过程。而使用线程池可以避免频繁的创建线程和销毁线程，线程池中线程可以重复使用。
* 提高响应速度。当请求到达时，由于线程池中的线程已经创建好了，使用线程池，可以省去线程创建的这段时间。
* 提高线程的可管理性。线程是稀缺资源，当创建过多的线程时，会造成系统性能的下降，而使用线程池，可以对线程进行统一分配、调优和监控。

## 实现原理

在线程池中存在几个概念：`核心线程数`、`最大线程数`、`任务队列`。

* 核心线程数指的是线程池的基本大小；
* 最大线程数指的是，同一时刻线程池中线程的数量最大不能超过该值；
* 任务队列是当任务较多时，线程池中线程的数量已经达到了核心线程数，这时候就是用任务队列来存储我们提交的任务。

与其他池化技术不同的是，线程池是基于`生产者-消费者模式`来实现的，任务的提交方是生产者，线程池是消费者。当我们需要执行某个任务时，只需要把任务扔到线程池中即可。线程池中执行任务的流程如下图如下。

![image.png](https://i.loli.net/2021/11/08/vxTNEw4lkABLQiH.png)

* 先判断线程池中线程的数量是否超过核心线程数，如果没有超过核心线程数，就创建新的线程去执行任务；如果超过了核心线程数，就进入到下面流程。
* 判断任务队列是否已经满了，如果没有满，就将任务添加到任务队列中；如果已经满了，就进入到下面的流程。
* 再判断如果创建一个线程后，线程数是否会超过最大线程数，如果不会超过最大线程数，就创建一个新的线程来执行任务；如果会，则进入到下面的流程。
* 执行拒绝策略。

## ThreadPoolExecutor

在JUC包下，已经提供了线程池的具体的实现：ThreadPoolExecutor。ThreadPoolExecutor提供了很多的构造方法，其中最复杂的构造方法有7个参数。

```java
public ThreadPoolExecutor(int corePoolSize,
                          int maximumPoolSize,
                          long keepAliveTime,
                          TimeUnit unit,
                          BlockingQueue<Runnable> workQueue,
                          ThreadFactory threadFactory,
                          RejectedExecutionHandler handler) {
}
```

* `corePoolSize`：该参数表示的是线程池的核心线程数。当任务提交到线程池时，如果线程池的线程数量还没有达到corePoolSize，那么就会新创建的一个线程来执行任务，如果达到了，就将任务添加到任务队列中。
* `maximumPoolSize`：该参数表示的是线程池中允许存在的最大线程数量。当任务队列满了以后，再有新的任务进入到线程池时，会判断再新建一个线程是否会超过maximumPoolSize，如果会超过，则不创建线程，而是执行拒绝策略。如果不会超过maximumPoolSize，则会创建新的线程来执行任务。
* `keepAliveTime`：当线程池中的线程数量大于corePoolSize时，那么大于corePoolSize这部分的线程，如果没有任务去处理，那么就表示它们是空闲的，这个时候是不允许它们一直存在的，而是允许它们最多空闲一段时间，这段时间就是keepAliveTime，时间的单位就是TimeUnit。
* `unit`：空闲线程允许存活时间的单位，TimeUnit是一个枚举值，它可以是纳秒、微妙、毫秒、秒、分、小时、天。
* `workQueue`：任务队列，用来存放任务。该队列的类型是阻塞队列，常用的阻塞队列有ArrayBlockingQueue、LinkedBlockingQueue、SynchronousQueue、PriorityBlockingQueue等。
* `ArrayBlockingQueue`是一个基于数组实现的阻塞队列，元素按照先进先出（FIFO）的顺序入队、出队。因为底层实现是数组，数组在初始化时必须指定大小，因此ArrayBlockingQueue是有界队列。
* `LinkedBlockingQueue`是一个基于链表实现的阻塞队列，元素按照先进先出（FIFO）的顺序入队、出队。因为顶层是链表，链表是基于节点之间的指针指向来维持前后关系的，如果不指链表的大小，它默认的大小是Integer.MAX_VALUE，即，这个数值太大了，因此通常称LinkedBlockingQueue是一个无界队列。当然如果在初始化的时候，就指定链表大小，那么它就是有界队列了。
* `SynchronousQueue`是一个不存储元素的阻塞队列。每个插入操作必须得等到另一个线程调用了移除操作后，该线程才会返回，否则将一直阻塞。吞吐量通常要高于LinkedBlockingQueue。
* `PriorityBlockingQueue`是一个将元素按照优先级排序的阻塞的阻塞队列，元素的优先级越高，将会越先出队列。这是一个无界队列。
* `threadFactory`：线程池工厂，用来创建线程。通常在实际项目中，为了便于后期排查问题，在创建线程时需要为线程赋予一定的名称，通过线程池工厂，可以方便的为每一个创建的线程设置具有业务含义的名称。
* `handler`：拒绝策略。当任务队列已满，线程数量达到maximumPoolSize后，线程池就不会再接收新的任务了，这个时候就需要使用拒绝策略来决定最终是怎么处理这个任务。默认情况下使用AbortPolicy，表示无法处理新任务，直接抛出异常。在ThreadPoolExecutor类中定义了四个内部类，分别表示四种拒绝策略。我们也可以通过实现RejectExecutionHandler接口来实现自定义的拒绝策略。

> AbortPocily：不再接收新任务，直接抛出异常。
> CallerRunsPolicy：提交任务的线程自己处理。
> DiscardPolicy：不处理，直接丢弃。
> DiscardOldestPolicy：丢弃任务队列中排在最前面的任务，并执行当前任务。（排在队列最前面的任务并不一定是在队列中待的时间最长的任务，因为有可能是按照优先级排序的队列）

在使用ThreadPoolExecutor时，可以使用`execute(Runnable task)`方法向线程池中提交一个任务，没有返回值。也可以使用`submit()`方法向线程池中添加任务，有返回值，返回值对象是Future。submit()方法有三个重载的方法。

* `submit(Runnable task)`，该方法虽然返回值对象是Future，但是使用Future.get()获取结果是null。
* `submit(Runnable task,T result)`，方法的返回值对象是Future，通过Future.get()获取具体的返回值时，结果与方法的第二个参数result相等。
* `submit(Callable task)`，该方法的参数是一个Callable类型的对象，方法有返回值。

## 源码分析

了解了`ThreadPoolExecutor`的基本用法，下面将结合源码来分析下线程池的代码实现。从上面的线程池的原理中，我们可以发现，线程池的原理相对比较简单，代码实现起来应该不难，看源码主要是为了学习他人写的优秀代码，尤其是编程大师Doug Lea写的代码。
 
对于一个线程池，除了上面介绍的几个重要属性以外，我们还需要一个变量来表示线程池状态，线程池也需要有运行中、关闭中、已关闭等状态。如果要我们去实现一个线程池，可能第一反应就是用一个单独的变量来表示线程池的状态，再用另一个变量来表示线程池中线程的数量。这样的确可以，不过Doug Lea并不是这样实现的，他将两者用一个变量来表示（不得不感叹下，大佬就是大佬，想法果然和他人不一样）。那么问题来了，如何用一个变量来表示两个值？在读写锁的实现中将一个int型的数值，按照高低位来拆分，高位表示一个数，低位再表示另一个数，在线程池的实现中，Doug Lea再次使用了按位拆分的技巧。
 
在线程池中，使用了一个原子类AtomicInteger的变量来表示线程池状态和线程数量，该变量在内存中会占用4个字节，也就是32bit，其中高3位用来表示线程池的状态，低29位用来表示线程的数量。线程池的状态一共有5中状态，用3bit最多可以表示8种状态，因此采用高3位来表示线程池的状态完全能满足需求。示意图如下。

![image.png](https://i.loli.net/2021/11/08/9Ygfl52B84vHcDJ.png)

在看线程池的核心实现逻辑之前，先简单看下ThreadPoolExecutor中关于各种变量和方法的定义。因为在核心逻辑中，经常会用到它们，而且这些方法和变量大量用到了位运算，看起来不是特别直观，所以提前熟悉它们的功能对于看核心逻辑有很大的帮助。相关源码和注释如下。

```java
// 高2位表示线程池的状态，其他29位表示线程的数量，即worker的数量
private final AtomicInteger ctl = new AtomicInteger(ctlOf(RUNNING, 0));
// 计数的位数，29
private static final int COUNT_BITS = Integer.SIZE - 3;
// 线程池的最大大小，2^29 -1，
private static final int CAPACITY   = (1 << COUNT_BITS) - 1;

// runState is stored in the high-order bits
// 线程池的状态，高三位表示线程的运行状态，
// RUNNING: 111
private static final int RUNNING    = -1 << COUNT_BITS;
// SHUTDOWN: 000
private static final int SHUTDOWN   =  0 << COUNT_BITS;
// STOP: 001
private static final int STOP       =  1 << COUNT_BITS;
// TIFYING(整理): 010
private static final int TIDYING    =  2 << COUNT_BITS;
// TERMINATED: 011
private static final int TERMINATED =  3 << COUNT_BITS;

// Packing and unpacking ctl
// 计算线程池的状态，计算结果的低29位全为0，因此最终结果就是线程池的状态
private static int runStateOf(int c)     { return c & ~CAPACITY; }
// 工作线程的数量，计算结果的高3位全是0，因此最终结果就是工作线程的数量
private static int workerCountOf(int c)  { return c & CAPACITY; }
// 根据线程池的状态和工作线程的数量，计算ctl，实际上就是将两者合并成ctl
private static int ctlOf(int rs, int wc) { return rs | wc; }

/*
 * Bit field accessors that don't require unpacking ctl.
 * These depend on the bit layout and on workerCount being never negative.
 */

// 线程池的状态是否小于s
private static boolean runStateLessThan(int c, int s) {
    return c < s;
}

// 线程池的状态大于等于s
private static boolean runStateAtLeast(int c, int s) {
    return c >= s;
}

// 判断线程池是否处于运行状态
private static boolean isRunning(int c) {
    return c < SHUTDOWN;
}

```

  有了前面的基础，接下来分析下核心实现。再使用线程池时我们可以通过execute(Runnable task)来提交一个任务到线程池，因此我们从核心入口execute(Runnable task)方法开始分析。execute()方法的源码如下。在源码中我添加了部分注释，以供参考。

```java
public void execute(Runnable command) {
    if (command == null)
        throw new NullPointerException();
    
    int c = ctl.get();
    // workerCountOf(c)方法时计算工作线程的数量，
    // 1. 工作线程数是否小于核心线程数，如果小于核心线程数，就创建新的线程去执行任务
    if (workerCountOf(c) < corePoolSize) {
        if (addWorker(command, true))
            return;
        // 任务执行失败后，重新获取ctl的值，供下面的逻辑计算
        c = ctl.get();
    }
    // 2. 当工作线程数大于等于核心线程数时，线程池是运行状态，且任务添加到队列成功
    if (isRunning(c) && workQueue.offer(command)) {
        int recheck = ctl.get();
        // 如果线程池状态不是RUNNING状态，就执行拒绝策略
        if (! isRunning(recheck) && remove(command))
            reject(command);
        // 如果线程池中线程的数量为0，就调用addWorker()方法创建新的worker线程
        else if (workerCountOf(recheck) == 0)
            addWorker(null, false);
    }
    // 3. 线程池非运行状态，或者任务入队失败，就尝试创建新的worker线程
    else if (!addWorker(command, false))
        // 4. 如果创建新的worker线程失败，就执行拒绝策略。
        reject(command);
}
```

execute()方法的逻辑大致分为4部分，分别对应线程池原理部分所提到的4个步骤。

* 先通过workerCountOf(c)方法计算当前线程池中线程的数量，然后与初始化线程池时指定的核心线程数相比较，如果小于核心线程数，就调用addWorker()方法，实际上就是创建新的线程来执行任务。addWorker()方法的源码后面分析。
* 如果当前线程数大于等于核心线程数，那么就通过workQueue.off(command)方法，将任务添加到任务队列中。如果此时任务队列还没有满，那么就会添加成功，workQueue.off(command)就会返回true，那么就会进入到if逻辑块中，进行一些其他的判断。如果此时任务队列已经满了，workQueue.off(command)方法就会返回false，那么就会执行后面的3和4。
* 当任务队列满了以后，就会再次调用addWorker()方法，在addworker()方法中会在创建新的线程之前，判断线程数会不会超过最大线程数，如果会，addworker()就会返回false。如果不会，就会创建新的线程去执行任务。
* 如果addWorker()返回true，表示不能再创建新的线程了，那么此时就会执行到4，即调用reject()方法，执行拒绝策略。reject()方法的逻辑比较简单，就是调用了我们指定的handler的rejectedExecution()方法。其源码如下。

```java
final void reject(Runnable command) {
    handler.rejectedExecution(command, this);
}
```

从上面的分析中，可以看出，在好几处逻辑中均调用了addWorker()方法，这说明该方法十分重要。事实也是如此，该方法不仅重要，代码实现还十分复杂。该方法需要两个参数，第一个参数就是我们传入的Runnable任务，第二参数是一个boolean值，传入true表示的是当前线程池中的线程数还没有达到核心线程数，传false表示当前线程数已经大于等于核心线程数了。addWorker()方法的源码很长，这里我将其分为两个部分，下面先看前面一部分的源码。

```java
private boolean addWorker(Runnable firstTask, boolean core) {
    retry:
    for (;;) {
        int c = ctl.get();
        int rs = runStateOf(c);

        // Check if queue empty only if necessary.
        // 1. 当线程池的状态大于SHUTDOWN时，返回false。因为线程池处于关闭状态了，就不能再接受任务了
        // 2. 当线程池的状态等于SHUTDOWN时，firstTask不为空或者任务队列为空，返回false
        if (rs >= SHUTDOWN &&
            ! (rs == SHUTDOWN &&
               firstTask == null &&
               ! workQueue.isEmpty()))
            return false;

        for (;;) {
            int wc = workerCountOf(c);
            // 1. 线程数大于等于理论上的最大数(2^29-1)，则直接返回false。（因为线程数不能再增加了）
            // 2. 根据core来决定线程数应该和谁比较。当线程数大于核心线程数或者最大线程数时，直接返回false。
            // （因为当大于核心线程数时，表示此时任务应该直接添加到队列中(如果队列满了，可能入队失败)；当大于最大线程数时，肯定不能再新创建线程了，不然设置最大线程数有毛用）
            if (wc >= CAPACITY ||
                wc >= (core ? corePoolSize : maximumPoolSize))
                return false;
            // 线程数+1，如果设置成功，就跳出外层循环
            if (compareAndIncrementWorkerCount(c))
                break retry;
            // 再次获取线程池的状态，并将其与前面获取到的值比较，
            // 如果相同，说明线程池的状态没有发生变化，继续在内循环中进行循环
            // 如果不相同，说明在这期间，线程池的状态发生了变化，需要跳到外层循环，然后再重新进行循环
            c = ctl.get();  // Re-read ctl
            if (runStateOf(c) != rs)
                continue retry;
            // else CAS failed due to workerCount change; retry inner loop
        }
    }
    // 省略后半部分代码
    // ......
}
```

在这部分代码中，我们可以看到一个很陌生的语法：retry...break retry...continue retry。这种写法真的是太少见了，少见到我第一眼看到的时候，以为是我不小心碰到键盘，把源码给改了。这种语法有点类似于C语言里面的goto（已经被遗弃），其作用就是在for循环之前定义一个retry，然后在循环中，使用break retry时，就会让代码跳出循环，并不再进入循环；当使用continue retry时，表示跳出当前循环，立马进入到下一次循环。由于这里使用了两层for循环，因此为了方便在内层循环中一下子跳出到外层循环，就使用了retry这种语法。需要说明的是，这里的retry并不是Java里面的关键字，而是随机定义的一个字符串，我们也可以写成a,b,c等，但是后面的break和continue后面的字符串需要和前面定义的这个字符串对应。
 
我们可以看到，前半部分的核心逻辑就是使用了两个无限for和一个CAS操作来设置线程池的线程数量。如果线程池的线程数修改成功，就中断循环，进入后半部分代码的逻辑，如果修改失败，就利用for循环再一次进行修改，这样的好处是，既实现了线程安全，也避免使用锁，提高了效率。在这一部分代码中，进行了很多判断，这些判断主要是校验线程池的状态以及线程数，个人认为不是特别重要，我们主要抓住核心逻辑即可。
  
当成功修改线程数量以后，就会执行addWorker()方法的后半部分代码，其源码如下。

```java
private boolean addWorker(Runnable firstTask, boolean core) {
    // 省略前半部分代码
    // ......
    
    boolean workerStarted = false;
    boolean workerAdded = false;
    Worker w = null;
    try {
        // 创建一个新的worker线程
        w = new Worker(firstTask);
        final Thread t = w.thread;
        if (t != null) {
            final ReentrantLock mainLock = this.mainLock;
            mainLock.lock();
            try {
                // Recheck while holding lock.
                // Back out on ThreadFactory failure or if
                // shut down before lock acquired.
                // 再次获取线程池的状态，因为在获取锁期间，线程池的状态可能改变了
                int rs = runStateOf(ctl.get());

                // 如果线程池状态时运行状态或者是关闭状态但是firstTask是空，就将worker线程添加到线程池
                if (rs < SHUTDOWN ||
                    (rs == SHUTDOWN && firstTask == null)) {
                    // 判断worker线程是否已经启动了，如果已经启动，就抛出异常
                    // 个人觉得这一步没有任何意义，因为worker线程是刚new出来的，没有在任何地方启动
                    if (t.isAlive()) // precheck that t is startable
                        throw new IllegalThreadStateException();
                    workers.add(w);
                    int s = workers.size();
                    if (s > largestPoolSize)
                        largestPoolSize = s;
                    workerAdded = true;
                }
            } finally {
                mainLock.unlock();
            }
            // 启动线程
            if (workerAdded) {
                t.start();
                workerStarted = true;
            }
        }
    } finally {

        // 如果启动失败，就将worker线程从线程池移除，并将线程数减1
        if (! workerStarted)
            addWorkerFailed(w);
    }
    return workerStarted;
}
```

在这一部分代码中，通过new Worker(firstTask)创建了一个Worker对象，Worker对象继承了AQS，同时实现了Runnable接口，它是线程池中真正干活的人。我们提交到线程的任务，最终都是封装成Worker对象，然后由Worker对象来完成任务。先简单看下Woker的构造方法，其源码如下。在构造方法中，首先设置了同步变量state为-1，然后通过ThreadFactory创建了一个线程，注意在通过ThreadFactory创建线程时，将Worker自身也就是this，传入了进去，也就是说最后创建出来的线程对象，它里面的target属性就是指向这个Worker对象。

```java
private final class Worker
    extends AbstractQueuedSynchronizer
    implements Runnable{

    /** Thread this worker is running in.  Null if factory fails. */
    final Thread thread;
    /** Initial task to run.  Possibly null. */
    Runnable firstTask;
    /** Per-thread task counter */
    volatile long completedTasks;

    /**
     * Creates with given first task and thread from ThreadFactory.
     * @param firstTask the first task (null if none)
     */
    Worker(Runnable firstTask) {
        setState(-1); // inhibit interrupts until runWorker
        this.firstTask = firstTask;
        // 将this传入进去，最后就是使线程的target属性等于当前的worker对象
        this.thread = getThreadFactory().newThread(this);
    }
}
```

当通过new Worker(firstTask)创建完worker对象后，此时线程已经被创建好了，在启动线程之前，先通过t.isAlive()判断线程是已经启动，如果没有启动，才会调用线程的start()方法来启动线程。这里有一点需要注意的是，创建完worker对象后，调用了mainLock.lock()来保证线程安全，因为这一步workers.add(w)存在并发的可能，所以需要通过获取锁来保证线程安全。

当调用线程的start()方法之后，如果线程获取到CPU的执行权，那么就会执行线程的run()方法，在线程的run()方法中，会执行线程中target属性的run()方法。这里线程的target属性就是我们创建的worker对象，因此最终会执行到Worker的run()

```java
private final class Worker
    extends AbstractQueuedSynchronizer
    implements Runnable{

    public void run() {
        runWorker(this);
    }
}
```

在Worker类的run()中，直接调用了runWorker()方法。所以Worker执行任务的核心逻辑就是在runWorker()方法中实现的。其源码如下。

```java
final void runWorker(Worker w) {
    Thread wt = Thread.currentThread();
    Runnable task = w.firstTask;
    w.firstTask = null;
    w.unlock(); // allow interrupts
    boolean completedAbruptly = true;
    try {
        // 如果worker线程的firstTask不为空或者能从任务队列中获取到任务，就执行
        // 否则就会一直阻塞到getTask()方法处
        while (task != null || (task = getTask()) != null) {
            // 保证worker串行的执行线程
            w.lock();
            // If pool is stopping, ensure thread is interrupted;
            // if not, ensure thread is not interrupted.  This
            // requires a recheck in second case to deal with
            // shutdownNow race while clearing interrupt
            if ((runStateAtLeast(ctl.get(), STOP) ||
                 (Thread.interrupted() &&
                  runStateAtLeast(ctl.get(), STOP))) &&
                !wt.isInterrupted())
                wt.interrupt();
            try {
                // beforeExecute()是空方法，由子类具体实现
                // 该方法的目的是为了让任务执行前做一些其他操作
                beforeExecute(wt, task);
                Throwable thrown = null;
                try {
                    // 真正执行任务
                    task.run();
                } catch (RuntimeException x) {
                    thrown = x; throw x;
                } catch (Error x) {
                    thrown = x; throw x;
                } catch (Throwable x) {
                    thrown = x; throw new Error(x);
                } finally {
                    // afterExecute()空方法，由子类具体实现
                    // 该方法的目的是为了让任务执行后做一些其他操作
                    afterExecute(task, thrown);
                }
            } finally {
                task = null;
                w.completedTasks++;
                w.unlock();
            }
        }
        completedAbruptly = false;
    } finally {
        processWorkerExit(w, completedAbruptly);
    }
}
```

runWorker()的源码看起来也比较长，但核心逻辑就一行，即：task.run()，最终执行了我们提交的Runnable任务。在runWorker()方法中通过一个while循环来让Worker对象一直来执行任务。当传入的task对象不为空或者通过getTask()方法能从任务队列中获取到任务时，worker就会一直执行。否则将在finally语句块中调用processWorkerExit退出，让线程中断，最终销毁。

getTask()方法是一个阻塞的方法，当能从任务队列中获取到任务时，就会立即返回一个任务。如果获取不到任务，就会阻塞。它支持超时，当超过线程池初始化时指定的线程最大存活时间后，就会返回null，从而导致worker线程退出while循环，最终线程销毁。

到这儿线程池的execute()方法就分析完了。最后简单分析下线程池的shutdown()方法和shutdownNow()方法。当调用shutdown()方法时，会令线程池的状态为SHUTDOWN，然后中断空闲的线程，对于已经在执行任务的线程并不会中断。当调用shutdownNow()方法时，会令线程池的状态为STOP，然后在中断所有的线程，包括正在执行任务的线程。

shutdown()方法的源码如下。

```java
public void shutdown() {
    final ReentrantLock mainLock = this.mainLock;
    mainLock.lock();
    try {
        // 权限校验
        checkShutdownAccess();
        // 将线程池的状态设置为SHUTDOWN状态
        advanceRunState(SHUTDOWN);
        // 中断空闲的worker线程
        interruptIdleWorkers();
        // 空方法，由子类具体去实现，例如ScheduledThreadPoolExecutor
        onShutdown(); // hook for ScheduledThreadPoolExecutor
    } finally {
        mainLock.unlock();
    }
    // 尝试将线程池的状态设置为TERMINATED
    tryTerminate();
}
```

shutdownNow()方法的源码如下。

```java
public List<Runnable> shutdownNow() {
    List<Runnable> tasks;
    final ReentrantLock mainLock = this.mainLock;
    mainLock.lock();
    try {
        checkShutdownAccess();
        // 线程池状态设置为STOP
        advanceRunState(STOP);
        // 中断所有线程，包括正在执行任务的线程
        interruptWorkers();
        // 清除任务队列中的所有任务
        tasks = drainQueue();
    } finally {
        mainLock.unlock();
    }
    tryTerminate();
    return tasks;
}
```

在实际工作当中，对于究竟应该使用哪一种方法去中断线程池，应该结合具体的任务来决定，如果要求任务必须执行完成，那么就是用shutdown()方法。通常也建议使用shutdown()方法，更加优雅。

## 总结

本文主要介绍了线程池的实现原理，其原理主要分为4个核心步骤，先判断线程数量是否超过核心线程数，然后再判断任务队列是否已经满了，再判断线程数会不会超过设置的最大线程数，最后执行拒绝策略。接着本文详细介绍了线程池的几个核心参数corePoolSize,maximumPoolSize,keepAliveTime,unit,workQueue,threadFactory,handler以及它们的各自的意义，然后结合源码实现，详细分析了任务的执行过程。

无论是读写锁的实现，还是线程池的实现，Doug Lea都使用了将一个int型的变量按照高低位拆分的技巧，这种思想很值得学习，不仅是因为设计巧妙，还因为在计算机中位运算的执行效率更高。

最后解释下关于文章开头提到的一点疑惑：为什么是先判断任务队列有没有满，再判断线程数有没有超过最大线程数？而不是先判断最大线程数，再判断任务队列是否已满？

答案和具体的源码实现有关。因为当需要创建线程的时候，都会调用addWorker()方法，在addWorker()的后半部分的逻辑中，会调用mainLock.lock()方法来获取全局锁，而获取锁就会造成一定的资源争抢。如果先判断最大线程数，再判断任务队列是否已满，这样就会造成线程池原理的4个步骤中，第1步判断核心线程数时要获取全局锁，第2步判断最大线程数时，又要获取全局锁，这样相比于先判断任务队列是否已满，再判断最大线程数，就可能会多出一次获取全局锁的过程。因此在设计线程池，为了尽可能的避免因为获取全局锁而造成资源的争抢，所以会先判断任务队列是否已满，再判断最大线程数。

另外一个疑惑就是：LinkedBlockingQueue的吞吐量比ArrayBlockingQueue的吞吐量要高。前者是基于链表实现的，后者是基于数组实现的，正常情况下，不应该是数组的性能要高于链表吗？

然后看了一下这两个阻塞队列的源码才发现，这是因为LinkedBlockingQueue的读和写操作使用了两个锁，takeLock和putLock，读写操作不会造成资源的争抢。而ArrayBlockingQueue的读和写使用的是同一把锁，读写操作存在锁的竞争。因此LinkedBlockingQueue的吞吐量高于ArrayBlockingQueue。



*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java原子类AtomicInteger实现原理### 典型回答

`AtomicInteger`是对int类型的一个封装，提供原子性的访问和更新操作，其原子性操作的实现是基于`CAS（compare-and-swap）`技术。

所谓CAS，表现为一组指令，当利用CAS执行试图进行一些更新操作时。会首先比较当前数值，如果数值未变，代表没有其它线程进行并发修改，则成功更新。如果数值改变，则可能出现不同的选择，要么进行重试，要么就返回是否成功。也就是所谓的“乐观锁”。

从`AtomicInteger`的内部属性可以看出，它依赖于Unsafe提供的一些底层能力，进行底层操作；以volatile的value字段，记录数值，以保证可见性。

```java
private static final jdk.internal.misc.Unsafe U = jdk.internal.misc.Unsafe.getUnsafe();
private static final long VALUE = U.objectFieldOffset(AtomicInteger.class, "value");
private volatile int value;
```

具体的原子操作细节，可以参考任意一个原子更新方法，比如下面的getAndIncrement。Unsafe会利用value字段的内存地址偏移，直接完成操作。

```java
public final int getAndIncrement() {
  return U.getAndAddInt(this, VALUE, 1);
}
```

因为getAndIncrement需要返回数值，所以需要添加失败重试逻辑。

```java
public final int getAndAddInt(Object o, long offset, int delta) {
  int v;
  do {
    v = getIntVolatile(o, offset);
  } while (!weakCompareAndSetInt(o, offset, v, v + delta));
  return v;
}
```

而类似compareAndSet这种返回boolean类型的函数，因为其返回值表现的就是是否成功与否，所以不需要重试。

```java
public final boolean compareAndSet(int expectedValue, int newValue)
```

CAS是Java并发中所谓lock-free机制的基础。

### 知识扩展

接下来我们通过一个例子看看如何利用Java标准库使用CAS。设想这样一个场景：在数据库产品中，为保证索引的一致性，一个常见的选择是，保证只有一个线程能够排他性地修改一个索引分区。如何在数据库抽象层面实现呢？

可以考虑为索引分区对象添加一个逻辑上的锁。例如，以当前独占的线程ID作为锁的数值，然后通过原子操作设置lock数值，来实现加锁和释放锁，伪代码如下：

```java
public class AtomicBTreePartition {
  private volatile long lock;
  public void acquireLock() {}
  public void releaseLock() {}
}
```

那么在Java代码中，我们怎么实现锁操作呢？Unsafe似乎不是个好的选择，它设计之初仅仅打算提供给Java标准库自己使用，它的名字也暗示我们最好不要用它。目前Java提供了两种公共API，可以实现这种CAS操作。比如使用`java.util.concurrent.atomic.AtomicLongFieldUpdater`，它是基于反射机制创建，我们需要保证类型和字段名正确。

```java
private static final AtomicLongFieldUpdater<AtomicBTreePartition>
  LOCK_FIELD_UPDATER = AtomicLongFieldUpdater.newUpdater(
    AtomicBTreePartition.class,
    "lock");
 
private void acquireLock() {
  long t = Thread.currentThread().getId();
  while (!LOCK_FIELD_UPDATER.compareAndSet(this, 0L, t)) {
    // 等待一会儿，数据库操作可能比较慢。
    ...
  }
}
```

`java.util.current.atomic`包提供了最常用的原子性数据类型，甚至是引用、数组等相关原子类型和更新操作工具，是很多线程安全程序的首选。

如果是`Java 9`以后，我们完全可以采用另外一种方式实现，也就是`Variable Handler API`，提供了各种粒度的原子或有序性的操作。将前面的代码修改如下：

```java
private static final VarHandle HANDLER = MethodHandles
  .lookup()
  .findStaticVarHandle(AtomicBTreePartition.class, "lock");
 
private void acquireLock() {
  long t = Thread.currentThread().getId();
  while (!HANDLE.compareAndSet(this, 0L, t)) {
    // 等待一会儿，数据库操作可能比较慢。
    ...
  }
}
```

过程非常直观，首先，获取相应的变量句柄，然后直接调用其提供的CAS方法。

一般来说，我们进行的类似CAS操作，可以并且推荐使用Variable Handler API去实现，其提供了精细粒度的公共底层API。这里强调“公共”，是因为其API不会内部API（例如Unsafe）那样，发生不可预测的修改。

CAS也并不是没有副作用。试想，其常用的失败重试机制，隐含着一个假设，即竞争情况是短暂的。大多数应用场景中，确实大部分重试只会发生一次就获得了成功。但是总是有意外情况，所以在有需要的时候，还是要考虑限制自旋的次数，以免过度消耗CPU。

另外一个就是著名的ABA问题，这是通常只在lock-free算法下暴露的问题。前面说过CAS是在更新时比较前值，如果对方只是恰好相同，例如期间发生了`A->B->A`的更新，仅仅判断数值是A，可能导致不合理的修改操作。针对这种情况，Java提供了`AtomicStampedReference`工具类。通过为引用建立类似版本号（stamp）的方式，来保证CAS的正确性。

前面介绍了CAS的场景与实现，幸运的是，大多数情况下，Java开发者并不需要直接利用CAS代码去实现线程安全容器等，更多是通过并发包等间接享受到ock-free机制在扩展性上的好处。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## ReentrantLock实现原理使用 `synchronize` 来做同步处理时，锁的获取和释放都是隐式的，实现的原理是通过编译后加上不同的机器指令来实现。

而 `ReentrantLock` 就是一个普通的类，它是基于 `AQS(AbstractQueuedSynchronizer)` 来实现的。

是一个**重入锁**：一个线程获得了锁之后仍然可以**反复**的加锁，不会出现自己阻塞自己的情况。

> AQS 是 Java 并发包里实现锁、同步的一个重要的基础框架。

### 锁类型

ReentrantLock 分为公平锁和非公平锁，可以通过构造方法来指定具体类型：

```java
//默认非公平锁
public ReentrantLock() {
    sync = new NonfairSync();
}
//公平锁
public ReentrantLock(boolean fair) {
    sync = fair ? new FairSync() : new NonfairSync();
}
```

默认一般使用非公平锁，它的效率和吞吐量都比公平锁高的多(后面会分析具体原因)。

### 获取锁

通常的使用方式如下:

```java
private ReentrantLock lock = new ReentrantLock();
public void run() {
    lock.lock();
    try {
        //do bussiness
    } catch (InterruptedException e) {
        e.printStackTrace();
    } finally {
        lock.unlock();
    }
}
```

### 公平锁获取锁

首先看下获取锁的过程：

```java
public void lock() {
    sync.lock();
}
```

可以看到是使用 sync的方法，而这个方法是一个抽象方法，具体是由其子类(FairSync)来实现的，以下是公平锁的实现:

```java
final void lock() {
	acquire(1);
}

//AbstractQueuedSynchronizer 中的 acquire()
public final void acquire(int arg) {
  if (!tryAcquire(arg) &&
  	acquireQueued(addWaiter(Node.EXCLUSIVE), arg))
  selfInterrupt();
}
```

第一步是尝试获取锁(tryAcquire(arg)),这个也是由其子类实现：

```java
protected final boolean tryAcquire(int acquires) {
        final Thread current = Thread.currentThread();
        int c = getState();
        if (c == 0) {
            if (!hasQueuedPredecessors() &&
                compareAndSetState(0, acquires)) {
                setExclusiveOwnerThread(current);
                return true;
            }
        }
        else if (current == getExclusiveOwnerThread()) {
            int nextc = c + acquires;
            if (nextc < 0)
                throw new Error("Maximum lock count exceeded");
            setState(nextc);
            return true;
        }
        return false;
    }
}
```

首先会判断 AQS 中的 state 是否等于 0，0 表示目前没有其他线程获得锁，当前线程就可以尝试获取锁。

注意:尝试之前会利用 hasQueuedPredecessors() 方法来判断 AQS 的队列中中是否有其他线程，如果有则不会尝试获取锁(这是公平锁特有的情况)。

如果队列中没有线程就利用 CAS 来将 AQS 中的 state 修改为1，也就是获取锁，获取成功则将当前线程置为获得锁的独占线程(setExclusiveOwnerThread(current))。

如果 state 大于 0 时，说明锁已经被获取了，则需要判断获取锁的线程是否为当前线程(ReentrantLock 支持重入)，是则需要将 state + 1，并将值更新。

### 写入队列

如果 tryAcquire(arg) 获取锁失败，则需要用 addWaiter(Node.EXCLUSIVE) 将当前线程写入队列中。

写入之前需要将当前线程包装为一个 Node 对象(addWaiter(Node.EXCLUSIVE))。

> AQS 中的队列是由 Node 节点组成的双向链表实现的。

包装代码:

```java
private Node addWaiter(Node mode) {
    Node node = new Node(Thread.currentThread(), mode);
    // Try the fast path of enq; backup to full enq on failure
    Node pred = tail;
    if (pred != null) {
        node.prev = pred;
        if (compareAndSetTail(pred, node)) {
            pred.next = node;
            return node;
        }
    }
    enq(node);
    return node;
}
```

首先判断队列是否为空，不为空时则将封装好的 Node 利用 CAS 写入队尾，如果出现并发写入失败就需要调用 enq(node); 来写入了。

```java
private Node enq(final Node node) {
    for (;;) {
        Node t = tail;
        if (t == null) { // Must initialize
            if (compareAndSetHead(new Node()))
                tail = head;
        } else {
            node.prev = t;
            if (compareAndSetTail(t, node)) {
                t.next = node;
                return t;
            }
        }
    }
}
```

这个处理逻辑就相当于自旋加上 CAS 保证一定能写入队列。

### 挂起等待线程

写入队列之后需要将当前线程挂起(利用acquireQueued(addWaiter(Node.EXCLUSIVE), arg))：

```java
final boolean acquireQueued(final Node node, int arg) {
    boolean failed = true;
    try {
        boolean interrupted = false;
        for (;;) {
            final Node p = node.predecessor();
            if (p == head && tryAcquire(arg)) {
                setHead(node);
                p.next = null; // help GC
                failed = false;
                return interrupted;
            }
            if (shouldParkAfterFailedAcquire(p, node) &&
                parkAndCheckInterrupt())
                interrupted = true;
        }
    } finally {
        if (failed)
            cancelAcquire(node);
    }
}
```

首先会根据 node.predecessor() 获取到上一个节点是否为头节点，如果是则尝试获取一次锁，获取成功就万事大吉了。

如果不是头节点，或者获取锁失败，则会根据上一个节点的 waitStatus 状态来处理(shouldParkAfterFailedAcquire(p, node))。

waitStatus 用于记录当前节点的状态，如节点取消、节点等待等。

shouldParkAfterFailedAcquire(p, node) 返回当前线程是否需要挂起，如果需要则调用 parkAndCheckInterrupt()：

```java
private final boolean parkAndCheckInterrupt() {
    LockSupport.park(this);
    return Thread.interrupted();
}
```

他是利用 LockSupport 的 part 方法来挂起当前线程的，直到被唤醒。

### 非公平锁获取锁

公平锁与非公平锁的差异主要在获取锁：

公平锁就相当于买票，后来的人需要排到队尾依次买票，不能插队。

而非公平锁则没有这些规则，是抢占模式，每来一个人不会去管队列如何，直接尝试获取锁。

非公平锁:

```java
final void lock() {
    //直接尝试获取锁
    if (compareAndSetState(0, 1))
        setExclusiveOwnerThread(Thread.currentThread());
    else
        acquire(1);
}
```

公平锁:

```java
final void lock() {
    acquire(1);
}
```

还要一个重要的区别是在尝试获取锁时tryAcquire(arg)，非公平锁是不需要判断队列中是否还有其他线程，也是直接尝试获取锁：

```java
final boolean nonfairTryAcquire(int acquires) {
    final Thread current = Thread.currentThread();
    int c = getState();
    if (c == 0) {
        //没有 !hasQueuedPredecessors() 判断
        if (compareAndSetState(0, acquires)) {
            setExclusiveOwnerThread(current);
            return true;
        }
    }
    else if (current == getExclusiveOwnerThread()) {
        int nextc = c + acquires;
        if (nextc < 0) // overflow
            throw new Error("Maximum lock count exceeded");
        setState(nextc);
        return true;
    }
    return false;
}
```

### 释放锁

公平锁和非公平锁的释放流程都是一样的：

```java
public void unlock() {
    sync.release(1);
}
public final boolean release(int arg) {
    if (tryRelease(arg)) {
        Node h = head;
        if (h != null && h.waitStatus != 0)
        	   //唤醒被挂起的线程
            unparkSuccessor(h);
        return true;
    }
    return false;
}
//尝试释放锁
protected final boolean tryRelease(int releases) {
    int c = getState() - releases;
    if (Thread.currentThread() != getExclusiveOwnerThread())
        throw new IllegalMonitorStateException();
    boolean free = false;
    if (c == 0) {
        free = true;
        setExclusiveOwnerThread(null);
    }
    setState(c);
    return free;
}
```

首先会判断当前线程是否为获得锁的线程，由于是重入锁所以需要将 state 减到 0 才认为完全释放锁。

释放之后需要调用 unparkSuccessor(h) 来唤醒被挂起的线程。

### 总结

由于公平锁需要关心队列的情况，得按照队列里的先后顺序来获取锁(会造成大量的线程上下文切换)，而非公平锁则没有这个限制。

所以也就能解释非公平锁的效率会被公平锁更高。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 启动nginx容器（随机端口映射），并挂载本地文件目录到容器html的命令？
```
Docker run -d -p --name nginx2 -v /home/nginx:/usr/share/nginx/html nginx
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 容器与主机之间的数据拷贝命令？
Docker cp命令用于穷奇与主机之间的数据拷贝

- 主机到哦容器：docker cp /www 96f7f14e99ab:/www/
- 容器到主机：docker cp 96f7f14e99ab:/www /tmp

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Docker的常用命令？
| 命令          | 备注                 |
| ------------- | -------------------- |
| docker pull   | 拉去或更新指定的镜像 |
| docker push   | 将镜像推送到远程仓库 |
| docker rm     | 删除容器             |
| docker rmi    | 删除镜像             |
| docker images | 列出所有镜像         |
| docker ps     | 列出所有容器         |

*** 
## ⭐️⭐️⭐️⭐️⭐️
## DockerFile中的命令COPY和ADD命令有什么区别？
COPY和ADD的区别时COPY的SRC只能是本地文件，其他用法一致。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## DockerFile中最常见的指定是什么?
| 指令  | 备注                   |
| ----- | ---------------------- |
| FROM  | 指定基础镜像           |
| LABEL | 功能为镜像指定标签     |
| RUN   | 运行指定命令           |
| CMD   | 容器启动时要运行的命令 |

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Docker容器有几种状态
四种状态：运行、已暂停、重新启动、已退出。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Docker容器
Docker容器包括应用程序及其所有依赖项，作为操作系统的独立进程运行。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Docker镜像
Docker镜像是Docker容器的源代码，Docker镜像用于创建容器。使用build命令创建镜像。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Docker与虚拟机有何不同
Docker不是虚拟化方法。它依赖于实际实现基于容器的虚拟化或操作系统级虚拟化的其他工具。为此，Docker最初使用LXC驱动程序，然后移动到libcontainer现在重命名为runc。Docker主要专注于在应用程序容器内自动部署应用程序。应用程序容器旨在打包和运行单个服务，而系统容器则设计为运行多个进程，如虚拟机。因此，Docker被视为容器化系统上的容器管理或应用程序部署工具。
A 容器不需要引导操作系统内核，因此可以在不到一秒的时间内创建容器。此功能使基于容器的虚拟化比其他虚拟化方法更加独特和可取。
B 由于基于容器的虚拟化为主机增加了很少或没有开销，因此基于容器的虚拟化具有接近本机的性能。
C 对于基于容器的虚拟化，与其他虚拟化不同，不需要其他软件。
D 主机上的所有容器共享主机的调度程序，从而节省了额外资源的需求。
E 与虚拟机映像相比，容器状态（Docker或LXC映像）的大小很小，因此容器映像很容易分发。
F 容器中的资源管理是通过cgroup实现的。Cgroups不允许容器消耗比分配给它们更多的资源。虽然主机的所有资源都在虚拟机中可见，但无法使用。这可以通过在容器和主机上同时运行top或htop来实现。所有环境的输出看起来都很相似。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么Docker
Docker是一个容器化平台，它以容器的形式将您的应用程序及其所有依赖项打包在一起，以确保您的应用程序在任何环境中无缝运行。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么使用消息队列？
##### 面试官心理分析

其实面试官主要是想看看：

- 第一，你知不知道你们系统里为什么要用消息队列这个东西？

  不少候选人，说自己项目里用了 Redis、MQ，但是其实他并不知道自己为什么要用这个东西。其实说白了，就是为了用而用，或者是别人设计的架构，他从头到尾都没思考过。

  没有对自己的架构问过为什么的人，一定是平时没有思考的人，面试官对这类候选人印象通常很不好。因为面试官担心你进了团队之后只会木头木脑的干呆活儿，不会自己思考。

- 第二，你既然用了消息队列这个东西，你知不知道用了有什么好处&坏处？

  你要是没考虑过这个，那你盲目弄个 MQ 进系统里，后面出了问题你是不是就自己溜了给公司留坑？你要是没考虑过引入一个技术可能存在的弊端和风险，面试官把这类候选人招进来了，基本可能就是挖坑型选手。就怕你干 1 年挖一堆坑，自己跳槽了，给公司留下无穷后患。

- 第三，既然你用了 MQ，可能是某一种 MQ，那么你当时做没做过调研？

  你别傻乎乎的自己拍脑袋看个人喜好就瞎用了一个 MQ，比如 Kafka，甚至都从没调研过业界流行的 MQ 到底有哪几种。每一个 MQ 的优点和缺点是什么。每一个 MQ 没有绝对的好坏，但是就是看用在哪个场景可以扬长避短，利用其优势，规避其劣势。

  如果是一个不考虑技术选型的候选人招进了团队，leader 交给他一个任务，去设计个什么系统，他在里面用一些技术，可能都没考虑过选型，最后选的技术可能并不一定合适，一样是留坑。

##### 面试题剖析

其实就是问问你消息队列都有哪些使用场景，然后你项目里具体是什么场景，说说你在这个场景里用消息队列是什么？

面试官问你这个问题，期望的一个回答是说，你们公司有个什么业务场景，这个业务场景有个什么技术挑战，如果不用 MQ 可能会很麻烦，但是你现在用了 MQ 之后带给了你很多的好处。

先说一下消息队列常见的使用场景吧，其实场景有很多，但是比较核心的有 3 个：解耦、异步、削峰。

##### 解耦

看这么个场景。A 系统发送数据到 BCD 三个系统，通过接口调用发送。如果 E 系统也要这个数据呢？那如果 C 系统现在不需要了呢？A 系统负责人几乎崩溃......

![file](https://img2018.cnblogs.com/blog/1756639/201909/1756639-20190908223436765-607649977.jpg)



在这个场景中，A 系统跟其它各种乱七八糟的系统严重耦合，A 系统产生一条比较关键的数据，很多系统都需要 A 系统将这个数据发送过来。A 系统要时时刻刻考虑 BCDE 四个系统如果挂了该咋办？要不要重发，要不要把消息存起来？头发都白了啊！

如果使用 MQ，A 系统产生一条数据，发送到 MQ 里面去，哪个系统需要数据自己去 MQ 里面消费。如果新系统需要数据，直接从 MQ 里消费即可；如果某个系统不需要这条数据了，就取消对 MQ 消息的消费即可。这样下来，A 系统压根儿不需要去考虑要给谁发送数据，不需要维护这个代码，也不需要考虑人家是否调用成功、失败超时等情况。

![file](https://img2018.cnblogs.com/blog/1756639/201909/1756639-20190908223437000-220196142.jpg)

总结：通过一个 MQ，Pub/Sub 发布订阅消息这么一个模型，A 系统就跟其它系统彻底解耦了。

面试技巧：你需要去考虑一下你负责的系统中是否有类似的场景，就是一个系统或者一个模块，调用了多个系统或者模块，互相之间的调用很复杂，维护起来很麻烦。但是其实这个调用是不需要直接同步调用接口的，如果用 MQ 给它异步化解耦，也是可以的，你就需要去考虑在你的项目里，是不是可以运用这个 MQ 去进行系统的解耦。在简历中体现出来这块东西，用 MQ 作解耦。

##### 异步

再来看一个场景，A 系统接收一个请求，需要在自己本地写库，还需要在 BCD 三个系统写库，自己本地写库要 3ms，BCD 三个系统分别写库要 300ms、450ms、200ms。最终请求总延时是 3 + 300 + 450 + 200 = 953ms，接近 1s，用户感觉搞个什么东西，慢死了慢死了。用户通过浏览器发起请求，等待个 1s，这几乎是不可接受的。

![file](https://img2018.cnblogs.com/blog/1756639/201909/1756639-20190908223437240-841013337.jpg)

一般互联网类的企业，对于用户直接的操作，一般要求是每个请求都必须在 200 ms 以内完成，对用户几乎是无感知的。

如果使用 MQ，那么 A 系统连续发送 3 条消息到 MQ 队列中，假如耗时 5ms，A 系统从接受一个请求到返回响应给用户，总时长是 3 + 5 = 8ms，对于用户而言，其实感觉上就是点个按钮，8ms 以后就直接返回了，爽！网站做得真好，真快

![file](https://img2018.cnblogs.com/blog/1756639/201909/1756639-20190908223437468-1330530320.jpg)

##### 削峰

每天 0:00 到 12:00，A 系统风平浪静，每秒并发请求数量就 50 个。结果每次一到 12:00 ~ 13:00 ，每秒并发请求数量突然会暴增到 5k+ 条。但是系统是直接基于 MySQL 的，大量的请求涌入 MySQL，每秒钟对 MySQL 执行约 5k 条 SQL。

一般的 MySQL，扛到每秒 2k 个请求就差不多了，如果每秒请求到 5k 的话，可能就直接把 MySQL 给打死了，导致系统崩溃，用户也就没法再使用系统了。

但是高峰期一过，到了下午的时候，就成了低峰期，可能也就 1w 的用户同时在网站上操作，每秒中的请求数量可能也就 50 个请求，对整个系统几乎没有任何的压力。

![file](https://img2018.cnblogs.com/blog/1756639/201909/1756639-20190908223437702-1402821528.jpg)

如果使用 MQ，每秒 5k 个请求写入 MQ，A 系统每秒钟最多处理 2k 个请求，因为 MySQL 每秒钟最多处理 2k 个。A 系统从 MQ 中慢慢拉取请求，每秒钟就拉取 2k 个请求，不要超过自己每秒能处理的最大请求数量就 ok，这样下来，哪怕是高峰期的时候，A 系统也绝对不会挂掉。而 MQ 每秒钟 5k 个请求进来，就 2k 个请求出去，结果就导致在中午高峰期（1 个小时），可能有几十万甚至几百万的请求积压在 MQ 中。

![file](https://img2018.cnblogs.com/blog/1756639/201909/1756639-20190908223437928-344432831.jpg)

这个短暂的高峰期积压是 ok 的，因为高峰期过了之后，每秒钟就 50 个请求进 MQ，但是 A 系统依然会按照每秒 2k 个请求的速度在处理。所以说，只要高峰期一过，A 系统就会快速将积压的消息给解决掉。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何解决消息队列的延时以及过期失效问题？消息队列满了以后该怎么处理？有几百万消息持续积压几小时怎么解决？
（一）、大量消息在mq里积压了几个小时了还没解决

几千万条数据在MQ里积压了七八个小时，从下午4点多，积压到了晚上很晚，10点多，11点多
这个是我们真实遇到过的一个场景，确实是线上故障了，这个时候要不然就是修复consumer的问题，让他恢复消费速度，然后傻傻的等待几个小时消费完毕。这个肯定不能在面试的时候说吧。

一个消费者一秒是1000条，一秒3个消费者是3000条，一分钟是18万条，1000多万条，所以如果你积压了几百万到上千万的数据，即使消费者恢复了，也需要大概1小时的时间才能恢复过来。

一般这个时候，只能操作临时紧急扩容了，具体操作步骤和思路如下：

先修复consumer的问题，确保其恢复消费速度，然后将现有cnosumer都停掉。
新建一个topic，partition是原来的10倍，临时建立好原先10倍或者20倍的queue数量。
然后写一个临时的分发数据的consumer程序，这个程序部署上去消费积压的数据，消费之后不做耗时的处理，直接均匀轮询写入临时建立好的10倍数量的queue。
接着临时征用10倍的机器来部署consumer，每一批consumer消费一个临时queue的数据。
这种做法相当于是临时将queue资源和consumer资源扩大10倍，以正常的10倍速度来消费数据。
等快速消费完积压数据之后，得恢复原先部署架构，重新用原先的consumer机器来消费消息。
（二）、消息队列过期失效问题

假设你用的是rabbitmq，rabbitmq是可以设置过期时间的，就是TTL，如果消息在queue中积压超过一定的时间就会被rabbitmq给清理掉，这个数据就没了。那这就是第二个坑了。这就不是说数据会大量积压在mq里，而是大量的数据会直接搞丢。

这个情况下，就不是说要增加consumer消费积压的消息，因为实际上没啥积压，而是丢了大量的消息。我们可以采取一个方案，就是批量重导，这个我们之前线上也有类似的场景干过。就是大量积压的时候，我们当时就直接丢弃数据了，然后等过了高峰期以后，比如大家一起喝咖啡熬夜到晚上12点以后，用户都睡觉了。

这个时候我们就开始写程序，将丢失的那批数据，写个临时程序，一点一点的查出来，然后重新灌入mq里面去，把白天丢的数据给他补回来。也只能是这样了。

假设1万个订单积压在mq里面，没有处理，其中1000个订单都丢了，你只能手动写程序把那1000个订单给查出来，手动发到mq里去再补一次。

(三)、消息队列满了怎么搞？

如果走的方式是消息积压在mq里，那么如果你很长时间都没处理掉，此时导致mq都快写满了，咋办？这个还有别的办法吗？没有，谁让你第一个方案执行的太慢了，你临时写程序，接入数据来消费，消费一个丢弃一个，都不要了，快速消费掉所有的消息。然后走第二个方案，到了晚上再补数据吧。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 各种MQ的比较
| 特性                | activeMQ                 | rabbitMQ                             | rocketMQ                                                     | kafka                                                        |
| ------------------- | ------------------------ | ------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 单机吞吐量          | 万/秒                    | 万/秒                                | 10万/秒                                                      | 10万/秒                                                      |
| topic对吞吐量的影响 | 无                       | 无                                   | topic达到几百/几千个级别，吞吐量会有小幅下降；  这是rocket的最大优势 所以非常适用于支撑大批量topic场景 | topic可以达到几十/几百个级别，吞吐量会有大幅下降    kafka不适用大批量topic场景，除非加机器 |
| 时效性              | 毫秒                     | 微秒  这是rabbit 最大优势，延迟低    | 毫秒                                                         | 毫秒                                                         |
| 可用性              | 高。主从架构             | 高。主从架构                         | 非常高。分布式。                                             | 非常高。分布式。数据多副本，不会丢数据，不会不可用。         |
| 可靠性              | 有较低概率丢失数据       | ----                                 | 经配置优化可达到0丢失                                        | 经配置优化可达到0丢失                                        |
| 功能特性            | 功能齐全，但已不怎么维护 | erlang开发，并发强，性能极好，延迟低 | MQ功能较为齐全，扩展好                                       | 功能简单，主要用于大数据实时计算和日志采集，事实标准         |

综上，总结如下：

------

【activeMQ】

> - 优点：技术成熟，功能齐全，历史悠久，有大量公司在使用
> - 缺点：偶尔会有较低概率丢失数据，而且社区已经不怎么维护5.15.X版本
> - 使用场景：主要用于系统解耦和异步处理，不适用与大数据量吞吐情况。互联网公司很少适用

------

【rabitMQ】

> - 优点：吞吐量高，功能齐全，管理界面易用，社区活跃，性能极好，；
> - 缺点：吞吐量只是万级，erlang难以二次开发和掌控；集群动态扩展非常麻烦；
> - 使用场景：吞吐量不高而要求低延迟，并且不会频繁调整和扩展的场景。非常适合国内中小型互联网公司适用，因为管理界面非常友好，可以在界面进行配置和优化/集群监控。

------

【rocketMQ】

> - 优点：支持百千级大规模topic。吞吐量高（十万级，日处理上百亿）。接口易用。，分布式易扩展，阿里支持。java开发易于掌控。
> - 缺点：与阿里（社区）存在绑定。不兼容JMS规范。
> - 使用场景：高吞吐量

------

【kafka】

> - 优点：超高吞吐量，超高可用性和可靠性，分布式易扩展
> - 缺点：topic支持少，MQ功能简单，消息可能会重复消费影响数据精确度
> - 使用场景：超高吞吐量场景而数据精确度没那么高，天然适合大数据实时计算和日志采集场景

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 消息队列积压怎么办
当消费者出现异常，很容易引起队列积压，如果一秒钟1000个消息，那么一个小时就是几千万的消息积压，是非常可怕的事情，但是生产线上又有可能会出现；

当消息积压来不及处理，rabbitMQ如果设置了消息过期时间，那么就有可能由于积压无法及时处理而过期，这消息就被丢失了；

解决方法如下：

> - 不建议在生产环境使用数据过期策略，一是数据是否丢失无法控制，二是一旦积压就很有可能丢失；建议数据的处理都有代码来控制；
> - 当出现消息积压时，做法就是临时扩大consumer个数，让消息快速消费，一般都是通过业务逻辑的手段来完成：如下：

【rabbitmq解决积压范例】

> > 1. 修复consumer代码故障，确保consumer逻辑正确可以消费；
> > 2. 停止consumer，开启10倍20倍的queue个数；
> >     \* 创建一个临时的consumer程序，消费积压的queue，并把消息写入到扩建的10倍queue中；
> >     \*  再开启10倍20倍的consumer对新的扩充后队列进行消费；
> >     \* 这种做法相当于通过物理资源扩充了10倍来快速消费；

> > 1. 当消费完成后，需要恢复原有架构，开启原来的consumer进行正常消费；

【kafka解决范例】

> > 1. 修复consumer代码故障，确保consumer逻辑正确可以消费；
> > 2. 停止consumer，新建topic，新建10倍20倍的partition个数；
> >     \* 创建对应原topic的partition个数的临时的consumer程序，消费原来的topic，并把消息写入到扩建的新topic中；
> >     \*  再开启对应新partition个数的consumer对新的topic进行消费；
> >     \* 这种做法相当于通过物理资源扩充了10倍来快速消费；

> > 1. 当消费完成后，需要恢复原有架构，开启原来的consumer进行正常消费；

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 消息如何保证幂等性
例如kafka的offset可能是消费者批量处理后才提交到zk，重启后再消费时就可能会收到重复消息，需要消费者在处理消息时做幂等性设计，即先判断是否消费过，把已消费的放到本地缓存或者redis中，每次消费时先做个判断即可。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Kafka的消息是有序的吗？如果保证Kafka消息的顺序性？
Kafka只能保证局部有序，即只能保证一个分区里的消息有序。而其具体实现是通过生产者为每个分区的消息维护一个发送队列，我们需要将保证顺序的消息都发送到同一个分区中。并且由于Kafka会同时发送多个消息，所以还需指定max.in.flight.requests.per.connection为1，保证前一个消息发送成功，后一个消息才开始发送。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 使用消息队列，如果处理重复消息？
1）利用数据库的唯一约束实现幂等 2）为更新的数据设置前置条件（CAS） 3）记录并检查操作（在发送消息时，给每条消息指定一个全局唯一的 ID，消费时，先根据这个 ID 检查这条消息是否有被消费过，如果没有消费过，才更新数据，然后将消费状态置为已消费。）

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 使用消息队列，怎么确保消息不丢失？
在生产阶段，你需要捕获消息发送的错误，并重发消息。 在存储阶段，你可以通过配置刷盘和复制相关的参数，让消息写入到多个副本的磁盘上，来确保消息不会因为某个 Broker 宕机或者磁盘损坏而丢失。 在消费阶段，你需要在处理完全部消费业务逻辑之后，再发送消费确认。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 消息队列的弊端有哪些？
数据延迟；增加系统复杂度；可能产生数据不一致的问题。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 消息队列有哪些应用场景？
异步处理、流量控制、服务解耦、消息广播

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Eureka的基本架构是什么？
Spring Cloud 封装了 Netflix 公司开发的 Eureka 模块来实现服务注册和发现(请对比Zookeeper)。

Eureka 采用了 C-S 的设计架构。Eureka Server 作为服务注册功能的服务器，它是服务注册中心。

而系统中的其他微服务，使用 Eureka 的客户端连接到 Eureka Server并维持心跳连接。这样系统的维护人员就可以通过 Eureka Server 来监控系统中各个微服务是否正常运行。SpringCloud 的一些其他模块（比如Zuul）就可以通过 Eureka Server 来发现系统中的其他微服务，并执行相关的逻辑。

Eureka包含两个组件： Eureka Server 和 Eureka Client

Eureka Server提供服务注册服务各个节点启动后，会在EurekaServer中进行注册，这样EurekaServer中的服务注册表中将会存储所有可用服务节点的信息，服务节点的信息可以在界面中直观的看到

EurekaClient是一个Java客户端用于简化Eureka Server的交互，客户端同时也具备一个内置的、使用轮询(round-robin)负载算法的负载均衡器。在应用启动后，将会向Eureka Server发送心跳(默认周期为30秒)。如果Eureka Server在多个心跳周期内没有接收到某个节点的心跳，EurekaServer将会从服务注册表中把这个服务节点移除（默认90秒）

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是 Eureka服务注册与发现？
Eureka是Netflix的一个子模块，也是核心模块之一。Eureka是一个基于REST的服务，用于定位服务，以实现云端中间层服务发现和故障转移。服务注册与发现对于微服务架构来说是非常重要的，有了服务发现与注册，只需要使用服务的标识符，就可以访问到服务，而不需要修改服务调用的配置文件了。功能类似于dubbo的注册中心，比如Zookeeper。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 你所知道的微服务技术栈有哪些？
服务开发Springboot、Spring、SpringMVC
服务配置与管理Netflix公司的Archaius、阿里的Diamond等
服务注册与发现Eureka、Consul、Zookeeper等
服务调用Rest、RPC、gRPC
服务熔断器Hystrix、Envoy等
负载均衡Ribbon、Nginx等
服务接口调用(客户端调用服务的简化工具)Feign等
消息队列Kafka、RabbitMQ、ActiveMQ等
服务配置中心管理SpringCloudConfig、Chef等
服务路由（API网关）Zuul等
服务监控Zabbix、Nagios、Metrics、Spectator等
全链路追踪Zipkin，Brave、Dapper等
服务部署Docker、OpenStack、Kubernetes等
数据流操作开发包SpringCloud Stream（封装与Redis,Rabbit、Kafka等发送接收消息）
事件消息总线Spring Cloud Bus

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是服务熔断，什么是服务降级
服务熔断
熔断机制是应对雪崩效应的一种微服务链路保护机制。当扇出链路的某个微服务不可用或者响应时间太长时，会进行服务的降级，进而熔断该节点微服务的调用，快速返回”错误”的响应信息。当检测到该节点微服务调用响应正常后恢复调用链路。在SpringCloud框架里熔断机制通过Hystrix实现。Hystrix会监控微服务间调用的状况，当失败的调用到一定阈值，缺省是5秒内20次调用失败就会启动熔断机制。熔断机制的注解是@HystrixCommand。

服务降级
其实就是线程池中单个线程障处理，防止单个线程请求时间太长，导致资源长期被占有而得不到释放，从而导致线程池被快速占用完，导致服务崩溃。

Hystrix能解决如下问题：
请求超时降级，线程资源不足降级，降级之后可以返回自定义数据
线程池隔离降级，分布式服务可以针对不同的服务使用不同的线程池，从而互不影响
自动触发降级与恢复
实现请求缓存和请求合并

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 请谈谈对SpringBoot 和SpringCloud的理解
SpringBoot专注于快速方便的开发单个个体微服务。
SpringCloud是关注全局的微服务协调整理治理框架，它将SpringBoot开发的一个个单体微服务整合并管理起来，为各个微服务之间提供，配置管理、服务发现、断路器、路由、微代理、事件总线、全局锁、决策竞选、分布式会话等等集成服务
SpringBoot可以离开SpringCloud独立使用开发项目，但是SpringCloud离不开SpringBoot，属于依赖的关系。
SpringBoot专注于快速、方便的开发单个微服务个体，SpringCloud关注全局的服务治理框架。
Spring Boot可以离开Spring Cloud独立使用开发项目，但是Spring Cloud离不开Spring Boot，属于依赖的关系。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 微服务之间是如何通讯的？
第一种：远程过程调用（Remote Procedure Invocation）

直接通过远程过程调用来访问别的service。
示例：REST、gRPC、Apache、Thrift

优点：
简单，常见。因为没有中间件代理，系统更简单

缺点：
只支持请求/响应的模式，不支持别的，比如通知、请求/异步响应、发布/订阅、发布/异步响应降低了可用性，因为客户端和服务端在请求过程中必须都是可用的

第二种：消息

使用异步消息来做服务间通信。服务间通过消息管道来交换消息，从而通信。
示例：Apache Kafka、RabbitMQ

优点:
把客户端和服务端解耦，更松耦合 提高可用性，因为消息中间件缓存了消息，直到消费者可以消费
支持很多通信机制比如通知、请求/异步响应、发布/订阅、发布/异步响应

缺点:
消息中间件有额外的复杂性

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是微服务？
微服务架构是一种架构模式或者说是一种架构风格，它提倡将单一应用程序划分成一组小的服务，每个服务运行在其独立的自己的进程中，服务之间互相协调、互相配合，为用户提供最终价值。 服务之间采用轻量级的通信机制互相沟通（通常是基于HTTP的RESTful API）。每个服务都围绕着具体业务进行构建，并且能够被独立地部署到生产环境、类生产环境等。另外，应尽量避免统一的、集中式的服务管理机制，对具体的一个服务而言，应根据业务上下文，选择合适的语言、工具对其进行构建，可以有一个非常轻量级的集中式管理来协调这些服务，可以使用不同的语言来编写服务，也可以使用不同的数据存储。

从技术维度来说：
微服务化的核心就是将传统的一站式应用，根据业务拆分成一个一个的服务，彻底地去耦合,每一个微服务提供单个业务功能的服务，一个服务做一件事，从技术角度看就是一种小而独立的处理过程，类似进程概念，能够自行单独启动或销毁，拥有自己独立的数据库。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring Cloud 和dubbo的区别?
（1）服务调用方式 dubbo是RPC springcloud Rest Api
（2）注册中心,dubbo 是zookeeper springcloud是eureka，也可以是zookeeper
（3）服务网关,dubbo本身没有实现，只能通过其他第三方技术整合，springcloud有Zuul路由网关，作为路由服务器，进行消费者的请求分发,springcloud支持断路器，与git完美集成配置文件支持版本控制，事物总线实现配置文件的更新与服务自动装配等等一系列的微服务架构要素。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 服务注册和发现是什么意思？Spring Cloud 如何实现？
当我们开始一个项目时，我们通常在属性文件中进行所有的配置。随着越来越多的服务开发和部署，添加和修改这些属性变得更加复杂。有些服务可能会下降，而某些位置可能会发生变化。手动更改属性可能会产生问题。 Eureka 服务注册和发现可以在这种情况下提供帮助。由于所有服务都在 Eureka 服务器上注册并通过调用 Eureka 服务器完成查找，因此无需处理服务地点的任何更改和处理。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Spring Cloud 解决了哪些问题？
· 与分布式系统相关的复杂性 – 包括网络问题，延迟开销，带宽问题，安全问题。
· 处理服务发现的能力 – 服务发现允许集群中的进程和服务找到彼此并进行通信。
· 解决冗余问题 – 冗余问题经常发生在分布式系统中。
· 负载平衡 – 改进跨多个计算资源（例如计算机集群，网络链接，中央处理单元）的工作负载分布。
· 减少性能问题 – 减少因各种操作开销导致的性能问题。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 单片，SOA 和微服务架构有什么区别？
· 单片架构类似于大容器，其中应用程序的所有软件组件组装在一起并紧密封装。
· 一个面向服务的架构（SOA）是一种相互通信服务的集合。通信可以涉及简单的数据传递，也可以涉及两个或多个协调某些活动的服务。
· 微服务架构是一种架构风格，它将应用程序构建为以业务域为模型的小型自治服务集合。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 微服务有哪些特点？
· 解耦 – 系统内的服务很大程度上是分离的。因此，整个应用程序可以轻松构建，更改和扩展
· 组件化 – 微服务被视为可以轻松更换和升级的独立组件
· 业务能力 – 微服务非常简单，专注于单一功能
· 自治 – 开发人员和团队可以彼此独立工作，从而提高速度
· 持续交付 – 通过软件创建，测试和批准的系统自动化，允许频繁发布软件
· 责任 – 微服务不关注应用程序作为项目。相反，他们将应用程序视为他们负责的产品
· 分散治理 – 重点是使用正确的工具来做正确的工作。这意味着没有标准化模式或任何技术模式。开发人员可以自由选择最有用的工具来解决他们的问题
· 敏捷 – 微服务支持敏捷开发。任何新功能都可以快速开发并再次丢弃

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是B+树?
B树的变种，拥有B树的特点

独有特点：

节点中的关键字与子树数目相同。
关键字对应的子树节点都大于等于该关键字，子树包含该关键字自身。
所有关键字都出现在叶节点之中。
所有叶节点都有指向下一个叶节点的指针。
搜索：只在叶节点搜索。

叶子节点保存关键字和对应的数据，非叶节点只保存关键字和指向叶节点的指针，同等关键字数量的B树和B+树，B+树更小。

更适合做索引系统，原因：

由于叶节点有指针项链，B+树更适合做范围检索。
由于非叶节点只保存关键字和指向叶节点的指针，B+树可以容纳更多的关键字，树层数变小，磁盘查询次数更低。
B+树的查询效率比较稳定，查询所有关键字的路径相同。（MySQL索引就提供了B+树的实现方式）

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是B树?
B树是一种多叉树，也叫多路搜索树，适合用于文件索引上，减少磁盘IO次数，子节点存储最大数成为B树的阶，图中为2-3树。

m阶B树特点：

非叶节点最多有m棵子树。
根节点最少有两棵子树，非根非叶节点最少有m/2棵子树。
非叶节点保存的关键字个数等于该节点子树个数-1。
非叶节点保存的关键字大小有序。
节点中每个关键字左子树的关键字都小于该该关键字，右子树的关键字都大于该该关键字。
所有叶节点都在同一层。
查找：

对节点关键字进行二分查找。
如果找不到，进入对应的子树进行二分查找，如此循环。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么要设计后缀表达式，有什么好处？
后缀表达式又叫逆波兰表达式，逆波兰记法不需要括号来标识操作符的优先级。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 请你讲讲LRU算法的实现原理？
①LRU（Least recently used，最近最少使用）算法根据数据的历史访问记录来进行淘汰数据，其核心思想是“如果数据最近被访问过，那么将来被访问的几率也很高”，反过来说“如果数据最近这段时间一直都没有访问,那么将来被访问的概率也会很低”，两种理解是一样的；常用于页面置换算法，为虚拟页式存储管理服务。

②达到这样一种情形的算法是最理想的：每次调换出的页面是所有内存页面中最迟将被使用的；这可以最大限度的推迟页面调换，这种算法，被称为理想页面置换算法。可惜的是，这种算法是无法实现的。 为了尽量减少与理想算法的差距，产生了各种精妙的算法，最近最少使用页面置换算法便是其中一个。LRU 算法的提出，是基于这样一个事实：在前面几条指令中使用频繁的页面很可能在后面的几条指令中频繁使用。反过来说，已经很久没有使用的页面很可能在未来较长的一段时间内不会被用到 。这个，就是著名的局部性原理——比内存速度还要快的cache，也是基于同样的原理运行的。因此，我们只需要在每次调换时，找到最近最少使用的那个页面调出内存。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何在一个1到100的整数数组中找到丢失的数字?
如果是丢了一个数字，用个遍历把这些数字累加求和，

然后用 （1 + 100）*100/2 减去这个累加的总和，就是少的那一个数.

如果是丢了一些数字，

方法一：

先 1-100 遍历 创建一个字典，key为1-100，值默认都为NO。

然后把那一些数字作为一个数组，判断是否包含每一个key，包含那key，则那key的值改为YES，

最后值为NO的数则为缺失的数字

方法二：

先排序,并创建一个用来装缺失数的空数组，排好序后遍历,最大的数用101减，其余用后一个值减去前一个值如果差值不是1而是为n，就把被减数分别加1到（n-1）得出的数保存下来就是缺少的数字

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 数组和链表的区别
1、数组是将元素在内存中连续存放，由于每个元素占用内存相同，可以通过下标迅速访问数组中任何元素。但是如果要在数组中增加一个元素，需要移动大量元素，在内存中空出一个元素的空间，然后将要增加的元素放在其中。同样的道理，如果想删除一个元素，同样需要移动大量元素去填掉被移动的元素。如果应用需要快速访问数据，很少或不插入和删除元素，就应该用数组。

2、链表恰好相反，链表中的元素在内存中不是顺序存储的，而是通过存在元素中的指针联系到一起。比如：上一个元素有个指针指到下一个元素，以此类推，直到最后一个元素。如果要访问链表中一个元素，需要从第一个元素开始，一直找到需要的元素位置。但是增加和删除一个元素对于链表数据结构就非常简单了，只要修改元素中的指针就可以了。如果应用需要经常插入和删除元素你就需要用链表数据结构了。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 介绍一下，堆排序的原理是什么？
堆排序就是把最大堆堆顶的最大数取出，将剩余的堆继续调整为最大堆，再次将堆顶的最大数取出，这个过程持续到剩余数只有一个时结束。在堆中定义以下几种操作：

（1）最大堆调整（Max-Heapify）：将堆的末端子节点作调整，使得子节点永远小于父节点。

（2）创建最大堆（Build-Max-Heap）：将堆所有数据重新排序，使其成为最大堆。

（3）堆排序（Heap-Sort）：移除位在第一个数据的根节点，并做最大堆调整的递归运算

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何知道二叉树的深度？
实现二叉树的深度方式有两种，递归以及非递归。

①递归实现：

为了求树的深度，可以先求其左子树的深度和右子树的深度，可以用递归实现，递归的出口就是节点为空。返回值为0；

②非递归实现：

利用层次遍历的算法，设置变量level记录当前节点所在的层数，设置变量last指向当前层的最后一个节点，当处理完当前层的最后一个节点，让level指向+1操作。设置变量cur记录当前层已经访问的节点的个数，当cur等于last时，表示该层访问结束。

层次遍历在求树的宽度、输出某一层节点，某一层节点个数，每一层节点个数都可以采取类似的算法。

树的宽度：在树的深度算法基础上，加一个记录访问过的层节点个数最多的变量max,在访问每层前max与last比较，如果max比较大，max不变，如果max小于last，把last赋值给max;

*** 
## ⭐️⭐️⭐️⭐️⭐️
## TreeMap和TreeSet在排序时如何比较元素？Collections工具类中的sort()方法如何比较元素？
TreeSet要求存放的对象所属的类必须实现Comparable接口，该接口提供了比较元素的compareTo()方法，当插入元素时会回调该方法比较元素的大小。TreeMap要求存放的键值对映射的键必须实现Comparable接口从而根据键对元素进行排序。Collections工具类的sort方法有两种重载的形式，第一种要求传入的待排序容器中存放的对象比较实现Comparable接口以实现元素的比较；第二种不强制性的要求容器中的元素必须可比较，但是要求传入第二个参数，参数是Comparator接口的子类型（需要重写compare方法实现元素的比较），相当于一个临时定义的排序规则，其实就是通过接口注入比较元素大小的算法，也是对回调模式的应用（Java中对函数式编程的支持）。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是算法？
算法简单来说就是解决问题的步骤。

在Java中，算法通常都是由类的方法来实现的。前面的数据结构，比如链表为啥插入、删除快，而查找慢，平衡的二叉树插入、删除、查找都快，这都是实现这些数据结构的算法所造成的。后面我们讲的各种排序实现也是算法范畴的重要领域。

一、算法的五个特征

①、`有穷性：对于任意一组合法输入值，在执行又穷步骤之后一定能结束，即：算法中的每个步骤都能在有限时间内完成。`

②、确定性：在每种情况下所应执行的操作，在算法中都有确切的规定，使算法的执行者或阅读者都能明确其含义及如何执行。并且在任何条件下，算法都只有一条执行路径。

③、`可行性：算法中的所有操作都必须足够基本，都可以通过已经实现的基本操作运算有限次实现之。`

④、有输入：作为算法加工对象的量值，通常体现在算法当中的一组变量。有些输入量需要在算法执行的过程中输入，而有的算法表面上可以没有输入，实际上已被嵌入算法之中。

⑤、`有输出：它是一组与“输入”有确定关系的量值，是算法进行信息加工后得到的结果，这种确定关系即为算法功能。`

二、算法的设计原则

①、正确性：首先，算法应当满足以特定的“规则说明”方式给出的需求。其次，对算法是否“正确”的理解可以有以下四个层次：

一、程序语法错误。

二、程序对于几组输入数据能够得出满足需要的结果。

三、程序对于精心选择的、典型、苛刻切带有刁难性的几组输入数据能够得出满足要求的结果。

四、程序对于一切合法的输入数据都能得到满足要求的结果。

PS：通常以第 三 层意义的正确性作为衡量一个算法是否合格的标准。

②、可读性：算法为了人的阅读与交流，其次才是计算机执行。因此算法应该易于人的理解；另一方面，晦涩难懂的程序易于隐藏较多的错误而难以调试。

③、健壮性：当输入的数据非法时，算法应当恰当的做出反应或进行相应处理，而不是产生莫名其妙的输出结果。并且，处理出错的方法不应是中断程序执行，而是应当返回一个表示错误或错误性质的值，以便在更高的抽象层次上进行处理。

④、高效率与低存储量需求：通常算法效率值得是算法执行时间；存储量是指算法执行过程中所需要的最大存储空间，两者都与问题的规模有关。

前面三点 正确性，可读性和健壮性相信都好理解。对于第四点算法的执行效率和存储量，我们知道比较算法的时候，可能会说“A算法比B算法快两倍”之类的话，但实际上这种说法没有任何意义。因为当数据项个数发生变化时，A算法和B算法的效率比例也会发生变化，比如数据项增加了50%，可能A算法比B算法快三倍，但是如果数据项减少了50%，可能A算法和B算法速度一样。所以描述算法的速度必须要和数据项的个数联系起来。也就是“大O”表示法，它是一种算法复杂度的相对表示方式，这里我简单介绍一下，后面会根据具体的算法来描述。

相对(relative)：你只能比较相同的事物。你不能把一个做算数乘法的算法和排序整数列表的算法进行比较。但是，比较2个算法所做的算术操作（一个做乘法，一个做加法）将会告诉你一些有意义的东西；

表示(representation)：大O(用它最简单的形式)把算法间的比较简化为了一个单一变量。这个变量的选择基于观察或假设。例如，排序算法之间的对比通常是基于比较操作(比较2个结点来决定这2个结点的相对顺序)。这里面就假设了比较操作的计算开销很大。但是，如果比较操作的计算开销不大，而交换操作的计算开销很大，又会怎么样呢？这就改变了先前的比较方式；

复杂度(complexity)：如果排序10,000个元素花费了我1秒，那么排序1百万个元素会花多少时间？在这个例子里，复杂度就是相对其他东西的度量结果。

然后我们在说说算法的存储量，包括：

程序本身所占空间；

输入数据所占空间；

辅助变量所占空间；

一个算法的效率越高越好，而存储量是越低越好。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 适配器模式是什么？什么时候使用？
适配器模式（Adapter Pattern）是作为两个不兼容的接口之间的桥梁。这种类型的设计模式属于结构型模式，它结合了两个独立接口的功能。适配器模式提供对接口的转换。如果你的客户端使用某些接口，但是你有另外一些接口，你就可以写一个适配去来连接这些接口。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 拥塞控制
在某段时间，若对网络中某一资源的需求超过了该资源所能提供的可用部分，网络的性能就要变坏。这种情况就叫拥塞。拥塞控制就是为了防止过多的数据注入到网络中，这样就可以使网络中的路由器或链路不致过载。拥塞控制所要做的都有一个前提，就是网络能够承受现有的网络负荷。拥塞控制是一个全局性的过程，涉及到所有的主机，所有的路由器，以及与降低网络传输性能有关的所有因素。相反，流量控制往往是点对点通信量的控制，是个端到端的问题。流量控制所要做到的就是抑制发送端发送数据的速率，以便使接收端来得及接收。

为了进行拥塞控制，TCP 发送方要维持一个 拥塞窗口(cwnd) 的状态变量。拥塞控制窗口的大小取决于网络的拥塞程度，并且动态变化。发送方让自己的发送窗口取为拥塞窗口和接收方的接受窗口中较小的一个。

TCP的拥塞控制采用了四种算法，即 慢开始 、 拥塞避免 、快重传 和 快恢复。在网络层也可以使路由器采用适当的分组丢弃策略（如主动队列管理 AQM），以减少网络拥塞的发生。

- 慢开始： 慢开始算法的思路是当主机开始发送数据时，如果立即把大量数据字节注入到网络，那么可能会引起网络阻塞，因为现在还不知道网络的符合情况。经验表明，较好的方法是先探测一下，即由小到大逐渐增大发送窗口，也就是由小到大逐渐增大拥塞窗口数值。cwnd初始值为1，每经过一个传播轮次，cwnd加倍。
- 拥塞避免： 拥塞避免算法的思路是让拥塞窗口cwnd缓慢增大，即每经过一个往返时间RTT就把发送放的cwnd加1.
- 快重传与快恢复： 在 TCP/IP 中，快速重传和恢复（fast retransmit and recovery，FRR）是一种拥塞控制算法，它能快速恢复丢失的数据包。没有 FRR，如果数据包丢失了，TCP 将会使用定时器来要求传输暂停。在暂停的这段时间内，没有新的或复制的数据包被发送。有了 FRR，如果接收机接收到一个不按顺序的数据段，它会立即给发送机发送一个重复确认。如果发送机接收到三个重复确认，它会假定确认件指出的数据段丢失了，并立即重传这些丢失的数据段。有了 FRR，就不会因为重传时要求的暂停被耽误。 　当有单独的数据包丢失时，快速重传和恢复（FRR）能最有效地工作。当有多个数据信息包在某一段很短的时间内丢失时，它则不能很有效地工作。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 守护、僵尸、孤儿进程的概念
守护进程：运行在后台的一种特殊进程，独立于控制终端并周期性地执行某些任务。

僵尸进程：一个进程 fork 子进程，子进程退出，而父进程没有wait/waitpid子进程，那么子进程的进程描述符仍保存在系统中，这样的进程称为僵尸进程。

孤儿进程：一个父进程退出，而它的一个或多个子进程还在运行，这些子进程称为孤儿进程。（孤儿进程将由 init 进程收养并对它们完成状态收集工作）


*** 
## ⭐️⭐️⭐️⭐️⭐️
## 系统调用与库函数的区别
系统调用(System call)是程序向系统内核请求服务的方式。可以包括硬件相关的服务(例如，访问硬盘等)，或者创建新进程，调度其他进程等。系统调用是程序和操作系统之间的重要接口。

库函数：把一些常用的函数编写完放到一个文件里，编写应用程序时调用，这是由第三方提供的，发生在用户地址空间。

在移植性方面，不同操作系统的系统调用一般是不同的，移植性差；而在所有的ANSI C编译器版本中，C库函数是相同的。

在调用开销方面，系统调用需要在用户空间和内核环境间切换，开销较大；而库函数调用属于“过程调用”，开销较小。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 内部碎片与外部碎片分别是什么？
在内存管理中，内部碎片是已经被分配出去的的内存空间大于请求所需的内存空间。

外部碎片是指还没有分配出去，但是由于大小太小而无法分配给申请空间的新进程的内存空间空闲块。

固定分区存在内部碎片，可变式分区分配会存在外部碎片；

页式虚拟存储系统存在内部碎片；段式虚拟存储系统，存在外部碎片

为了有效的利用内存，使内存产生更少的碎片，要对内存分页，内存以页为单位来使用，最后一页往往装不满，于是形成了内部碎片。

为了共享要分段，在段的换入换出时形成外部碎片，比如5K的段换出后，有一个4k的段进来放到原来5k的地方，于是形成1k的外部碎片。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 用户态和核心态(内核态）之间的区别是什么呢？
权限不一样。

用户态的进程能存取它们自己的指令和数据，但不能存取内核指令和数据（或其他进程的指令和数据）。

核心态下的进程能够存取内核和用户地址某些机器指令是特权指令，在用户态下执行特权指令会引起错误。在系统中内核并不是作为一个与用户进程平行的估计的进程的集合。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 用户态切换到内核态的方式有哪些？
系统调用：程序的执行一般是在用户态下执行的，但当程序需要使用操作系统提供的服务时，比如说打开某一设备、创建文件、读写文件（这些均属于系统调用）等，就需要向操作系统发出调用服务的请求，这就是系统调用。

异常：当CPU在执行运行在用户态下的程序时，发生了某些事先不可知的异常，这时会触发由当前运行进程切换到处理此异常的内核相关程序中，也就转到了内核态，比如缺页异常。

外围设备的中断：当外围设备完成用户请求的操作后，会向CPU发出相应的中断信号，这时CPU会暂停执行下一条即将要执行的指令转而去执行与中断信号对应的处理程序，如果先前执行的指令是用户态下的程序，那么这个转换的过程自然也就发生了由用户态到内核态的切换。比如硬盘读写操作完成，系统会切换到硬盘读写的中断处理程序中执行后续操作等。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 中断与系统调用了解吗？
所谓的中断就是在计算机执行程序的过程中，由于出现了某些特殊事情，使得CPU暂停对程序的执行，转而去执行处理这一事件的程序。等这些特殊事情处理完之后再回去执行之前的程序。中断一般分为三类：

由计算机硬件异常或故障引起的中断，称为内部异常中断；

由程序中执行了引起中断的指令而造成的中断，称为软中断（这也是和我们将要说明的系统调用相关的中断）；

由外部设备请求引起的中断，称为外部中断。简单来说，对中断的理解就是对一些特殊事情的处理。

与中断紧密相连的一个概念就是中断处理程序了。当中断发生的时候，系统需要去对中断进行处理，对这些中断的处理是由操作系统内核中的特定函数进行的，这些处理中断的特定的函数就是我们所说的中断处理程序了。

另一个与中断紧密相连的概念就是中断的优先级。中断的优先级说明的是当一个中断正在被处理的时候，处理器能接受的中断的级别。中断的优先级也表明了中断需要被处理的紧急程度。每个中断都有一个对应的优先级，当处理器在处理某一中断的时候，只有比这个中断优先级高的中断可以被处理器接受并且被处理。优先级比这个当前正在被处理的中断优先级要低的中断将会被忽略。

典型的中断优先级如下所示：
机器错误 > 时钟 > 磁盘 > 网络设备 > 终端 > 软件中断


在讲系统调用之前，先说下进程的执行在系统上的两个级别：用户级和核心级，也称为用户态和系统态(user mode and kernel mode)。
用户空间就是用户进程所在的内存区域，相对的，系统空间就是操作系统占据的内存区域。用户进程和系统进程的所有数据都在内存中。处于用户态的程序只能访问用户空间，而处于内核态的程序可以访问用户空间和内核空间。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 页面置换算法了解多少？
操作系统将内存按照页面进行管理，在需要的时候才把进程相应的部分调入内存。当产生缺页中断时，需要选择一个页面写入。如果要换出的页面在内存中被修改过，变成了“脏”页面，那就需要先写会到磁盘。页面置换算法，就是要选出最合适的一个页面，使得置换的效率最高。页面置换算法有很多，简单介绍几个，重点介绍比较重要的LRU及其实现算法。

一、最优页面置换算法

最理想的状态下，我们给页面做个标记，挑选一个最远才会被再次用到的页面调出。当然，这样的算法不可能实现，因为不确定一个页面在何时会被用到。

二、先进先出页面置换算法（FIFO）及其改进

这种算法的思想和队列是一样的，该算法总是淘汰最先进入内存的页面，即选择在内存中驻留时间最久的页面予淘汰。实现：把一个进程已调入内存的页面按先后次序链接成一个队列，并且设置一个指针总是指向最老的页面。缺点：对于有些经常被访问的页面如含有全局变量、常用函数、例程等的页面，不能保证这些不被淘汰。

三、最近最少使用页面置换算法LRU（Least Recently Used）

根据页面调入内存后的使用情况做出决策。LRU置换算法是选择最近最久未使用的页面进行淘汰。

1.为每个在内存中的页面配置一个移位寄存器。（P165）定时信号将每隔一段时间将寄存器右移一位。最小数值的寄存器对应页面就是最久未使用页面。

2.利用一个特殊的栈保存当前使用的各个页面的页面号。每当进程访问某页面时，便将该页面的页面号从栈中移出，将它压入栈顶。因此，栈顶永远是最新被访问的页面号，栈底是最近最久未被访问的页面号。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说下对虚拟内存的理解
定义：具有请求调入功能和置换功能，能从逻辑上对内存容量加以扩充得一种存储器系统。其逻辑容量由内存之和和外存之和决定。

与传统存储器比较虚拟存储器有以下三个主要特征：
多次性，是指无需在作业运行时一次性地全部装入内存，而是允许被分成多次调入内存运行。
对换性，是指无需在作业运行时一直常驻内存，而是允许在作业的运行过程中，进行换进和换出。
虚拟性，是指从逻辑上扩充内存的容量，使用户所看到的内存容量，远大于实际的内存容量。

虚拟内存的实现有以下两种方式：
请求分页存储管理。
请求分段存储管理。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 动态链接库与静态链接库的区别
静态库
静态库是一个外部函数与变量的集合体。静态库的文件内容，通常包含一堆程序员自定的变量与函数，其内容不像动态链接库那么复杂，在编译期间由编译器与链接器将它集成至应用程序内，并制作成目标文件以及可以独立运作的可执行文件。而这个可执行文件与编译可执行文件的程序，都是一种程序的静态创建（static build）。

动态库
静态库很方便，但是如果我们只是想用库中的某一个函数，却仍然得把所有的内容都链接进去。一个更现代的方法则是使用共享库，避免了在文件中静态库的大量重复。
动态链接可以在首次载入的时候执行(load-time linking)，这是 Linux 的标准做法，会由动态链接器ld-linux.so 完成，比方标准 C 库(libc.so) 通常就是动态链接的，这样所有的程序可以共享同一个库，而不用分别进行封装。
动态链接也可以在程序开始执行的时候完成(run-time linking)，在 Linux 中使用 dlopen()接口来完成（会使用函数指针），通常用于分布式软件，高性能服务器上。而且共享库也可以在多个进程间共享。
链接使得我们可以用多个对象文件构造我们的程序。可以在程序的不同阶段进行（编译、载入、运行期间均可），理解链接可以帮助我们避免遇到奇怪的错误。

区别：
使用静态库的时候，静态链接库要参与编译，在生成执行文件之前的链接过程中，要将静态链接库的全部指令直接链接入可执行文件中。而动态库提供了一种方法，使进程可以调用不属于其可执行代码的函数。函数的可执行代码位于一个.dll文件中，该dll包含一个或多个已被编译，链接并与使用它们的进程分开储存的函数。
静态库中不能再包含其他动态库或静态库，而在动态库中还可以再包含其他动态或者静态库。
静态库在编译的时候，就将库函数装在到程序中去了，而动态库函数必须在运行的时候才被装载，所以使用静态库速度快一些。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 介绍一下内存池、进程池、线程池
首先介绍一个概念“池化技术 ”。池化技术就是：提前保存大量的资源，以备不时之需以及重复使用。池化技术应用广泛，如内存池，线程池，连接池等等。内存池相关的内容，建议看看Apache、Nginx等开源web服务器的内存池实现。
由于在实际应用当做，分配内存、创建进程、线程都会设计到一些系统调用，系统调用需要导致程序从用户态切换到内核态，是非常耗时的操作。因此，当程序中需要频繁的进行内存申请释放，进程、线程创建销毁等操作时，通常会使用内存池、进程池、线程池技术来提升程序的性能。

线程池：线程池的原理很简单，类似于操作系统中的缓冲区的概念，它的流程如下：先启动若干数量的线程，并让这些线程都处于睡眠状态，当需要一个开辟一个线程去做具体的工作时，就会唤醒线程池中的某一个睡眠线程，让它去做具体工作，当工作完成后，线程又处于睡眠状态，而不是将线程销毁。

进程池与线程池同理。

内存池：内存池是指程序预先从操作系统申请一块足够大内存，此后，当程序中需要申请内存的时候，不是直接向操作系统申请，而是直接从内存池中获取；同理，当程序释放内存的时候，并不真正将内存返回给操作系统，而是返回内存池。当程序退出(或者特定时间)时，内存池才将之前申请的内存真正释放。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是临界资源
在操作系统中，进程是占有资源的最小单位（线程可以访问其所在进程内的所有资源，但线程本身并不占有资源或仅仅占有一点必须资源）。但对于某些资源来说，其在同一时间只能被一个进程所占用。这些一次只能被一个进程所占用的资源就是所谓的临界资源。典型的临界资源比如物理上的打印机，或是存在硬盘或内存中被多个进程所共享的一些变量和数据等(如果这类资源不被看成临界资源加以保护，那么很有可能造成丢数据的问题)。

对于临界资源的访问，必须是互斥进行。也就是当临界资源被占用时，另一个申请临界资源的进程会被阻塞，直到其所申请的临界资源被释放。而进程内访问临界资源的代码被成为临界区。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何处理死锁问题
忽略该问题。例如鸵鸟算法，该算法可以应用在极少发生死锁的的情况下。为什么叫鸵鸟算法呢，因为传说中鸵鸟看到危险就把头埋在地底下，可能鸵鸟觉得看不到危险也就没危险了吧。跟掩耳盗铃有点像。

检测死锁并且恢复。

仔细地对资源进行动态分配，使系统始终处于安全状态以避免死锁。

通过破除死锁四个必要条件之一，来防止死锁产生。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 死锁出现的条件？
定义:如果一组进程中的每一个进程都在等待仅由该组进程中的其他进程才能引发的事件,那么该组进程就是死锁的。或者在两个或多个并发进程中，如果每个进程持有某种资源而又都等待别的进程释放它或它们现在保持着的资源，在未改变这种状态之前都不能向前推进，称这一组进程产生了死锁。通俗地讲，就是两个或多个进程被无限期地阻塞、相互等待的一种状态。

产生死锁的必要条件：
互斥条件(Mutual exclusion)：资源不能被共享，只能由一个进程使用。
请求与保持条件(Hold and wait)：已经得到资源的进程可以再次申请新的资源。
非抢占条件(No pre-emption)：已经分配的资源不能从相应的进程中被强制地剥夺。
循环等待条件(Circular wait)：系统中若干进程组成环路，该环路中每个进程都在等待相邻进程正占用的资源。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 一个程序从开始运行到结束的完整过程（四个过程）
预处理：条件编译，头文件包含，宏替换的处理，生成.i文件。

编译：将预处理后的文件转换成汇编语言，生成.s文件

汇编：汇编变为目标代码(机器代码)生成.o的文件

链接：连接目标代码,生成可执行程序

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说下你知道的调度算法
FIFO或First Come, First Served (FCFS)先来先服务
调度的顺序就是任务到达就绪队列的顺序
公平、简单(FIFO队列)、非抢占、不适合交互式
未考虑任务特性，平均等待时间可以缩短

Shortest Job First (SJF)
最短的作业(CPU区间长度最小)最先调度
SJF可以保证最小的平均等待时间

Shortest Remaining Job First (SRJF)
SJF的可抢占版本，比SJF更有优势
SJF(SRJF): 如何知道下一CPU区间大小？根据历史进行预测: 指数平均法

优先权调度
每个任务关联一个优先权，调度优先权最高的任务
注意：优先权太低的任务一直就绪，得不到运行，出现“饥饿”现象

Round-Robin(RR)轮转调度算法
设置一个时间片，按时间片来轮转调度（“轮叫”算法）
优点: 定时有响应，等待时间较短；缺点: 上下文切换次数较多
时间片太大，响应时间太长；吞吐量变小，周转时间变长；当时间片过长时，退化为FCFS

多级队列调度
按照一定的规则建立多个进程队列
不同的队列有固定的优先级（高优先级有抢占权）
不同的队列可以给不同的时间片和采用不同的调度方法
存在问题1：没法区分I/O bound和CPU bound
存在问题2：也存在一定程度的“饥饿”现象

多级反馈队列
在多级队列的基础上，任务可以在队列之间移动，更细致的区分任务
可以根据“享用”CPU时间多少来移动队列，阻止“饥饿”
最通用的调度算法，多数OS都使用该方法或其变形，如UNIX、Windows等

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 非抢占式调度与抢占式调度的区别是什么？
非抢占式：分派程序一旦把处理机分配给某进程后便让它一直运行下去，直到进程完成或发生进程调度进程调度某事件而阻塞时，才把处理机分配给另一个进程
抢占式：操作系统将正在运行的进程强行暂停，由调度程序将CPU分配给其他就绪进程的调度方式

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 进程调度的种类有哪些？
高级调度：(High-Level Scheduling)又称为作业调度，它决定把后备作业调入内存运行
低级调度：(Low-Level Scheduling)又称为进程调度，它决定把就绪队列的某进程获得CPU
中级调度：(Intermediate-Level Scheduling)又称为在虚拟存储器中引入，在内、外存对换区进行进程对换

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 进程的通信方式有哪些
进程通信，是指进程之间的信息交换（信息量少则一个状态或数值，多者则是成千上万个字节）。因此，对于用信号量进行的进程间的互斥和同步，由于其所交换的信息量少而被归结为低级通信

所谓高级进程通信指：用户可以利用操作系统所提供的一组通信命令传送大量数据的一种通信方式。操作系统隐藏了进程通信的实现细节。或者说，通信过程对用户是透明的

高级通信机制可归结为三大类：
共享存储器系统（存储器中划分的共享存储区）；实际操作中对应的是“剪贴板”（剪贴板实际上是系统维护管理的一块内存区域）的通信方式，比如举例如下：word进程按下ctrl+c，在ppt进程按下ctrl+v，即完成了word进程和ppt进程之间的通信，复制时将数据放入到剪贴板，粘贴时从剪贴板中取出数据，然后显示在ppt窗口上
消息传递系统（进程间的数据交换以消息（message）为单位，当今最流行的微内核操作系统中，微内核与服务器之间的通信，无一例外地都采用了消息传递机制。应用举例：邮槽（MailSlot）是基于广播通信体系设计出来的，它采用无连接的不可靠的数据传输。邮槽是一种单向通信机制，创建邮槽的服务器进程读取数据，打开邮槽的客户机进程写入数据
管道通信系统（管道即：连接读写进程以实现他们之间通信的共享文件（pipe文件，类似先进先出的队列，由一个进程写，另一进程读））。实际操作中，管道分为：匿名管道、命名管道。匿名管道是一个未命名的、单向管道，通过父进程和一个子进程之间传输数据。匿名管道只能实现本地机器上两个进程之间的通信，而不能实现跨网络的通信。命名管道不仅可以在本机上实现两个进程间的通信，还可以跨网络实现两个进程间的通信
管道：管道是单向的、先进先出的、无结构的、固定大小的字节流，它把一个进程的标准输出和另一个进程的标准输入连接在一起。写进程在管道的尾端写入数据，读进程在管道的道端读出数据。数据读出后将从管道中移走，其它读进程都不能再读到这些数据。管道提供了简单的流控制机制。进程试图读空管道时，在有数据写入管道前，进程将一直阻塞。同样地，管道已经满时，进程再试图写管道，在其它进程从管道中移走数据之前，写进程将一直阻塞。
信号量：信号量是一个计数器，可以用来控制多个进程对共享资源的访问。它常作为一种锁机制，防止某进程正在访问共享资源时，其它进程也访问该资源。因此，主要作为进程间以及同一进程内不同线程之间的同步手段
消息队列：是一个在系统内核中用来保存消 息的队列，它在系统内核中是以消息链表的形式出现的。消息队列克服了信号传递信息少、管道只能承载无格式字节流以及缓冲区大小受限等缺点
共享内存：共享内存允许两个或多个进程访问同一个逻辑内存。这一段内存可以被两个或两个以上的进程映射至自身的地址空间中，一个进程写入共享内存的信息，可以被其他使用这个共享内存的进程，通过一个简单的内存读取读出，从而实现了进程间的通信。如果某个进程向共享内存写入数据，所做的改动将立即影响到可以访问同一段共享内存的任何其他进程。共享内存是最快的IPC方式，它是针对其它进程间通信方式运行效率低而专门设计的。它往往与其它通信机制（如信号量）配合使用，来实现进程间的同步和通信
套接字：套接字也是一种进程间通信机制，与其它通信机制不同的是，它可用于不同机器间的进程通信

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说下你对进程同步的理解
进程同步的主要任务：是对多个相关进程在执行次序上进行协调，以使并发执行的诸进程之间能有效地共享资源和相互合作，从而使程序的执行具有可再现性

同步机制遵循的原则：
空闲让进；
忙则等待（保证对临界区的互斥访问）；
有限等待（有限代表有限的时间，避免死等）；
让权等待（当进程不能进入自己的临界区时，应该释放处理机，以免陷入忙等状态）

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么进程上下文切换比线程上下文切换代价高？
进程切换分两步：
切换页目录以使用新的地址空间
切换内核栈和硬件上下文
对于linux来说，线程和进程的最大区别就在于地址空间，对于线程切换，第1步是不需要做的，第2是进程和线程切换都要做的

切换的性能消耗：
线程上下文切换和进程上下问切换一个最主要的区别是线程的切换虚拟内存空间依然是相同的，但是进程切换是不同的。这两种上下文切换的处理都是通过操作系统内核来完成的。内核的这种切换过程伴随的最显著的性能损耗是将寄存器中的内容切换出
另外一个隐藏的损耗是上下文的切换会扰乱处理器的缓存机制。简单的说，一旦去切换上下文，处理器中所有已经缓存的内存地址一瞬间都作废了。还有一个显著的区别是当你改变虚拟内存空间的时候，处理的页表缓冲（processor's Translation Lookaside Buffer (TLB)）或者相当的神马东西会被全部刷新，这将导致内存的访问在一段时间内相当的低效。但是在线程的切换中，不会出现这个问题

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说下进程和线程的联系与区别
进程是具有一定独立功能的程序关于某个数据集合上的一次运行活动，进程是系统进行资源分配和调度的一个独立单位
线程是进程的一个实体，是CPU调度和分派的基本单位，它是比进程更小的能独立运行的基本单位

进程和线程的关系
一个线程只能属于一个进程，而一个进程可以有多个线程，但至少有一个线程。线程是操作系统可识别的最小执行和调度单位
资源分配给进程，同一进程的所有线程共享该进程的所有资源。 同一进程中的多个线程共享代码段(代码和常量)，数据段(全局变量和静态变量)，扩展段(堆存储)。但是每个线程拥有自己的栈段，栈段又叫运行时段，用来存放所有局部变量和临时变量
处理机分给线程，即真正在处理机上运行的是线程
线程在执行过程中，需要协作同步。不同进程的线程间要利用消息通信的办法实现同步

进程与线程的区别
进程有自己的独立地址空间，线程没有
进程是资源分配的最小单位，线程是CPU调度的最小单位
进程和线程通信方式不同(线程之间的通信比较方便。同一进程下的线程共享数据（比如全局变量，静态变量），通过这些数据来通信不仅快捷而且方便，当然如何处理好这些访问的同步与互斥正是编写多线程程序的难点。而进程之间的通信只能通过进程通信的方式进行。)
进程上下文切换开销大，线程开销小
一个进程挂掉了不会影响其他进程，而线程挂掉了会影响其他线程
对进程进程操作一般开销都比较大，对线程开销就小了

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis中的管道有什么用？
一次请求/响应服务器能实现处理新的请求即使旧的请求还未被响应。这样就可以将多个命令发送到服务器，而不用等待回复，最后在一个步骤中读取该答复。

这就是管道（pipelining），是一种几十年来广泛使用的技术。例如许多POP3协议已经实现支持这个功能，大大加快了从服务器下载新邮件的过程。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis和Redisson有什么关系？
Redisson是一个高级的分布式协调Redis客服端，能帮助用户在分布式环境中轻松实现一些Java的对象 (Bloom filter, BitSet, Set, SetMultimap, ScoredSortedSet, SortedSet, Map, ConcurrentMap, List, ListMultimap, Queue, BlockingQueue, Deque, BlockingDeque, Semaphore, Lock, ReadWriteLock, AtomicLong, CountDownLatch, Publish / Subscribe, HyperLogLog)。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis有哪些适合的场景？
（1）会话缓存（Session Cache）

最常用的一种使用Redis的情景是会话缓存（session cache）。用Redis缓存会话比其他存储（如Memcached）的优势在于：Redis提供持久化。当维护一个不是严格要求一致性的缓存时，如果用户的购物车信息全部丢失，大部分人都会不高兴的，现在，他们还会这样吗？

幸运的是，随着 Redis 这些年的改进，很容易找到怎么恰当的使用Redis来缓存会话的文档。甚至广为人知的商业平台Magento也提供Redis的插件。

（2）全页缓存（FPC）

除基本的会话token之外，Redis还提供很简便的FPC平台。回到一致性问题，即使重启了Redis实例，因为有磁盘的持久化，用户也不会看到页面加载速度的下降，这是一个极大改进，类似PHP本地FPC。

再次以Magento为例，Magento提供一个插件来使用Redis作为全页缓存后端。

此外，对WordPress的用户来说，Pantheon有一个非常好的插件 wp-redis，这个插件能帮助你以最快速度加载你曾浏览过的页面。

（3）队列

Reids在内存存储引擎领域的一大优点是提供 list 和 set 操作，这使得Redis能作为一个很好的消息队列平台来使用。Redis作为队列使用的操作，就类似于本地程序语言（如Python）对 list 的 push/pop 操作。

如果你快速的在Google中搜索“Redis queues”，你马上就能找到大量的开源项目，这些项目的目的就是利用Redis创建非常好的后端工具，以满足各种队列需求。例如，Celery有一个后台就是使用Redis作为broker，你可以从这里去查看。

（4）排行榜/计数器

Redis在内存中对数字进行递增或递减的操作实现的非常好。集合（Set）和有序集合（Sorted Set）也使得我们在执行这些操作的时候变的非常简单，Redis只是正好提供了这两种数据结构。

所以，我们要从排序集合中获取到排名最靠前的10个用户–我们称之为“user_scores”，我们只需要像下面一样执行即可：

当然，这是假定你是根据你用户的分数做递增的排序。如果你想返回用户及用户的分数，你需要这样执行：

ZRANGE user_scores 0 10 WITHSCORES

Agora Games就是一个很好的例子，用Ruby实现的，它的排行榜就是使用Redis来存储数据的，你可以在这里看到。

（5）发布/订阅

最后（但肯定不是最不重要的）是Redis的发布/订阅功能。发布/订阅的使用场景确实非常多。我已看见人们在社交网络连接中使用，还可作为基于发布/订阅的脚本触发器，甚至用Redis的发布/订阅功能来建立聊天系统！

*** 
## ⭐️⭐️⭐️⭐️⭐️
## MySQL 里有 2000w 数据，redis 中只存 20w 的数据，如何保证 redis 中的数据都是热点数据？
redis 内存数据集大小上升到一定大小的时候，就会施行数据淘汰策略。

其实面试除了考察 Redis，不少公司都很重视高并发高可用的技术，特别是一线互联网公司，分布式、

JVM、spring 源码分析、微服务等知识点已是面试的必考题。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis 集群方案什么情况下会导致整个集群不可用？
有 A，B，C 三个节点的集群,在没有复制模型的情况下,如果节点 B 失败了，那么整个集群就会以为缺少5501-11000 这个范围的槽而不可用。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis 集群方案应该怎么做？都有哪些方案？
- codis
- 目前用的最多的集群方案，基本和 twemproxy 一致的效果，但它支持在节点数量改变情况下，旧节点数据可恢复到新 hash 节点。
- redis cluster3.0 自带的集群，特点在于他的分布式算法不是一致性 hash，而是 hash 槽的概念，以及自身支持节点设置从节点。具体看官方文档介绍。
- 在业务代码层实现，起几个毫无关联的 redis 实例，在代码层，对 key 进行 hash 计算，然后去对应的redis 实例操作数据。这种方式对 hash 层代码要求比较高，考虑部分包括，节点失效后的替代算法方案，数据震荡后的自动脚本恢复，实例的监控，等等。
- Java 架构学习资料（里面有高可用、高并发、高性能及分布式、Jvm 性能调优、Spring 源码，MyBatis，Netty,Redis,Kafka,Mysql,Zookeeper,Tomcat,Docker,Dubbo,Nginx 等多个知识点的架构资料）合理利用自己每一分每一秒的时间来学习提升自己，不要再用"没有时间“来掩饰自己思想上的懒惰！趁年轻，使劲拼，给未来的自己一个交代！

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis String的内部编码有哪些？
int、embstr、raw
10000以下的整数会使用缓存里的int常量。
长度小于等于44字节：embstr编码
长度大于44字节：raw编码

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 用Redis做延时队列，具体应该怎么实现？
可以使用Zset实现。member是任务描述，score是执行时间，然后用定时器定时去扫描，一旦有执行时间小于或等于当前时间的任务，就立即执行。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis在集群种查找key的时候，是怎么定位到具体节点的？
使用crc16算法对key进行hash
将hash值对16384取模，得到具体的槽位
根据节点和槽位的映射信息（与集群建立连接后，客户端可以取得槽位映射信息），找到具体的节点地址
去具体的节点找key
如果key不在这个节点上，则redis集群会返回moved指令，加上新的节点地址给客户端，同时，客户端会刷新本地的节点槽位映射关系
如果槽位正在迁移中，那么redis集群会返回asking指令给客户端，这是临时纠正，客户端不会刷新本地的节点槽位映射关系

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis的持久化了解过吗？
Redis持久化有RDB和AOF这2种方式。
RDB：将数据库快照以二进制的方式保存到磁盘中。
AOF：以协议文本方式，将所有对数据库进行过写入的命令和参数记录到AOF文件，从而记录数据库状态。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis在什么情况下会触发key的回收？
2种情况：1、定时（抽样）清理；2、执行命令时，判断内存是否超过maxmemory。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis key的淘汰策略有哪些？
8种：noeviction，volatile-lru，volatile-lfu，volatile-ttl，volatile-random，allkey-lru，allkeys-lfu，allkeys-random

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis事务机制了解过吗？
Redis事务的概念：
Redis 事务的本质是一组命令的集合。事务支持一次执行多个命令，一个事务中所有命令都会被序列化。在事务执行过程，会按照顺序串行化执行队列中的命令，其他客户端提交的命令请求不会插入到事务执行命令序列中。
Redis事务就是一次性、顺序性、排他性的执行一个队列中的一系列命令。　　

Redis事务没有隔离级别的概念：
批量操作在发送 EXEC 命令前被放入队列缓存，并不会被实际执行，也就不存在事务内的查询要看到事务里的更新，事务外查询不能看到。
Redis不保证原子性：
Redis中，单条命令是原子性执行的，但事务不保证原子性，且没有回滚。事务中任意命令执行失败，其余的命令仍会被执行。

Redis事务的三个阶段：
开始事务
命令入队
执行事务

Redis事务相关命令：
watch key1 key2 ... : 监视一或多个key,如果在事务执行之前，被监视的key被其他命令改动，则事务被打断 （ 类似乐观锁 ）
multi : 标记一个事务块的开始（ queued ）
exec : 执行所有事务块的命令 （ 一旦执行exec后，之前加的监控锁都会被取消掉 ）　
discard : 取消事务，放弃事务块中的所有命令
unwatch : 取消watch对所有key的监控

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 使用Redis统计网站的UV，应该怎么做？
UV与PV不同，UV需要去重。一般有2种方案：
1、用BitMap。存的是用户的uid，计算UV的时候，做下bitcount就行了。
2、用布隆过滤器。将每次访问的用户uid都放到布隆过滤器中。优点是省内存，缺点是无法得到精确的UV。但是对于不需要精确知道具体UV，只需要大概的数量级的场景，是个不错的选择。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis中的大key怎么处理？
大key指的是value特别大的key。比如很长的字符串，或者很大的set等等。
大key会造成2个问题：1、数据倾斜，比如某些节点内存占用过高。2、当删除大key或者大key自动过期的时候，会造成QPS突降，因为Redis是单线程的缘故。
处理方案：可以将一个大key进行分片处理，比如：将一个大set分成多个小的set。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis中的热key怎么处理？
1、对热key进行分散处理。比如：在key上加上不同的前后缀，缓存多个key，使得各个key分散到不同的节点上。
2、采用多级缓存。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 缓存失效？缓存穿透？缓存雪崩？缓存并发？
1. 缓存失效
   缓存失效指的是大量的缓存在同一时间失效，到时DB的瞬间压力飙升。造成这种现象的原因是，key的过期时间都设置成一样了。解决方案是，key的过期时间引入随机因素，比如5分钟+随机秒这种方式。

2. 缓存穿透
   缓存穿透是指查询一条数据库和缓存都没有的一条数据，就会一直查询数据库，对数据库的访问压力就会增大，缓存穿透的解决方案，有以下2种：
   缓存空对象：代码维护较简单，但是效果不好。
   布隆过滤器：代码维护复杂，效果很好。

3. 缓存雪崩
   缓存雪崩 是指在某一个时间段，缓存集中过期失效。此刻无数的请求直接绕开缓存，直接请求数据库。
   造成缓存雪崩的原因，有以下2种：
   reids宕机。
   大部分数据失效。

对于缓存雪崩的解决方案有以下2种：
搭建高可用的集群，防止单机的redis宕机。
设置不同的过期时间，防止同意之间内大量的key失效。

4. 缓存并发
   有时候如果网站并发访问高，一个缓存如果失效，可能出现多个进程同时查询DB，同时设置缓存的情况，如果并发确实很大，这也可能造成DB压力过大，还有缓存频繁更新的问题。
   一般处理方案是在查DB的时候进行加锁，如果KEY不存在，就加锁，然后查DB入缓存，然后解锁；其他进程如果发现有锁就等待，然后等解锁后再查缓存或者进入DB查询。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis集群如何选择数据库？
Redis集群目前无法做数据库选择，默认在0数据库。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis如何设置密码及验证密码？
设置密码：config set requirepass 123456

授权密码：auth 123456

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么 Redis 需要把所有数据放到内存中？
Redis 为了达到最快的读写速度将数据都读到内存中，并通过异步的方式将数据写入磁盘。

所以 redis 具有快速和数据持久化的特征，如果不将数据放在内存中，磁盘 I/O 速度为严重影响 redis 的性能。

在内存越来越便宜的今天，redis 将会越来越受欢迎， 如果设置了最大使用的内存，则数据已有记录数达到内存限值后不能继续插入新值。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis 官方为什么不提供 Windows 版本？
因为目前 Linux 版本已经相当稳定，而且用户量很大，无需开发 windows 版本，反而会带来兼容性等问题。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis是单线程还是多线程？
Redis6.0采用多线程IO，不过命令的执行还是单线程的。
Redis6.0之前，IO线程和执行线程都是单线程的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis为什么那么快？
1、内存操作；
2、单线程，省去线程切换、锁竞争的开销；
3、非阻塞IO模型，epoll。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 一个字符串类型的值能存储最大容量是多少？
512M

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis的全称是什么？
Remote Dictionary Server。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis主要消耗什么物理资源？
内存。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis相比memcached有哪些优势？
(1) memcached所有的值均是简单的字符串，redis作为其替代者，支持更为丰富的数据类型

(2) redis的速度比memcached快很多

(3) redis可以持久化其数据

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Redis？简述它的优缺点？
Redis本质上是一个Key-Value类型的内存数据库，很像memcached，整个数据库统统加载在内存当中进行操作，定期通过异步操作把数据库数据flush到硬盘上进行保存。

因为是纯内存操作，Redis的性能非常出色，每秒可以处理超过 10万次读写操作，是已知性能最快的Key-Value DB。

Redis的出色之处不仅仅是性能，Redis最大的魅力是支持保存多种数据结构，此外单个value的最大限制是1GB，不像 memcached只能保存1MB的数据，因此Redis可以用来实现很多有用的功能。

比方说用他的List来做FIFO双向链表，实现一个轻量级的高性 能消息队列服务，用他的Set可以做高性能的tag系统等等。

另外Redis也可以对存入的Key-Value设置expire时间，因此也可以被当作一 个功能加强版的memcached来用。 Redis的主要缺点是数据库容量受到物理内存的限制，不能用作海量数据的高性能读写，因此Redis适合的场景主要局限在较小数据量的高性能操作和运算上。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Mysql如何优化DISTINCT?
DISTINCT在所有列上转换为GROUP BY，并与ORDER BY子句结合使用。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 自增主键最大ID记录，MyISAM和InnoDB分别是如何存储的
- MyISAM表把自增主键的最大ID记录到数据文件里
- InnoDB表把自增主键的最大ID记录到内存中

*** 
## ⭐️⭐️⭐️⭐️⭐️
## MySQL主从复制原理流程
- 主：binlog线程——记录下所有改变了数据库数据的语句，放进master上的binlog中；
- 从：io线程——在使用start slave 之后，负责从master上拉取 binlog 内容，放进 自己的relay log中；
- 从：sql执行线程——执行relay log中的语句；

*** 
## ⭐️⭐️⭐️⭐️⭐️
## delete、truncate、drop区别
- truncate和delete只删除数据，不删除表结构 ,drop删除表结构，并且释放所占的空间。
- 删除数据的速度，drop> truncate > delete
- delete属于DML语言，需要事务管理，commit之后才能生效。drop和truncate属于DDL语言，操作立刻生效，不可回滚。使用场合： 当你不再需要该表时， 用 drop; 当你仍要保留该表，但要删除所有记录时， 用 truncate; 当你要删除部分记录时（always with a where clause), 用 delete。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## key和index的区别
1. key 是数据库的物理结构，它包含两层意义和作用，一是约束（偏重于约束和规范数据库的结构完整性），二是索引（辅助查询用的）。包括primary key, unique key, foreign key 等
2. index是数据库的物理结构，它只是辅助查询的，它创建时会在另外的表空间（mysql中的innodb表空间）以一个类似目录的结构存储。索引要分类的话，分为前缀索引、全文本索引等；

*** 
## ⭐️⭐️⭐️⭐️⭐️
## MySQL优化
1. 开启查询缓存，优化查询

2. explain你的select查询，这可以帮你分析你的查询语句或是表结构的性能瓶颈。EXPLAIN 的查询结果还会告诉你你的索引主键被如何利用的，你的数据表是如何被搜索和排序的

3. 当只要一行数据时使用limit 1，MySQL数据库引擎会在找到一条数据后停止搜索，而不是继续往后查少下一条符合记录的数据

4. 为搜索字段建索引

5. 使用 ENUM 而不是 VARCHAR。如果你有一个字段，比如“性别”，“国家”，“民族”，“状态”或“部门”，你知道这些字段的取值是有限而且固定的，那么，你应该使用 ENUM 而不是VARCHAR

6. Prepared StatementsPrepared Statements很像存储过程，是一种运行在后台的SQL语句集合，我们可以从使用 prepared statements 获得很多好处，无论是性能问题还是安全问题。

   Prepared Statements 可以检查一些你绑定好的变量，这样可以保护你的程序不会受到“SQL注入式”攻击

7. 垂直分表

8. 选择正确的存储引擎

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 行级锁定的缺点
1. 比页级或表级锁定占用更多的内存。
2. 当在表的大部分中使用时，比页级或表级锁定速度慢，因为你必须获取更多的锁。
3. 如果你在大部分数据上经常进行GROUP BY操作或者必须经常扫描整个表，比其它锁定明显慢很多。
4. 用高级别锁定，通过支持不同的类型锁定，你也可以很容易地调节应用程序，因为其锁成本小于行级锁定。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 行级锁定的优点
1、当在许多线程中访问不同的行时只存在少量锁定冲突。

2、回滚时只有少量的更改

3、可以长时间锁定单一的行。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在哪些情况下会发生针对该列创建了索引但是在查询的时候并没有使用呢?
- 使用不等于查询,
- 列参与了数学运算或者函数
- 在字符串like时左边是通配符.类似于'%aaa'.
- 当mysql分析全表扫描比使用索引快的时候不使用索引.
- 当使用联合索引,前面一个条件为范围查询,后面的即使符合最左前缀原则,也无法使用索引.

以上情况,MySQL无法使用索引.

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在MVCC并发控制中，读操作可以分成哪几类？
1. 快照读 (snapshot read)：读取的是记录的可见版本 (有可能是历史版本)，不用加锁（共享读锁s锁也不加，所以不会阻塞其他事务的写）
2. 当前读 (current read)：读取的是记录的最新版本，并且，当前读返回的记录，都会加上锁，保证其他事务不会再并发修改这条记录

*** 
## ⭐️⭐️⭐️⭐️⭐️
## MVVC了解过吗
MySQL InnoDB存储引擎，实现的是基于多版本的并发控制协议——MVCC (Multi-Version Concurrency Control) 

注：与MVCC相对的，是基于锁的并发控制，Lock-Based Concurrency Control

MVCC最大的好处：读不加锁，读写不冲突。在读多写少的OLTP应用中，读写不冲突是非常重要的，极大的增加了系统的并发性能，现阶段几乎所有的RDBMS，都支持了MVCC。

1. LBCC：Lock-Based Concurrency Control，基于锁的并发控制

2. MVCC：Multi-Version Concurrency Control

   基于多版本的并发控制协议。纯粹基于锁的并发机制并发量低，MVCC是在基于锁的并发控制上的改进，主要是在读操作上提高了并发量。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 表分区有什么好处？
1、存储更多数据。分区表的数据可以分布在不同的物理设备上，从而高效地利用多个硬件设备。和单个磁盘或者文件系统相比，可以存储更多数据

2、优化查询。在where语句中包含分区条件时，可以只扫描一个或多个分区表来提高查询效率；涉及sum和count语句时，也可以在多个分区上并行处理，最后汇总结果。

3、分区表更容易维护。例如：想批量删除大量数据可以清除整个分区。

4、避免某些特殊的瓶颈，例如InnoDB的单个索引的互斥访问，ext3问价你系统的inode锁竞争等。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 表分区与分表的区别
分表：指的是通过一定规则，将一张表分解成多张不同的表。比如将用户订单记录根据时间成多个表。

分表与分区的区别在于：分区从逻辑上来讲只有一张表，而分表则是将一张表分解成多张表。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是表分区？
表分区，是指根据一定规则，将数据库中的一张表分解成多个更小的，容易管理的部分。从逻辑上看，只有一张表，但是底层却是由多个物理分区组成。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么情况下应不建或少建索引
1、表记录太少

2、经常插入、删除、修改的表

3、数据重复且分布平均的表字段，假如一个表有10万行记录，有一个字段A只有T和F两种值，且每个值的分布概率大约为50%，那么对这种表A字段建索引一般不会提高数据库的查询速度。

4、经常和主字段一块查询但主字段索引值比较多的表字段

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说一说三个范式
第一范式: 每个列都不可以再拆分. 第二范式: 非主键列完全依赖于主键,而不能是依赖于主键的一部分. 第三范式: 非主键列只依赖于主键,不依赖于其他非主键。

在设计数据库结构的时候,要尽量遵守三范式,如果不遵守,必须有足够的理由.比如性能. 事实上我们经常会为了性能而妥协数据库的设计。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是存储过程？有哪些优缺点？
存储过程是一些预编译的SQL语句。

1、更加直白的理解：存储过程可以说是一个记录集，它是由一些T-SQL语句组成的代码块，这些T-SQL语句代码像一个方法一样实现一些功能（对单表或多表的增删改查），然后再给这个代码块取一个名字，在用到这个功能的时候调用他就行了。

2、存储过程是一个预编译的代码块，执行效率比较高,一个存储过程替代大量T_SQL语句 ，可以降低网络通信量，提高通信速率,可以一定程度上确保数据安全

但是,在互联网项目中,其实是不太推荐存储过程的,比较出名的就是阿里的《Java开发手册》中禁止使用存储过程,我个人的理解是,在互联网项目中,迭代太快,项目的生命周期也比较短,人员流动相比于传统的项目也更加频繁,在这样的情况下,存储过程的管理确实是没有那么方便,同时,复用性也没有写在服务层那么好。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 关心过业务系统里面的sql耗时吗?统计过慢查询吗?对慢查询都怎么优化过?
在业务系统中,除了使用主键进行的查询,其他的我都会在测试库上测试其耗时,慢查询的统计主要由运维在做,会定期将业务中的慢查询反馈给我们。

慢查询的优化首先要搞明白慢的原因是什么? 是查询条件没有命中索引?是load了不需要的数据列?还是数据量太大?

所以优化也是针对这三个方向来的,

- 首先分析语句,看看是否load了额外的数据,可能是查询了多余的行并且抛弃掉了,可能是加载了许多结果中并不需要的列,对语句进行分析以及重写。
- 分析语句的执行计划,然后获得其使用索引的情况,之后修改语句或者修改索引,使得语句可以尽可能的命中索引。
- 如果对语句的优化已经无法进行,可以考虑表中的数据量是否太大,如果是的话可以进行横向或者纵向的分表。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 超大分页怎么处理?
超大的分页一般从两个方向上来解决.

- 数据库层面,这也是我们主要集中关注的(虽然收效没那么大),类似于`select * from table where age > 20 limit 1000000,10`这种查询其实也是有可以优化的余地的. 这条语句需要load1000000数据然后基本上全部丢弃,只取10条当然比较慢. 当时我们可以修改为`select * from table where id in (select id from table where age > 20 limit 1000000,10)`.这样虽然也load了一百万的数据,但是由于索引覆盖,要查询的所有字段都在索引中,所以速度会很快. 同时如果ID连续的好,我们还可以`select * from table where id > 1000000 limit 10`,效率也是不错的,优化的可能性有许多种,但是核心思想都一样,就是减少load的数据.
- 从需求的角度减少这种请求….主要是不做类似的需求(直接跳转到几百万页之后的具体某一页.只允许逐页查看或者按照给定的路线走,这样可预测,可缓存)以及防止ID泄漏且连续被人恶意攻击.

解决超大分页,其实主要是靠缓存,可预测性的提前查到内容,缓存至redis等k-V数据库中,直接返回即可.

在阿里巴巴《Java开发手册》中,对超大分页的解决办法是类似于上面提到的第一种。

![img](https://imgs.itxueyuan.com/990913-20190806091439548-806498135.png)

*** 
## ⭐️⭐️⭐️⭐️⭐️
## MySQL的binlog有有几种录入格式?分别有什么区别?
有三种格式,statement,row和mixed.

- statement模式下,记录单元为语句.即每一个sql造成的影响会记录.由于sql的执行是有上下文的,因此在保存的时候需要保存相关的信息,同时还有一些使用了函数之类的语句无法被记录复制.
- row级别下,记录单元为每一行的改动,基本是可以全部记下来但是由于很多操作,会导致大量行的改动(比如alter table),因此这种模式的文件保存的信息太多,日志量太大.
- mixed. 一种折中的方案,普通操作使用statement记录,当无法使用statement的时候使用row.

此外,新版的MySQL中对row级别也做了一些优化,当表结构发生变化的时候,会记录语句而不是逐行记录。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## varchar(10)和int(10)代表什么含义?
varchar的10代表了申请的空间长度,也是可以存储的数据的最大长度,而int的10只是代表了展示的长度,不足10位以0填充.也就是说,int(1)和int(10)所能存储的数字大小以及占用的空间都是相同的,只是在展示时按照长度展示。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如果要存储用户的密码散列,应该使用什么字段进行存储?
密码散列,盐,用户身份证号等固定长度的字符串应该使用char而不是varchar来存储,这样可以节省空间且提高检索效率。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 字段为什么要求定义为not null?
MySQL官网这样介绍:

> NULL columns require additional space in the rowto record whether their values are NULL. For MyISAM tables, each NULL columntakes one bit extra, rounded up to the nearest byte.

null值会占用更多的字节,且会在程序中造成很多与预期不符的情况。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 主键使用自增ID还是UUID?
推荐使用自增ID,不要使用UUID.

因为在InnoDB存储引擎中,主键索引是作为聚簇索引存在的,也就是说,主键索引的B+树叶子节点上存储了主键索引以及全部的数据(按照顺序),如果主键索引是自增ID,那么只需要不断向后排列即可,如果是UUID,由于到来的ID与原来的大小不确定,会造成非常多的数据插入,数据移动,然后导致产生很多的内存碎片,进而造成插入性能的下降.

总之,在数据量大一些的情况下,用自增主键性能会好一些.

*图片来源于《高性能MySQL》: 其中默认后缀为使用自增ID,_uuid为使用UUID为主键的测试,测试了插入100w行和300w行的性能

![img](https://imgs.itxueyuan.com/990913-20190806091416714-780950030.png)

关于主键是聚簇索引,如果没有主键,InnoDB会选择一个唯一键来作为聚簇索引,如果没有唯一键,会生成一个隐式的主键。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么要尽量设定一个主键?
 主键是数据库确保数据行在整张表唯一性的保障,即使业务上本张表没有主键,也建议添加一个自增长的ID列作为主键.设定了主键之后,在后续的删改查的时候可能更加快速以及确保操作数据范围安全。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## MySQL有哪些日志，分别是什么用处？
mysql日志一般分为5种

- 错误日志：-log-err (记录启动，运行，停止mysql时出现的信息)
- 二进制日志：-log-bin （记录所有更改数据的语句，还用于复制，恢复数据库用）
- 查询日志：-log （记录建立的客户端连接和执行的语句）
- 慢查询日志: -log-slow-queries （记录所有执行超过long_query_time秒的所有查询）
- 更新日志: -log-update （二进制日志已经代替了老的更新日志，更新日志在MySQL5.1中不再使用）

*** 
## ⭐️⭐️⭐️⭐️⭐️
## MySQL中varchar与char的区别以及varchar(50)中的50代表的涵义
(1)、varchar与char的区别
(2)、varchar(50)中50的涵义
(3)、int（20）中20的涵义
(4)、mysql为什么这么设计

*** 
## ⭐️⭐️⭐️⭐️⭐️
## MySQL的redo日志的刷盘时机
log buffer空间不足时
事务提交时
后台线程不停的刷刷刷
正常关闭服务器时
做所谓的checkpoint时

*** 
## ⭐️⭐️⭐️⭐️⭐️
## MySQL的redo日志和undo日志分别有什么用？
1）redo
作用：保证事务的持久性
MySQL作为一个存储系统，为了保证数据的可靠性，最终得落盘。但是，又为了数据写入的速度，需要引入基于内存的"缓冲池"。其实不止MySQL，这种引入缓冲来解决速度问题的思想无处不在。既然数据是先缓存在缓冲池中，然后再以某种方式刷新到磁盘，那么就存在因宕机导致的缓冲池中的数据丢失，为了解决这种情况下的数据丢失问题，引入了redo log。在其他存储系统，比如Elasticsearch中，也有类似的机制，叫translog。
但是一般讨论数据写入时，在MySQL中，一般叫事务操作，根据事务的ACID特性，如何保证一个事务提交后Durability的保证？而这就是 redo log 的作用。当向MySQL写用户数据时，先写redo log，然后redo log根据"某种方式"持久化到磁盘，变成redo log file，用户数据则在"buffer"中(比如数据页、索引页)。如果发生宕机，则读取磁盘上的 redo log file 进行数据的恢复。从这个角度来说，MySQL 事务的持久性是通过 redo log 来实现的。

2）undo
作用：实现事务回滚
Undo log是InnoDB MVCC事务特性的重要组成部分。当我们对记录做了变更操作时就会产生undo记录，Undo记录默认被记录到系统表空间(ibdata)中，但从5.6开始，也可以使用独立的Undo 表空间。
Undo记录中存储的是老版本数据，当一个旧的事务需要读取数据时，为了能读取到老版本的数据，需要顺着undo链找到满足其可见性的记录。当版本链很长时，通常可以认为这是个比较耗时的操作。
大多数对数据的变更操作包括INSERT/DELETE/UPDATE，其中INSERT操作在事务提交前只对当前事务可见，因此产生的Undo日志可以在事务提交后直接删除（谁会对刚插入的数据有可见性需求呢！！），而对于UPDATE/DELETE则需要维护多版本信息，在InnoDB里，UPDATE和DELETE操作产生的Undo日志被归成一类，即update_undo。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么InnoDB一定会生成主键？
因为Innodb的数据结构是通过聚簇索引组织起来的，如果没有主键的话，通过其他索引回表的时候没法查到相应的数据行。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## InnoDB如果没有设置主键的话，它内部会怎么处理？
优先使用用户自定义主键作为主键，如果用户没有定义主键，则选取一个Unique键作为主键，如果表中连Unique键都没有定义的话，则InnoDB会为表默认添加一个名为row_id的隐藏列作为主键。所以我们从上表中可以看出：InnoDB存储引擎会为每条记录都添加 transaction_id 和 roll_pointer 这两个列，但是 row_id 是可选的（在没有自定义主键以及Unique键的情况下才会添加该列）。这些隐藏列的值不用我们操心，InnoDB存储引擎会自己帮我们生成的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## InnoDB删除某条记录后，内部会怎么处理？
记录头信息里的delete_mask标记位设置为1（表示该记录已删除），同时将记录从记录行链表中断开，并加入到垃圾链表中，垃圾链表的空间后续可以复用。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## InnoDB主键索引跟非主键索引在数据存储上的差异
主键索引的叶子节点存的是整行数据。在 InnoDB 里，主键索引也被称为聚簇索引（clustered index）。
非主键索引的叶子节点内容是主键的值。在 InnoDB 里，非主键索引也被称为二级索引（secondary index）。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## InnoDB的数据是怎么存储的？
InnoDB的主键索引文件上直接存放该行数据，称为聚簇索引，非主索引指向对主键的引用。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## MyIsam的数据是怎么存储的？
MyIsam索引的节点中存储的是数据的物理地址（磁道和扇区），在查找数据时，查找到索引后，根据索引节点中的物理地址，查找到具体的数据内容。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## InnoDB有聚簇索引吗？MyIsam呢？
InnoDB有聚簇索引，主键索引就是聚簇索引。MyIsam没有聚簇索引，因为他的索引和记录行是分开存储的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是聚簇索引？
聚簇索引：将数据存储与索引放到了一块，找到索引也就找到了数据
非聚簇索引：将数据与索引分开存储，索引结构的叶子节点指向了数据的对应行

*** 
## ⭐️⭐️⭐️⭐️⭐️
## MySQL索引的类型
聚簇索引、二级（辅助）索引
B树索引、hash索引

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 有了解过“回表”的概念吗？什么情况下会出现“回表”？
回表就是先通过数据库索引扫描出数据所在的行，再通过行主键id取出索引中未提供的数据，即基于非主键索引的查询需要多扫描一棵索引树。
当查询的字段在二级索引上没有的时候，就需要“回表”在主键索引上再查一次。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 事务的隔离级别了解过吗？
1、读未提交（Read Uncommited），该隔离级别允许脏读取，其隔离级别最低；比如事务A和事务B同时进行，事务A在整个执行阶段，会将某数据的值从1开始一直加到10，然后进行事务提交，此时，事务B能够看到这个数据项在事务A操作过程中的所有中间值（如1变成2，2变成3等），而对这一系列的中间值的读取就是未授权读取

2、授权读取也称为已提交读（Read Commited），授权读取只允许获取已经提交的数据。比如事务A和事务B同时进行，事务A进行+1操作，此时，事务B无法看到这个数据项在事务A操作过程中的所有中间值，只能看到最终的10。另外，如果说有一个事务C，和事务A进行非常类似的操作，只是事务C是将数据项从10加到20，此时事务B也同样可以读取到20，即授权读取允许不可重复读取。

3、可重复读（Repeatable Read)

就是保证在事务处理过程中，多次读取同一个数据时，其值都和事务开始时刻是一致的，因此该事务级别禁止不可重复读取和脏读取，但是有可能出现幻影数据。所谓幻影数据，就是指同样的事务操作，在前后两个时间段内执行对同一个数据项的读取，可能出现不一致的结果。在上面的例子中，可重复读取隔离级别能够保证事务B在第一次事务操作过程中，始终对数据项读取到1，但是在下一次事务操作中，即使事务B（注意，事务名字虽然相同，但是指的是另一个事务操作）采用同样的查询方式，就可能读取到10或20；

4、串行化

是最严格的事务隔离级别，它要求所有事务被串行执行，即事务只能一个接一个的进行处理，不能并发执行。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说一下什么是事务的ACID属性吧
1. 原子性（atomicity)
   一个事务要么全部提交成功，要么全部失败回滚，不能只执行其中的一部分操作，这就是事务的原子性

2. 一致性（consistency)
   事务的执行不能破坏数据库数据的完整性和一致性，一个事务在执行之前和执行之后，数据库都必须处于一致性状态。
   如果数据库系统在运行过程中发生故障，有些事务尚未完成就被迫中断，这些未完成的事务对数据库所作的修改有一部分已写入物理数据库，这是数据库就处于一种不正确的状态，也就是不一致的状态

3. 隔离性（isolation）
   事务的隔离性是指在并发环境中，并发的事务时相互隔离的，一个事务的执行不能不被其他事务干扰。不同的事务并发操作相同的数据时，每个事务都有各自完成的数据空间，即一个事务内部的操作及使用的数据对其他并发事务时隔离的，并发执行的各个事务之间不能相互干扰。
   在标准SQL规范中，定义了4个事务隔离级别，不同的隔离级别对事务的处理不同，分别是：未授权读取，授权读取，可重复读取和串行化

4. 持久性（durability）
   一旦事务提交，那么它对数据库中的对应数据的状态的变更就会永久保存到数据库中。--即使发生系统崩溃或机器宕机等故障，只要数据库能够重新启动，那么一定能够将其恢复到事务成功结束的状态

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 了解过哪些存储引擎？各有什么优缺点？
常用的是MyISAM和InnoDB。
InnoDB：支持事务、支持外键、支持行级锁、不支持全文索引、
MyISAM：不支持事务、不支持外键、不支持行级锁、支持全文索引

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在建立索引的时候,都有哪些需要考虑的因素呢?
建立索引的时候一般要考虑到字段的使用频率,经常作为条件进行查询的字段比较适合.如果需要建立联合索引的话,还需要考虑联合索引中的顺序.此外也要考虑其他方面,比如防止过多的所有对表造成太大的压力.这些都和实际的表结构以及查询方式有关。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Hash索引和B+树索引有什么区别或者说优劣呢?
首先要知道Hash索引和B+树索引的底层实现原理:

hash索引底层就是hash表,进行查找时,调用一次hash函数就可以获取到相应的键值,之后进行回表查询获得实际数据.B+树底层实现是多路平衡查找树.对于每一次的查询都是从根节点出发,查找到叶子节点方可以获得所查键值,然后根据查询判断是否需要回表查询数据.

那么可以看出他们有以下的不同:

- hash索引进行等值查询更快(一般情况下),但是却无法进行范围查询.

因为在hash索引中经过hash函数建立索引之后,索引的顺序与原顺序无法保持一致,不能支持范围查询.而B+树的的所有节点皆遵循(左节点小于父节点,右节点大于父节点,多叉树也类似),天然支持范围.

- hash索引不支持使用索引进行排序,原理同上.
- hash索引不支持模糊查询以及多列索引的最左前缀匹配.原理也是因为hash函数的不可预测.AAAA和AAAAB的索引没有相关性.
- hash索引任何时候都避免不了回表查询数据,而B+树在符合某些条件(聚簇索引,覆盖索引等)的时候可以只通过索引完成查询.
- hash索引虽然在等值查询上较快,但是不稳定.性能不可预测,当某个键值存在大量重复的时候,发生hash碰撞,此时效率可能极差.而B+树的查询效率比较稳定,对于所有的查询都是从根节点到叶子节点,且树的高度较低.

因此,在大多数情况下,直接选择B+树索引可以获得稳定且较好的查询速度.而不需要使用hash索引.

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 索引是个什么样的数据结构呢?
索引的数据结构和具体存储引擎的实现有关, 在MySQL中使用较多的索引有Hash索引,B+树索引等,而我们经常使用的InnoDB存储引擎的默认索引实现为:B+树索引。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是索引?
索引是一种数据结构,可以帮助我们快速的进行数据的查找。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 程序计数器为什么是私有的?
程序计数器主要有下面两个作用：

字节码解释器通过改变程序计数器来依次读取指令，从而实现代码的流程控制，如：顺序执行、选择、循环、异常处理。
在多线程的情况下，程序计数器用于记录当前线程执行的位置，从而当线程被切换回来的时候能够知道该线程上次运行到哪儿了。
需要注意的是，如果执行的是 native 方法，那么程序计数器记录的是 undefined 地址，只有执行的是 Java 代码时程序计数器记录的才是下一条指令的地址。

所以，程序计数器私有主要是为了线程切换后能恢复到正确的执行位置。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## JRE、JDK、JVM 及 JIT 之间有什么不同？* JRE 代表 Java 运行时（Java run-time），是运行 Java 引用所必须的。
* JDK 代表 Java 开发工具（Java development kit），是 Java 程序的开发工具，如 Java编译器，它也包含 JRE。
* JVM 代表 Java 虚拟机（Java virtual machine），它的责任是运行 Java 应用。
* JIT 代表即时编译（Just In Time compilation），当代码执行的次数超过一定的阈值时，会将 Java 字节码转换为本地代码，如，主要的热点代码会被准换为本地代码，这样有利大幅度提高 Java 应用的性能。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## JVM调优命令有哪些？
jps，JVM Process Status Tool,显示指定系统内所有的HotSpot虚拟机进程。
jstat，JVM statistics Monitoring是用于监视虚拟机运行时状态信息的命令，它可以显示出虚拟机进程中的类装载、内存、垃圾收集、JIT编译等运行数据。
jmap，JVM Memory Map命令用于生成heap dump文件
jhat，JVM Heap Analysis Tool命令是与jmap搭配使用，用来分析jmap生成的dump，jhat内置了一个微型的HTTP/HTML服务器，生成dump的分析结果后，可以在浏览器中查看
jstack，用于生成java虚拟机当前时刻的线程快照。
jinfo，JVM Conﬁguration info 这个命令作用是实时查看和调整虚拟机运行参数。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说一下 JVM 调优的工具？
常用调优工具分为两类,jdk自带监控工具：jconsole和jvisualvm，第三方有：MAT(Memory AnalyzerTool)、GChisto。

jconsole，Java Monitoring and Management Console是从java5开始，在JDK中自带的java监控和管理控制台，用于对JVM中内存， 线程和类等的监控。
jvisualvm，jdk自带全能工具，可以分析内存快照、线程快照；监控内存变化、GC变化等。
MAT，Memory Analyzer Tool，一个基于Eclipse的内存分析工具，是一个快速、功能丰富的Javaheap分析工具，它可以帮助我们查找内存泄漏和减少内存消耗。
GChisto，一款专业分析gc日志的工具。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 介绍一下类文件结构吧！
魔数: 确定这个文件是否为一个能被虚拟机接收的 Class 文件。
Class 文件版本 ：Class 文件的版本号，保证编译正常执行。
常量池 ：常量池主要存放两大常量：字面量和符号引用。
访问标志 ：标志用于识别一些类或者接口层次的访问信息，包括：这个 Class 是类还是接口，是否为 public 或者 abstract 类型，如果是类的话是否声明为 final 等等。
当前类索引,父类索引 ：类索引用于确定这个类的全限定名，父类索引用于确定这个类的父类的全限定名，由于 Java 语言的单继承，所以父类索引只有一个，除了 java.lang.Object 之外，所有的 java 类都有父类，因此除了 java.lang.Object 外，所有 Java 类的父类索引都不为 0。
接口索引集合 ：接口索引集合用来描述这个类实现了那些接口，这些被实现的接口将按implents(如果这个类本身是接口的话则是extends) 后的接口顺序从左到右排列在接口索引集合中。
字段表集合 ：描述接口或类中声明的变量。字段包括类级变量以及实例变量，但不包括在方法内部声明的局部变量。
方法表集合 ：类中的方法。
属性表集合 ： 在 Class 文件，字段表，方法表中都可以携带自己的属性表集合。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何判断一个类是无用的类?
方法区主要回收的是无用的类，判定一个常量是否是“废弃常量”比较简单，而要判定一个类是否是“无用的类”的条件则相对苛刻许多。类需要同时满足下面3个条件才能算是 “无用的类” ：
该类所有的实例都已经被回收，也就是 Java 堆中不存在该类的任何实例。
加载该类的 ClassLoader 已经被回收。
该类对应的 java.lang.Class 对象没有在任何地方被引用，无法在任何地方通过反射访问该类的方法。

虚拟机可以对满足上述3个条件的无用类进行回收，这里说的仅仅是“可以”，而并不是和对象一样不使用了就会必然被回收。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java会存在内存泄漏吗？请简单描述。
内存泄漏是指不再被使用的对象或者变量一直被占据在内存中。理论上来说，Java是有GC垃圾回收机制的，也就是说，不再被使用的对象，会被GC自动回收掉，自动从内存中清除

但是，即使这样，Java也还是存在着内存泄漏的情况，java导致内存泄露的原因很明确：长生命周期的对象持有短生命周期对象的引用就很可能发生内存泄露，尽管短生命周期对象已经不再需要，但是因为长生命周期对象持有它的引用而导致不能被回收，这就是java中内存泄露的发生场景。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## Minor Gc和Full GC 有什么不同呢？
大多数情况下，对象在新生代中 eden 区分配。当 eden 区没有足够空间进行分配时，虚拟机将发起一次Minor GC。
新生代GC（Minor GC）:指发生新生代的的垃圾收集动作，Minor GC非常频繁，回收速度一般也比较快。
老年代GC（Major GC/Full GC）:指发生在老年代的GC，出现了Major GC经常会伴随至少一次的Minor GC（并非绝对），Major GC的速度一般会比Minor GC的慢10倍以上。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说一下堆内存中对象的分配的基本策略
eden区、s0区、s1区都属于新生代，tentired 区属于老年代。大部分情况，对象都会首先在 Eden 区域分配，在一次新生代垃圾回收后，如果对象还存活，则会进入 s0 或者 s1，并且对象的年龄还会加 1(Eden区->Survivor 区后对象的初始年龄变为1)，当它的年龄增加到一定程度（默认为15岁），就会被晋升到老年代中。对象晋升到老年代的年龄阈值，可以通过参数 -XX:MaxTenuringThreshold 来设置。
另外，大对象和长期存活的对象会直接进入老年代。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 对象的访问定位有哪几种方式?
建立对象就是为了使用对象，我们的Java程序通过栈上的 reference 数据来操作堆上的具体对象。对象的访问方式有虚拟机实现而定，目前主流的访问方式有使用句柄和直接指针2种：

句柄： 如果使用句柄的话，那么Java堆中将会划分出一块内存来作为句柄池，reference 中存储的就是对象的句柄地址，而句柄中包含了对象实例数据与类型数据各自的具体地址信息。

直接指针： 如果使用直接指针访问，那么 Java 堆对象的布局中就必须考虑如何放置访问类型数据的相关信息，而reference 中存储的直接就是对象的地址。

这两种对象访问方式各有优势。使用句柄来访问的最大好处是 reference 中存储的是稳定的句柄地址，在对象被移动时只会改变句柄中的实例数据指针，而 reference 本身不需要修改。使用直接指针访问方式最大的好处就是速度快，它节省了一次指针定位的时间开销。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说一下Java对象的创建过程
1）类加载检查： 虚拟机遇到一条 new 指令时，首先将去检查这个指令的参数是否能在常量池中定位到这个类的符号引用，并且检查这个符号引用代表的类是否已被加载过、解析和初始化过。如果没有，那必须先执行相应的类加载过程。
2）分配内存： 在类加载检查通过后，接下来虚拟机将为新生对象分配内存。对象所需的内存大小在类加载完成后便可确定，为对象分配空间的任务等同于把一块确定大小的内存从 Java 堆中划分出来。分配方式有 “指针碰撞” 和 “空闲列表” 两种，选择那种分配方式由 Java 堆是否规整决定，而Java堆是否规整又由所采用的垃圾收集器是否带有压缩整理功能决定。
选择以上2种方式中的哪一种，取决于 Java 堆内存是否规整。而 Java 堆内存是否规整，取决于 GC 收集器的算法是"标记-清除"，还是"标记-整理"（也称作"标记-压缩"），值得注意的是，复制算法内存也是规整的。

在创建对象的时候有一个很重要的问题，就是线程安全，因为在实际开发过程中，创建对象是很频繁的事情，作为虚拟机来说，必须要保证线程是安全的，通常来讲，虚拟机采用两种方式来保证线程安全：
CAS+失败重试： CAS 是乐观锁的一种实现方式。所谓乐观锁就是，每次不加锁而是假设没有冲突而去完成某项操作，如果因为冲突失败就重试，直到成功为止。虚拟机采用 CAS 配上失败重试的方式保证更新操作的原子性。
TLAB： 为每一个线程预先在Eden区分配一块儿内存，JVM在给线程中的对象分配内存时，首先在TLAB分配，当对象大于TLAB中的剩余内存或TLAB的内存已用尽时，再采用上述的CAS进行内存分配

3）初始化零值： 内存分配完成后，虚拟机需要将分配到的内存空间都初始化为零值（不包括对象头），这一步操作保证了对象的实例字段在 Java 代码中可以不赋初始值就直接使用，程序能访问到这些字段的数据类型所对应的零值。

4）设置对象头： 初始化零值完成之后，虚拟机要对对象进行必要的设置，例如这个对象是那个类的实例、如何才能找到类的元数据信息、对象的哈希吗、对象的 GC 分代年龄等信息。 这些信息存放在对象头中。 另外，根据虚拟机当前运行状态的不同，如是否启用偏向锁等，对象头会有不同的设置方式。

5）执行 init 方法： 在上面工作都完成之后，从虚拟机的视角来看，一个新的对象已经产生了，但从 Java 程序的视角来看，对象创建才刚开始，init 方法还没有执行，所有的字段都还为零。所以一般来说，执行 new 指令之后会接着执行 init 方法，把对象按照程序员的意愿进行初始化，这样一个真正可用的对象才算完全产生出来。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java 8 为什么要将永久代(PermGen)替换为元空间(MetaSpace)呢？
整个永久代有一个 JVM 本身设置固定大小上线，无法进行调整，而元空间使用的是直接内存，受本机可用内存的限制，并且永远不会出现java.lang.OutOfMemoryError。你可以使用 -XX：MaxMetaspaceSize 标志设置最大元空间大小，默认值为 unlimited，这意味着它只受系统内存的限制。-XX：MetaspaceSize 调整标志定义元空间的初始大小如果未指定此标志，则 Metaspace 将根据运行时的应用程序需求动态地重新调整大小。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说一下堆和栈的区别
1）物理地址
堆的物理地址分配对对象是不连续的。因此性能慢些。在GC的时候也要考虑到不连续的分配，所以有各种算法。比如，标记-消除，复制，标记-压缩，分代（即新生代使用复制算法，老年代使用标记——压缩）
栈使用的是数据结构中的栈，先进后出的原则，物理地址分配是连续的。所以性能快。

2）内存分别
堆因为是不连续的，所以分配的内存是在运行期确认的，因此大小不固定。一般堆大小远远大于栈。
栈是连续的，所以分配的内存大小要在编译期就确认，大小是固定的。

3）存放的内容
堆存放的是对象的实例和数组。因此该区更关注的是数据的存储
栈存放：局部变量，操作数栈，返回结果。该区更关注的是程序方法的执行。

4）程序的可见度
堆对于整个应用程序都是共享、可见的。
栈只对于线程是可见的。所以也是线程私有。他的生命周期和线程相同。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 怎么打破双亲委派模型？
打破双亲委派机制则不仅要继承ClassLoader类，还要重写loadClass和findClass方法。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么需要双亲委派模式？
在这里，先想一下，如果没有双亲委派，那么用户是不是可以自己定义一个java.lang.Object的同名类，java.lang.String的同名类，并把它放到ClassPath中,那么类之间的比较结果及类的唯一性将无法保证，因此，为什么需要双亲委派模型？防止内存中出现多份同样的字节码。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 怎么打出线程栈信息？
输入jps，获得进程号。
top -Hp pid 获取本进程中所有线程的CPU耗时性能
jstack pid命令查看当前java进程的堆栈状态
或者 jstack -l > /tmp/output.txt 把堆栈信息打到一个txt文件。
可以使用fastthread 堆栈定位（fastthread.io）

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说说你知道的几种主要的JVM参数1）堆栈配置相关
-Xmx3550m： 最大堆大小为3550m。
-Xms3550m： 设置初始堆大小为3550m。
-Xmn2g： 设置年轻代大小为2g。
-Xss128k： 每个线程的堆栈大小为128k。
-XX:MaxPermSize： 设置持久代大小为16m
-XX:NewRatio=4: 设置年轻代（包括Eden和两个Survivor区）与年老代的比值（除去持久代）。
-XX:SurvivorRatio=4： 设置年轻代中Eden区与Survivor区的大小比值。设置为4，则两个Survivor区与一个Eden区的比值为2:4，一个Survivor区占整个年轻代的1/6
-XX:MaxTenuringThreshold=0： 设置垃圾最大年龄。如果设置为0的话，则年轻代对象不经过Survivor区，直接进入年老代。

2）垃圾收集器相关
-XX:+UseParallelGC： 选择垃圾收集器为并行收集器。
-XX:ParallelGCThreads=20： 配置并行收集器的线程数
-XX:+UseConcMarkSweepGC： 设置年老代为并发收集。
-XX:CMSFullGCsBeforeCompaction：由于并发收集器不对内存空间进行压缩、整理，所以运行一段时间以后会产生“碎片”，使得运行效率降低。此值设置运行多少次GC以后对内存空间进行压缩、整理。
-XX:+UseCMSCompactAtFullCollection： 打开对年老代的压缩。可能会影响性能，但是可以消除碎片

3）辅助信息相关
-XX:+PrintGC 输出形式:
[GC 118250K->113543K(130112K), 0.0094143 secs] [Full GC 121376K->10414K(130112K), 0.0650971 secs]

-XX:+PrintGCDetails 输出形式:
[GC [DefNew: 8614K->781K(9088K), 0.0123035 secs] 118250K->113543K(130112K), 0.0124633 secs] [GC [DefNew: 8614K->8614K(9088K), 0.0000665 secs][Tenured: 112761K->10414K(121024K), 0.0433488 secs] 121376K->10414K(130112K), 0.0436268 secs

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是happen-before原则？
单线程happen-before原则：在同一个线程中，书写在前面的操作happen-before后面的操作。 锁的happen-before原则：同一个锁的unlock操作happen-before此锁的lock操作。
volatile的happen-before原则：对一个volatile变量的写操作happen-before对此变量的任意操作(当然也包括写操作了)。
happen-before的传递性原则：如果A操作 happen-before B操作，B操作happen-before C操作，那么A操作happen-before C操作。
线程启动的happen-before原则：同一个线程的start方法happen-before此线程的其它方法。
线程中断的happen-before原则 ：对线程interrupt方法的调用happen-before被中断线程的检测到中断发送的代码。
线程终结的happen-before原则： 线程中的所有操作都happen-before线程的终止检测。
对象创建的happen-before原则： 一个对象的初始化完成先于他的finalize方法调用。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是内存屏障？
内存屏障，也叫内存栅栏，是一种CPU指令，用于控制特定条件下的重排序和内存可见性问题。
LoadLoad屏障：对于这样的语句Load1; LoadLoad; Load2，在Load2及后续读取操作要读取的数据被访问前，保证Load1要读取的数据被读取完毕。
StoreStore屏障：对于这样的语句Store1; StoreStore; Store2，在Store2及后续写入操作执行前，保证Store1的写入操作对其它处理器可见。
LoadStore屏障：对于这样的语句Load1; LoadStore; Store2，在Store2及后续写入操作被刷出前，保证Load1要读取的数据被读取完毕。
StoreLoad屏障：对于这样的语句Store1; StoreLoad; Load2，在Load2及后续所有读取操作执行前，保证Store1的写入对所有处理器可见。它的开销是四种屏障中最大的。 在大多数处理器的实现中，这个屏障是个万能屏障，兼具其它三种内存屏障的功能。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是指令重排序？
在实际运行时，代码指令可能并不是严格按照代码语句顺序执行的。大多数现代微处理器都会采用将指令乱序执行（out-of-order execution，简称OoOE或OOE）的方法，在条件允许的情况下，直接运行当前有能力立即执行的后续指令，避开获取下一条指令所需数据时造成的等待。通过乱序执行的技术，处理器可以大大提高执行效率。而这就是指令重排。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## JVM中一次完整的GC流程是怎样的，对象如何晋升到老年代？
当 Eden 区的空间满了， Java虚拟机会触发一次 Minor GC，以收集新生代的垃圾，存活下来的对象，则会转移到 Survivor区。
大对象（需要大量连续内存空间的Java对象，如那种很长的字符串）直接进入老年态；
如果对象在Eden出生，并经过第一次Minor GC后仍然存活，并且被Survivor容纳的话，年龄设为1，每熬过一次Minor GC，年龄+1，若年龄超过一定限制（15），则被晋升到老年态。即长期存活的对象进入老年态。
老年代满了而无法容纳更多的对象，Minor GC 之后通常就会进行Full GC，Full GC 清理整个内存堆 – 包括年轻代和年老代。
Major GC 发生在老年代的GC，清理老年区，经常会伴随至少一次Minor GC，比Minor GC慢10倍以上。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## JVM新生代中为什么要分为Eden和Survivor？
如果没有Survivor，Eden区每进行一次Minor GC，存活的对象就会被送到老年代。老年代很快被填满，触发Major GC.老年代的内存空间远大于新生代，进行一次Full GC消耗的时间比Minor GC长得多,所以需要分为Eden和Survivor。
Survivor的存在意义，就是减少被送到老年代的对象，进而减少Full GC的发生，Survivor的预筛选保证，只有经历16次Minor GC还能在新生代中存活的对象，才会被送到老年代。
设置两个Survivor区最大的好处就是解决了碎片化，刚刚新建的对象在Eden中，经历一次Minor GC，Eden中的存活对象就会被移动到第一块survivor space S0，Eden被清空；等Eden区再满了，就再触发一次Minor GC，Eden和S0中的存活对象又会被复制送入第二块survivor space S1（这个过程非常重要，因为这种复制算法保证了S1中来自S0和Eden两部分的存活对象占用连续的内存空间，避免了碎片化的发生）

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么情况下会发生栈内存溢出？
栈是线程私有的，他的生命周期与线程相同，每个方法在执行的时候都会创建一个栈帧，用来存储局部变量表，操作数栈，动态链接，方法出口等信息。局部变量表又包含基本数据类型，对象引用类型。
如果线程请求的栈深度大于虚拟机所允许的最大深度，将抛出StackOverflowError异常，方法递归调用产生这种结果。
如果Java虚拟机栈可以动态扩展，并且扩展的动作已经尝试过，但是无法申请到足够的内存去完成扩展，或者在新建立线程的时候没有足够的内存去创建对应的虚拟机栈，那么Java虚拟机将抛出一个OutOfMemory 异常。(线程启动过多)。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java对象的布局了解过吗？
对象头区域此处存储的信息包括两部分：
1、对象自身的运行时数据( MarkWord )，占8字节
存储 hashCode、GC 分代年龄、锁类型标记、偏向锁线程 ID 、 CAS 锁指向线程 LockRecord 的指针等， synconized 锁的机制与这个部分( markwork )密切相关，用 markword 中最低的三位代表锁的状态，其中一位是偏向锁位，另外两位是普通锁位。
2、对象类型指针( Class Pointer )，占4字节
对象指向它的类元数据的指针、 JVM 就是通过它来确定是哪个 Class 的实例。

实例数据区域 
此处存储的是对象真正有效的信息，比如对象中所有字段的内容

对齐填充区域
JVM 的实现 HostSpot 规定对象的起始地址必须是 8 字节的整数倍，换句话来说，现在 64 位的 OS 往外读取数据的时候一次性读取 64bit 整数倍的数据，也就是 8 个字节，所以 HotSpot 为了高效读取对象，就做了"对齐"，如果一个对象实际占的内存大小不是 8byte 的整数倍时，就"补位"到 8byte 的整数倍。所以对齐填充区域的大小不是固定的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Tomcat是怎么打破双亲委派机制的呢？
是通过重写ClassLoader#loadClass和ClassLoader#findClass 实现的。可以看图中的WebAppClassLoader，它加载自己目录下的.class文件，并不会传递给父类的加载器。但是，它却可以使用 SharedClassLoader 所加载的类，实现了共享和分离的功能。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 双亲委派机制可以被违背吗？请举例说明。
可以被违背。
打破双亲委派的例子：Tomcat

对于一些需要加载的非基础类，会由一个叫作WebAppClassLoader的类加载器优先加载。等它加载不到的时候，再交给上层的ClassLoader进行加载。
这个加载器用来隔绝不同应用的 .class 文件，比如你的两个应用，可能会依赖同一个第三方的不同版本，它们是相互没有影响的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是双亲委派机制？
双亲委派机制的意思是除了顶层的启动类加载器以外，其余的类加载器，在加载之前，都会委派给它的父加载器进行加载。这样一层层向上传递，直到祖先们都无法胜任，它才会真正的加载。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说下有哪些类加载器？
Bootstrap ClassLoader（启动类加载器）
Extention ClassLoader（扩展类加载器）
App ClassLoader（应用类加载器）

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说说类加载的过程
加载
验证
准备（为一些类变量分配内存，并将其初始化为默认值）
解析（将符号引用替换为直接引用。类和接口、类方法、接口方法、字段等解析）
初始化

*** 
## ⭐️⭐️⭐️⭐️⭐️
## ZGC收集器中的染色指针有什么用？
染色指针是一种直接将少量额外的信息存储在指针上的技术，可是为什么指针本身也可以存储额外信息呢？在64位系统中，理论可以访问的内存高达16EB（2的64次幂）字节 [3] 。实际上，基于需求（用不到那么多内存）、性能（地址越宽在做地址转换时需要的页表级数越多）和成本（消耗更多晶体管）的考虑，在AMD64架构 [4] 中只支持到52位（4PB）的地址总线和48位（256TB）的虚拟地址空间，所以目前64位的硬件实际能够支持的最大内存只有256TB。此外，操作系统一侧也还会施加自己的约束，64位的Linux则分别支持47位（128TB）的进程虚拟地址空间和46位（64TB）的物理地址空间，64位的Windows系统甚至只支持44位（16TB）的物理地址空间。
尽管Linux下64位指针的高18位不能用来寻址，但剩余的46位指针所能支持的64TB内存在今天仍然能够充分满足大型服务器的需要。鉴于此，ZGC的染色指针技术继续盯上了这剩下的46位指针宽度，将其高4位提取出来存储四个标志信息。通过这些标志位，虚拟机可以直接从指针中看到其引用对象的三色标记状态、是否进入了重分配集（即被移动过）、是否只能通过finalize()方法才能被访问到。当然，由于这些标志位进一步压缩了原本就只有46位的地址空间，也直接导致ZGC能够管理的内存不可以超过4TB（2的42次幂） 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说说ZGC垃圾收集器的工作原理
1）内存布局
·小型Region（Small Region）：容量固定为2MB，用于放置小于256KB的小对象。
·中型Region（Medium Region）：容量固定为32MB，用于放置大于等于256KB但小于4MB的对象。
·大型Region（Large Region）：容量不固定，可以动态变化，但必须为2MB的整数倍，用于放置4MB或以上的大对象。每个大型Region中只会存放一个大对象，这也预示着虽然名字叫作“大型Region”，但它的实际容量完全有可能小于中型Region，最小容量可低至4MB。大型Region在ZGC的实现中是不会被重分配（重分配是ZGC的一种处理动作，用于复制对象的收集器阶段，稍后会介绍到）的，因为复制一个大对象的代价非常高昂。

2）染色指针
染色指针是一种直接将少量额外的信息存储在指针上的技术，可是为什么指针本身也可以存储额外信息呢？在64位系统中，理论可以访问的内存高达16EB（2的64次幂）字节 [3] 。实际上，基于需求（用不到那么多内存）、性能（地址越宽在做地址转换时需要的页表级数越多）和成本（消耗更多晶体管）的考虑，在AMD64架构 [4] 中只支持到52位（4PB）的地址总线和48位（256TB）的虚拟地址空间，所以目前64位的硬件实际能够支持的最大内存只有256TB。此外，操作系统一侧也还会施加自己的约束，64位的Linux则分别支持47位（128TB）的进程虚拟地址空间和46位（64TB）的物理地址空间，64位的Windows系统甚至只支持44位（16TB）的物理地址空间。
尽管Linux下64位指针的高18位不能用来寻址，但剩余的46位指针所能支持的64TB内存在今天仍然能够充分满足大型服务器的需要。鉴于此，ZGC的染色指针技术继续盯上了这剩下的46位指针宽度，将其高4位提取出来存储四个标志信息。通过这些标志位，虚拟机可以直接从指针中看到其引用对象的三色标记状态、是否进入了重分配集（即被移动过）、是否只能通过finalize()方法才能被访问到。当然，由于这些标志位进一步压缩了原本就只有46位的地址空间，也直接导致ZGC能够管理的内存不可以超过4TB（2的42次幂） 。

3）收集过程
·并发标记 （Concurrent Mark）：与G1、Shenandoah一样，并发标记是遍历对象图做可达性分析的阶段，前后也要经过类似于G1、Shenandoah的初始标记、最终标记（尽管ZGC中的名字不叫这些）的短暂停顿，而且这些停顿阶段所做的事情在目标上也是相类似的。与G1、Shenandoah不同的是，ZGC的标记是在指针上而不是在对象上进行的，标记阶段会更新染色指针中的Marked 0、Marked 1标志位。
·并发预备重分配 （Concurrent Prepare for Relocate）：这个阶段需要根据特定的查询条件统计得出本次收集过程要清理哪些Region，将这些Region组成重分配集（Relocation Set）。重分配集与G1收集器的回收集（Collection Set）还是有区别的，ZGC划分Region的目的并非为了像G1那样做收益优先的增量回收。相反，ZGC每次回收都会扫描所有的Region，用范围更大的扫描成本换取省去G1中记忆集的维护成本。因此，ZGC的重分配集只是决定了里面的存活对象会被重新复制到其他的Region中，里面的Region会被释放，而并不能说回收行为就只是针对这个集合里面的Region进行，因为标记过程是针对全堆的。此外，在JDK 12的ZGC中开始支持的类卸载以及弱引用的处理，也是在这个阶段中完成的。
·并发重分配 （Concurrent Relocate）：重分配是ZGC执行过程中的核心阶段，这个过程要把重分配集中的存活对象复制到新的Region上，并为重分配集中的每个Region维护一个转发表（Forward Table），记录从旧对象到新对象的转向关系。得益于染色指针的支持，ZGC收集器能仅从引用上就明确得知一个对象是否处于重分配集之中，如果用户线程此时并发访问了位于重分配集中的对象，这次访问将会被预置的内存屏障所截获，然后立即根据Region上的转发表记录将访问转发到新复制的对象上，并同时修正更新该引用的值，使其直接指向新对象，ZGC将这种行为称为指针的“自愈”（Self-Healing）能力。这样做的好处是只有第一次访问旧对象会陷入转发，也就是只慢一次，对比Shenandoah的Brooks转发指针，那是每次对象访问都必须付出的固定开销，简单地说就是每次都慢，因此ZGC对用户程序的运行时负载要比Shenandoah来得更低一些。还有另外一个直接的好处是由于染色指针的存在，一旦重分配集中某个Region的存活对象都复制完毕后，这个Region就可以立即释放用于新对象的分配（但是转发表还得留着不能释放掉），哪怕堆中还有很多指向这个对象的未更新指针也没有关系，这些旧指针一旦被使用，它们都是可以自愈的。
·并发重映射 （Concurrent Remap）：重映射所做的就是修正整个堆中指向重分配集中旧对象的所有引用，这一点从目标角度看是与Shenandoah并发引用更新阶段一样的，但是ZGC的并发重映射并不是一个必须要“迫切”去完成的任务，因为前面说过，即使是旧引用，它也是可以自愈的，最多只是第一次
使用时多一次转发和修正操作。重映射清理这些旧引用的主要目的是为了不变慢（还有清理结束后可以释放转发表这样的附带收益），所以说这并不是很“迫切”。因此，ZGC很巧妙地把并发重映射阶段要做的工作，合并到了下一次垃圾收集循环中的并发标记阶段里去完成，反正它们都是要遍历所有对象的，这样合并就节省了一次遍历对象图 [9] 的开销。一旦所有指针都被修正之后，原来记录新旧对象关系的转发表就可以释放掉了。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说说G1垃圾收集器的工作原理
优点：指定最大停顿时间、分Region的内存布局、按收益动态确定回收集

G1开创的基于Region的堆内存布局是它能够实现这个目标的关键。虽然G1也仍是遵循分代收集理论设计的，但其堆内存的布局与其他收集器有非常明显的差异：G1不再坚持固定大小以及固定数量的分代区域划分，而是把连续的Java堆划分为多个大小相等的独立区域（Region），每一个Region都可以根据需要，扮演新生代的Eden空间、Survivor空间，或者老年代空间。收集器能够对扮演不同角色的Region采用不同的策略去处理，这样无论是新创建的对象还是已经存活了一段时间、熬过多次收集的旧对象都能获取很好的收集效果。 

虽然G1仍然保留新生代和老年代的概念，但新生代和老年代不再是固定的了，它们都是一系列区域（不需要连续）的动态集合。G1收集器之所以能建立可预测的停顿时间模型，是因为它将Region作为单次回收的最小单元，即每次收集到的内存空间都是Region大小的整数倍，这样可以有计划地避免在整个Java堆中进行全区域的垃圾收集。更具体的处理思路是让G1收集器去跟踪各个Region里面的垃圾堆积的“价值”大小，价值即回收所获得的空间大小以及回收所需时间的经验值，然后在后台维护一个优先级列表，每次根据用户设定允许的收集停顿时间（使用参数-XX：MaxGCPauseMillis指定，默认值是200毫秒），优先处理回收价值收益最大的那些Region，这也就是“Garbage First”名字的由来。这种使用Region划分内存空间，以及具有优先级的区域回收方式，保证了G1收集器在有限的时间内获取尽可能高的收集效率。 

G1收集器的运作过程大致可划分为以下四个步骤：
·初始标记 （Initial Marking）：仅仅只是标记一下GC Roots能直接关联到的对象，并且修改TAMS指针的值，让下一阶段用户线程并发运行时，能正确地在可用的Region中分配新对象。这个阶段需要停顿线程，但耗时很短，而且是借用进行Minor GC的时候同步完成的，所以G1收集器在这个阶段实际并没有额外的停顿。
·并发标记 （Concurrent Marking）：从GC Root开始对堆中对象进行可达性分析，递归扫描整个堆里的对象图，找出要回收的对象，这阶段耗时较长，但可与用户程序并发执行。当对象图扫描完成以后，还要重新处理SATB记录下的在并发时有引用变动的对象。
·最终标记 （Final Marking）：对用户线程做另一个短暂的暂停，用于处理并发阶段结束后仍遗留下来的最后那少量的SATB记录。
·筛选回收 （Live Data Counting and Evacuation）：负责更新Region的统计数据，对各个Region的回收价值和成本进行排序，根据用户所期望的停顿时间来制定回收计划，可以自由选择任意多个Region构成回收集，然后把决定回收的那一部分Region的存活对象复制到空的Region中，再清理掉整个旧Region的全部空间。这里的操作涉及存活对象的移动，是必须暂停用户线程，由多条收集器线程并行完成的。
从上述阶段的描述可以看出，G1收集器除了并发标记外，其余阶段也是要完全暂停用户线程的 。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说说CMS垃圾收集器的工作原理
Concurrent mark sweep(CMS)收集器是一种年老代垃圾收集器，其最主要目标是获取最短垃圾回收停顿时间， 和其他年老代使用标记-整理算法不同，它使用多线程的标记-清除算法。
最短的垃圾收集停顿时间可以为交互比较高的程序提高用户体验。
CMS 工作机制相比其他的垃圾收集器来说更复杂，整个过程分为以下 4 个阶段：
1）初始标记
只是标记一下 GC Roots 能直接关联的对象，速度很快，仍然需要暂停所有的工作线程。
2）并发标记
进行 GC Roots 跟踪的过程，和用户线程一起工作，不需要暂停工作线程。
3）重新标记
为了修正在并发标记期间，因用户程序继续运行而导致标记产生变动的那一部分对象的标记记录，仍然需要暂停所有的工作线程。
4）并发清除
清除 GC Roots 不可达对象，和用户线程一起工作，不需要暂停工作线程。由于耗时最长的并发标记和并发清除过程中，垃圾收集线程可以和用户线程一起并发工作， 所以总体上来看CMS 收集器的内存回收和用户线程是一起并发地执行。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 你了解过哪些垃圾收集器？
年轻代
Serial 垃圾收集器（单线程，通常用在客户端应用上。因为客户端应用不会频繁创建很多对象，用户也不会感觉出明显的卡顿。相反，它使用的资源更少，也更轻量级。）
ParNew 垃圾收集器（多线程，追求降低用户停顿时间，适合交互式应用。）
Parallel Scavenge 垃圾收集器（追求 CPU 吞吐量，能够在较短时间内完成指定任务，适合没有交互的后台计算。）

老年代
Serial Old 垃圾收集器
Parallel Old垃圾收集器
CMS 垃圾收集器（以获取最短 GC 停顿时间为目标的收集器，它在垃圾收集时使得用户线程和 GC 线程能够并发执行，因此在垃圾收集过程中用户也不会感到明显的卡顿。）

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 对象都是优先分配在年轻代上的吗？
不是。当新生代内存不够时，老年代分配担保。而大对象则是直接在老年代分配。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 你知道哪些GC类型？
Minor GC：发生在年轻代的 GC。
Major GC：发生在老年代的 GC。
Full GC：全堆垃圾回收。比如 Metaspace 区引起年轻代和老年代的回收。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## GC Roots 有哪些？
GC Roots 是一组必须活跃的引用。用通俗的话来说，就是程序接下来通过直接引用或者间接引用，能够访问到的潜在被使用的对象。

GC Roots 包括：
Java 线程中，当前所有正在被调用的方法的引用类型参数、局部变量、临时值等。也就是与我们栈帧相关的各种引用。
所有当前被加载的 Java 类。
Java 类的引用类型静态变量。
运行时常量池里的引用类型常量（String 或 Class 类型）。
JVM 内部数据结构的一些引用，比如 sun.jvm.hotspot.memory.Universe 类。
用于同步的监控对象，比如调用了对象的 wait() 方法。
JNI handles，包括 global handles 和 local handles。

这些 GC Roots 大体可以分为三大类，下面这种说法更加好记一些：
活动线程相关的各种引用。
类的静态变量的引用。
JNI 引用。

有两个注意点：
我们这里说的是活跃的引用，而不是对象，对象是不能作为 GC Roots 的。
GC 过程是找出所有活对象，并把其余空间认定为“无用”；而不是找出所有死掉的对象，并回收它们占用的空间。所以，哪怕 JVM 的堆非常的大，基于 tracing 的 GC 方式，回收速度也会非常快。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## JVM怎么判断一个对象是不是要回收？
引用计数法（缺点是对于相互引用的对象，无法进行清除）
可达性分析

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java里有哪些引用类型？
强引用
这种引用属于最普通最强硬的一种存在，只有在和 GC Roots 断绝关系时，才会被消灭掉。

软引用
软引用用于维护一些可有可无的对象。在内存足够的时候，软引用对象不会被回收，只有在内存不足时，系统则会回收软引用对象，如果回收了软引用对象之后仍然没有足够的内存，才会抛出内存溢出异常。
可以看到，这种特性非常适合用在缓存技术上。比如网页缓存、图片缓存等。
软引用可以和一个引用队列（ReferenceQueue）联合使用，如果软引用所引用的对象被垃圾回收，Java 虚拟机就会把这个软引用加入到与之关联的引用队列中。

弱引用
弱引用对象相比较软引用，要更加无用一些，它拥有更短的生命周期。当JVM进行垃圾回收时，无论内存是否充足，都会回收被弱引用关联的对象。弱引用拥有更短的生命周期，在 Java 中，用 java.lang.ref.WeakReference 类来表示。它的应用场景和软引用类似，可以在一些对内存更加敏感的系统里采用。

虚引用
这是一种形同虚设的引用，在现实场景中用的不是很多。虚引用必须和引用队列（ReferenceQueue）联合使用。如果一个对象仅持有虚引用，那么它就和没有任何引用一样，在任何时候都可能被垃圾回收。实际上，虚引用的 get，总是返回 null。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 你熟悉哪些垃圾收集算法？
标记清除（缺点是碎片化）
复制算法（缺点是浪费空间）
标记整理算法（效率比前两者差）
分代收集算法（老年代一般使用“标记-清除”、“标记-整理”算法，年轻代一般用复制算法）

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 字符串常量存放在哪个区域？
1. 字符串常量池，已经移动到堆上（jdk8之前是perm区），也就是执行intern方法后存的地方。
2. 类文件常量池，constant_pool，是每个类每个接口所拥有的，这部分数据在方法区，也就是元数据区。而运行时常量池是在类加载后的一个内存区域，它们都在元空间。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 程序计数器有什么作用？
程序计数器是一块较小的内存空间，它的作用可以看作是当前线程所执行的字节码的行号指示器。这里面存的，就是当前线程执行的进度。
程序计数器还存储了当前正在运行的流程，包括正在执行的指令、跳转、分支、循环、异常处理等。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 栈帧里面包含哪些东西？
局部变量表、操作数栈、动态连接、返回地址等

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 同步方法和同步块，哪个是更好的选择？
同步块，这意味着同步块之外的代码是异步执行的，这比同步整个方法更提升代码的效率。请知道一条原则：同步的范围越小越好。

虽说同步的范围越少越好，但是在Java虚拟机中还是存在着一种叫做锁粗化的优化方法，这种方法就是把同步范围变大。这是有用的，比方说StringBuffer，它是一个线程安全的类，自然最常用的append()方法是一个同步方法，我们写代码的时候会反复append字符串，这意味着要进行反复的加锁->解锁，这对性能不利，因为这意味着Java虚拟机在这条线程上要反复地在内核态和用户态之间进行切换，因此Java虚拟机会将多次append方法调用的代码进行一个锁粗化的操作，将多次的append的操作扩展到append方法的头尾，变成一个大的同步块，这样就减少了加锁–>解锁的次数，有效地提升了代码执行的效率。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何避免“伪共享”？
1. 字节填充（创建变量时，使用字段对其进行填充，避免多个变量被分派到同一个缓存行里）。
2. JDK8提供了一个Contended注解来解决伪共享。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么要有 hashCode
##### 我们以“HashSet 如何检查重复”为例子来说明为什么要有 hashCode：

当你把对象加入 HashSet 时，HashSet 会先计算对象的 hashcode 值来判断对象加入的位置，同时也会与其他已经加入的对象的 hashcode 值作比较，如果没有相符的hashcode，HashSet会假设对象没有重复出现。但是如果发现有相同 hashcode 值的对象，这时会调用 equals()方法来检查 hashcode 相等的对象是否真的相同。如果两者相同，HashSet 就不会让其加入操作成功。如果不同的话，就会重新散列到其他位置。（摘自我的Java启蒙书《Head first java》第二版）。这样我们就大大减少了 equals 的次数，相应就大大提高了执行速度。

##### hashCode()与equals()的相关规定

如果两个对象相等，则hashcode一定也是相同的

两个对象相等，对两个对象分别调用equals方法都返回true

两个对象有相同的hashcode值，它们也不一定是相等的

##### 因此，equals 方法被覆盖过，则 hashCode 方法也必须被覆盖

hashCode() 的默认行为是对堆上的对象产生独特值。如果没有重写 hashCode()，则该 class 的两个对象无论如何都不会相等（即使这两个对象指向相同的数据）

##### 对象的相等与指向他们的引用相等，两者有什么不同？

对象的相等 比的是内存中存放的内容是否相等而 引用相等 比较的是他们指向的内存地址是否相等。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 静态代理和动态代理的区别
静态代理中代理类在编译期就已经确定，而动态代理则是JVM运行时动态生成，静态代理的效率相对动态代理来说相对高一些，但是静态代理代码冗余大，一单需要修改接口，代理类和委托类都需要修改。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## ArrayList和LinkedList有什么区别？
1. ArrayList和LinkedList的差别主要来自于Array和LinkedList数据结构的不同。ArrayList是基于数组实现的，LinkedList是基于双链表实现的。另外LinkedList类不仅是List接口的实现类，可以根据索引来随机访问集合中的元素，除此之外，LinkedList还实现了Deque接口，Deque接口是Queue接口的子接口，它代表一个双向队列，因此LinkedList可以作为双向队列 ，栈（可以参见Deque提供的接口方法）和List集合使用，功能强大。

2. 因为Array是基于索引(index)的数据结构，它使用索引在数组中搜索和读取数据是很快的，可以直接返回数组中index位置的元素，因此在随机访问集合元素上有较好的性能。Array获取数据的时间复杂度是O(1),但是要插入、删除数据却是开销很大的，因为这需要移动数组中插入位置之后的的所有元素。

3. 相对于ArrayList，LinkedList的随机访问集合元素时性能较差，因为需要在双向列表中找到要index的位置，再返回；但在插入，删除操作是更快的。因为LinkedList不像ArrayList一样，不需要改变数组的大小，也不需要在数组装满的时候要将所有的数据重新装入一个新的数组，这是ArrayList最坏的一种情况，时间复杂度是O(n)，而LinkedList中插入或删除的时间复杂度仅为O(1)。ArrayList在插入数据时还需要更新索引（除了插入数组的尾部）。

4. LinkedList需要更多的内存，因为ArrayList的每个索引的位置是实际的数据，而LinkedList中的每个节点中存储的是实际的数据和前后节点的位置。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 重写和重载的区别
重写是子类对父类的允许访问的方法的实现过程进行重新编写, 返回值和形参都不能改变。即外壳不变，核心重写！
重写的好处在于子类可以根据需要，定义特定于自己的行为。 也就是说子类能够根据需要实现父类的方法。
重写方法不能抛出新的检查异常或者比被重写方法申明更加宽泛的异常。

重载(overloading) 是在一个类里面，方法名字相同，而参数不同。返回类型可以相同也可以不同。
每个重载的方法（或者构造函数）都必须有一个独一无二的参数类型列表。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java 8的接口新增了哪些特性？
增加了default方法和static方法，这2种方法可以有方法体。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 抽象类和接口（Java7）的区别
1. 抽象类可以提供成员方法的实现细节，而接口中只能存在public abstract 方法；
2. 抽象类中的成员变量可以是各种类型的，而接口中的成员变量只能是public static final类型的；
3. 接口中不能含有静态代码块以及静态方法，而抽象类可以有静态代码块和静态方法；
4. 一个类只能继承一个抽象类，而一个类却可以实现多个接口。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## hashCode()介绍
hashCode() 的作用是获取哈希码，也称为散列码；它实际上是返回一个int整数。这个哈希码的作用是确定该对象在哈希表中的索引位置。hashCode() 定义在JDK的Object.java中，这就意味着Java中的任何类都包含有hashCode()函数。

散列表存储的是键值对(key-value)，它的特点是：能根据“键”快速的检索出对应的“值”。这其中就利用到了散列码！（可以快速找到所需要的对象）

*** 
## ⭐️⭐️⭐️⭐️⭐️
## hashCode 与 equals (重要)
HashSet如何检查重复

两个对象的 hashCode() 相同，则 equals() 也一定为 true，对吗？

hashCode和equals方法的关系

面试官可能会问你：“你重写过 hashcode 和 equals 么，为什么重写equals时必须重写hashCode方法？”

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 内部类的分类有哪些
内部类可以分为四种： 成员内部类、局部内部类、匿名内部类和静态内部类 。

 #### 41.Java中异常分为哪些种类？

按照异常需要处理的时机分为编译时异常(也叫受控异常)也叫 CheckedException 和运行时异常(也叫非受控异常)也叫 UnCheckedException。Java认为Checked异常都是可以被处理的异常，所以Java程序必须显式处理Checked异常。如果程序没有处理Checked 异常，该程序在编译时就会发生错误无法编译。这体现了Java 的设计哲学：没有完善错误处理的代码根本没有机会被执行。对Checked异常处理方法有两种：

● 第一种：当前方法知道如何处理该异常，则用try...catch块来处理该异常。

● 第二种：当前方法不知道如何处理，则在定义该方法时声明抛出该异常。

运行时异常只有当代码在运行时才发行的异常，编译的时候不需要try…catch。Runtime如除数是0和数组下标越界等，其产生频繁，处理麻烦，若显示申明或者捕获将会对程序的可读性和运行效率影响很大。所以由系统自动检测并将它们交给缺省的异常处理程序。当然如果你有处理要求也可以显示捕获它们。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是内部类？
在Java中，可以将一个类的定义放在另外一个类的定义内部，这就是 内部类 。内部类本身就是类的一个属性，与其他属性定义方式一致。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是方法的返回值？返回值的作用是什么？
方法的返回值是指我们获取到的某个方法体中的代码执行后产生的结果！（前提是该方法可能产生结果）。返回值的作用:接收出结果，使得它可以用于其他的操作！

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 静态方法和实例方法有何不同？
静态方法和实例方法的区别主要体现在两个方面：

1. 在外部调用静态方法时，可以使用"类名.方法名"的方式，也可以使用"对象名.方法名"的方式。而实例方法只有后面这种方式。也就是说，调用静态方法可以无需创建对象。
2. 静态方法在访问本类的成员时，只允许访问静态成员（即静态成员变量和静态方法），而不允许访问实例成员变量和实例方法；实例方法则无此限制

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 静态变量和实例变量区别
静态变量： 静态变量由于不属于任何实例对象，属于类的，所以在内存中只会有一份，在类的加载过程中，JVM只为静态变量分配一次内存空间。

实例变量： 每次创建对象，都会为每个对象分配成员变量内存空间，实例变量是属于实例对象的，在内存中，创建几次对象，就有几份成员变量。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 构造方法有哪些特性？
名字与类名相同；

没有返回值，但不能用void声明构造函数；

生成类的对象时自动执行，无需调用。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在Java中定义一个不做事且没有参数的构造方法的作用
Java程序在执行子类的构造方法之前，如果没有用super()来调用父类特定的构造方法，则会调用父类中“没有参数的构造方法”。因此，如果父类中只定义了有参数的构造方法，而在子类的构造方法中又没有用super()来调用父类中特定的构造方法，则编译时将发生错误，因为Java程序在父类中找不到没有参数的构造方法可供执行。解决办法是在父类里加上一个不做事且没有参数的构造方法。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## break ,continue ,return 的区别及作用
break 跳出总上一层循环，不再执行循环(结束当前的循环体)

continue 跳出本次循环，继续执行下次循环(结束正在执行的循环 进入下一个循环条件)

return 程序返回，不再执行下面的代码(结束当前的方法 直接返回)

*** 
## ⭐️⭐️⭐️⭐️⭐️
## static注意事项
1、静态只能访问静态。 2、非静态既可以访问非静态的，也可以访问静态的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## static应用场景
因为static是被类的实例对象所共享，因此如果 某个成员变量是被所有对象所共享的，那么这个成员变量就应该定义为静态变量 。

因此比较常见的static应用场景有：

1、修饰成员变量 2、修饰成员方法 3、静态代码块 4、修饰类【只能修饰内部类也就是静态内部类】 5、静态导包

*** 
## ⭐️⭐️⭐️⭐️⭐️
## static的独特之处
1、被static修饰的变量或者方法是独立于该类的任何对象，也就是说，这些变量和方法 不属于任何一个实例对象，而是被类的实例对象所共享 。

怎么理解 “被类的实例对象所共享” 这句话呢？就是说，一个类的静态成员，它是属于大伙的【大伙指的是这个类的多个对象实例，我们都知道一个类可以创建多个实例！】，所有的类对象共享的，不像成员变量是自个的【自个指的是这个类的单个实例对象】…我觉得我已经讲的很通俗了，你明白了咩？

2、在该类被第一次加载的时候，就会去加载被static修饰的部分，而且只在类第一次使用时加载并进行初始化，注意这是第一次用就要初始化，后面根据需要是可以再次赋值的。

3、static变量值在类加载的时候分配空间，以后创建类对象的时候不会重新分配。赋值的话，是可以任意赋值的！

4、被static修饰的变量或者方法是优先于对象存在的，也就是说当一个类加载完毕之后，即便没有创建对象，也可以去访问。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## static存在的主要意义
static的主要意义是在于创建独立于具体对象的域变量或者方法。 以致于即使没有创建对象，也能使用属性和调用方法 ！

static关键字还有一个比较关键的作用就是 用来形成静态代码块以优化程序性能 。static块可以置于类中的任何地方，类中可以有多个static块。在类初次被加载的时候，会按照static块的顺序来执行每个static块，并且只会执行一次。

为什么说static块可以用来优化程序性能，是因为它的特性:只会在类加载的时候执行一次。因此，很多时候会将一些只需要进行一次的初始化操作都放在static代码块中进行。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## this与super的区别
- super:它引用当前对象的直接父类中的成员（用来访问直接父类中被隐藏的父类中成员数据或函数，基类与派生类中有相同成员定义时如：super.变量名 super.成员函数据名（实参）
- this：它代表当前对象名（在程序中易产生二义性之处，应使用this来指明当前对象；如果函数的形参与类中的成员数据同名，这时需用this来指明成员变量名）
- super()和this()类似,区别是，super()在子类中调用父类的构造方法，this()在本类内调用本类的其它构造方法。
- super()和this()均需放在构造方法内第一行。
- 尽管可以用this调用一个构造器，但却不能调用两个。
- this和super不能同时出现在一个构造函数里面，因为this必然会调用其它的构造函数，其它的构造函数必然也会有super语句的存在，所以在同一个构造函数里面有相同的语句，就失去了语句的意义，编译器也不会通过。
- this()和super()都指的是对象，所以，均不可以在static环境中使用。包括：static变量,static方法，static语句块。
- 从本质上讲，this是一个指向本对象的指针, 然而super是一个Java关键字。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## super关键字的用法
super可以理解为是指向自己超（父）类对象的一个指针，而这个超类指的是离自己最近的一个父类。

super也有三种用法：

1.普通的直接引用

与this类似，super相当于是指向当前对象的父类的引用，这样就可以用super.xxx来引用父类的成员。

2.子类中的成员变量或方法与父类中的成员变量或方法同名时，用super进行区分

```java
class Person{
    protected String name;
 
    public Person(String name) {
        this.name = name;
    }
 
}
 
class Student extends Person{
    private String name;
 
    public Student(String name, String name1) {
        super(name);
        this.name = name1;
    }
 
    public void getInfo(){
        System.out.println(this.name);      //Child
        System.out.println(super.name);     //Father
    }
 
}

public class Test {
    public static void main(String[] args) {
       Student s1 = new Student("Father","Child");
       s1.getInfo();
 
    }
}
```

3.引用父类构造函数

3、引用父类构造函数

- super（参数）：调用父类中的某一个构造函数（应该为构造函数中的第一条语句）。
- this（参数）：调用本类中另一种形式的构造函数（应该为构造函数中的第一条语句）。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## this关键字的用法
this是自身的一个对象，代表对象本身，可以理解为：指向对象本身的一个指针。

this的用法在java中大体可以分为3种：

1.普通的直接引用，this相当于是指向当前对象本身。

2.形参与成员名字重名，用this来区分：

```java
public Person(String name, int age) {
    this.name = name;
    this.age = age;
}
```

3.引用本类的构造函数

```java
class Person{
    private String name;
    private int age;
    
    public Person() {
    }
 
    public Person(String name) {
        this.name = name;
    }
    public Person(String name, int age) {
        this(name);
        this.age = age;
    }
}
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## char型变量中能否能不能存储一个中文汉字，为什么？
char可以存储一个中文汉字，因为Java中使用的编码是Unicode(不选择任何特定的编码，直接使用字符在字符集中的编号，这是统一的唯一方法），一个char 类型占2个字节（16 比特），所以放一个中文是没问题的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## String类的常用方法有哪些？
•indexof();返回指定字符的的索引。

•charAt();返回指定索引处的字符。

•replace();字符串替换。

•trim();去除字符串两端空格。

•splt()；字符串分割，返回分割后的字符串数组。

•getBytes()；返回字符串byte类型数组。

•length()；返回字符串长度。

•toLowerCase();将字符串转换为小写字母。

•toUpperCase();将字符串转换为大写字母。

•substring();字符串截取。

•equals();比较字符串是否相等。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 是否可以继承String类？
String 类是final类，不可以被继承。

补充：继承String本身就是一个错误的行为，对String类型最好的重用方式是关联关系（Has-A）和依赖关系（Use-A）而不是继承关系（Is-A）。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 两个对象值相同(x.equals(y) == true)，但却可有不同的hash code，这句话对不对？
不对，如果两个对象x和y满足x.equals(y) == true，它们的哈希码（hash code）应当相同。

Java对于eqauls方法和hashCode方法是这样规定的：

(1)如果两个对象相同（equals方法返回true），那么它们的hashCode值一定要相同；

(2)如果两个对象的hashCode相同，它们并不一定相同。

当然，你未必要按照要求去做，但是如果你违背了上述原则就会发现在使用容器时，相同的对象可以出现在Set集合中，同时增加新元素的效率会大大下降（对于使用哈希存储的系统，如果哈希码频繁的冲突将会造成存取性能急剧下降）。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 构造器（constructor）是否可被重写（override）？
答：构造器不能被继承，因此不能被重写，但可以被重载。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 谈谈你对多态的理解？
多态就是指程序中定义的引用变量所指向的具体类型和通过该引用变量发出的方法调用在编程时并不确定，而是在程序运行期间才确定，即一个引用变量到底会指向哪个类的实例对象，该引用变量发出的方法调用到底是哪个类中实现的方法，必须在程序运行期间才能决定。因为在程序运行时才确定具体的类，这样，不用修改源代码，就可以让引用变量绑定到各种不同的对象上，从而导致该引用调用的具体方法随之改变，即不修改程序代码就可以改变程序运行时所绑定的具体代码，让程序可以选择多个运行状态，这就是多态性。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java中实现多态的机制是什么？
Java中的多态靠的是父类或接口定义的引用变量可以指向子类或具体实现类的实例对象，而程序调用的方法在运行期才动态绑定，就是引用变量所指向的具体实例对象的方法，也就是内存里正在运行的那个对象的方法，而不是引用变量的类型中定义的方法。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## new一个对象的过程和clone一个对象的区别？
new 操作符的本意是分配内存。程序执行到 new 操作符时，首先去看 new 操作符后面的类型，因为知道了类型，才能知道要分配多大的内存空间。分配完内存之后，再调用构造函数，填充对象的各个域，这一步叫做对象的初始化，构造方法返回后，一个对象创建完毕，可以把他的引用（地址）发布到外部，在外部就可以使用这个引用操纵这个对象。

clone 在第一步是和 new 相似的，都是分配内存，调用 clone 方法时，分配的内存和原对象（即调用 clone 方法的对象）相同，然后再使用原对象中对应的各个域，填充新对象的域，填充完成之后，clone方法返回，一个新的相同的对象被创建，同样可以把这个新对象的引用发布到外部。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 深克隆和浅克隆？
浅克隆：创建一个新对象，新对象的属性和原来对象完全相同，对于非基本类型属性，仍指向原有属性所指向的对象的内存地址。


深克隆：创建一个新对象，属性中引用的其他对象也会被克隆，不再指向原有对象地址。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java中为什么要用 clone？
在实际编程过程中，我们常常要遇到这种情况：有一个对象 A，在某一时刻 A 中已经包含了一些有效值，此时可能会需要一个和 A 完全相同新对象 B，并且此后对 B 任何改动都不会影响到 A 中的值，也就是说，A 与 B 是两个独立的对象，但 B 的初始值是由 A 对象确定的。在 Java 语言中，用简单的赋值语句是不能满足这种需求的。要满足这种需求虽然有很多途径，但clone()方法是其中最简单，也是最高效的手段。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java 中操作字符串都有哪些类？它们之间有什么区别？
操作字符串的类有：String、StringBuffer、StringBuilder。
String 和 StringBuffer、StringBuilder 的区别在于 String 声明的是不可变的对象，每次操作都会生成新的 String 对象，再将指针指向新的 String 对象，而 StringBuffer 、 StringBuilder 可以在原有对象的基础上进行操作，所以在经常改变字符串内容的情况下最好不要使用 String。
StringBuffer 和 StringBuilder 最大的区别在于，StringBuffer 是线程安全的，而 StringBuilder 是非线程安全的，但 StringBuilder 的性能却高于 StringBuffer，所以在单线程环境下推荐使用 StringBuilder，多线程环境下推荐使用 StringBuffer。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## String str = "i" 和String str = new String("1")一样吗？
不一样，因为内存的分配方式不一样。String str = "i"的方式JVM会将其分配到常量池中，而String str = new String("i")JVM会将其分配到堆内存中。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## final finally finalize的区别
- final可以修饰类、变量、方法，修饰类表示该类不能被继承、修饰方法表示该方法不能被重写、修饰变量表 
  示该变量是一个常量不能被重新赋值。
- finally一般作用在try-catch代码块中，在处理异常的时候，通常我们将一定要执行的代码方法finally代码块 
  中，表示不管是否出现异常，该代码块都会执行，一般用来存放一些关闭资源的代码。
- finalize是一个方法，属于Object类的一个方法，而Object类是所有类的父类，该方法一般由垃圾回收器来调 
  用，当我们调用System.gc() 方法的时候，由垃圾回收器调用finalize()，回收垃圾，一个对象是否可回收的 
  最后判断。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## final 有什么用？
用于修饰类、属性和方法；

- 被final修饰的类不可以被继承
- 被final修饰的方法不可以被重写
- 被final修饰的变量不可以被改变，被final修饰不可变的是变量的引用，而不是引用指向的内容，引用指向的内容是可以改变的

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java有哪些数据类型
定义：Java语言是强类型语言，对于每一种数据都定义了明确的具体的数据类型，在内存中分配了不同大小的内存空间。

- 基本数据类型
  - 数值型
    - 整数类型(byte,short,int,long)
    - 浮点类型(float,double)
  - 字符型(char)
  - 布尔型(boolean)
- 引用数据类型
  - 类(class)
  - 接口(interface)
  - 数组([])

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Java注释
定义：用于解释说明程序的文字

Java注释的分类
- 单行注释 
  格式： // 注释文字
- 多行注释 
  格式： /* 注释文字 */
- 文档注释 
  格式：/** 注释文字 */

Java注释的作用
在程序中，尤其是复杂的程序中，适当地加入注释可以增加程序的可读性，有利于程序的修改、调试和交流。注释的内容在程序编译的时候会被忽视，不会产生目标代码，注释的部分不会对程序的执行结果产生任何影响。

注意事项：多行和文档注释都不能嵌套使用。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 用最有效率的方法计算2乘以8？
2 << 3

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Math.round(11.5) 等于多少？Math.round(-11.5)等于多少？
Math.round(11.5)的返回值是12，Math.round(-11.5)的返回值是-11。四舍五入的原理是在参数上加0.5然后进行下取整。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## &和&&的区别？
&运算符有两种用法：(1)按位与；(2)逻辑与。

&&运算符是短路与运算。

逻辑与跟短路与的差别是非常巨大的，虽然二者都要求运算符左右两端的布尔值都是true整个表达式的值才是true。&&之所以称为短路运算是因为，如果&&左边的表达式的值是false，右边的表达式会被直接短路掉，不会进行运算。很多时候我们可能都需要用&&而不是&，例如在验证用户登录时判定用户名不是null而且不是空字符串，应当写为：username != null &&!username.equals("")，二者的顺序不能交换，更不能用&运算符，因为第一个条件如果不成立，根本不能进行字符串的equals比较，否则会产生NullPointerException异常。注意：逻辑或运算符（|）和短路或运算符（||）的差别也是如此。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java有没有goto？
goto 是Java中的保留字，在目前版本的Java中没有使用。（根据James Gosling（Java之父）编写的《The Java Programming Language》一书的附录中给出了一个Java关键字列表，其中有goto和const，但是这两个是目前无法使用的关键字，因此有些地方将其称之为保留字，其实保留字这个词应该有更广泛的意义，因为熟悉C语言的程序员都知道，在系统类库中使用过的有特殊意义的单词或单词的组合都被视为保留字）

*** 
## ⭐️⭐️⭐️⭐️⭐️
## float f=3.4;是否正确？
不正确。3.4是双精度数，将双精度型（double）赋值给浮点型（float）属于下转型（down-casting，也称为窄化）会造成精度损失，因此需要强制类型转换float f =(float)3.4; 或者写成float f =3.4F;。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 访问修饰符public,private,protected,以及不写（默认）时的区别？
| 修饰符    | 当前类 | 同 包 | 子 类 | 其他包 |
| --------- | ------ | ----- | ----- | ------ |
| public    | √      | √     | √     | √      |
| protected | √      | √     | √     | ×      |
| default   | √      | √     | ×     | ×      |
| private   | √      | ×     | ×     | ×      |

类的成员不写访问修饰时默认为default。默认对于同一个包中的其他类相当于公开（public），对于不是同一个包中的其他类相当于私有（private）。受保护（protected）对子类相当于公开，对不是同一包中的没有父子关系的类相当于私有。Java中，外部类的修饰符只能是public或默认，类的成员（包括内部类）的修饰符可以是以上四种。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Java程序的主类？应用程序和小程序的主类有何不同？
一个程序中可以有多个类，但只能有一个类是主类。在Java应用程序中，这个主类是指包含main()方法的类。而在Java小程序中，这个主类是一个继承自系统类JApplet或Applet的子类。应用程序的主类不一定要求是public类，但小程序的主类要求必须是public类。主类是Java程序执行的入口点。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java语言有哪些特点
简单易学（Java语言的语法与C语言和C++语言很接近）

面向对象（封装，继承，多态）

平台无关性（Java虚拟机实现平台无关性）

支持网络编程并且很方便（Java语言诞生本身就是为简化网络编程设计的）

支持多线程（多线程机制使应用程序在同一时间并行执行多项任）

健壮性（Java语言的强类型机制、异常处理、垃圾的自动收集等）

安全性

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说下面向对象四大特性
封装、继承、多态、抽象。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 微服务有哪些优缺点？
优点：
独立的可扩展性，每个微服务都可以独立进行横向或纵向扩展，根据业务实际增长情况来进行快速扩展；
独立的可升级性，每个微服务都可以独立进行服务升级、更新，不用依赖于其它服务，结合持续集成工具可以进行持续发布，开发人员就可以独立快速完成服务升级发布流程；
易维护性，每个微服务的代码均只专注于完成该单个业务范畴的事情，因此微服务项目代码数量将减少至IDE可以快速加载的大小，这样可以提高了代码的可读性，进而可以提高研发人员的生产效率；
语言无关性，研发人员可以选用自己最为熟悉的语言和框架来完成他们的微服务项目（当然，一般根据每个公司的实际技术栈需要来了），这样在面对新技术或新框架的选用时，微服务能够更好地进行快速响应；
故障和资源的隔离性，在系统中出现不好的资源操作行为时，例如内存泄露、数据库连接未关闭等情况，将仅仅只会影响单个微服务；
优化跨团队沟通，如果要完全实践微服务架构设计风格，研发团队势必会按照新的原则来进行划分，由之前的按照技能、职能划分的方式变为按照业务（单个微服务）来进行划分，如此这般团队里将有各个方向技能的研发人员，沟通效率上来说要优于之前按照技能进行划分的组织架构；
原生基于“云”的系统架构设计，基于微服务架构设计风格，我们能构建出来原生对于“云”具备超高友好度的系统，与常用容器工具如Docker能够很方便地结合，构建持续发布系统与IaaS、PaaS平台对接，使其能够方便的部署于各类“云”上，如公用云、私有云以及混合云。

缺点：
增加了系统复杂性；
运维难度增加；
本地调用变成RPC调用，接口耗时增加；
可能会引入分布式事务。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Dubbo 源码使用了哪些设计模式？
责任链模式：责任链中的每个节点实现 Filter 接口，然后由 ProtocolFilterWrapper，将所有 Filter 串连起来。
 Dubbo 的许多功能都是通过 Filter 扩展实现的，比如监控、日志、缓存、安全、telnet 以及 RPC 本身都是。

观察者模式：消费者在初始化的时候回调用 subscribe 方法，注册一个观察者，如果观察者引用的服务地址列表发生改变，
 就会通过 NotifyListener 通知消费者。

装饰器模式：比如 ProtocolFilterWrapper 类是对 Protocol 类的修饰。

工厂模式：如 ExtenstionLoader.getExtenstionLoader(Protocol.class).getAdaptiveExtenstion()。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 工厂模式与抽象工厂模式的区别？
首先来看看这两者的定义区别：

工厂模式：定义一个用于创建对象的借口，让子类决定实例化哪一个类

抽象工厂模式：为创建一组相关或相互依赖的对象提供一个接口，而且无需指定他们的具体类

​    个人觉得这个区别在于产品，如果产品单一，最合适用工厂模式，但是如果有多个业务品种、业务分类时，通过抽象工厂模式产生需要的对象是一种非常好的解决方式。再通俗深化理解下：工厂模式针对的是一个产品等级结构 ，抽象工厂模式针对的是面向多个产品等级结构的。

再来看看工厂方法模式与抽象工厂模式对比：

| 工厂方法模式                               | 抽象工厂模式                               |
| ------------------------------------------ | ------------------------------------------ |
| 针对的是一个产品等级结构                   | 针对的是面向多个产品等级结构               |
| 一个抽象产品类                             | 多个抽象产品类                             |
| 可以派生出多个具体产品类                   | 每个抽象产品类可以派生出多个具体产品类     |
| 一个抽象工厂类，可以派生出多个具体工厂类   | 一个抽象工厂类，可以派生出多个具体工厂类   |
| 每个具体工厂类只能创建一个具体产品类的实例 | 每个具体工厂类可以创建多个具体产品类的实例 |

 #### 15.举出一个例子，在这种情况你会更倾向于使用抽象类，而不是接口？

这是很常用但又是很难回答的设计面试问题。接口和抽象类都遵循”面向接口而不是实现编码”设计原则，它可以增加代码的灵活性，可以适应不断变化的需求。下面有几个点可以帮助你回答这个问题：

1. 在一些对时间要求比较高的应用中，倾向于使用抽象类，它会比接口稍快一点。
2. 如果希望把一系列行为都规范在类继承层次内，并且可以更好地在同一个地方进行编码，那么抽象类是一个更好的选择。有时，接口和抽象类可以一起使用，接口中定义函数，而在抽象类中定义默认的实现。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 给我一个符合开闭原则的设计模式的例子？
开闭原则要求你的代码对扩展开放，对修改关闭。这个意思就是说，如果你想增加一个新的功能，你可以很容易的在不改变已测试过的代码的前提下增加新的代码。有好几个设计模式是基于开闭原则的，如策略模式，如果你需要一个新的策略，只需要实现接口，增加配置，不需要改变核心逻辑。一个正在工作的例子是 Collections.sort() 方法，这就是基于策略模式，遵循开闭原则的，你不需为新的对象修改 sort() 方法，你需要做的仅仅是实现你自己的 Comparator 接口。



*** 
## ⭐️⭐️⭐️⭐️⭐️
## OOP中的组合、聚合和关联有什么区别？
如果两个对象彼此有关系，就说他们是彼此相关联的。组合和聚合是面向对象中的两种形式的关联。组合是一种比聚合更强力的关联。组合中，一个对象是另一个的拥有者，而聚合则是指一个对象使用另一个对象。如果对象 A 是由对象 B 组合的，则 A 不存在的话，B一定不存在，但是如果 A 对象聚合了一个对象 B，则即使 A 不存在了，B 也可以单独存在。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是模板方法模式？试举例说明。<p>一、什么是模板方法模式</p><p>　　所谓模板方法模式，其实很简单，可以从模板的角度考虑，就是一个对模板的应用，就好比老师出试卷，每个人的试卷都是一样的，即都是从老师的原版试卷复印来的，这个原版试卷就是一个模板，可每个人写在试卷上的答案都是不一样的，这就是模板方法模式，是不是很好理解。它的主要用途在于将不变的行为从子类搬到超类，去除了子类中的重复代码。</p><p></p><p>　　模板方法模式（TemplateMethod），定义一个操作中的算法的骨架，而将一些步骤延迟到子类中，使得子类可以不改变一个算法的结构即可重定义该算法的某些特定步骤。<span style="color:#000000"><span style="font-size:14px"><span style="background-color:#ffffff">UML结构图如下:</span></span></span></p><p></p><div class="media-wrap image-wrap"><img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAOcAAAEmCAYAAACZN4eFAAAAAXNSR0IArs4c6QAAIABJREFUeF7tnQe0VTX2xoMVsaAg2EVFREXFBmJHHSyIoqCABdABdewKYm9jxV6xK1ZsFCs6UkRUVOw6jg0rfxVR6djLf/3C5M15h3vfPcl9t5x7v6zlkvfeSU7OTr58Ozt7Zzf466+//jKe5ccffzSNGjXyrPW/x1Vf8tP8yY2fBgKn/xqjxUWLSzEWF4HTH5tG4BQ4Bc4swBE4BI5igCPbul2s+SfmFHN6S6BYk7PU4Cj1+wVO76lppNbKIFgUg6jAKXB6S0DMWZxthcDpPTXFnAKnwJkVNpocxZkcpd5zVfv7xZxiTm8JaHEszuIocHpPTam1AqfAKbVW57wZJVAti4OYU8zpLYFqAUep97wCp/fUlForcBZJrZ0/f753VErAfFYVSUAS8JSAmNNTYDwu5igOc5RarSz1+wVOgdNbAlqcirM4CZzeU1PMKXAKnDpK0VGKjlJ8yUMrZ3FWzlLvefT+zBIo1vyXWuu7MskgJINYkULmBE6B01sCxWKOamdugdN7asogJHAWZ1sjcAqc3hIQOAVOWWtlrZW11nfp1MpZnJWz2vdc1f79Umt9VyZZa2WtlbU2O2rE3GJu3VurPU9V73mqXa0s9fenUq0988wzzeKLLx6gkC6o8ttvv6l+lcivS5cuZosttqg1V9KieTVIWzznRRddZF588UWz4447BoNTFatDAvPnzzd33HGHmTp1aio/OHXM+c9//tOQtfDcc89NpcDV6eJJ4NtvvzVt27Y106ZNSydzpi0FoMBZvMmd9jcJnAEjmI/OL3AGCLxKqwicAQMvcAYITVW8JSBweossP8dxMWeAwKu0isAZMPBizgChqYq3BAROb5Gllzlvv/12079/f7PbbruZ++67zzRt2rTm6/n5yCOPNM8884zp0KFDgFSKW4VjhuHDh5uhQ4ea5557zrRo0cIcfPDBZsCAAaZJkybmu+++MwceeKBp166dOf/8882iiy5a3A7Ww9scOKdMmVKrtZ9//tk0bNjQLLnkkkHn3fmQCx1JWl9HKQknwTfffGP69OljvvjiC5s49cEHHzStW7e2tTnaQd1+4oknzAMPPGDWXXfdhK0ueIy2jzrqKNvGJpts4lU3ycPx9gHewIEDzZNPPmkOOOAAs8suu5hXXnnF3HDDDaZ3797m0ksvNZ988onZb7/97HNHHHFEkteU3TMCZ8CQJF05MjVdqj0nrHnrrbdadjz22GNrMSTfc/zxx1uQ3XPPPWaFFVbwksrIkSPNddddZ9l41VVX9aqb5OFo+yuttJIFH++7++67LTAbNGhgfv/9dzN48GDDs/yeb9l1110tq+6www5JXlN2zwicAUOSNnA61tx6663Nvvvua3r27GlVPf5P+frrr81BBx1k1lhjDbP++uubW265xSy33HLmiiuuMJ06dTIzZswwV155pbn33nst82611VaWJZn0J510kmUsCgfmMPKECRPMjTfeaM455xzbBmzWuXNn+84RI0ZY98NevXqZCy+80DRr1sz8+eeflgWvueYaM27cONv+qaeeatXvePu0d8YZZ9hnACmqnSsAdJFFFrH/XXXVVVblfeihh+w3vfXWWwbvrKefftqqgixQgwYNMksvvXStv9EWLnMXX3yxVZWzfTvAZ1EoZBE4A6SbNnDCmkxqVNbGjRvbvRgq34knnmi//p133rE/s1djAgOYo48+2gIUJr3zzjvNXXfdZYYMGWJV3muvvdZ89tln5uqrrzY//PCD3cd27NjRAmmZZZaxoKTOtttua/bcc0/Tvn178/DDD5uXX37Z9uPLL780f//73+1zqJyPPvqoBTD7RdpiIQBEAH2xxRar1f7kyZPN7rvvbvuDmp6p/Prrrxbc//nPfyybL7HEErZtwItnFgtAv379rPZA33gn/eZv7GVPPvlky8hoEywYmb4dGay44ooBsyd5FYEzuaxqnkwTOB1rbrjhhpZp5s2bZ1mSn1EDmbiPPfaY6dq1q2W1bt26mZ9++skC9/PPP7eTGya9+eabLWMBtpVXXtmyE+X11183e+21l7nssstsu7Nnz7aTHdAC7NVWW20hCX/wwQemR48edgGAQXmefvE8Ex52BvwbbbSR/Xe0ffqD4acudXXmzJkW7DAfiwHGk2iZOHGi9W0GnFtuuaV9FjYHlPzMAuYKDJrt2wOmjlcVgdNLXAseThM4nYU2/plMSJhw2WWXXUgFnDt3rgUOKh2AgXEAJszL31D7YLdWrVpZYAMWZ+UFTDAz6jDMiOqH4zYsi+r64Ycf1nSFOmuuuaZVr/fZZ5+a56N9jbfvwEld3hFVaWE9gIV1E9B3797dnHba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"/></div><p></p><p style="text-align:left;text-indent:2em;">其中，AbstractClass实现类一个模板方法，定义了算法的骨架，具体子类将重定义PrimitiveOperation以实现一个算法的步骤；而ConcreteClass实现了PrimitiveOperation以完成算法中与特定子类相关的步骤。</p><p><strong>1. 抽象模板类</strong></p><p>定义一个模板方法来组合PrimitiveOperation1()和PrimitiveOperation2()两个方法形成一个算法，然后让子类重定义这两个方法。</p><p></p><pre><code>public abstract class AbstractClass {<br/><br/>    public abstract void PrimitiveOperation1();<br/>    public abstract void PrimitiveOperation2();<br/><br/>    public void TemplateMethod() {<br/>        PrimitiveOperation1();<br/>        PrimitiveOperation2();<br/>    }<br/><br/>}</code></pre><h3 style="text-align:left;text-indent:2em;"><strong>2. 具体模板类</strong></h3><p style="text-align:left;text-indent:2em;">　　</p><p>这里定义两个具体模板类，ConcreteClassA及ConcreteClassB来进行测试，继承抽象模板类，实现具体方法。</p><pre><code>public class ConcreteClassA extends AbstractClass {<br/><br/>    @Override<br/>    public void PrimitiveOperation1() {<br/>        System.out.println(&quot;具体方法A方法1实现&quot;);<br/>    }<br/><br/>    @Override<br/>    public void PrimitiveOperation2() {<br/>        System.out.println(&quot;具体方法A方法2实现&quot;);<br/>    }<br/><br/>}</code></pre><h3 style="text-align:left;text-indent:2em;"><strong>　3. Client客户端</strong></h3><p style="text-align:left;text-indent:2em;">　　</p><p>通过调用模板方法来分别得到不同的结果。</p><p></p><pre><code>public class Client {<br/><br/>    public static void main(String[] args) {<br/>        AbstractClass abstractClass;<br/><br/>        abstractClass = new ConcreteClassA();<br/>        abstractClass.TemplateMethod();<br/><br/>        abstractClass = new ConcreteClassB();<br/>        abstractClass.TemplateMethod();<br/>    }<br/><br/>}</code></pre><p><span style="color:#000000"><span style="font-size:14px"><span style="background-color:#ffffff"> 　　运行结果如下：</span></span></span></p><p></p><div class="media-wrap image-wrap float-left" style="float:left"><img src="data:image/png;base64,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"/></div><p></p><p></p><p></p><p></p><p></p><h2 style="text-align:left;text-indent:2em;"><strong>二、模板方法模式的应用</strong></h2><h3 style="text-align:left;text-indent:2em;"><strong>　　1. 何时使用</strong></h3><ul><li>有一些通用的方法时</li></ul><h3 style="text-align:left;text-indent:2em;"><strong>　　2. 方法</strong></h3><ul><li>将通用算法抽象出来</li></ul><h3 style="text-align:left;text-indent:2em;"><strong>　　3. 优点</strong></h3><ul><li>封装不变部分，扩展可变部分</li><li>提取公共部分代码，便于维护</li><li>行为由父类控制，子类实现</li></ul><h3 style="text-align:left;text-indent:2em;"><strong>　　4. 缺点</strong></h3><ul><li>每一个不同的实现都需要一个子类实现，导致类的个数增加，使得系统更加庞大</li></ul><h3 style="text-align:left;text-indent:2em;"><strong>　　5. 使用场景</strong></h3><ul><li>有多个子类共有的方法，且逻辑相同</li><li>重要的、复杂的方法，可以考虑作为模板方法</li><li>重构时，模板方法模式是一个经常使用到的模式，把相同的代码抽取到父类中，通过钩子函数约束其行为</li></ul><h3 style="text-align:left;text-indent:2em;"><strong>　　6. 应用实例</strong></h3><ul><li>做试卷，大家题目都是一样的，只是答案不同</li><li>对于汽车，车从发动到停车的顺序是相同的，不同的是引擎声、鸣笛声等</li><li>造房时，地基、走线、水管都一样，只有在建筑后期才有差异</li></ul><h3 style="text-align:left;text-indent:2em;"><strong>　　7. 注意事项</strong></h3><ul><li>为防恶意操作，一般模板方法都加上final关键字</li></ul><h2 style="text-align:left;text-indent:2em;"><strong>三、模板方法模式的实现</strong></h2><p style="text-align:left;text-indent:2em;">　　</p><p>下面就以上方提到的做试卷为例，具体实现一下以说明如何将模板方法模式应用在实际案例中，UML图如下：</p><p></p><div class="media-wrap image-wrap"><img src="data:image/png;base64,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"/></div><p></p><h3 style="text-align:left;text-indent:2em;"><strong>1. 试卷抽象类</strong></h3><p style="text-align:left;text-indent:2em;">　　</p><p>如下在抽象类中定义三个普通方法代表试卷的问题，再定义三个抽象方法代码试题答案。</p><p></p><pre><code>public class TestPaperA extends TestPaper {<br/><br/>    @Override<br/>    protected String answer1() {<br/>        return &quot;2&quot;;<br/>    }<br/><br/>    @Override<br/>    protected String answer2() {<br/>        return &quot;4&quot;;<br/>    }<br/><br/>    @Override<br/>    protected String answer3() {<br/>        return &quot;6&quot;;<br/>    }<br/><br/>}</code></pre><h3 style="text-align:left;text-indent:2em;"><strong>2. 具体试卷</strong></h3><p style="text-align:left;text-indent:2em;">　　</p><p>下面定义一个学生甲的试卷，学生乙的试卷与之相比只是返回的答案不同。</p><p></p><pre><code>public class TestPaperA extends TestPaper {<br/><br/>    @Override<br/>    protected String answer1() {<br/>        return &quot;2&quot;;<br/>    }<br/><br/>    @Override<br/>    protected String answer2() {<br/>        return &quot;4&quot;;<br/>    }<br/><br/>    @Override<br/>    protected String answer3() {<br/>        return &quot;6&quot;;<br/>    }<br/><br/>}</code></pre><h3 style="text-align:left;text-indent:2em;"><strong>　3. Client客户端</strong></h3><p style="text-align:left;text-indent:2em;">　　</p><p>基于同一个模板，学生甲乙分别进行答题，得到不一样的结果。</p><pre><code>public class Client {<br/><br/>    public static void main(String[] args) {<br/>        System.out.println(&quot;学生甲的试卷：&quot;);<br/>        TestPaper studentA = new TestPaperA();<br/>        studentA.question1();<br/>        studentA.question2();<br/>        studentA.question3();<br/><br/>        //分隔符<br/>        System.out.println(&quot;------------------------------------------------&quot;);<br/><br/>        System.out.println(&quot;学生乙的试卷：&quot;);<br/>        TestPaper studentB = new TestPaperB();<br/>        studentB.question1();<br/>        studentB.question2();<br/>        studentB.question3();<br/>    }<br/><br/>}</code></pre><p><span style="color:#000000"><span style="font-size:14px"><span style="background-color:#ffffff">运行结果如下：</span></span></span></p><p></p><p></p><div class="media-wrap image-wrap"><img src="data:image/png;base64,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"/></div><p><span style="color:#000000"><span style="font-size:14px"><span style="background-color:#ffffff">当我们要完成在某一细节层次一致的一个过程或一系列步骤，但其个别步骤在更详细的层次上的实现可能不同时，我们通常考虑用模板方法模式来处理。</span></span></span></p><p></p><p></p><p></p><p></p><p></p><p></p><p></p><p></p><p></p>
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 适配器模式和代理模式之间有什么不同？
这个问题与前面的类似，适配器模式和代理模式的区别在于他们的意图不同。由于适配器模式和代理模式都是封装真正执行动作的类，因此结构是一致的，但是适配器模式用于接口之间的转换，而代理模式则是增加一个额外的中间层，以便支持分配、控制或智能访问。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 适配器模式与装饰器模式有什么区别？
虽然适配器模式和装饰器模式的结构类似，但是每种模式的出现意图不同。适配器模式被用于桥接两个接口，而装饰模式的目的是在不修改类的情况下给类增加新的功能。

装饰者模式：动态地将责任附加到对象上，若要扩展功能，装饰者模提供了比继承更有弹性的替代方案。 
通俗的解释：装饰模式就是给一个对象增加一些新的功能，而且是动态的，要求装饰对象和被装饰对象实现同一个接口，装饰对象持有被装饰对象的实例。

适配器模式：将一个类的接口，转换成客户期望的另一个接口。适配器让原本接口不兼容的类可以合作无间。 
适配器模式有三种：类的适配器模式、对象的适配器模式、接口的适配器模式。 
通俗的说法：适配器模式将某个类的接口转换成客户端期望的另一个接口表示，目的是消除由于接口不匹配所造成的类的兼容性问题。

举例如下：

1、适配器模式 

```java
//file 为已定义好的文件流 
FileInputStream fileInput = new FileInputStream(file); 
InputStreamReader inputStreamReader = new InputStreamReader(fileInput);
```

以上就是适配器模式的体现，FileInputStream是字节流，而并没有字符流读取字符的一些api，因此通过InputStreamReader将其转为Reader子类，因此有了可以操作文本的文件方法。 

2、装饰者模式

BufferedReader bufferedReader=new BufferedReader(inputStreamReader);构造了缓冲字符流，将FileInputStream字节流包装为BufferedReader过程就是装饰的过程，刚开始的字节流FileInputStream只有read一个字节的方法，包装为inputStreamReader后，就有了读取一个字符的功能，在包装为BufferedReader后，就拥有了read一行字符的功能。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 简述一下你了解的 Java 设计模式（总结）
标星号的为常用设计模式

```
★单例模式：保证某个类只能有一个唯一实例，并提供一个全局的访问点。
★简单工厂：一个工厂类根据传入的参数决定创建出那一种产品类的实例。
工厂方法：定义一个创建对象的接口，让子类决定实例化那个类。
抽象工厂：创建一组相关或依赖对象族，比如创建一组配套的汉堡可乐鸡翅。
★建造者模式：封装一个复杂对象的构建过程，并可以按步骤构造，最后再build。
★原型模式：通过复制现有的实例来创建新的实例，减少创建对象成本（字段需要复杂计算或者创建成本高）。
 
★适配器模式：将一个类的方法接口转换成我们希望的另外一个接口。
★组合模式：将对象组合成树形结构以表示“部分-整体”的层次结构。（无限层级的知识点树）
★装饰模式：动态的给对象添加新的功能。
★代理模式：为对象提供一个代理以增强对象内的方法。
亨元（蝇量）模式：通过共享技术来有效的支持大量细粒度的对象（Integer中的少量缓存）。
★外观模式：对外提供一个统一的方法，来访问子系统中的一群接口。
桥接模式：将抽象部分和它的实现部分分离，使它们都可以独立的变化（比如插座和充电器，他们之间相插是固定的，
但是至于插座是插在220V还是110V，充电器是充手机还是pad可以自主选择）。
 
★模板方法模式：定义一个算法步骤，每个小步骤由子类各自实现。
解释器模式：给定一个语言，定义它的文法的一种表示，并定义一个解释器。
★策略模式：定义一系列算法，把他们封装起来，并且使它们可以相互替换。
★状态模式：允许一个对象根据其内部状态改变而改变它的行为。
★观察者模式：被观测的对象发生改变时通知它的所有观察者。
备忘录模式：保存一个对象的某个状态，以便在适当的时候恢复对象。
中介者模式：许多对象利用中介者来进行交互，将网状的对象关系变为星状的（最少知识原则）。
命令模式：将命令请求封装为一个对象，可用于操作的撤销或重做。
访问者模式：某种物体的使用方式是不一样的，将不同的使用方式交给访问者，而不是给这个物体。（例如对铜的使用，造币厂
造硬币。雕刻厂造铜像，不应该把造硬币和造铜像的功能交给铜自己实现，这样才能解耦）
★责任链模式：避免请求发送者与接收者耦合在一起，让多个对象都有可能接收请求，将这些对象连接成一条链，
并且沿着这条链传递请求，直到有对象处理它为止。
迭代器模式：一种遍历访问聚合对象中各个元素的方法，不暴露该对象的内部结构。
```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说说你所熟悉或听说过的 j2ee 中的几种常用模式?
IO 流的装饰器模式，Web 过滤器的责任链模式，Spring 的单例模式和工厂模式，
Spring 中根据不同配置方式进行初始化的策略模式

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 设计模式的类型
根据设计模式的参考书 Design Patterns - Elements of Reusable Object-Oriented Software（中文译名：设计模式 - 可复用的面向对象软件元素） 中所提到的，总共有 23 种设计模式。这些模式可以分为三大类：创建型模式（Creational Patterns）、结构型模式（Structural Patterns）、行为型模式（Behavioral Patterns）。当然，我们还会讨论另一类设计模式：J2EE 设计模式。

| 序号 | 模式 & 描述                                                  | 包括                                                         |
| :--- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| 1    | 创建型模式 这些设计模式提供了一种在创建对象的同时隐藏创建逻辑的方式，而不是使用 new 运算符直接实例化对象。这使得程序在判断针对某个给定实例需要创建哪些对象时更加灵活。 | 工厂模式（Factory Pattern）抽象工厂模式（Abstract Factory Pattern）单例模式（Singleton Pattern）建造者模式（Builder Pattern）原型模式（Prototype Pattern） |
| 2    | 结构型模式 这些设计模式关注类和对象的组合。继承的概念被用来组合接口和定义组合对象获得新功能的方式。 | 适配器模式（Adapter Pattern）桥接模式（Bridge Pattern）过滤器模式（Filter、Criteria Pattern）组合模式（Composite Pattern）装饰器模式（Decorator Pattern）外观模式（Facade Pattern）享元模式（Flyweight Pattern）代理模式（Proxy Pattern） |
| 3    | 行为型模式 这些设计模式特别关注对象之间的通信。          | 责任链模式（Chain of Responsibility Pattern）命令模式（Command Pattern）解释器模式（Interpreter Pattern）迭代器模式（Iterator Pattern）中介者模式（Mediator Pattern）备忘录模式（Memento Pattern）观察者模式（Observer Pattern）状态模式（State Pattern）空对象模式（Null Object Pattern）策略模式（Strategy Pattern）模板模式（Template Pattern）访问者模式（Visitor Pattern） |
| 4    | J2EE 模式 这些设计模式特别关注表示层。这些模式是由 Sun Java Center 鉴定的。 | MVC 模式（MVC Pattern）业务代表模式（Business Delegate Pattern）组合实体模式（Composite Entity Pattern）数据访问对象模式（Data Access Object Pattern）前端控制器模式（Front Controller Pattern）拦截过滤器模式（Intercepting Filter Pattern）服务定位器模式（Service Locator Pattern）传输对象模式（Transfer Object Pattern） |

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java怎么实现单例模式？
- 懒汉式：懒加载，线程不安全

```java
public class Singleton
{
    private static Singleton singleton;

    private Singleton()
    {
    }

    public static Singleton getInstance()
    {
        if (singleton == null)
            singleton = new Singleton();
        return singleton;
    }
}

```

- 懒汉式线程安全版：同步效率低

```java
public class Singleton
{
    private static Singleton singleton;

    private Singleton()
    {
    }

    public synchronized static Singleton getInstance()
    {
        if (singleton == null)
            singleton = new Singleton();
        return singleton;
    }
}

```

- 饿汉式：

```java
public class Singleton
{
    private static Singleton singleton = new Singleton();

    private Singleton()
    {
    }

    public static Singleton getInstance()
    {
        return singleton;
    }
}

```

- 饿汉式变种：

```java
public class Singleton
{
    private static Singleton singleton;
    static
    {
        singleton = new Singleton();
    }

    private Singleton()
    {
    }

    public static Singleton getInstance()
    {
        return singleton;
    }
}

```

- 静态内部类方式:利用 JVM 的加载机制，当使用到 SingletonHolder 才会进行初始化。

```java
public class Singleton
{
    private Singleton()
    {
    }

    private static class SingletonHolder
    {
        private static final Singleton singleton = new Singleton();
    }

    public static Singleton getInstance()
    {
        return SingletonHolder.singleton;
    }
}

```

- 枚举：

```java
public enum Singletons
{
    INSTANCE;
    // 此处表示单例对象里面的各种方法
    public void Method()
    {
    }
}
```

- 双重校验锁:

```java
public class Singleton
{
    private volatile static Singleton singleton;

    private Singleton()
    {
    }

    public static Singleton getInstance()
    {
        if (singleton == null)
        {
            synchronized (Singleton.class)
            {
                if (singleton == null)
                {
                    singleton = new Singleton();
                }
            }
        }
        return singleton;
    }
}

```

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 设计模式六大原则？
1、开闭原则（Open Close Principle）

开闭原则就是说对扩展开放，对修改关闭。在程序需要进行拓展的时候，不能去修改原有的代码，实现一个热插拔的效果。所以一句话概括就是：为了使程序的扩展性好，易于维护和升级。想要达到这样的效果，我们需要使用接口和抽象类，后面的具体设计中我们会提到这点。

2、里氏代换原则（Liskov Substitution Principle）

里氏代换原则(Liskov Substitution Principle LSP)面向对象设计的基本原则之一。 里氏代换原则中说，任何基类可以出现的地方，子类一定可以出现。 LSP是继承复用的基石，只有当衍生类可以替换掉基类，软件单位的功能不受到影响时，基类才能真正被复用，而衍生类也能够在基类的基础上增加新的行为。里氏代换原则是对“开-闭”原则的补充。实现“开-闭”原则的关键步骤就是抽象化。而基类与子类的继承关系就是抽象化的具体实现，所以里氏代换原则是对实现抽象化的具体步骤的规范。—— From Baidu 百科

3、依赖倒转原则（Dependence Inversion Principle）

这个是开闭原则的基础，具体内容：真对接口编程，依赖于抽象而不依赖于具体。

4、接口隔离原则（Interface Segregation Principle）

这个原则的意思是：使用多个隔离的接口，比使用单个接口要好。还是一个降低类之间的耦合度的意思，从这儿我们看出，其实设计模式就是一个软件的设计思想，从大型软件架构出发，为了升级和维护方便。所以上文中多次出现：降低依赖，降低耦合。

5、迪米特法则（最少知道原则）（Demeter Principle）

为什么叫最少知道原则，就是说：一个实体应当尽量少的与其他实体之间发生相互作用，使得系统功能模块相对独立。

6、合成复用原则（Composite Reuse Principle）

原则是尽量使用合成/聚合的方式，而不是使用继承

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 接口是什么？为什么要使用接口而不是直接使用具体类？
接口用于定义 API。它定义了类必须得遵循的规则。同时，它提供了一种抽象，因为客户端只使用接口，这样可以有多重实现，如 List 接口，你可以使用可随机访问的 ArrayList，也可以使用方便插入和删除的 LinkedList。接口中不允许写代码，以此来保证抽象，但是 Java 8 中你可以在接口声明静态的默认方法，这种方法是具体的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 非对称加密
示例

- 首先生成密钥对, 公钥为(5,14), 私钥为(11,14)
- 现在A希望将原文2发送给B
- A使用公钥加密数据. 2的5次方mod 14 = 4 , 将密文4发送给B
- B使用私钥解密数据. 4的11次方mod14 = 2, 得到原文2

特点

- 加密和解密使用不同的密钥
- 如果使用私钥加密, 只能使用公钥解密
- 如果使用公钥加密, 只能使用私钥解密
- 处理数据的速度较慢, 因为安全级别高

常见算法

- RSA
- ECC

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 复杂的对称加密（DES、PBE）、非对称加密算法
DES(Data Encryption Standard，数据加密算法)
PBE(Password-based encryption，基于密码验证)
RSA(算法的名字以发明者的名字命名：Ron Rivest, AdiShamir 和Leonard Adleman)
DH(Diffie-Hellman算法，密钥一致协议)
DSA(Digital Signature Algorithm，数字签名)
ECC(Elliptic Curves Cryptography，椭圆曲线密码编码学)

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 单向加密算法
单向加密是非可逆加密，就是不可解密的加密方法。
BASE64 严格地说，属于编码格式，而非加密算法
MD5(Message Digest algorithm 5，信息摘要算法)
SHA(Secure Hash Algorithm，安全散列算法)
HMAC(Hash Message Authentication Code，散列消息鉴别码)

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 密码的常用术语
1.密码体制：由明文空间、密文空间、密钥空间、加密算法和解密算法5部分组成。

2.密码协议：也称为安全协议，是指以密码学为基础的消息交换的通信协议，目的是在网络环境中提供安全的服务。

3.柯克霍夫原则：数据的安全基于密钥而不是算法的保密。即系统的安全取决于密钥，对密钥保密，对算法公开。——现代密码学设计的基本原则。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 解释一下HMAC
HMAC(Hash Message Authentication Code，散列消息鉴别码，基于密钥的Hash算法的认证协议。消息鉴别码实现鉴别的原理是，用公开函数和密钥产生一个固定长度的值作为认证标识，用这个标识鉴别消息的完整性。使用一个密钥生成一个固定大小的小数据块，即MAC，并将其加入到消息中，然后传输。接收方利用与发送方共享的密钥进行鉴别认证等。

我们为什么要使用加密算法，分析用户登录时密码安全问题的演变过程：

明文存储，这是一种最简单的存储方式，但是有着很大的安全隐患，首先密码暴露在网络传输的过程中，很容易被黑客拦截，其次如果服务器的数据库被脱库后，所有用户的密码一览无余，最后不称职的系统管理员可以很容易拿到用户登录密码，进行一些非法的交易，如果这个用户所有的密码都是一样的话，那么这个用户算是完蛋了。

所以后来演变为使用MD5来存储密码，但是这样也会出现问题，因为只要密码在网络中传输都有可能被黑客拦截，互联网上有着各种各样的MD5数据库，也是比较容易解密出用户原来的密码信息。对称加密算法，对称加密算法破解起来有一定的难度，但是关于这种加密算法有一个缺陷就是，客户端也需要进行加密，通过反编译或者查看网页源码等方式，也能够推算出加密算法，所以也存在着一定的风险性。基于以上出现的种种原因，采用非对称加密算法是一个非常不错的选择。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 解释一下SHA
安全哈希算法（Secure Hash Algorithm）主要适用于数字签名标准（Digital Signature Standard DSS）里面定义的数字签名算法（Digital Signature Algorithm DSA）。对于长度小于2^64位的消息，SHA1会产生一个160位的消息摘要。该算法经过加密专家多年来的发展和改进已日益完善，并被广泛使用。该算法的思想是接收一段明文，然后以一种不可逆的方式将它转换成一段（通常更小）密文，也可以简单的理解为取一串输入码（称为预映射或信息），并把它们转化为长度较短、位数固定的输出序列即散列值（也称为信息摘要或信息认证代码）的过程。散列函数值可以说是对明文的一种"指纹"或是"摘要"所以对散列值的数字签名就可以视为对此明文的数字签名。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## MD5
MD5即Message-Digest Algorithm 5（信息-摘要算法5），用于确保信息传输完整一致。是计算机广泛使用的杂凑算法之一（又译摘要算法、哈希算法），主流编程语言普遍已有MD5实现。将数据（如汉字）运算为另一固定长度值，是杂凑算法的基础原理，MD5的前身有MD2、MD3和MD4。广泛用于加密和解密技术，常用于文件校验。校验？不管文件多大，经过MD5后都能生成唯一的MD5值。好比现在的ISO校验，都是MD5校验。怎么用？当然是把ISO经过MD5后产生MD5的值。一般下载linux-ISO的朋友都见过下载链接旁边放着MD5的串。就是用来验证文件是否一致的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是base64
Base64是网络上最常见的用于传输8Bit字节码的编码方式之一，Base64就是一种基于64个可打印字符来表示二进制数据的方法，不属于加密算法，只是是编码方式。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java中常用的加密算法
散列算法

- MD5
- SHA

对称加密

- DES
- 3DES
- AES

非对称加密

- RSA
- ECC

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 段式虚拟存储器
段式管理: 把主存按段分配的存储管理方式.它是一种模块化的存储管理方式,每个用户程序模块可分到一个段,该程序模块只能访问分配给该模块的段所对应的主存空间.段长可以任意设定,并可放大和缩小.

系统中通过一个段表指明各段在主存中的位置.段表中包括段名(段号),段起点,装入位和段长等.段表本身也是一个段.段一般是按程序模块分的.

*** 
## ⭐️⭐️⭐️⭐️⭐️
## ####  18.页式虚拟存储器
页式管理:是把虚拟存储空间和实际空间等分成固定大小的页,各虚拟页可装入主存中的不同实际页面位置.页式存储中,处理机逻辑地址由虚页号和页内地址两部分组成,实际地址也分为页号和页内地址两部分,由地址映射机构将虚页号转换成主存的实际页号.

页式管理用一个页表,包括页号,每页在主存中起始位置,装入位等.页表是虚拟页号与物理页号的映射表.页式管理由操作系统进行,对应用程序员的透明的.

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 虚拟存储器的基本概念
虚拟存储器是指具有请求调入和置换功能，能从逻辑上对内存容量加以扩存的一种存储器系统

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 浮点数之间做加减法运算需要几个步骤？每个步骤都是必须的吗？为什么？
浮点数加减法需要经过以下几个步骤：对阶、尾数求和、尾数规格化、舍入、溢出判断。对阶是为了使得尾数可以进行运算，阶码不一致尾数运算无效，尾数规格化、舍入是为了正确存储结果，溢出判断是为了判断运算过程是否有误，如果溢出将会发出信号进行溢出处理。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是溢出？什么是上溢？什么是下溢？
溢出即计算机无法表示数值。上溢是指数值绝对值大于表示范围，下溢是指计算机无法提供有效精度表示数值。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 请计算12、124、1023、-1、-127的二进制原码。
12(0b1100)、124(0b1111100)、1023(0b1111111111)、-1(-0b1)、-127(-0b1111111)

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 计算机直接使用原码计算有什么缺点？
0有两种表示方法，减法运算复杂。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 二进制一般使用什么方法转换成十进制？
整数：按权展开法。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## ####  10. Cache中主存块的替换算法
|                   | 思想                                             | 优点                                                 | 缺点                                                         |
| ----------------- | ------------------------------------------------ | ---------------------------------------------------- | ------------------------------------------------------------ |
| 随机算法RAND      | 用软的或硬的随机数产生器产生上层中要被替换的页号 | 简单,易于实现                                        | 没有利用上层存储器使用的"历史信息",没有反映等程序局部性,命中率低. |
| 先进先出FIFO      | 选择最早装入上层的页作为被替换的页               | 实现方便,利用了主存历史的信息                        | 不能正确反映程序局部性原理,命中率不高,可能出现一种异常现象.  |
| 近期最少使用法LRU | 选择近期最少访问的页作为被替换的页               | 比较正确反映程序局部性,利用访存的历史信息,命中率较高 | 实现较复杂                                                   |
| 优化替换算法OPT   | 将未来近期不用的页换出去                         | 命中率最高,可作为衡量其他替换算法的标准              | 不现实,只是一种理想算法                                      |

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Cache和主存之间的映射方式
l 直接映射就是将主存地址映射到Cache中的一个指定地址.任何时候,主存中存储单元的数据只能调入到Cache中的一个位置,这是固定的,若这个位置已有数据,则产生冲突,原来的块将无条件地被替换出去.

l 全相联映射就是任何主存地址可映射到任何Cache地址的方式.在这种方式下,主存中存储单元的数据可调入到Cache中的任意位置.只有在Cache中的块全部装满后才会出现块冲突.

l 组相联映射指的是将存储空间的页面分成若干组,各组之间的直接映射,而组内各块之间则是全相联映射.

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Cache的基本工作原理
Cache通常由两部分组成,块表和快速存储器.其工作原理是:处理机按主存地址访问存储器,存储器地址的高段通过主存-Cache地址映射机构借助查块表判定该地址的存储单元是否在Cache中,如果在,则Cache命中,按Cache地址访问Cache.否则,Cache不命中,则需要访问主存,并从主存中调入相应数据块到Cache中,若Cache中已写满,则要按某种算法将Cache中的某一块替换出去,并修改有关的地址映射关系.

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 字长
l 机器字长：计算机能直接处理的二进制位数

l 指令字长：一个指令字中包含的二进制代码位数

l 存储字长：一个存储单元存储二进制代码长度

l CPI：执行一条指令需要的时钟周期数

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 程序访问的局部性
l 时间局部性:如果一个存储项被访问,则可能该项会很快被再次访问.

l 空间局部性:如果一个存储项被访问,则该项及其邻近的项也可能很快被访问. 

**解释**

计算机不能直接理解高级语言，只能直接理解机器语言，所以必须要把高级语言翻译成机器语言，计算机才能执行高级语言编写的程序。

翻译的方式有两种，一个是编译，一个是解释。

l 编译型语言写的程序在执行之前，需要一个专门的编译过程，把程序编译成为机器语言的文件，比如exe文件，如果源程序不变以后要运行的话就不用重新翻译。

l 解释则不同，解释性语言的程序不需要编译，在运行程序的时候才翻译，翻译一句执行一句，不生成目标程序，这样解释性语言每执行一次就要翻译一次，效率比较低。

l .java文件->编译->.class文件，编译成.class字节码,.class需要jvm解释，然后解释执行。Java很特殊，Java程序需要编译但是没有直接编译成机器语言，即二进制语言，而是编译成字节码（.class）再用解释方式执行。java程序编译以后的class属于中间代码，并不是可执行程序exe，不是二进制文件，所以在执行的时候需要一个中介来解释中间代码，这就是所谓的java虚拟机（JVM），也叫JDK。

l C语言编译过程分成四个步骤：

1， 由.c文件到.i文件，这个过程叫预处理

将#include包含的头文件直接拷贝到hell.c当中；将#define定义的宏进行替换，同时将代码中没用的注释部分删除等

2， 由.i文件到.s文件，这个过程叫编译

3， 由.s文件到.o文件，这个过程叫汇编

高级语言->汇编语言->机器语言

4， 由.o文件到可执行文件，这个过程叫链接

将翻译成的二进制与需要用到库绑定在一块

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 冯诺依曼机器的主要特点？
1）计算机由运算器、存储器、控制器、输入设备和输出设备五大部分组成；
2）指令和数据存储在存储器中，并可以按地址访问；
3）指令和数据均以二进制表示；
4）指令由操作码和地址码构成，操作码指明操作的性质，地址码表示操作数在存储器中的位置；
5）指令在存储器内按顺序存放，通常按自动的顺序取出执行；
6）机器以运算器为中心，I/O设备与存储器交换数据也要通过运算器。（因此，后来有了以存储器为中心的计算机结构）

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是计算机体系结构？什么是计算机组成？以乘法指令为例说明二者区别。
1）计算机体系结构是指那些能够被程序员看到的计算机的属性。如指令集、数据类型等；
2）计算机组成是指如何实现计算机体系结构所体现出来的属性；
3）以乘法指令为例，计算机是否有乘法指令，属于体系结构的问题。乘法指令是采用专用的乘法器，还是使用加法器和移位器构成，属于计算机组成的问题。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在计算机系统结构中，什么是翻译？什么是解释？
1）翻译：将一种语言编写的程序全部翻译成另一种语言，然后再执行；
2）解释：将一种语言编写的程序的一条语句翻译成另一种语言的一条或多条语句，然后执行，执行完这条语言后，再解释下一条。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 计算机系统5层层次结构从下到上由哪五层组成？哪些是物理机，哪些是虚拟机？
1）微程序机器、传统机器、操作系统机器、汇编语言机器、高级语言机器
2）微程序机器和传统机器是物理机，其他是虚拟机。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 计算机系统由哪两部分组成？计算机系统性能取决于什么？
计算机系统是由“硬件”和“软件”组成。衡量一台计算机性能的优劣是根据多项技术指标综合确定的，既包括硬件的各种性能指标，又包括软件的各种功能。

1）计算机系统由硬件和软件两部分组成。
2）计算机系统性能由硬件和软件共同决定。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在浏览器中输入url地址到显示主页的过程
百度好像最喜欢问这个问题。

> 打开一个网页，整个过程会使用哪些协议

图解（图片来源：《图解HTTP》）：

![img](https://my-blog-to-use.oss-cn-beijing.aliyuncs.com/2019-11/url%E8%BE%93%E5%85%A5%E5%88%B0%E5%B1%95%E7%A4%BA%E5%87%BA%E6%9D%A5%E7%9A%84%E8%BF%87%E7%A8%8B.jpg)

总体来说分为以下几个过程:

1. DNS解析
2. TCP连接
3. 发送HTTP请求
4. 服务器处理请求并返回HTTP报文
5. 浏览器解析渲染页面
6. 连接结束

具体可以参考下面这篇文章：

- https://segmentfault.com/a/1190000006879700


*** 
## ⭐️⭐️⭐️⭐️⭐️
## 滑动窗口和流量控制
TCP 利用滑动窗口实现流量控制。流量控制是为了控制发送方发送速率，保证接收方来得及接收。 接收方发送的确认报文中的窗口字段可以用来控制发送方窗口大小，从而影响发送方的发送速率。将窗口字段设置为 0，则发送方不能发送数据。



*** 
## ⭐️⭐️⭐️⭐️⭐️
## TCP建立连接时为什么要传回 SYN
接收端传回发送端所发送的 SYN 是为了告诉发送端，我接收到的信息确实就是你所发送的信号了。

> SYN 是 TCP/IP 建立连接时使用的握手信号。在客户机和服务器之间建立正常的 TCP 网络连接时，客户机首先发出一个 SYN 消息，服务器使用 SYN-ACK 应答表示接收到了这个消息，最后客户机再以 ACK(Acknowledgement[汉译：确认字符 ,在数据通信传输中，接收站发给发送站的一种传输控制字符。它表示确认发来的数据已经接受无误。 ]）消息响应。这样在客户机和服务器之间才能建立起可靠的TCP连接，数据才可以在客户机和服务器之间传递。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么TCP要三次握手
三次握手的目的是建立可靠的通信信道，说到通讯，简单来说就是数据的发送与接收，而三次握手最主要的目的就是双方确认自己与对方的发送与接收是正常的。

第一次握手：Client 什么都不能确认；Server 确认了对方发送正常，自己接收正常

第二次握手：Client 确认了：自己发送、接收正常，对方发送、接收正常；Server 确认了：对方发送正常，自己接收正常

第三次握手：Client 确认了：自己发送、接收正常，对方发送、接收正常；Server 确认了：自己发送、接收正常，对方发送、接收正常

所以三次握手就能确认双发收发功能都正常，缺一不可。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说一说TCP的三次握手
在TCP/IP协议中，TCP协议提供可靠的连接服务，连接是通过三次握手进行初始化的。三次握手的目的是同步连接双方的序列号和确认号并交换TCP窗口大小信息

![图片描述](https://segmentfault.com/img/bVTyxj?w=600&h=669)

- 核心思想：让双方都证实对方能发收。知道对方能收是因为收到对方的因为收到信息之后发的回应(ACK)。
- 客户端–发送带有 SYN 标志的数据包–一次握手–服务端
- 服务端–发送带有 SYN/ACK 标志的数据包–二次握手–客户端
- 客户端–发送带有带有 ACK 标志的数据包–三次握手–服务端

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 简述ICMP、TFTP、HTTP、NAT、DHCP协议
ICMP : 因特网控制报文协议。它是TCP/IP协议族的一个子协议，用于在IP主机、路由器之间传递控制消息

TFTP：是TCP/IP协议族中的一个用来在客户机和服务器之间进行简单的文件传输的协议，提供不复杂、开销不大的文件传输服务

HTTP：超文本传输层协议，是一个属于应用层的面向对象的协议

NAT协议：网络地址转换接入广域网（WAN）技术，是一种将私有地址转换为合法IP地址的转换技术

DHCP协议：动态主机配置协议，使用UDP协议工作。给内部的网络和网络服务供应商自动的分配IP地址。

RARP是逆地址解析协议，作用是完成从硬件地址到IP地址的映射，RARP只能用于具有广播能力的网络。封装一个RARP的数据包里面有MAC地址， 然后广播到网络上，当服务器收到请求包后，就查找对应的MAC地址的IP地址装入到响应报文中发送给请求者。

一些常见的端口号及其用途：

TCP 21端口 ： FTP 文件传输服务

TCP 23 端口：TELNET 终端仿真服务

TCP 25端口：SMTP简单邮件传输服务

UDP 53端口：DNS域名解析服务

TCP 80端口：HTTP超文本传输服务

TCP 109端口：POP2邮局协议2

TCP 110端口 ： POP3邮局协议版本3使用的端口

UDP 69 端口：TFTP 简单文件传输协议

3306：Mysql端口号

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 简述ARP地址解析协议工作原理
首先， 每个主机会在自己的ARP缓冲区简历一个ARP列表，以表示IP地址和MAC地址之间的对应关系。

当源主机要发送数据时，首先检查自己的ARP列表中是否有对应的目的主机的MAC地址，如果有就直接发送数据，如果没有，就向本网段的所有的主机发送ARP数据包， 该数据包括的内容由：源主机IP地址，源主机的MAC地址，目的主机的IP地址

当本网络的所有主机收到ARP数据包时，首先检查数据包中的IP地址是否是自己的IP地址，如果不是，则忽略该数据包，如果是，则首先从数据包中取出源主机的IP和MAC地址写入到ARP列表中，如果已经存在，则覆盖，然后将自己的MAC地址中放入到ARP响应包中，告诉源主机自己是它想找的MAC地址。

源主机接收到ARP响应包后，将目的主机的IP和MAC地址写入到ARP列表，并利用此消息发送数据。如果源主机一直没有收到ARP响应数据包，表示ARP查询失败。

广播发送ARP请求，单播发送ARP响应。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 简述IP地址的分类?
IP地址分为网络号和主机号， A类地址的前8位是网络地址，B类地址的前16位是网络地址，C类地址的前24位是网络地址。

A类地址： 1.0.0.0~126.0.0.0

B类地址：128.0.0.0 ~ 191.255.255.255

C类地址：192.0.0.0 ~ 223.255.255.255

D类地址：224.0.0.0 ~ 239.255.255.255 （作为多播使用）

E类地址：保留

A,B,C是基本类，D、E类作为多播和保留使用。主机号，全0的是网络号，主机号全1的是广播地址。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 你能说一说OSI七层模型?
![img](https://pic3.zhimg.com/80/v2-2af488004591cbc12cd82c44518523de_720w.jpg)

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 有哪些私有（保留）地址？
A类：10.0.0.0 - 10.255.255.255

B类：172.16.0.0 - 172.31.255.255

C类：192.168.0.0 - 192.168.255.255

*** 
## ⭐️⭐️⭐️⭐️⭐️
## TCP对应的协议和UDP对应的协议
TCP对应的协议：

- FTP：定义了文件传输协议，使用21端口。
- Telnet：一种用于远程登陆的端口，使用23端口，用户可以以自己的身份远程连接到计算机上，可提供基于DOS模式下的通信服务。
- SMTP：邮件传送协议，用于发送邮件。服务器开放的是25号端口。
- POP3：它是和SMTP对应，POP3用于接收邮件。POP3协议所用的是110端口。
- HTTP：是从Web服务器传输超文本到本地浏览器的传送协议。

UDP对应的协议：

- DNS：用于域名解析服务，将域名地址转换为IP地址。DNS用的是53号端口。
- SNMP：简单网络管理协议，使用161号端口，是用来管理网络设备的。由于网络设备很多，无连接的服务就体现出其优势。
- TFTP(Trival File TransferProtocal)，简单文件传输协议，该协议在熟知端口69上使用UDP服务。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 请简述TCP/UDP的区别
TCP和UDP是OSI模型中的运输层中的协议。TCP提供可靠的通信传输，而UDP则常被用于让广播和细节控制交给应用的通信传输。
两者的区别大致如下：

- TCP面向连接，UDP面向非连接即发送数据前不需要建立链接
- TCP提供可靠的服务（数据传输），UDP无法保证
- TCP面向字节流，UDP面向报文
- TCP数据传输慢，UDP数据传输快
- TCP提供一种面向连接的、可靠的字节流服务
- 在一个TCP连接中，仅有两方进行彼此通信，因此广播和多播不能用于TCP
- TCP使用校验和，确认和重传机制来保证可靠传输
- TCP使用累积确认
- TCP使用滑动窗口机制来实现流量控制，通过动态改变窗口的大小进行拥塞控制



*** 
## ⭐️⭐️⭐️⭐️⭐️
## BASE理论了解过吗？
BASE是 Basically Available (基本可用) Soft state(软状态) Eventually consistent(最终一致性)这几个单词的缩写,是从CAP理论发展而来的,其核心思想是:即使无法做到强一致性,但每个应用都可以根据自身特点,采取适当的方式来使系统达到最终一致性.

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何保障请求执行顺序
一般来说，从业务逻辑上最好设计系统不需要这种顺序的保证，因为一旦引入顺序性保障，会导致系统复杂度的上升，效率会降低，对于热点数据会压力过大等问题。
首先使用一致性hash负载均衡策略，将同一个id的请求都分发到同一个机器上面去处理，比如订单可以根据订单id。如果处理的机器上面是多线程处理的，可以引入内存队列去处理，将相同id的请求通过hash到同一个队列当中，一个队列只对应一个处理线程。
最好能将多个操作合并成一个操作。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 分布式系统的接口幂等性设计
唯一id。每次操作，都根据操作和内容生成唯一的id，在执行之前先判断id是否存在，如果不存在则执行后续操作，并且保存到数据库或者redis等。
服务端提供发送token的接口，业务调用接口前先获取token,然后调用业务接口请求时，把token携带过去,务器判断token是否存在redis中，存在表示第一次请求，可以继续执行业务，执行业务完成后，最后需要把redis中的token删除
建去重表。将业务中有唯一标识的字段保存到去重表，如果表中存在，则表示已经处理过了
版本控制。增加版本号，当版本号符合时，才能更新数据
状态控制。例如订单有状态已支付 未支付 支付中 支付失败，当处于未支付的时候才允许修改为支付中等

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何设计一个秒杀系统?
前端：在秒杀之前，按钮置灰，并且不给前端真正的请求地址。前端定时请求后端接口，如果到了秒杀时间，则返回给前端真正的地址，前端放开按钮，每次点击后都要等X秒才能点击。
服务器：服务器用nginx做集群、redis也做集群
限流：在秒杀之前，将秒杀数量的令牌存入到redis中，可以用list，每次来请求都去redis中取出令牌，如果获取到说明秒杀成功，然后去访问数据库下单，如果没有获取到，则说明商品卖完了。
消息中间件：如果秒杀数量比较多，例如上万十万，则秒杀成功之后，将成功的请求放入到mq或者kafka中间件中，再从消息队列中获取请求。
服务降级：为了以防万一，还是要做服务熔断降级。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何防止表单重复提交？
前端。每次点击后都要等X秒才能点击。
数据库添加唯一索引
服务器返回表单页面时，会先生成一个token保存于session或redis，当表单提交时候携带token，如果token一致，则执行后续，并将服务器中的token删除。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 分布式 Session了解过吗？如何实现？
如果不做任何处理的话，用户将出现频繁登录的现象，比如集群中存在 A、B 两台服务器，用户在第一次访问网站时，Nginx 通过其负载均衡机制将用户请求转发到 A 服务器，这时 A 服务器就会给用户创建一个 Session。当用户第二次发送请求时，Nginx 将其负载均衡到 B 服务器，而这时候 B 服务器并不存在 Session，所以就会将用户踢到登录页面。这将大大降低用户体验度，导致用户的流失，这种情况是项目绝不应该出现的。

1. 粘性 Session
原理
粘性 Session 是指将用户锁定到某一个服务器上，比如上面说的例子，用户第一次请求时，负载均衡器将用户的请求转发到了 A 服务器上，如果负载均衡器设置了粘性 Session 的话，那么用户以后的每次请求都会转发到 A 服务器上，相当于把用户和 A 服务器粘到了一块，这就是粘性 Session 机制。

优点
简单，不需要对 Session 做任何处理。

缺点
缺乏容错性，如果当前访问的服务器发生故障，用户被转移到第二个服务器上时，他的 Session 信息都将失效。

适用场景
发生故障对客户产生的影响较小；
服务器发生故障是低概率事件。

2. 服务器 Session 复制

原理
任何一个服务器上的 Session 发生改变，该节点会把这个 Session 的所有内容序列化，然后广播给所有其它节点，不管其他服务器需不需要 Session，以此来保证 Session 同步。

优点
可容错，各个服务器间 Session 能够实时响应。

缺点
会对网络负荷造成一定压力，如果 Session 量大的话可能会造成网络堵塞，拖慢服务器性能。

实现方式
设置 Tomcat 的 server.xml 开启 tomcat 集群功能。
在应用里增加信息：通知应用当前处于集群环境中，支持分布式，即在 web.xml 中添加 选项。

3. Session 共享机制

使用分布式缓存方案比如 Memcached、Redis，但是要求 Memcached 或 Redis 必须是集群。
使用 Session 共享也分两种机制，两种情况如下：

3.1 粘性 Session 共享机制
和粘性 Session 一样，一个用户的 Session 会绑定到一个 Tomcat 上。Memcached 只是起到备份作用。

3.2 非粘性 Session 共享机制

原理
Tomcat 本身不存储 Session，而是存入 Memcached 中。Memcached 集群构建主从复制架构。

优点
可容错，Session 实时响应。
实现方式
用开源的 msm 插件解决 Tomcat 之间的 Session 共享：Memcached_Session_Manager（MSM）

4. Session 持久化到数据库

原理
拿出一个数据库，专门用来存储 Session 信息。保证 Session 的持久化。

优点
服务器出现问题，Session 不会丢失。

缺点
如果网站的访问量很大，把 Session 存储到数据库中，会对数据库造成很大压力，还需要增加额外的开销维护数据库。

5. Terracotta 实现 Session 复制

原理
Terracotta 的基本原理是对于集群间共享的数据，当在一个节点发生变化的时候，Terracotta 只把变化的部分发送给 Terracotta 服务器，然后由服务器把它转发给真正需要这个数据的节点。它是服务器 Session 复制的优化。

优点
这样对网络的压力就非常小，各个节点也不必浪费 CPU 时间和内存进行大量的序列化操作。把这种集群间数据共享的机制应用在 Session 同步上，既避免了对数据库的依赖，又能达到负载均衡和灾难恢复的效果。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 正向代理和反向代理的区别
正向代理：发生在客户端，是由用户主动发起的。比如翻墙，客户端通过主动访问代理服务器，让代理服务器获得需要的外网数据，然后转发回客户端。
反向代理：发生在服务器端，用户不知道发生了代理。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 负载均衡的实现方案有哪些？
DNS 解析
使用 DNS 作为负载均衡器，会根据负载情况返回不同服务器的 IP 地址。大型网站基本使用了这种方式最为第一级负载均衡手段，然后在内部在第二级负载均衡。

修改 MAC 地址
使用 LVS（Linux Virtual Server）这种链路层负载均衡器，根据负载情况修改请求的 MAC 地址。

修改 IP 地址
在网络层修改请求的目的 IP 地址。

HTTP 重定向
HTTP 重定向负载均衡服务器收到 HTTP 请求之后会返回服务器的地址，并将该地址写入 HTTP 重定向响应中返回给浏览器，浏览器收到后再次发送请求。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 了解过哪些负载均衡算法？
轮询（Round Robin）
轮询算法把每个请求轮流发送到每个服务器上。
该算法比较适合每个服务器的性能差不多的场景，如果有性能存在差异的情况下，那么性能较差的服务器可能无法承担多大的负载。

加权轮询（Weighted Round Robbin）
加权轮询是在轮询的基础上，根据服务器的性能差异，为服务器赋予一定的权值。

最少连接（least Connections）
由于每个请求的连接时间不一样，使用轮询或者加权轮询算法的话，可能会让一台服务器当前连接数过多，而另一台服务器的连接数过少，造成负载不均衡。最少连接算法就是将请求发送给当前最少连接数的服务器上。

加权最小连接（Weighted Least Connection）
在最小连接的基础上，根据服务器的性能为每台服务器分配权重，然后根据权重计算出每台服务器能处理的连接数。

随机算法（Random）
把请求随机发送到服务器上。和轮询算法类似，该算法比较适合服务器性能差不多的场景。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## TCC了解过吗？
try,commit,cancel的缩写,try阶段进行检测,commit提交执行,只要try阶段成功了commit就一定会被执行,cancel业务出现错误时执行,回滚事务,释放资源.

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是二阶段提交（2PC）？什么是三阶段提交（3PC）？
二阶段提交2PC:第一步请求阶段通过协调者来统计表决结果,第二步执行表决后的结果,如果表决的结果是提交,那就提交执行,否则不执行提交.缺点是同步阻塞,而且万一协调者挂了就无法保证ACID.

三阶段提交3PC:在2PC的第一步拆分成了2步并且引入了超时机制,解决了2PC的痛点.第一步先向参与者发出一个信号,看看大家是否都能提交,如果可以就返回yes,否则返回no.第二步PreCommit阶段,预提交一下,如果参与者可以完成commit,就返回ack进确认,如果不能则放弃提交本次事务.第三步doCommit阶段,进行真正的事务提交.

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 分布式事务了解过吗？
涉及到多个数据库操作的事务即为分布式事务,目的是为保证分布式系统中的数据一致性.

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是CAP定理？
任何分布式系统都无法同时满足一致性(consistency),可用性(availibity),分区容错性(partition tolerance)这三项,最多只可同时满足其中的两项。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 雪花算法了解过吗？
雪花算法生成的是Long类型的ID，一个Long类型占8个字节，每个字节占8比特，也就是说一个Long类型占64个比特。 雪花ID组成结构：正数位（占1比特）+ 时间戳（占41比特）+ 机器ID（占5比特）+ 数据中心（占5比特）+ 自增值（占12比特），总共64比特组成的一个Long类型。 第一个bit位（1bit）：Java中long的最高位是符号位代表正负，正数是0，负数是1，一般生成ID都为正数，所以默认为0。 时间戳部分（41bit）：毫秒级的时间，不建议存当前时间戳，而是用（当前时间戳 - 固定开始时间戳）的差值，可以使产生的ID从更小的值开始；41位的时间戳可以使用69年，(1L << 41) / (1000L * 60 * 60 * 24 * 365) = 69年 工作机器id（10bit）：也被叫做workId，这个可以灵活配置，机房或者机器号组合都可以。 序列号部分（12bit），自增值支持同一毫秒内同一个节点可以生成4096个ID

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 在Java中Lock接口比synchronized块的优势是什么？你需要实现一个高效的缓存，它允许多个用户读，但只允许一个用户写，以此来保持它的完整性，你会怎样去实现它？
lock接口在多线程和并发编程中最大的优势是它们为读和写分别提供了锁，它能满足你写像ConcurrentHashMap这样的高性能数据结构和有条件的阻塞。Java线程面试的问题越来越会根据面试者的回答来提问。我强烈建议在你去参加多线程的面试之前认真读一下Locks，因为当前其大量用于构建电子交易终统的客户端缓存和交易连接空间。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 高并发、任务执行时间短的业务怎样使用线程池？并发不高、任务执行时间长的业务怎样使用线程池？并发高、业务执行时间长的业务怎样使用线程池？1）高并发、任务执行时间短的业务，线程池线程数可以设置为CPU核数+1，减少线程上下文的切换

2）并发不高、任务执行时间长的业务要区分开看：
a）假如是业务时间长集中在IO操作上，也就是IO密集型的任务，因为IO操作并不占用CPU，所以不要让所有的CPU闲下来，可以加大线程池中的线程数目，让CPU处理更多的业务
b）假如是业务时间长集中在计算操作上，也就是计算密集型任务，这个就没办法了，和（1）一样吧，线程池中的线程数设置得少一些，减少线程上下文的切换
c）并发高、业务执行时间长，解决这种类型任务的关键不在于线程池而在于整体架构的设计，看看这些业务里面某些数据是否能做缓存是第一步，增加服务器是第二步，至于线程池的设置，设置参考其他有关线程池的文章。最后，业务执行时间长的问题，也可能需要分析一下，看看能不能使用中间件对任务进行拆分和解耦。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Hashtable的size()方法中明明只有一条语句"return count"，为什么还要做同步？
1）同一时间只能有一条线程执行固定类的同步方法，但是对于类的非同步方法，可以多条线程同时访问。所以，这样就有问题了，可能线程A在执行Hashtable的put方法添加数据，线程B则可以正常调用size()方法读取Hashtable中当前元素的个数，那读取到的值可能不是最新的，可能线程A添加了完了数据，但是没有对size++，线程B就已经读取size了，那么对于线程B来说读取到的size一定是不准确的。而给size()方法加了同步之后，意味着线程B调用size()方法只有在线程A调用put方法完毕之后才可以调用，这样就保证了线程安全性

2）CPU执行代码，执行的不是Java代码，这点很关键，一定得记住。Java代码最终是被翻译成机器码执行的，机器码才是真正可以和硬件电路交互的代码。即使你看到Java代码只有一行，甚至你看到Java代码编译之后生成的字节码也只有一行，也不意味着对于底层来说这句语句的操作只有一个。一句"return count"假设被翻译成了三句汇编语句执行，一句汇编语句和其机器码做对应，完全可能执行完第一句，线程就切换了。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Semaphore有什么作用？
Semaphore就是一个信号量，它的作用是限制某段代码块的并发数。Semaphore有一个构造函数，可以传入一个int型整数n，表示某段代码最多只有n个线程可以访问，如果超出了n，那么请等待，等到某个线程执行完毕这段代码块，下一个线程再进入。由此可以看出如果Semaphore构造函数中传入的int型整数n=1，相当于变成了一个synchronized了。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 单例模式的线程安全性
1）饿汉式单例模式的写法：线程安全

2）懒汉式单例模式的写法：非线程安全

3）双检锁单例模式的写法：线程安全

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Thread.sleep(0)的作用是什么？
由于Java采用抢占式的线程调度算法，因此可能会出现某条线程常常获取到CPU控制权的情况，为了让某些优先级比较低的线程也能获取到CPU控制权，可以使用Thread.sleep(0)手动触发一次操作系统分配时间片的操作，这也是平衡CPU控制权的一种操作。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java中用到的线程调度算法是什么？
抢占式。一个线程用完CPU之后，操作系统会根据线程优先级、线程饥饿情况等数据算出一个总的优先级并分配下一个时间片给某个线程执行。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java中如何获取到线程dump文件
死循环、死锁、阻塞、页面打开慢等问题，打线程dump是最好的解决问题的途径。所谓线程dump也就是线程堆栈，获取到线程堆栈有两步：

1）获取到线程的pid，可以通过使用jps命令，在Linux环境下还可以使用ps -ef | grep java
2）打印线程堆栈，可以通过使用jstack pid命令，在Linux环境下还可以使用kill -3 pid

另外提一点，Thread类提供了一个getStackTrace()方法也可以用于获取线程堆栈。这是一个实例方法，因此此方法是和具体线程实例绑定的，每次获取获取到的是具体某个线程当前运行的堆栈。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是线程安全？
如果你的代码在多线程下执行和在单线程下执行永远都能获得一样的结果，那么你的代码就是线程安全的。

这个问题有值得一提的地方，就是线程安全也是有几个级别的：

1）不可变
像String、Integer、Long这些，都是final类型的类，任何一个线程都改变不了它们的值，要改变除非新创建一个，因此这些不可变对象不需要任何同步手段就可以直接在多线程环境下使用

2）绝对线程安全
不管运行时环境如何，调用者都不需要额外的同步措施。要做到这一点通常需要付出许多额外的代价，Java中标注自己是线程安全的类，实际上绝大多数都不是线程安全的，不过绝对线程安全的类，Java中也有，比方说CopyOnWriteArrayList、CopyOnWriteArraySet

3）相对线程安全
相对线程安全也就是我们通常意义上所说的线程安全，像Vector这种，add、remove方法都是原子操作，不会被打断，但也仅限于此，如果有个线程在遍历某个Vector、有个线程同时在add这个Vector，99%的情况下都会出现ConcurrentModificationException，也就是fail-fast机制。

4）线程非安全
这个就没什么好说的了，ArrayList、LinkedList、HashMap等都是线程非安全的类，点击这里了解为什么不安全。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 线程池都有哪几种工作队列？
ArrayBlockingQueue：是一个基于数组结构的有界阻塞队列，此队列按FIFO（先进先出）原则对元素进行排序。
LinkedBlockingQueue：是一个基于链表结构的阻塞队列，此队列按FIFO排序元素，吞吐量通常要高于ArrayBlockingQueue。静态工厂方法Executors.newFixedThreadPool()使用了这个队列。
SynchronousQueue：是一个不存储元素的阻塞队列。每个插入操作必须等到另一个线程调用移除操作，否则插入操作一直处于阻塞状态，吞吐量通常要高于Linked-BlockingQueue，静态工厂方法Executors.newCachedThreadPool使用了这个队列。
PriorityBlockingQueue：一个具有优先级的无限阻塞队列。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说一说几种常见的线程池及适用场景？
FixedThreadPool：可重用固定线程数的线程池。（适用于负载比较重的服务器）
FixedThreadPool使用无界队列LinkedBlockingQueue作为线程池的工作队列
该线程池中的线程数量始终不变。当有一个新的任务提交时，线程池中若有空闲线程，则立即执行。若没有，则新的任务会被暂存在一个任务队列中，待有线程空闲时，便处理在任务队列中的任务。

SingleThreadExecutor：只会创建一个线程执行任务。（适用于需要保证顺序执行各个任务；并且在任意时间点，没有多线程活动的场景。）
SingleThreadExecutorl也使用无界队列LinkedBlockingQueue作为工作队列
若多余一个任务被提交到该线程池，任务会被保存在一个任务队列中，待线程空闲，按先入先出的顺序执行队列中的任务。

CachedThreadPool：是一个会根据需要调整线程数量的线程池。（大小无界，适用于执行很多的短期异步任务的小程序，或负载较轻的服务器）
CachedThreadPool使用没有容量的SynchronousQueue作为线程池的工作队列，但CachedThreadPool的maximumPool是无界的。
线程池的线程数量不确定，但若有空闲线程可以复用，则会优先使用可复用的线程。若所有线程均在工作，又有新的任务提交，则会创建新的线程处理任务。所有线程在当前任务执行完毕后，将返回线程池进行复用。

ScheduledThreadPool：继承自ThreadPoolExecutor。它主要用来在给定的延迟之后运行任务，或者定期执行任务。使用DelayQueue作为任务队列。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## synchronized 关键字和 volatile 关键字的区别
volatile关键字是线程同步的轻量级实现，所以volatile性能比synchronized关键字要好。但是volatile关键字只能用于变量而synchronized关键字可以修饰方法以及代码块。
多线程访问volatile关键字不会发生阻塞，而synchronized关键字可能会发生阻塞。
volatile关键字主要用于解决变量在多个线程之间的可见性，而 synchronized关键字解决的是多个线程之间访问资源的同步性。
volatile关键字能保证数据的可见性，但不能保证数据的原子性。synchronized关键字两者都能保证。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是线程的阻塞问题？如何解决？
阻塞是用来形容多线程的问题，几个线程之间共享临界区资源，那么当一个线程占用了临界区资源后，所有需要使用该资源的线程都需要进入该临界区等待，等待会导致线程挂起，一直不能工作，这种情况就是阻塞，如果某一线程一直都不释放资源，将会导致其他所有等待在这个临界区的线程都不能工作。当我们使用synchronized或重入锁时，我们得到的就是阻塞线程，如论是synchronized或者重入锁，都会在试图执行代码前，得到临界区的锁，如果得不到锁，线程将会被挂起等待，知道其他线程执行完成并释放锁且拿到锁为止。

解决方法：
可以通过减少锁持有时间，读写锁分离，减小锁的粒度，锁分离，锁粗化等方式来优化锁的性能。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是线程的饥饿问题？如何解决？
饥饿指的是某一线程或多个线程因为某些原因一直获取不到资源，导致程序一直无法执行。如某一线程优先级太低导致一直分配不到资源，或者是某一线程一直占着某种资源不放，导致该线程无法执行等。

解决方法：
与死锁相比，饥饿现象还是有可能在一段时间之后恢复执行的。可以设置合适的线程优先级来尽量避免饥饿的产生。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是活锁？
活锁体现了一种谦让的美德，每个线程都想把资源让给对方，但是由于机器“智商”不够，可能会产生一直将资源让来让去，导致资源在两个线程间跳动而无法使某一线程真正的到资源并执行，这就是活锁的问题。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是线程安全问题？如何解决？
线程安全问题指的是在某一线程从开始访问到结束访问某一数据期间，该数据被其他的线程所修改，那么对于当前线程而言，该线程就发生了线程安全问题，表现形式为数据的缺失，数据不一致等。

线程安全问题发生的条件：

1）多线程环境下，即存在包括自己在内存在有多个线程。
2）多线程环境下存在共享资源，且多线程操作该共享资源。
3）多个线程必须对该共享资源有非原子性操作。

线程安全问题的解决思路：
1）尽量不使用共享变量，将不必要的共享变量变成局部变量来使用。
2）使用synchronized关键字同步代码块，或者使用jdk包中提供的Lock为操作进行加锁。
3）使用ThreadLocal为每一个线程建立一个变量的副本，各个线程间独立操作，互不影响。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么我们调用 start() 方法时会执行 run() 方法，为什么我们不能直接调用 run() 方法？
new 一个 Thread，线程进入初始状态；调用 start()方法，会启动一个线程并使线程进入了就绪状态，当分配到时间片后就可以开始运行了。 start() 会执行线程的相应准备工作，然后自动执行 run() 方法的内容，这是真正的多线程工作。 而直接执行 run() 方法，会把 run 方法当成一个 main 线程下的普通方法去执行，并不会在某个线程中执行它，所以这并不是多线程工作。

总结： 调用 start 方法可启动线程并使线程进入就绪状态，而 run 方法只是 thread 的一个普通方法调用，还是在主线程里执行。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## sleep() 方法和 wait() 方法的区别和共同点?
相同点：
两者都可以暂停线程的执行，都会让线程进入等待状态。

不同点：
sleep()方法没有释放锁，而 wait()方法释放了锁。
sleep()方法属于Thread类的静态方法，作用于当前线程；而wait()方法是Object类的实例方法，作用于对象本身。
执行sleep()方法后，可以通过超时或者调用interrupt()方法唤醒休眠中的线程；执行wait()方法后，通过调用notify()或notifyAll()方法唤醒等待线程。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是线程死锁?如何避免死锁?
多个线程同时被阻塞，它们中的一个或者全部都在等待某个资源被释放。由于线程被无限期地阻塞，因此程序不可能正常终止。

假如线程 A 持有资源 2，线程 B 持有资源 1，他们同时都想申请对方的资源，所以这两个线程就会互相等待而进入死锁状态。

避免死锁的几个常见方法：
避免一个线程同时获取多个锁
避免一个线程在锁内同时占用多个资源，尽量保证每个锁只占用一个资源。
尝试使用定时锁，使用 lock.tryLock(timeout) 来代替使用内部锁机制。
对于数据库锁，加锁和解锁必须在一个数据库连接里，否则会出现解锁失败的情况。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 并发与并行的区别？
并发指的是多个任务交替进行，并行则是指真正意义上的“同时进行”。

实际上，如果系统内只有一个CPU，使用多线程时，在真实系统环境下不能并行，只能通过切换时间片的方式交替进行，从而并发执行任务。真正的并行只能出现在拥有多个CPU的系统中。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 虚拟机栈和本地方法栈为什么是私有的?
虚拟机栈： 每个 Java 方法在执行的同时会创建一个栈帧用于存储局部变量表、操作数栈、常量池引用等信息。从方法调用直至执行完成的过程，就对应着一个栈帧在 Java 虚拟机栈中入栈和出栈的过程。
本地方法栈： 和虚拟机栈所发挥的作用非常相似，区别是： 虚拟机栈为虚拟机执行 Java 方法 （也就是字节码）服务，而本地方法栈则为虚拟机使用到的 Native 方法服务。 在 HotSpot 虚拟机中和 Java 虚拟机栈合二为一。
所以，为了保证线程中的局部变量不被别的线程访问到，虚拟机栈和本地方法栈是线程私有的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是线程和进程?
进程：在操作系统中能够独立运行，并且作为资源分配的基本单位。它表示运行中的程序。系统运行一个程序就是一个进程从创建、运行到消亡的过程。

线程：是一个比进程更小的执行单位，能够完成进程中的一个功能，也被称为轻量级进程。一个进程在其执行的过程中可以产生多个线程。

线程与进程不同的是：同类的多个线程共享进程的堆和方法区资源，但每个线程有自己的程序计数器、虚拟机栈和本地方法栈，所以系统在产生一个线程，或是在各个线程之间作切换工作时，负担要比进程小得多。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 程序计数器为什么是私有的?
程序计数器主要有下面两个作用：

字节码解释器通过改变程序计数器来依次读取指令，从而实现代码的流程控制，如：顺序执行、选择、循环、异常处理。
在多线程的情况下，程序计数器用于记录当前线程执行的位置，从而当线程被切换回来的时候能够知道该线程上次运行到哪儿了。
（需要注意的是，如果执行的是 native 方法，那么程序计数器记录的是 undefined 地址，只有执行的是 Java 代码时程序计数器记录的才是下一条指令的地址。）

所以，程序计数器私有主要是为了线程切换后能恢复到正确的执行位置。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是多线程的上下文切换？
即使是单核CPU也支持多线程执行代码，CPU通过给每个线程分配CPU时间片来实现这个机制。时间片是CPU分配给各个线程的时间，因为时间片非常短，所以CPU通过不停地切换线程执行，让我们感觉多个线程时同时执行的，时间片一般是几十毫秒（ms）

上下文切换过程中，CPU会停止处理当前运行的程序，并保存当前程序运行的具体位置以便之后继续运行
CPU通过时间片分配算法来循环执行任务，当前任务执行一个时间片后会切换到下一个任务。但是，在切换前会保存上一个任务的状态，以便下次切换回这个任务时，可以再次加载这个任务的状态
从任务保存到再加载的过程就是一次上下文切换

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是自旋锁？
自旋锁是SMP架构中的一种low-level的同步机制。
当线程A想要获取一把自旋锁而该锁又被其它线程锁持有时，线程A会在一个循环中自旋以检测锁是不是已经可用了。

自旋锁需要注意：
由于自旋时不释放CPU，因而持有自旋锁的线程应该尽快释放自旋锁，否则等待该自旋锁的线程会一直在那里自旋，这就会浪费CPU时间。
持有自旋锁的线程在sleep之前应该释放自旋锁以便其它线程可以获得自旋锁。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## AQS支持几种同步方式？
1）独占式

2）共享式

这样方便使用者实现不同类型的同步组件，独占式如ReentrantLock，共享式如Semaphore，CountDownLatch，组合式的如ReentrantReadWriteLock。总之，AQS为使用提供了底层支撑，如何组装实现，使用者可以自由发挥。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是AQS？
AQS是AbustactQueuedSynchronizer的简称，它是一个Java提高的底层同步工具类，用一个int类型的变量表示同步状态，并提供了一系列的CAS操作来管理这个同步状态。

AQS是一个用来构建锁和同步器的框架，使用AQS能简单且高效地构造出应用广泛的大量的同步器，比如我们提到的ReentrantLock，Semaphore，其他的诸如ReentrantReadWriteLock，SynchronousQueue，FutureTask等等皆是基于AQS的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## CAS的问题
1）CAS容易造成ABA问题

一个线程a将数值改成了b，接着又改成了a，此时CAS认为是没有变化，其实是已经变化过了，而这个问题的解决方案可以使用版本号标识，每操作一次version加1。在java5中，已经提供了AtomicStampedReference来解决问题。

2） 不能保证代码块的原子性

CAS机制所保证的知识一个变量的原子性操作，而不能保证整个代码块的原子性。比如需要保证3个变量共同进行原子性的更新，就不得不使用synchronized了。

3）CAS造成CPU利用率增加

之前说过了CAS里面是一个循环判断的过程，如果线程一直没有获取到状态，cpu资源会一直被占用。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是CAS？
CAS是compare and swap的缩写，即我们所说的比较交换。

cas是一种基于锁的操作，而且是乐观锁。在java中锁分为乐观锁和悲观锁。悲观锁是将资源锁住，等一个之前获得锁的线程释放锁之后，下一个线程才可以访问。而乐观锁采取了一种宽泛的态度，通过某种方式不加锁来处理资源，比如通过给记录加version来获取数据，性能较悲观锁有很大的提高。

CAS 操作包含三个操作数 —— 内存位置（V）、预期原值（A）和新值(B)。如果内存地址里面的值和A的值是一样的，那么就将内存里面的值更新成B。CAS是通过无限循环来获取数据的，若果在第一轮循环中，a线程获取地址里面的值被b线程修改了，那么a线程需要自旋，到下次循环才有可能机会执行。

java.util.concurrent.atomic 包下的类大多是使用CAS操作来实现的( AtomicInteger,AtomicBoolean,AtomicLong)。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## CyclicBarrier和CountDownLatch的区别
1）CountDownLatch简单的说就是一个线程等待，直到他所等待的其他线程都执行完成并且调用countDown()方法发出通知后，当前线程才可以继续执行。
2）cyclicBarrier是所有线程都进行等待，直到所有线程都准备好进入await()方法之后，所有线程同时开始执行！
3）CountDownLatch的计数器只能使用一次。而CyclicBarrier的计数器可以使用reset() 方法重置。所以CyclicBarrier能处理更为复杂的业务场景，比如如果计算发生错误，可以重置计数器，并让线程们重新执行一次。
4）CyclicBarrier还提供其他有用的方法，比如getNumberWaiting方法可以获得CyclicBarrier阻塞的线程数量。isBroken方法用来知道阻塞的线程是否被中断。如果被中断返回true，否则返回false。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 线程池的优点？
1）重用存在的线程，减少对象创建销毁的开销。
2）可有效的控制最大并发线程数，提高系统资源的使用率，同时避免过多资源竞争，避免堵塞。
3）提供定时执行、定期执行、单线程、并发数控制等功能。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 创建线程有哪些方式？
1）继承Thread类创建线程类

2）通过Runnable接口创建线程类

3）通过Callable和Future创建线程

4）通过线程池创建

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 并发编程三要素？
1）原子性
原子性指的是一个或者多个操作，要么全部执行并且在执行的过程中不被其他操作打断，要么就全部都不执行。

2）可见性
可见性指多个线程操作一个共享变量时，其中一个线程对变量进行修改后，其他线程可以立即看到修改的结果。

3）有序性
有序性，即程序的执行顺序按照代码的先后顺序来执行。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是悲观锁？什么是乐观锁？
当我们要对一个数据库中的一条数据进行修改的时候，为了避免同时被其他人修改，最好的办法就是直接对该数据进行加锁以防止并发。
这种借助数据库锁机制在修改数据之前先锁定，再修改的方式被称之为悲观并发控制（又名“悲观锁”，Pessimistic Concurrency Control，缩写“PCC”）。
之所以叫做悲观锁，是因为这是一种对数据的修改抱有悲观态度的并发控制方式。我们一般认为数据被并发修改的概率比较大，所以需要在修改之前先加锁。

乐观锁（ Optimistic Locking ） 是相对悲观锁而言的，乐观锁假设数据一般情况下不会造成冲突，所以在数据进行提交更新的时候，才会正式对数据的冲突与否进行检测，如果发现冲突了，则让返回用户错误的信息，让用户决定如何去做。
相对于悲观锁，在对数据库进行处理的时候，乐观锁并不会使用数据库提供的锁机制。一般的实现乐观锁的方式就是记录数据版本。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java里的线程有哪些状态？
1. 初始(NEW)：新创建了一个线程对象，但还没有调用start()方法。
2. 运行(RUNNABLE)：Java线程中将就绪（ready）和运行中（running）两种状态笼统的称为“运行”。线程对象创建后，其他线程(比如main线程）调用了该对象的start()方法。该状态的线程位于可运行线程池中，等待被线程调度选中，获取CPU的使用权，此时处于就绪状态（ready）。就绪状态的线程在获得CPU时间片后变为运行中状态（running）。
3. 阻塞(BLOCKED)：表示线程阻塞于锁。
4. 等待(WAITING)：进入该状态的线程需要等待其他线程做出一些特定动作（通知或中断）。
5. 超时等待(TIMED_WAITING)：该状态不同于WAITING，它可以在指定的时间后自行返回。
6. 终止(TERMINATED)：表示该线程已经执行完毕。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## “伪共享”出现的原因是什么？
因为CPU缓存和内存交换数据的单位是缓存行，而同一个缓存行里的多个变量不能同时被多个线程修改。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 了解过什么是“伪共享”吗？
CPU缓存从内存读数据时，是按缓存行读取的，即使只用到一个变量，也要将整行数据进行读取，这行数据量可能包含其他变量。当多个线程同时修改同一个缓存行里的不同变量时，由于同时只能有一个线程在操作，所以相比将每个变量放到不同缓存行里，性能会有所下降。多个线程同时修改了同一个缓存行上的不同变量，由于不能并发修改，所以称为“伪共享”。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说一下synchronized锁升级过程
1. 偏向锁
   在 JDK1.8 中，其实默认是轻量级锁，但如果设定了 -XX:BiasedLockingStartupDelay = 0 ，那在对一个 Object 做 syncronized 的时候，会立即上一把偏向锁。当处于偏向锁状态时， markwork 会记录当前线程 ID 。

2. 升级到轻量级锁
   当下一个线程参与到偏向锁竞争时，会先判断 markword 中保存的线程 ID 是否与这个线程 ID 相等，如果不相等，会立即撤销偏向锁，升级为轻量级锁。每个线程在自己的线程栈中生成一个 LockRecord ( LR )，然后每个线程通过 CAS (自旋)的操作将锁对象头中的 markwork 设置为指向自己的 LR 的指针，哪个线程设置成功，就意味着获得锁。关于 synchronized 中此时执行的 CAS 操作是通过 native 的调用 HotSpot 中 bytecodeInterpreter.cpp 文件 C++ 代码实现的，有兴趣的可以继续深挖。

3. 升级到重量级锁
   如果锁竞争加剧(如线程自旋次数或者自旋的线程数超过某阈值， JDK1.6 之后，由 JVM 自己控制该规则)，就会升级为重量级锁。此时就会向操作系统申请资源，线程挂起，进入到操作系统内核态的等待队列中，等待操作系统调度，然后映射回用户态。在重量级锁中，由于需要做内核态到用户态的转换，而这个过程中需要消耗较多时间，也就是"重"的原因之一。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## ReentrantLock与synchronized的区别
ReentrantLock 有如下特点：

1. 可重入
   ReentrantLock 和 syncronized 关键字一样，都是可重入锁，不过两者实现原理稍有差别， RetrantLock 利用 AQS 的的 state 状态来判断资源是否已锁，同一线程重入加锁， state 的状态 +1 ; 同一线程重入解锁, state 状态 -1 (解锁必须为当前独占线程，否则异常); 当 state 为 0 时解锁成功。
2. 需要手动加锁、解锁
   synchronized 关键字是自动进行加锁、解锁的，而 ReentrantLock 需要 lock() 和 unlock() 方法配合 try/finally 语句块来完成，来手动加锁、解锁。
3. 支持设置锁的超时时间
   synchronized 关键字无法设置锁的超时时间，如果一个获得锁的线程内部发生死锁，那么其他线程就会一直进入阻塞状态，而 ReentrantLock 提供 tryLock 方法，允许设置线程获取锁的超时时间，如果超时，则跳过，不进行任何操作，避免死锁的发生。
4. 支持公平/非公平锁
   synchronized 关键字是一种非公平锁，先抢到锁的线程先执行。而 ReentrantLock 的构造方法中允许设置 true/false 来实现公平、非公平锁，如果设置为 true ，则线程获取锁要遵循"先来后到"的规则，每次都会构造一个线程 Node ，然后到双向链表的"尾巴"后面排队，等待前面的 Node 释放锁资源。
5. 可中断锁
   ReentrantLock 中的 lockInterruptibly() 方法使得线程可以在被阻塞时响应中断，比如一个线程 t1 通过 lockInterruptibly() 方法获取到一个可重入锁，并执行一个长时间的任务，另一个线程通过 interrupt() 方法就可以立刻打断 t1 线程的执行，来获取t1持有的那个可重入锁。而通过 ReentrantLock 的 lock() 方法或者 Synchronized 持有锁的线程是不会响应其他线程的 interrupt() 方法的，直到该方法主动释放锁之后才会响应 interrupt() 方法。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 说说synchronized的实现原理
在 Java 中，每个对象都隐式包含一个 monitor（监视器）对象，加锁的过程其实就是竞争 monitor 的过程，当线程进入字节码 monitorenter 指令之后，线程将持有 monitor 对象，执行 monitorexit 时释放 monitor 对象，当其他线程没有拿到 monitor 对象时，则需要阻塞等待获取该对象。 

*** 
## ⭐️⭐️⭐️⭐️⭐️
## java中是值传递引用传递？理论上说，java都是引用传递，对于基本数据类型，传递是值的副本，而不是值本身。对于对象类型，传递是对象的引用，当在一个方法操作操作参数的时候，其实操作的是引用所指向的对象。
*** 
## ⭐️⭐️⭐️⭐️⭐️
## java中有没有指针？有指针，但是隐藏了，开发人员无法直接操作指针，由jvm来操作指针
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 一个java类中包含那些内容？属性、方法、内部类、构造方法、代码块
*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java中的包装类都是那些？
```
byte：Byte
short：Short
int：Integer
long：Long
float：Float
double：Double
char：Character
boolean：Boolean
```
*** 
## ⭐️⭐️⭐️⭐️⭐️
## Char类型能不能转成int、string或者double类型？Char在java中也是比较特殊的类型，它的int值从1开始，一共有2的16次方个数据；Char<int<long<float<double；Char类型可以隐式转成int,double类型，但是不能隐式转换成string；如果char类型转成byte，short类型的时候，需要强转。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## comparable 和 comparator的区别？* comparable接口实际上是出自java.lang包，它有一个 compareTo(Object obj)方法用来排序
* comparator接口实际上是出自 java.util 包，它有一个compare(Object obj1, Object obj2)方法用来排序

一般我们需要对一个集合使用自定义排序时，我们就要重写compareTo方法或compare方法，当我们需要对某一个集合实现两种排序方式，比如一个song对象中的歌名和歌手名分别采用一种排序方法的话，我们可以重写compareTo方法和使用自制的Comparator方法或者以两个Comparator来实现歌名排序和歌星名排序，第二种代表我们只能使用两个参数版的Collections.sort().
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 如何实现 Array 和 List 之间的转换？* Array 转 List： Arrays. asList(array) ；
* List 转 Array：List 的 toArray() 方法。
*** 
## ⭐️⭐️⭐️⭐️⭐️
## Array 和 ArrayList 有何区别？
* Array 可以存储基本数据类型和对象，ArrayList 只能存储对象。
* Array 是指定固定大小的，而 ArrayList 大小是自动扩展的。
* Array 内置方法没有 ArrayList 多，比如 addAll、removeAll、iteration 等方法只有 ArrayList 有。

对于基本类型数据，集合使用自动装箱来减少编码工作量。但是，当处理固定大小的基本数据类型的时候，这种方式相对比较慢。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是Hash算法
哈希算法是指把任意长度的二进制映射为固定长度的较小的二进制值，这个较小的二进制值叫做哈希值。
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 哪些集合类是线程安全的？* Vector：就比Arraylist多了个 synchronized （线程安全），因为效率较低，现在已经不太建议使用。
* hashTable：就比hashMap多了个synchronized (线程安全)，不建议使用。
* ConcurrentHashMap：是Java5中支持高并发、高吞吐量的线程安全HashMap实现。它由Segment数组结构和HashEntry数组结构组成。Segment数组在ConcurrentHashMap里扮演锁的角色，HashEntry则用于存储键-值对数据。一个ConcurrentHashMap里包含一个Segment数组，Segment的结构和HashMap类似，是一种数组和链表结构；一个Segment里包含一个HashEntry数组，每个HashEntry是一个链表结构的元素；每个Segment守护着一个HashEntry数组里的元素，当对HashEntry数组的数据进行修改时，必须首先获得它对应的Segment锁。（推荐使用）
* ...


*** 
## ⭐️⭐️⭐️⭐️⭐️
## List，Set，Map三者的区别？Java 容器分为 Collection 和 Map 两大类，Collection集合的子接口有Set、List、Queue三种子接口。我们比较常用的是Set、List，Map接口不是collection的子接口。

Collection集合主要有List和Set两大接口

* List：一个有序（元素存入集合的顺序和取出的顺序一致）容器，元素可以重复，可以插入多个null元素，元素都有索引。常用的实现类有 ArrayList、LinkedList 和 Vector。
* Set：一个无序（存入和取出顺序有可能不一致）容器，不可以存储重复元素，只允许存入一个null元素，必须保证元素唯一性。Set 接口常用实现类是 HashSet、LinkedHashSet 以及 TreeSet。

Map是一个键值对集合，存储键、值和之间的映射。 Key无序，唯一；value 不要求有序，允许重复。Map没有继承于Collection接口，从Map集合中检索元素时，只要给出键对象，就会返回对应的值对象。

Map 的常用实现类：HashMap、TreeMap、HashTable、LinkedHashMap、ConcurrentHashMap

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 为什么Java中的字符串对象是不可变的所谓不可变对象，是指一个对象在创建后，它的内部状态不会被改变的对象。这意味着当我们将一个不可变对象的引用赋值给某个变量后，我们就不能改变该对象的内部状态。 James Gosling也说过——Java开发者应该尽量使用不可变对象。 

在Java中将String对象设置为不可变对象的好处很多，例如：缓存、安全、同步、性能等方面。 

## 节省内存

字符串常量池：字符串常量池是JVM中的一块特殊区域（1.7之前存放在perm区，1.8之后存放在堆上），用来存放字符串对象的值。在JVM中字符串是不可变的，因此JVM对于相同的字符序列，可以只保存一份，这个特性称之为“interning”。由于字符串是JVM中最常见的对象，因此实现字符串共享可以节省很多堆内存。 

有两种方式定义的字符串，可以存放在常量池中：

* 使用常量字符串初始化字符串变量

```java
String s1 = "Hello World";
String s2 = "Hello World";
System.out.printlin(s1 == s2); //结果为true
```

* 调用String对象的intern方法，需要注意的是：直接通过String的构造方法初始化的字符串对象，它的值并没有存放在字符串常量池，需要对该对象调用intern方法之后，才会将它的值放入字符串常量池。

```java
String s1 = "Hello World";
String s2 = new String("Hello World");
System.out.println(s1 == s2); //结果为false

s2.intern();
System.out.println(s1 == s2); //结果为true
```

## 安全问题

Java应用中使用字符串对象存放一些敏感信息：用户名、密码、连接地址、IP地址等等。Java中类加载器加载类的时候，也是根据类的名字去文件系统中的对应路径去查找的，类的名称、对应的路径，都是使用字符串对象存储的。 

将字符串对象设计为不可变的，就意味着这个敏感信息一经生成就不会被改变（有点现在流行的区块链的思路）。 

常见的安全检查流程有两个步骤：

（1）校验安全信息；
（2）进行敏感操作。如果字符串对象是可变的，则在做完第（1）步安全校验后这个字符串对象依然可能被改变。例如，我们现在在维护一个用户服务，提供了更改用户昵称的服务，业务逻辑是先检查用户昵称的合法性，然后再进行数据库的操作，如果字符串对象是可变的，那么第一步的合法性检查就没有意义了。 

## 并发问题

不可变对象天然具备线程安全性，因为不用担心两个线程同时修改该对象时候产生的争用问题。假设字符串变量 `str = "hello"` 被多个线程同时使用，如果在某个线程中对str赋了新的字符串值，那么就会在字符串常量池中生成一份新的字符串，不会有并发争用。

## hashcode缓存

在Java集合框架的很多数据结构中都用到了字符串对象，例如HashMap、HashTable、HashSet等等，在这些数据结构的实现过程中，都使用hashcode()方法来进行hash操作。 

由于字符串对象的不变性，JDK将它的hashcode()做了缓存，这样对于同一个字符串对象，只会在第一次调用它的hashcode()方法的时候进行计算，后面的调用直接使用缓存中的值，这缓存也提升了集合数据结构的性能。 


*** 
## ⭐️⭐️⭐️⭐️⭐️
## 反射机制的应用场景有哪些？反射是框架设计的灵魂。

在我们平时的项目开发过程中，基本上很少会直接使用到反射机制，但这不能说明反射机制没有用，实际上有很多设计、开发都与反射机制有关，例如模块化的开发，通过反射去调用对应的字节码；动态代理设计模式也采用了反射机制，还有我们日常使用的 Spring／Hibernate 等框架也大量使用到了反射机制。

举例：

* 我们在使用JDBC连接数据库时使用Class.forName()通过反射加载数据库的驱动程序；
* Spring框架也用到很多反射机制，最经典的就是xml的配置模式。Spring 通过 XML 配置模式装载 Bean 的过程：
	* 将程序内所有 XML 或 Properties 配置文件加载入内存中; 
    * Java类里面解析xml或properties里面的内容，得到对应实体类的字节码字符串以及相关的属性信息;
* 使用反射机制，根据这个字符串获得某个类的Class实例; 
* 动态配置实例的属性
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 反射机制优缺点是什么？* 优点： 运行期类型的判断，动态加载类，提高代码灵活度。
* 缺点： 性能瓶颈：反射相当于一系列解释操作，通知 JVM 要做的事情，性能比直接的java代码要慢很多。


*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是反射机制？JAVA反射机制是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意一个方法和属性；这种动态获取的信息以及动态调用对象的方法的功能称为java语言的反射机制。
*** 
## ⭐️⭐️⭐️⭐️⭐️
## == 和 equals 的区别是什么？## ==

它的作用是判断两个对象的地址是不是相等。即，判断两个对象是不是同一个对象。(基本数据类型 == 比较的是值，引用数据类型 == 比较的是内存地址)

## equals()

它的作用也是判断两个对象是否相等。但它一般有两种使用情况：

* 情况1：类没有覆盖 equals() 方法。则通过 equals() 比较该类的两个对象时，等价于通过“==”比较这两个对象。
* 情况2：类覆盖了 equals() 方法。一般，我们都覆盖 equals() 方法来两个对象的内容相等；若它们的内容相等，则返回 true (即，认为这两个对象相等)。

## 举个例子

```java
public class test1 {
    public static void main(String[] args) {
        String a = new String("ab"); // a 为一个引用
        String b = new String("ab"); // b为另一个引用,对象的内容一样
        String aa = "ab"; // 放在常量池中
        String bb = "ab"; // 从常量池中查找
        if (aa == bb) // true
            System.out.println("aa==bb");
        if (a == b) // false，非同一对象
            System.out.println("a==b");
        if (a.equals(b)) // true
            System.out.println("aEQb");
        if (42 == 42.0) { // true
            System.out.println("true");
        }
    }
}
```

## 说明

String中的equals方法是被重写过的，因为object的equals方法是比较的对象的内存地址，而String的equals方法比较的是对象的值。

当创建String类型的对象时，虚拟机会在常量池中查找有没有已经存在的值和要创建的值相同的对象，如果有就把它赋给当前引用。如果没有就在常量池中重新创建一个String对象。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 线程的 sleep()方法和 yield()方法有什么区别？1、 sleep()方法给其他线程运行机会时不考虑线程的优先级，因此会给低优先级的线程以运行的机会；yield()方法只会给相同优先级或更高优先级的线程以运行的机会；

2、 线程执行 sleep()方法后转入阻塞（blocked）状态，而执行 yield()方法后转入就绪（ready）状态；

3、 sleep()方法声明抛出 InterruptedException，而 yield()方法没有声明任何异常；

4、 sleep()方法比 yield()方法（跟操作系统 CPU 调度相关）具有更好的可移植性，通常不建议使用yield()方法来控制并发线程的执行。
*** 
## ⭐️⭐️⭐️⭐️⭐️
## Java和C++有什么区别？* 都是面向对象的语言，都支持封装、继承和多态
* Java不提供指针来直接访问内存，程序内存更加安全
* Java的类是单继承的，C++支持多重继承；虽然Java的类不可以多继承，但是接口可以多继承。
* Java有自动内存管理机制，不需要程序员手动释放无用内存
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是字节码？采用字节码的最大好处是什么？## 字节码

Java源代码经过虚拟机编译器编译后产生的文件（即扩展为.class的文件），它不面向任何特定的处理器，只面向虚拟机。

## 采用字节码的好处

Java语言通过字节码的方式，在一定程度上解决了传统解释型语言执行效率低的问题，同时又保留了解释型语言可移植的特点。所以Java程序运行时比较高效，而且，由于字节码并不专对一种特定的机器，因此，Java程序无须重新编译便可在多种不同的计算机上运行。

先看下java中的编译器和解释器：

Java中引入了虚拟机的概念，即在机器和编译程序之间加入了一层抽象的虚拟机器。这台虚拟的机器在任何平台上都提供给编译程序一个的共同的接口。编译程序只需要面向虚拟机，生成虚拟机能够理解的代码，然后由解释器来将虚拟机代码转换为特定系统的机器码执行。在Java中，这种供虚拟机理解的代码叫做字节码（即扩展为.class的文件），它不面向任何特定的处理器，只面向虚拟机。每一种平台的解释器是不同的，但是实现的虚拟机是相同的。Java源程序经过编译器编译后变成字节码，字节码由虚拟机解释执行，虚拟机将每一条要执行的字节码送给解释器，解释器将其翻译成特定机器上的机器码，然后在特定的机器上运行，这就是上面提到的Java的特点的编译与解释并存的解释。

```
Java源代码---->编译器---->jvm可执行的Java字节码(即虚拟指令)---->jvm---->jvm中解释器----->机器可执行的二进制机器码---->程序运行。
```
*** 
## ⭐️⭐️⭐️⭐️⭐️
## java的跨平台性是什么？原理是什么？所谓跨平台性，是指java语言编写的程序，一次编译后，可以在多个系统平台上运行。

实现原理：Java程序是通过java虚拟机在系统平台上运行的，只要该系统可以安装相应的java虚拟机，该系统就可以运行java程序。
*** 
## ⭐️⭐️⭐️⭐️⭐️
## jdk1.5之后有哪几个大版本？* Java SE（J2SE，Java 2 Platform Standard Edition，标准版）

Java SE 以前称为 J2SE。它允许开发和部署在桌面、服务器、嵌入式环境和实时环境中使用的 Java 应用程序。Java SE 包含了支持 Java Web 服务开发的类，并为Java EE和Java ME提供基础。

* Java EE（J2EE，Java 2 Platform Enterprise Edition，企业版）

Java EE 以前称为 J2EE。企业版本帮助开发和部署可移植、健壮、可伸缩且安全的服务器端Java 应用程序。Java EE 是在 Java SE 的基础上构建的，它提供 Web 服务、组件模型、管理和通信 API，可以用来实现企业级的面向服务体系结构（service-oriented architecture，SOA）和 Web2.0应用程序。2018年2月，Eclipse 宣布正式将 JavaEE 更名为 JakartaEE

* Java ME（J2ME，Java 2 Platform Micro Edition，微型版）

Java ME 以前称为 J2ME。Java ME 为在移动设备和嵌入式设备（比如手机、PDA、电视机顶盒和打印机）上运行的应用程序提供一个健壮且灵活的环境。Java ME 包括灵活的用户界面、健壮的安全模型、许多内置的网络协议以及对可以动态下载的连网和离线应用程序的丰富支持。基于 Java ME 规范的应用程序只需编写一次，就可以用于许多设备，而且可以利用每个设备的本机功能。
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是JavaJava是一门面向对象编程语言，不仅吸收了C++语言的各种优点，还摒弃了C++里难以理解的多继承、指针等概念，因此Java语言具有功能强大和简单易用两个特征。Java语言作为静态面向对象编程语言的代表，极好地实现了面向对象理论，允许程序员以优雅的思维方式进行复杂的编程 。
*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是编程编程就是让计算机为解决某个问题而使用某种程序设计语言编写程序代码，并最终得到结果的过程。

为了使计算机能够理解人的意图，人类就必须要将需解决的问题的思路、方法、和手段通过计算机能够理解的形式告诉计算机，使得计算机能够根据人的指令一步一步去工作，完成某种特定的任务。这种人和计算机之间交流的过程就是编程。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 有穷自动机（有限自动机）
为什么是有穷？：状态和输入字母表有穷。
作用：是一种识别装置，识别正规文法所定义的语言和正规式所表示的集合。
分类：（i）确定的有穷自动机（DFA）（ii）不确定的有穷自动机（NFA）

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 句型、句子、语言
（1）句型和句子
句型：若符号串x是从开始符推导出来的,即S =>*x，则称x是文法G的句型
如果此时x只由终结符组成那么也称x为句子。
（2）语言
定义：由文法G生成的语言记为L(G),它是文法G的一切句子的集合。
文法和语言的关系：文法G生成的每个串都在L(G)中且L(G)中的每个串确实能被G生成。
（3）等价文法
若L（G1）=L（G2），则称文法G1和G2是等价的。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 出错处理
出错处理：编译过程中，发现源程序有错误（词法错误、语法错误、语义错误），编译程序应报告错误的性质和出错的地点，并将错误所造成的影响限制在尽可能小的范围内，使得源程序的其余部分继续被编译下去。这些工作称为出错处理(error handling)。目的是使得编译程序能够继续向下进行分析和处理。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 表格管理程序
编译过程中源程序的各种信息被保留在种种不同的表格里，编译各阶段的工作涉及到构造、查找或更新有关的表格，因此需要有表格管理工作。

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 目标代码生成
把中间代码变换成特定机器上的绝对指令代码或可重定位的指令代码或汇编指令代码,它的工作与硬件系统和指令含义有关.

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 中间代码生成
中间代码是一种结构简单，含义明确的记号系统。
将源程序生成一种内部表示形式，这种内部表示形式叫中间代码。（四元式就是一种中间代码形式）

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 语义分析
审查源程序有无语义错误，为代码生成阶段收集类型信息（如类型转化，类型匹配，上下文相关性等）。
主要是类型相容检查，有以下几种：
各种条件表达式的类型是不是boolean型？
运算符的分量类型是否相容？
赋值语句的左右部的类型是否相容？
形参和实参的类型是否相容?
下标表达式的类型是否为所允许的类型？
函数说明中的函数类型和返回值的类型是否一致？
V[E]中的V是不是变量，而且是数组类型？
V.i中的V是不是变量，而且是记录类型？i是不是该记录的域名？
x+f(…)中的f是不是函数名？形参个数和实参个数是否一致？
每个使用性标识符是否都有声明？有无标识符的重复声明？
在语义分析同时产生中间代码，在这种模式下，语义分析的主要功能如下：
语义审查
在扫描声明部分时构造标识符的符号表
在扫描语句部分时产生中间代码

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 语法分析
语法分析是编译过程的一个逻辑阶段。语法分析的任务是在词法分析的基础上将单词序列组合成各类语法短语，如“程序”，“语句”，“表达式”等等.语法分析程序判断源程序在结构上是否正确.

在词法分析的基础上，将单词序列（输出）分解成各类语法短语。（赋值语句等语句）
语法分析依据语言的语法规则，确定整个输入串是否在语法上正确。
If else是否匹配，无论是LL(1)文法分析，自顶向下还是自底向上都是要按照给定的语法，判断词法分析的词语是不是满足语法要求（标识符定义是否正确，括号是否匹配，关键字是否正确，标识符，函数定义是否正确，使用的函数或者标识符是否定义等等）

*** 
## ⭐️⭐️⭐️⭐️⭐️
## 什么是词法分析？
即对构成源程序的字符流进行扫描然后根据构词规则识别单词(也称单词符号或符号)。所以当单词不符合构词规则时词法分析会报错。
**读入一个一个的字符（输入）**，对这些字符进行扫描和分解，从而识别出**一个个单词**（输出）。



*** 
## ⭐️⭐️⭐️⭐️⭐️
## Redis有哪些数据结构？
Redis 有 5 种基础数据结构，它们分别是：string(字符串)、list(列表)、hash(字典)、set(集合) 和 zset(有序集合)。这 5 种是 Redis 相关知识中最基础、最重要的部分。

