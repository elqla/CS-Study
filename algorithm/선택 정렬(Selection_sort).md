# 선택 정렬(Selection Sort)

> Selection Sort는 Bubble Sort과 유사한 알고리즘으로, **해당 순서에 원소를 넣을 위치는 이미 정해져 있고, 어떤 원소를 넣을지 선택하는 알고리즘**이다.
>
> Selection Sort와 Insertion Sort를 헷갈려하는 사람들이 종종 있는데, Selection Sort는 배열에서 **해당 자리를 선택하고 그 자리에 오는 값을 찾는 것**이라고 생각하면 편하다.

![img](https://raw.githubusercontent.com/GimunLee/tech-refrigerator/master/Algorithm/resources/selection-sort-001.gif)



`진행순서`

- <u>주어진 배열 중에 최소값을 찾는다.</u>
- <u>그 값을 맨 앞에 위치한 값과 교체한다.</u> (pass)
- 맨 처음 위치를 뺀 나머지 배열을 같은 방법으로 교체한다.
-  (즉, 미정렬 리스트에서 최소값을 찾고 교체한다.)



```python
def SelctionSort(a[], n):
    for i from 0 to n-2   #(N-1도 됨)(두개 남았을때까지 하면 됌)
    	a[i],...,a[n-1]  #원소 중 최솟값 a[k]를 찾음
        a[i]<->a[k]
```

```python
def SelctionSort(a, N):
    for i in range(N-1):
        minIdx = i     #구간이 바뀔거라서 idx로 해야됨
        for j in range(i+1, N):    #비교할값, i부터 해도 상관 x 자기자신이라서
            if a[minIdx] > a[j]:
                minIdx = j
        a[i], a[minIdx] = a[minIdx], a[i]  #if문보다 앞에 위치한 이유: 
        								#for-if문에서 모든 구간을 다 돌고 나와야해서
```



`k th로 작은 원소 찾기`

```python
#k번째까지 작은 원소들을 찾아 이동시키고, 반환
def select(arr, k):
    for i in range(0, k):
    	minIdx = i
        for j in range(i+1, len(arr)):
            if arr[minIdx] > arr[j]:
                minIdx = j
        arr[i], arr[minIdx] = arr[minIdx], arr[i]
    return arr[k-1]
```







### 시간복잡도

------

데이터의 개수가 n개라고 했을 때,

- 첫 번째 회전에서의 비교횟수 : 1 ~ (n-1) => n-1

- 두 번째 회전에서의 비교횟수 : 2 ~ (n-1) => n-2

  ...

- `(n-1) + (n-2) + .... + 2 + 1 => n(n-1)/2`

비교하는 것이 상수 시간에 이루어진다는 가정 아래, n개의 주어진 배열을 정렬하는데 O(n^2) 만큼의 시간이 걸린다. 최선, 평균, 최악의 경우 시간복잡도는 **O(n^2)** 으로 동일하다.



### 공간복잡도

------

주어진 배열 안에서 교환(swap)을 통해, 정렬이 수행되므로 **O(n)** 이다.



### 장점

------

- Bubble sort와 마찬가지로 알고리즘이 단순하다.
- 정렬을 위한 비교 횟수는 많지만, Bubble Sort에 비해 실제로 교환하는 횟수는 적기 때문에 많은 교환이 일어나야 하는 자료상태에서 비교적 효율적이다.
- Bubble Sort와 마찬가지로 정렬하고자 하는 배열 안에서 교환하는 방식이므로, 다른 메모리 공간을 필요로 하지 않는다. => 제자리 정렬(in-place sorting)



### 단점

------

- 시간복잡도가 O(n^2)으로, 비효율적이다.
- **불안정 정렬(Unstable Sort)** 이다.



### [#](https://gyoogle.dev/blog/algorithm/Selection Sort.html#conclusion)Conclusion

------

Bubble Sort와 유사하지만, 조금 더 빠른 Selection Sort에 대해 알아봤다. 







참고자료

---

https://gyoogle.dev/blog/algorithm/Selection%20Sort.html