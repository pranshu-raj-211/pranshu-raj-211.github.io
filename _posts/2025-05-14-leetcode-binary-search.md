### #33 Search in Rotated Sorted Array

[link](https://leetcode.com/problems/search-in-rotated-sorted-array/description/)

Integer array, sorted then rotated by an unknown amount.

Do a search for some element on this array.

Issue: Cannot apply normal binary search -> part of array is not sorted (two sorted subarrays)

Intuition: One half of the subarray considered for binary search is always going to be sorted. If the target element lies in the sorted part of the subarray, consider that for the next search, otherwise its the other half.

Solution:

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        low = 0
        high = len(nums)-1

        while high>=low:
            mid = (low+high)//2
            if target == nums[mid]:
                return mid
            if nums[mid]>=nums[low]:
                if target <=nums[mid] and target >= nums[low]:
                    high = mid-1
                else:
                    low=mid+1
            else:
                if target <= nums[high] and target >= nums[mid]:
                    low=mid+1
                else:
                    high = mid-1
        return -1
```

Modification of this: #81 - array can have duplicates. This has two cases - the rotation brought all copies of that element to one side - can apply the above code to get same results. Otherwise it should still work but is kind of dubious.

### #1283 Smallest divisor of array given a threshold

[link](https://leetcode.com/problems/find-the-smallest-divisor-given-a-threshold/description/)

For a given array, sum the ceil of element/divisor for all elements in array. We need to find the least number that can be the divisor such that the sum is less than the threshold. 

Minimum sum will be the length of the array, since we are considering ceil. Search boundary should be between 1 and max element of the array (both inclusive).

Brute force solution can involve a linear search from 1 to the max element and trying out divisors. Quadratic time complexity.

Or just do a binary search on the search space of divisors, to find the least valid divisor.

```python
import math

class Solution:
    def smallestDivisor(self, nums: List[int], threshold: int) -> int:      
        high = max(nums)
        low = 1
        valid = max(nums)
        while high>=low:
            mid = (high+low)//2
            sum_div = 0
            for num in nums:
                sum_div += math.ceil(num/mid)
            if sum_div <= threshold:
                high = mid-1
                valid = min(valid, mid)
            else:
                low = mid+1
        return valid
```
