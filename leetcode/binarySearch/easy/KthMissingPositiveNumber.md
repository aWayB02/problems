
problem: https://leetcode.com/problems/kth-missing-positive-number/description/?envType=problem-list-v2&envId=binary-search  

date: 01.04.25

---------------------------------------------

## 1) Наивная реализация за $O(N + K)$
Нас просят вернуть K-e число которое отсутствует в этом массиве, поэтому можно перебрать все числа от 1 до N + K, добавив в новый массив лишь те, которых нет в исходном, в конце обратиться к K-ому индексу в массиве:

```python
def findKthPositive(arr: List[int], k: int) -> int:
	
	nums = []
	arr_set = set(arr)

	for i in range(1, len(arr) + k + 1):

		if i not in arr_set:

			nums.append(i)
	
	return nums[k - 1]
```

Почему мы используем диапазон $1,N + K$? Может возникнуть ситуация когда
будет дан массив вида $| a_i - a_{i+1} | = 1 \ \ \forall \ \ a_i,\ \ a_{i + 1}$ , тогда мы должны будем сделать $K$ шагов чтоб вернуть $K-e$ пропущенное.  

## 2) Реализация за $O(N)$

```python
def findKthPositive(arr: List[int], k: int) -> int: 
	for i, num in enumerate(arr): 
		missing = num - (i + 1) 
		 
		if missing >= k: 
			return k + i 
			
	return k + len(arr)
```

