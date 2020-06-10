# [46.全排列](https://leetcode-cn.com/problems/permutations/)

给定一个 **没有重复** 数字的序列，返回其所有可能的全排列。

**示例:**

```
输入: [1,2,3]
输出:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```

## 回溯法

套用模板就完事了。

```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var permute = function(nums) {
    const res = [];
    //套用模板
    const backtrack = (temp)=>{
        if(temp.length == nums.length){
            res.push([...temp]);
            return;
        }
        for(let i=0;i<nums.length;i++){
            if(temp.includes(nums[i])) continue;
            temp.push(nums[i]);
            backtrack(temp);
            temp.pop();
        }
    }
    backtrack([]);
    return res;
};
```

- 时间复杂度：$O(N \times N!)$。
- 空间复杂度：$O(N)$。

# [47. 全排列 II](https://leetcode-cn.com/problems/permutations-ii/)

给定一个可包含**重复数字**的序列，返回所有不重复的全排列。

**示例:**

```
输入: [1,1,2]
输出:
[
  [1,1,2],
  [1,2,1],
  [2,1,1]
]
```

## 回溯法

套用模板就完事了，因为是含重复数字的序列，唯一注意的如何进行减枝操作。

```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var permuteUnique = function(nums) {
    let res = [];
    nums = nums.sort((a,b)=>a-b);//排序是彻底减枝操作的前提
    //套用模板
    const backtrack = (temp,index)=>{
        if(temp.length == nums.length){
            res.push([...temp]);
            return;
        }
        for(let i=0;i<nums.length;i++){
            //以数组下标为突破口，进行减枝操作。
            if(index.includes(i) || (i>0 && nums[i] == nums[i-1] && !index.includes(i-1))) continue;
            index.push(i);
            temp.push(nums[i]);
            backtrack(temp,index);
            index.pop();
            temp.pop();
        }
    }
    backtrack([],[]);
    return res;
};
```

- 时间复杂度：$O(N \times N!)$。
- 空间复杂度：$O(N)$。