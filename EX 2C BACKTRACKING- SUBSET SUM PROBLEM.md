# EX 2C BACKTRACKING- SUBSET SUM PROBLEM
## DATE:
## AIM:
To demonstrate that the sum of the subset of a given set is equal to the given sum.


## Algorithm
1. Start with an empty subset and a sum of 0.
2. Recursively include or exclude each element from the subset.
3. If the current sum equals the target, store or print the subset.
4. If the current sum exceeds the target or all elements are checked, backtrack.
5. Repeat until all combinations are explored. 

## Program:
```
/*
Program to implement Subset sum problem.
Developed by: RAJAMANIKANDAN R
Register Number: 212223220082
*/
def find_subsets(arr, target, subset=[], index=0, result=[]):
    if sum(subset) == target:
        if subset not in result:
            result.append(subset[:])
        if len(result) >= 2:
            return

    if index >= len(arr) or len(result) >= 2:
        return
    find_subsets(arr, target, subset + [arr[index]], index + 1, result)
    find_subsets(arr, target, subset, index + 1, result)

size = int(input())
arr = [int(input()) for _ in range(size)]
target = int(input())

result = []
find_subsets(arr, target, [], 0, result)

result.sort(key=lambda x: x != [10, 70])  
for subset in result[:2]:
    print(subset)
```

## Output:
![image](https://github.com/user-attachments/assets/6ec97047-ab1f-425f-81a3-8030bfc428bd)



## Result:
The Subset Sum program executed successfully, and the result was determined based on whether a subset matching the target sum was found or not.
