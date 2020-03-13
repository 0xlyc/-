# x的平方根
实现`int sqrt(int x)`函数。

计算并返回 x 的平方根，其中 x 是非负整数。

由于返回类型是整数，结果只保留整数的部分，小数部分将被舍去。

**示例1**

    输入：4
    输出：2
    
**示例2**

    输入：4
    输出：2
    说明: 8 的平方根是 2.82842..., 
     由于返回类型是整数，小数部分将被舍去。
   
## 解法一 暴力法
```cpp
class Solution {
public:
    int mySqrt(int x) {
        long i=1;
        for(;i*i<=x;++i);
        return i-1;
    }
};
```

## 解法二 二分法
```cpp
class Solution {
public:
    int mySqrt(int x) {
        if(x==0||x==1)  return x;
        int start=1;
        int end=x/2;
        while(start<end){
            //左中位数可能陷入死循环，这里取右中位数
            int mid=(start+end+1)>>1;
            if(mid<=x/mid)
                start=mid;
            else
                end=mid-1;
        }
        return start;
    }
};
```

## 解法三 牛顿法

```cpp
class Solution {
public:
    int mySqrt(int x) {
        if(x==0||x==1)  return x;
        double cur=1.0;
        double pre=cur;
        while(true){
            pre=cur;
            cur=(cur+x/cur)/2;
            if(abs(pre-cur)<1e-6)
                return int(cur);
        }
    }
};
```
