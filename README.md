# 异常检测问题综述
> outlier-detection-review

## 介绍

![image-20211023145357382](.\assets\images\image-20211023145357382.png)

## 监督性异常检测

> 异常检测是从已知的数据中发现未知的数据，并且区分出来，可能是好的，又或者是坏的。
>
> 异常检测简单来说就是给一堆数据，训练出来的模型，模型可以判断这些记录是不是已知数据中类似的，否则标记为异常。

![image-20211023145754556](.\assets\images\image-20211023145754556.png)

> `Binary classification`, 好像可以区划分是或者不是，但是实际上是不可以的。
>
> 1. 异常检测无法确定边界，除了正类以为的所有类都是异常的。
> 2. 异常的数据量非常少。

![image-20211023150435994](.\assets\images\image-20211023150435994.png)

> 一般来说有如上两大类，
>
> 一类是带有类别标记的异常检测， --- 有监督
>
> 一类是不带有异常标记的或者有少量的异常的数据。 -- 无监督或者半监督

![image-20211023150843461](.\assets\images\image-20211023150843461.png)

> classifier中输出一个类别的同时，输出一个信心分数（有多少把握认为这个数据是这个类别）

![image-20211023151200663](.\assets\images\image-20211023151200663.png)

> 使用分类器计算各个类别的信心度，信心度如果比较平均或者值比较低，那么可以认为是异常的。正常的数据，模型应该有很高的信心认为其是正常的。

> classifier 的信心分数作为 base line

## 评价

由于异常和正常数据的数据量差距悬殊，简单使用比例来判断是不合理的。

![image-20211023153120959](.\assets\images\image-20211023153120959.png)

> 根据具体的任务，到底是false alarm 严重还是 missing 严重。

> 或者使用AUC图。

> 异常数据太少，生成异常数据。



## 无监督性异常检测

![image-20211023154739481](C:\Users\mushr\AppData\Roaming\Typora\typora-user-images\image-20211023154739481.png)

> 相比于监督模型的信心度，无监督模型可以使用类似概率的描述。
>
> 如果某个人的某个行为发生的概率离群了，那么他可能是离群点。

> 使用生成模型，似然函数，举出数据集的概率。

![image-20211023155618563](C:\Users\mushr\AppData\Roaming\Typora\typora-user-images\image-20211023155618563.png)

![image-20211023160223854](C:\Users\mushr\AppData\Roaming\Typora\typora-user-images\image-20211023160223854.png)

> 高斯模型如上可以直接套公式，解析解。现在模型得到了，只需要去给定一个阈值，去判断。

> 特征提升，寻找更多其他的特征去判断。![image-20211023160738746](D:\Code\outlier-detection-review\assets\images\image-20211023160738746.png)

## 自动编码器

![image-20211023160923004](D:\Code\outlier-detection-review\assets\images\image-20211023160923004.png)

> 自动编码器，使用正类数据训练一个自动编码器，如果是异常的数据，那么其自动编码器解码异常数据时候效果就会很差。

## 其他方法

![image-20211023161223167](D:\Code\outlier-detection-review\assets\images\image-20211023161223167.png)

