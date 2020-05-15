给定一个整数数组和一个整数 k，你需要找到该数组中和为 k 的连续的子数组的个数。

示例 1 :

输入:nums = [1,1,1], k = 2
输出: 2 , [1,1] 与 [1,1] 为两种不同的情况。
说明 :

数组的长度为 [1, 20,000]。
数组中元素的范围是 [-1000, 1000] ，且整数 k 的范围是 [-1e7, 1e7]。
```
 public int subarraySum(int[] nums, int k) {
	//暴力法直接遍历所有的值
        //    int res =0;
        //    for(int i =0;i<nums.length;i++){
        //        int sum =0;
        //        for(int j = i;j<nums.length;j++){
        //            sum+=nums[j];
        //            if(sum==k)res++;
        //        }
        //    } 
        //    return res;
	// 通过记录总值，减去目标值，看是否存在与之前的总值
        int count = 0, pre = 0;
        HashMap < Integer, Integer > mp = new HashMap < > ();
        mp.put(0, 1);
        for (int i = 0; i < nums.length; i++) {
            pre += nums[i];
            if (mp.containsKey(pre - k))
                count += mp.get(pre - k);
            mp.put(pre, mp.getOrDefault(pre, 0) + 1);
        }
        return count;
    }
```