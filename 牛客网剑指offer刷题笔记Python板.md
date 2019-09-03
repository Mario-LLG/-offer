[TOC]



# 牛客完刷题笔记Python板

## 数组中出现次数超过一半的数字

```python
class Solution:
    def MoreThanHalfNum_Solution(self, numbers):
        # write code here

        #use dict
        countNum = {}
        lenNum = len(numbers)
        for num in numbers:
            if num in countNum:
                countNum[num] += 1
            else:
                countNum[num] = 1
            if countNum[num] > (lenNum >> 1):
                return num
        return 0
```

> 使用dict来存取数，可以在不完全遍历的情况下输出

​                           

```python
class Solution:
    def MoreThanHalfNum_Solution(self, numbers):
        # write code here
        numbers.sort()
        i = 0
        j = 0
        numLen = len(numbers)
        number = numbers[numLen/2]
        for item in numbers:
            if(number == item):
                j += 1
        if(j > numLen/2):
            return number
        else:
            return 0
```

> 自己写的 用冒泡先排序，然后找到中间的值，如果大于一半肯定是最多的，这样只能处理最多的数大于一半，通用性较差

```python


```

> 空间复杂度为o（1），将不相同的数干掉，遇到不同的数字就想换抵消

## 整数中1出现的次数

**题目描述**：求出 1~13 的整数中1出现的次数,并算出 100~1300 的整数中1出现的次数？为此他特别数了一下1~13中包含1的数字有1、10、11、12、13因此共出现6次,但是对于后面问题他就没辙了。ACMer希望你们帮帮他,并把问题更加普遍化,可以很快的求出任意非负整数区间中1出现的次数（从1 到 n 中1出现的次数）。

**解题思路：**

1. 循环暴力解法

- 直接贴代码，较容易理解

  ```cpp
  public int NumberOf1Between1AndN_Solution(int n) {
      int count = 0;
      for(int i=0; i<=n; i++){
          int temp = i;
          //如果temp的任意位为1则count++
          while(temp!=0){
              if(temp%10 == 1){
                  count++;
              }
              temp /= 10;
          }
      }
      return count;
  }
  ```

  2. 数学规律（==复杂度O(log~n~)==）

  一、 1的数目

  编程之美上给出的规律：

  1. 如果第i位（自右至左，从1开始标号）上的数字为0，则第i位可能出现1的次数由更高位决定（若没有高位，视高位为0），等于更高位数字X当前位数的权重10^i-1^。
  2. 如果第i位上的数字为1，则第i位上可能出现1的次数不仅受更高位影响，还受低位影响（若没有低位，视低位为0），等于更高位数字X当前位数的权重10^i-1^+（低位数字+1）.
  3. 如果第i位上的数字大于1，则第i位上可能出现1的次数仅由更高位决定（若没有高位，视高位为0），等于（更高位数字+1）X当前位数的权重10^i-1^。

- 代码段

```python
class Solution:
    def NumberOf1Between1AndN_Solution(self, n):
        # write code here
        preValue = 1
        midValue = 1
        posValue = 1
        precise = 1
        sumNum = 0
        while preValue != 0:
            midValue = (n // precise)%10
            posValue = n % precise
            preValue = n // (precise * 10)
            
            if(midValue == 1):
                num = preValue * precise + posValue + 1
            elif(midValue > 1):
                num = (preValue+1) * precise
            else:
                num = preValue * precise
            precise = precise * 10
            sumNum = sumNum + num 
        return sumNum/

```



![1567513916103](C:\Users\L\AppData\Roaming\Typora\typora-user-images\1567513916103.png)

> 需要注意的一点是，if 。。elif。。else ，这里刚开始写成==if。。if。。else==
>
> 还有是不要理解为多算了几次，这里主要统计==1==出现的个数，所以可以重复算入==11==，要算两个*1*

