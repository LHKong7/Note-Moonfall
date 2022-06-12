

### Binary Search



有序的数组：规则 查中间的元素

二分查找利用数组的有序性。中间的索引 = `(left + right) = 2`

第k次的二分查找： `n / 2^k-1` `k= 1 + log2N.  ` `O(logn)`



最基本的二分查找：

中间偏左： `let mid = left + (right - left) / 2`

偶数时偏右边： `let mid = left + (right - left+1) / 2`

对降序数组进行二分查找：把符号变换即可









##### 查找第一个等于目标元素的下标 （有重复的元素）

```js
const fristTargetElement = (nums, target) => {
	if (nums === null || nums.length === 0) return -1;
	let left = 0, right = nums.length - 1;
	
	while (left <= right) {
		let mid = left + Math.floor((right - left) / 2)
		if (target === nums[mid]) {
			if (mid === 0 || nums[mid - 1] != target) return mid;
			else right = mid - 1;
		} else if (target < nums[mid]) {
			right = mid - 1;
		} else {
			left = mid + 1;
		}
	}
	
	return -1;
}
```



###### 查找第一个大于等于 目标元素的下标

```js
const fristGETargetElement = (nums, target) => {
	if (nums === null || nums.length === 0) return -1;
	let left = 0;
	let right = nums.length - 1;
	
	while (left <= right) {
		let mid = Math.floor(left + (right - left) + 1 / 2);
		if (target <= nums[mid]) {
      if (mid === 0 || nums[mid] < target) return mid;
      else right = mid - 1;
		} else {
			left = mid + 1;
		}
	}
	
	return -1;
}
```



##### 查找最后一个等于目标元素的下标

```js
const lastTargetElement = (nums, target) => {
	if (nums === null || nums.length === 0) return -1;
	let left = 0;
	let right = nums.length - 1;
	
	while (left <= right) {
		let mid = left + (right - left) + 1;
		if (target === nums[mid]) {
      //////////////// HERE ///////////////
			if (mid === nums.length-1 || nums[mid + 1] != target) return mid;
			else left = mid + 1;
      /////////////////////////////////////
		} else if (target < nums[mid]) {
			right = mid - 1;
		} else {
			left = mid + 1;
		}
	}
	
	return -1;
}
```



##### 查找最后一个小于等于目标元素的下标

```js
const lastTargetElement = (nums, target) => {
	if (nums === null || nums.length === 0) return -1;
	let left = 0;
	let right = nums.length - 1;
	
	while (left <= right) {
		let mid = left + (right - left) + 1;
		if (target >= nums[mid]) {
      //////////////// HERE ///////////////
			if (mid === nums.length-1 || nums[mid + 1] != target) return mid;
			else left = mid + 1;
 		else {
			right = mid - 1;
		}
	}
	
	return -1;
}
```



```javascript
const firstTargetElement = function (nums, target) {
    if (nums == null || nums.length == 0) return -1
    let left = 0
    let right = nums.length - 1
    while (left <= right) {
        const mid = left + Math.floor((right - left) / 2)
        if (target == nums[mid]) {
            // 符合下面的两个条件之一就返回 mid ,否则去左边找：
            // 1. mid 是数组的第一个元素
            // 2. mid 前面的那个元素不等于 target
            if (mid == 0 || nums[mid - 1] != target) return mid
            else right = mid - 1
        } else if (target < nums[mid]) {
            right = mid - 1
        } else {
            left = mid + 1
        }
    }
    return -1
}


const firstGETargetElement = function (nums, target) {
    if (nums == null || nums.length == 0) return -1
    let left = 0
    let right = nums.length - 1
    while (left <= right) {
        const mid = left + (right - left) / 2
        if (target <= nums[mid]) {
            // 符合下面的两个条件之一就返回 mid ：
            // 1. mid 是数组的第一个元素
            // 2. mid 前面的那个元素小于 target
            if (mid == 0 || nums[mid - 1] < target) return mid;
            else right = mid - 1
        } else { // target > nums[mid]
            left = mid + 1
        }
    }
    return -1
}

const lastTargetElement = function (nums, target) {
    if (nums == null || nums.length == 0) return -1
    let left = 0
    let right = nums.length - 1
    while (left <= right) {
        const mid = left + (right - left) / 2
        if (target == nums[mid]) {
            // 符合下面的两个条件之一就返回 mid ：
            // 1. mid 是数组的最后一个元素
            // 2. mid 后面的那个元素不等于 target
            if (mid == nums.length - 1 || nums[mid + 1] != target) return mid
            else left = mid + 1
        } else if (target < nums[mid]) {
            right = mid - 1
        } else {
            left = mid + 1
        }
    }
    return -1
}

const lastTargetElement = function (nums, target) {
    if (nums == null || nums.length == 0) return -1
    let left = 0
    let right = nums.length - 1
    while (left <= right) {
        const mid = left + (right - left) / 2
        if (target >= nums[mid]) {
            if (mid == nums.length - 1 || nums[mid + 1] > target) return mid
            else left = mid + 1
        } else { // target < nums[mid]
            right = mid - 1
        }
    }
    return -1
}
```

