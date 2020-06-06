# 模板一

用来查找一个明确的目标值，不需要后处理，因为每一步中，你都在检查是否找到了元素。如果到达末尾，则知道未找到该元素。

```javascript
function binarySearch(nums, target){
    if(!nums || nums.length == 0) return -1;
    let left = 0, right = nums.length - 1;
    while(left <= right){
        // Prevent (left + right) overflow
        const mid = left + parseInt((right - left)/2);
        if(nums[mid] == target) return mid;
        if(nums[mid] < target) { 
            left = mid + 1; 
        } else { 
            right = mid - 1; 
        }
    }
    return -1;
}
```

# 模板二

**模板二**是二分查找的高级模板。它用于查找需要*访问数组中当前索引及其直接右邻居索引*的元素或条件。

```javascript 
function binarySearch(nums, target){
    if(!nums || nums.length == 0) return -1;
    let left = 0, right = nums.length;
    while(left < right){
        // Prevent (left + right) overflow
        const mid = left + parseInt((right - left)/2);
        if(nums[mid] == target) return mid;
        if(nums[mid] < target) { 
            left = mid + 1; 
        } else { 
            right = mid; 
        }
    }
    if(left != nums.length && nums[left] == target) return left;
    return -1;
}
```

# 模板三

**模板三**是二分查找的另一种独特形式。 它用于搜索需要*访问当前索引及其在数组中的直接左右邻居索引*的元素或条件。

```javascript
function binarySearch(nums, target){
    if(!nums || nums.length == 0) return -1;
    let left = 0, right = nums.length-1;
    while(left + 1 < right){
        // Prevent (left + right) overflow
        const mid = left + parseInt((right - left)/2);
        if(nums[mid] == target) return mid;
        if(nums[mid] < target) { 
            left = mid; 
        } else { 
            right = mid; 
        }
    }
    if(nums[left] == target) return left;
    if(nums[right] == target) return right;
    return -1;
}
```