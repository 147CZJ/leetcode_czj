给定一个未排序的整数数组，找出最长连续序列的长度。

要求算法的时间复杂度为 O(n)。

示例:

输入: [100, 4, 200, 1, 3, 2]
输出: 4
解释: 最长连续序列是 [1, 2, 3, 4]。它的长度为 4。

```
 public int longestConsecutive(int[] nums) {
       Set<Integer> num_set = new HashSet<Integer>();
       int res = 0;
      for(int num:nums)num_set.add(num);
      for(int num:nums){
          if(!num_set.contains(num-1)){//没有这一行，好多出上千毫秒，直接拦截了不是最左边的数字
              int right= num;
          while(num_set.contains(right+1)){
              right++;
          }
          res=Math.max(res,right-num+1);
          }
      }
      return res;
    }
```