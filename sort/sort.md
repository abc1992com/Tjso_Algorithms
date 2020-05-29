# 经典排序

## 复杂度

|          | 平均时间复杂度 |    最好     |    最坏     |
| :------: | :------------: | :---------: | :---------: |
| 冒泡排序 |     O(n^2)     |    O(n)     |   O(n^2)    |
| 选择排序 |     O(n^2)     |   O(n^2)    |   O(n^2)    |
| 插入排序 |     O(n^2)     |    O(n)     |   O(n^2)    |
| 希尔排序 |   O(n log n)   | O(n log2 n) | O(n log2 n) |
| 归并排序 |   O(n log n)   | O(n log n)  | O(n log n)  |
| 快速排序 |   O(n log n)   | O(n log n)  |   O(n^2)    |
|  堆排序  |   O(n log n)   | O(n log n)  | O(n log n)  |
| 计数排序 |    O(n + k)    |  O(n + k)   |  O(n + k)   |
|  桶排序  |    O(n + k)    |  O(n + k)   |   O(n^2)    |
| 基数排序 |    O(n * k)    |  O(n * k)   |  O(n * k)   |

## 冒泡排序

一组数组，对相邻数据进行比对，大的往后排。

```javascript 
function bubble_sort(nums){
  	let len = nums.length;
    if(len == 0 || !nums) return;
  	let len = nums.length;
    for(let i=0;i<len-1;i++){
        let flag = true;
        for(let j=0;j<len-1-i;j++){
            if(nums[j] > nums[j+1]){
                flag = false;
                let temp = nums[j];
                nums[j] = nums[j+1];
                nums[j+1] = temp;
            }
        }
        if(flag) break;
    }
    return nums;
}
```

## 选择排序

遍历数组，选择最小的数据，与当前数据交换位置。

```javascript 
function select_sort(nums){
    let len = nums.length;
    if(len == 0 || !nums) return;
    for(let i=0;i<len-1;i++){
      	let min = i;
        for(let j=i+1;j<len;j++){
          	if(nums[j] < nums[min]){
              	min = j;
            }
        }
      	let temp = nums[i];
      	nums[i] = nums[min];
      	nums[min] = temp;
    }
    return nums;
}
```

## 插入排序

它的工作原理是通过构建有序序列，对于未排序数据，在已排序序列中从后向前扫描，找到相应位置并插入。

```javascript
function insertion_sort(nums){
    let len = nums.length;
    if(len == 0 || !nums) return;
    for(let i=1;i<len;i++){
      	let temp = nums[i]
        let j=i-1;
        while(temp < nums[j] && j>=0){
          nums[j+1] = nums[j];
          j--;
        }
      	nums[j+1] = temp;
    }
    return nums;
}
```

## 归并排序

```javascript
function merge_sort(nums){
    let len = nums.length;
    if(len == 0 || !nums) return;
    if(len > 1) {
        let mid = Math.floor(len/2);
        let left = merge_sort(nums.slice(0,mid));
        let right = merge_sort(nums.slice(mid));
      
        let array = [];
        while(left.length > 0 && right.length > 0){
            if( left[0] < right[0]){
                array.push(left.shift());
            } else {
                array.push(right.shift());
            }
        }
        if(left.length>0){
            nums = array.concat(left)
        } else if (right.length>0){
            nums = array.concat(right);
        }
    }
    return nums;
}
```

## 快速排序

```javascript 
function quick_sort(nums){
    let len = nums.length;
    if(len == 0 || !nums) return [];
    if(len > 1){
        let base = nums[0];
        let left = [];
        let right = [];
        for(let i=1;i<nums.length;i++){
            if(nums[i] < base){
                left.push(nums[i]);
            } else {
                right.push(nums[i]);
            }
        }
        quick_sort(left);
        quick_sort(right);
        nums = [...quick_sort(left),base,...quick_sort(right)];
    }
    return nums;
}
```

