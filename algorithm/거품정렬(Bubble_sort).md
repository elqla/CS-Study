## Bubble sort - 거품정렬

`sort(정렬)`
2개이상의 자료를 비교해 오름' 내림차순으로 재배열 하는 것


`버블소트`
- 비교하고, 교환한다!
- 서로 인접한 두 원소의 대소를 비교하고, 조건에 맞지 않다면 자리를 교환하며 정렬하는 알고리즘
- 시간복잡도 O(n**2)
    - (n-1) + (n-2) + (n-3) + .... + 2 + 1 => n(n-1)/2
- 공간 복잡도 O(n)

`공식`

```python
def bubblesort(A):
	for i in range(1, len(A)):        #왼쪽 원소[0]과 비교할 원소의 idx
    	for j in range(0, len(A)-1):   #왼쪽 원소의 idx
        	if A[j] > A[j+1]:  		  #왼쪽 원소가, 그 다음것보다 크면
            	A[j], A[j+1] = A[j+1], A[j] #두값의 위치 변경
```

`같지만 다른 공식`

```python
def bubblesort(a, N): 배열과 그 크기
	for i in range(N-1, 0, -1): #N-1에서 거꾸로 i값을 가짐 (가장 끝값과 비교하자?)
    	for j in range(0, i):	#왼쪽 원소의 idx
        	if a[j] > a[j+1]:   #왼쪽 원소가, 그 다음것보다 크면
            	a[j] a[j+1] = a[j+1], a[j] #두값의 위치 변경
```

`읽어볼것`
```python
def bubble_sort(num):


    # 3. 오른쪽 끝을 나타내는 i가 n-1 ~ 1 까지 이동합니다
    for i in range(len(num) - 1, 0, -1):

        # 1. index j가 0부터 i까지 이동하면서
        for j in range(0, i):

            # 2. num의 j번째 원소가 바로 오른쪽 원소보다 크면 위치를 바꿉니다
            if num[j] > num[j + 1]:
                num[j], num[j + 1] = num[j + 1], num[j]

    return num


num = [54, 26, 93, 17, 77, 31, 44, 55, 20]

print(bubble_sort(num))
```

`장점`
- 구현이 매우 간단하고, 소스코드가 직관적이다.

- 정렬하고자 하는 배열 안에서 교환하는 방식이므로, 다른 메모리 공간을 필요로 하지 않다. => 제자리 정렬(in-place sorting)

- 안정 정렬(Stable Sort) 이다.


`단점`
- 시간복잡도가 최악, 최선, 평균 모두 O(n^2)으로, 굉장히 비효율적이다.
- 정렬 돼있지 않은 원소가 정렬 됐을때의 자리로 가기 위해서, 교환 연산(swap)이 많이 일어나게 된다.






`참고자료`
- https://gyoogle.dev/blog/algorithm/Bubble%20Sort.html