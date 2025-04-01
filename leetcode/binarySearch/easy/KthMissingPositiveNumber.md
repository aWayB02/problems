
problem: https://leetcode.com/problems/kth-missing-positive-number/description/?envType=problem-list-v2&envId=binary-search  

date: 01.04.25

 $$\text{Реализация за}\ O(N + K)$$
```python
def findKthPositive(self, arr: List[int], k: int) -> int:
	
	nums = []
	arr_set = set(arr)

	for i in range(1, len(arr) + k + 1):

		if i not in arr_set:

			nums.append(i)
	
	return nums[k - 1]

```
