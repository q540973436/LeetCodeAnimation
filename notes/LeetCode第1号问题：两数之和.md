# LeetCode 第 1 号问题：两数之和

> 本文首发于公众号「五分钟学算法」，是[图解 LeetCode ](<https://github.com/MisterBooo/LeetCodeAnimation>)系列文章之一。
>
> 个人网站：[https://www.cxyxiaowu.com](https://www.cxyxiaowu.com)
>
> 视频讲解：[【跟着程序员小吴图解 LeetCode 】LeetCode 第 1 号问题：两数之和](<https://www.bilibili.com/video/av51296602>)

题目来源于 LeetCode 上第 1 号问题：两数之和。题目难度为 Easy，目前通过率为 45.8% 。

### 题目描述

给定一个整数数组 `nums` 和一个目标值 `target`，请你在该数组中找出和为目标值的那 **两个** 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。

**示例:**

```
给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```

### 题目解析

使用查找表来解决该问题。

设置一个 map 容器 record 用来记录元素的值与索引，然后遍历数组 nums。

* 每次遍历时使用临时变量 complement 用来保存目标值与当前值的差值
* 在此次遍历中查找 record ，查看是否有与 complement 一致的值，如果查找成功则返回查找值的索引值与当前变量的值 i
* 如果未找到，则在 record 保存该元素与索引值 i

### 动画描述

![](https://bucket-1257126549.cos.ap-guangzhou.myqcloud.com/20181028221055.gif)

### 代码实现

```
// 1. Two Sum
// https://leetcode.com/problems/two-sum/description/
// 时间复杂度：O(n)
// 空间复杂度：O(n)
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int,int> record;
        for(int i = 0 ; i < nums.size() ; i ++){
       
            int complement = target - nums[i];
            if(record.find(complement) != record.end()){
                int res[] = {i, record[complement]};
                return vector<int>(res, res + 2);
            }

            record[nums[i]] = i;
        }
    }
};

 /**
     * 
     * <br>
     * @author wwx683234
     * @since  iFad Platform V100R001, 2019年8月19日
     * 时间复杂度o(n)
     * sumMap记录已遍历数据和位置
     * 用目标值-当前值=差值  差值在map中查找
     * 如果用2次for循环查找则为o(n2)
     */
    private static int[] getTarget(int[] a){
        //key为值,value为地址
        Map<Integer, Integer> sumMap=new HashMap<Integer, Integer>();
        
        int[] index=new int[2];
        int temp=0;
        for(int i=0;i<a.length;i++) {
            temp=target-a[i];
            if(sumMap.containsKey(temp)){
                index[0]=i;
                index[1]=sumMap.get(temp);
                System.out.println(index[0]+"------"+index[1]);
            }
            sumMap.put(a[i], i);
        }
        
        return index;
    }
```



![](https://bucket-1257126549.cos.ap-guangzhou.myqcloud.com/blog/fz0rq.png)
