## 朴素模式匹配算法和KMP算法

### 一、朴素模式匹配算法

- #### 什么是字符串的模式匹配

  ![image-20251204153058969](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251204153058969.png)

  ![image-20251204153201524](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251204153201524.png)

- #### 两种模式匹配算法

  ![image-20251204153255630](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251204153255630.png)

- #### 朴素模式匹配算法

  ![image-20251204153551574](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251204153551574.png)

  ![image-20251204153749382](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251204153749382.png)

  ![image-20251204153951377](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251204153951377.png)

  ![image-20251204154120717](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251204154120717.png)

  ![image-20251204154227456](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251204154227456.png)

  ```c
  int Index(SString S,SString T)
  {
      int i = 1,j = 1;
      while(i <= S.length && j <= T.length)
      {
          if(S.ch[i] == T.ch[j])
          {
              ++i;     //继续比较后继字符
              ++j;
          }
          else
          {
          i = i - j + 2;
          j = 1;   //指针后退重新开始匹配
          }
      }
      if(j > T.length)
          return i - T.length;
      else
          return 0;
  }
  ```

  ![image-20251204154948904](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251204154948904.png)

  ![image-20251204155135230](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251204155135230.png)

  ![image-20251204155745563](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251204155745563.png)

### 二、KMP算法

 ![image-20251208095556689](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208095556689.png)

![image-20251208095931983](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208095931983.png)

![image-20251208102616050](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208102616050.png)

![image-20251208102650890](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208102650890.png)

![image-20251208102720883](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208102720883.png)

![image-20251208102750481](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208102750481.png)

![image-20251208102932683](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208102932683.png)

![image-20251208103011308](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208103011308.png)

![image-20251208103607037](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208103607037.png)

![image-20251208103642644](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208103642644.png)

```c
int Index_KMP(SString S,SString T,int next[])
{
    int i = 1,j = 1;
    while(i <= S.length && j <= T.length)
    {
        if(j == 0 || S.ch[i] == T.ch[i])
        {
            ++i;
            ++j;                    //继续比较后继字符
        }
        else
        {
            j = next[j];            //模式串向右移动
        }
        if(j > T.length)
            return i - T.length;    //匹配成功
        else
            return 0;
    }
}
```

![image-20251208104225505](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208104225505.png)

### 三、KMP算法求next数组

![image-20251208104651508](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208104651508.png)

![image-20251208104741847](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208104741847.png)

![image-20251208104936876](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208104936876.png)

![image-20251208105027665](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208105027665.png)

![image-20251208105609733](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208105609733.png)

![image-20251208105856004](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208105856004.png)

![image-20251208110042252](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208110042252.png)

![image-20251208110229216](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208110229216.png)

![image-20251208110323000](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208110323000.png)

![image-20251208144300900](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208144300900.png)

### 四、KMP算法优化

![image-20251208150948731](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208150948731.png)

![image-20251208151225420](https://gitee.com/Ryokoi/picgo-typora/raw/master/image-20251208151225420.png)