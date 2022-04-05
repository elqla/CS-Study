# 검색(search)

### 순차검색(sequential search)

- O(n)

- 정렬

  - ```python
    def sequentialSearch(a, n, key):
        i = 0
        while i < n and a[i]! = key:   #i인덱스 범위가 항상 먼저와야함. 
            i = i+1					 #그렇지 않으면 a[n]값이 없기 때문에 indexerror  (i+1 = n)
        if i < n and a[i] == key:
            return i
        else:
            return -1
    ```

    ```python
    a[i]!=key and i < n:
        ===========n보다 i가 작기 때문에 a[n] 값을 가질 수 없어 indexerror
    ```

    

- 비정렬

  - ```python
    def sequentialSearch(a, n, key):
        i = 0
        while i < n and a[i]! = key:
            i = i+1
        if i < n:
            return i
        else:
            return -1
    ```

  - ```python
    for i: 0-> 6
        if a[i] = key
        	return key
    return -1
    ```

    

### 이진검색(Binary Search)

> 이진검색을 하기 위해선, 자료가 정렬된 상태여야 한다.
>
> x**3 = [0, 1, 2, 3, 4, ...1000000] [0, 1, 4, 9, ...]  #배열을 만들어서 사용 (log n)
>
> 탐색 범위를 두 부분으로 분할하면서 찾는 방식
>
>  처음부터 끝까지 돌면서 탐색하는 것보다 훨씬 빠른 장점을 지님
>
> 
>
> 탐색 범위를 두 부분으로 분할하면서 찾는 방식

​	처음부터 끝까지 돌면서 탐색하는 것보다 훨씬 빠른 장점을 지님

```text
* 시간복잡도
전체 탐색 : O(N)
이분 탐색 : O(logN)
```

- 반복구조 추천 !

`진행순서`

- 우선 `정렬`을 해야 함
- left와 right로 mid 값 설정
- mid와 내가 구하고자 하는 값과 비교
- 구할 값이 mid보다 높으면 : left = mid+1 구할 값이 mid보다 낮으면 : right = mid - 1
- left > right가 될 때까지 계속 반복하기



```python
def binarysearch(a[], N, Key):
    start = 0  #변경가능
    end = N-1
    while start <= end:   # 하나 남았을때도, 키 값이랑 비교를 해야해
        middle = (start + end)//2
        if a[middle] == key:
            return True(middle)  #검색성공
        elif a[middle] > key:
            end = middle -1
        else:
            start = middle + 1
    return False(-1) #검색실패시
```

- ex) key = 9, s+e = 10+12, 22//2=>10   end =10-1,,  start = 10, end = 9?   return false

```python
def binarySearch(array, value, low, high):
	if low > high:
		return False
	mid = (low+high) / 2
	if array[mid] > value:
		return binarySearch(array, value, low, mid-1)
	elif array[mid] < value:
		return binarySearch(array, value, mid+1, high)
	else:
		return mid
```



```python
#재귀
def binarysearch2(a, low, high, key):
    if low>high:  #실패
        return False
    else:
        middle == (low + high)//2
        if key == a[middle] #성공
        	return True
        elif key < a[middle]:
            return binarysearch2(a, low, middle-1, key)
        elif a[middle] < key:
            return binarysearch2(a, middle+1, high, key)
```







