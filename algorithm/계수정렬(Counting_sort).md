# 계수정렬(counting_sort)



> 비교환 방식, 비교x
>
> 각 항목의 발생횟수를 기록하며, 정수 항목으로 인덱스 되는 카운트(갯수)들의 배열을 사용한다.



- 정수에 한하며, 비교적 n이 작을때 사용한다.

- 시간복잡도 O(n+k)
    - n = list의 길이
    - k = 배열에서 등장하는 정수의 최댓값
- 공간복잡도 O(n)
    - k만큼의 배열을 만들어야 함
- counting need !

---

`공식`

```python
def counting_sort(A, B, K):
#A[]- 입력배열(data)
#B[]- 정렬된배열(TEMP)
#C[]- count배열
#K = 배열에서 등장하는 최댓값


#count
C = [0]*(K+1)  #c=[0]*(max(A) +1)  ' len(A)+1			#최댓값+1 (+1은 0의 값추가)
for i in range(0, len(A)):
	c[A[i]] += 1  			#C에 [ A[i](즉, data값)을 idx로]를 +1해준다.
    					#ex) C[A[i]] = C[숫자3] +=1   ##배열에 값 추가
                            
                            
#누적
for i in range(1, len(C)):  #저장할 자리 기준 ㅁㅁㅁㅁ이면 0th 값은 누적시 그대로니까, 1부터시작!
	C[i] += C[i-1]			#C[i]저장할새로운 변수의 위치(ex,1th)에 += 전꺼더해주기
    						#그럼 C[i]도 바뀌어서 그 다음꺼 할때 계속 누적됨 !!
                            
                            
#temp                
for i in range(len(B)-1, -1, -1):   #len(B) == len(A)라서, 그냥 N-1을(모든값을) 거꾸로 적용한다고 생각!
	C[A[i]] -= 1				  #Count[A[i]_data값을 idx로] -= 1 (count줄이기)  (A[i], 끝부분 기준)
    B[C[A[i]] = A[i]			   #B_temp[C[A[i]]] = A[i]
    							 #B배열에[C[A[i]_data값]]
	  #B배열에[count값을 idx로(순차적이므로 1부터, 값 없으면 count안하니까 0xx)] = A[i]   (A의 i번째 인자)

```
`읽어볼것`

```python
#count-value
def counting_sort(input_arr, k):   # k : 0 ~ k
    
    counting_arr = [0] * (k + 1) #list초기화
    for i in range(len(input_arr)):  #갯수count      # for num in input_arr:
        counting_arr[input_arr[i]] += 1    			#counting_arr[num] += 1
			# 개수가 들어있는 counting array를 input_array의 원소들의 인덱스를 바라볼 수 있도록 변경	
    
	#누적
    for i in range(1, len(counting_arr)):   
        counting_arr[i] += counting_arr[i - 1]

        
 
    result_arr = [-1] * len(input_arr)     # 결과가 담길 리스트를 초기화 (0~k)값 X -오류 확인 시 용이

    input_arr = input_arr[::-1]   # 오른쪽 -> 왼쪽의 흐름을 왼쪽 
    							# -> 오른쪽 흐름으로 가져오기 위해 리스트를 뒤집음

    
    
# input_arr의 값을 index로 가져옵니다. 이를 사용하여 counting_arr에 들어있는 해당 값이 들어갈 수 있는 가장 오른쪽 index를 찾습니다.
# counting_arr의 숫자는 1부터 시작하는 "번째"의 개념이고, 파이썬은 0부터 시작하기 때문에 -1을 하여 값을 맞추어줍니다.
# -1을 한 값에 맨 처음 가져온 input_arr의 값을 넣어줍니다.
    for i in input_arr:
        counting_arr[i] -= 13  
        result_arr[counting_arr[i]] = i

    # {위 코드의 i} == {해당 코드의 input_arr[i]}입니다. why
    # for i in range(len(input_arr) - 1, -1, -1):
    #     counting_arr[input_arr[i]] -= 1
    #     result_arr[counting_arr[input_arr[i]]] = input_arr[i]

    return result_arr


lst = [0, 4, 1, 3, 1, 2, 4, 1]

print(counting_sort(lst, 5)) # [0, 1, 1, 1, 2, 3, 4, 4]
```

```python
#문제풀다 고민한..
def counting_sort(num):
    #count
    c = [0]*(max(num)+1) ##
    for i in range(len(num)):
        c[num[i]] += 1
    #누적
    for i in range(1, len(c)):
        c[i] += c[i-1]

    #재정렬
    new_lst = [0]*len(num)
    for i in range(len(num)):
        c[num[i]] -= 1
        new_lst[c[num[i]]] = num[i]

    return new_lst

num = [54, 26, 93, 17, 77, 31, 44, 55, 20]
print(counting_sort(num))
```





---
`관련문제`

- https://www.acmicpc.net/problem/10989

---

- 사용 : 정렬하는 숫자가 특정한 범위 내에 있을 때 사용
	(Suffix Array 를 얻을 때, 시간복잡도 O(nlgn)으로 얻을 수 있음.)

- 장점 : O(n) 의 시간복잡도


- non-Comparison Sort 이다.

```python
#Comparison Sort
N개 원소의 배열이 있을 때, 이를 모두 정렬하는 가짓수는 N!임

따라서, Comparison Sort를 통해 생기는 트리의 말단 노드가 N! 이상의 노드 갯수를 갖기 위해서는, 
2^h >= N! 를 만족하는 h를 가져야 하고, 이 식을 h > O(nlgn)을 가져야 한다. 
(h는 트리의 높이,,, 즉 Comparison sort의 시간 복잡도임)

이런 O(nlgn)을 줄일 수 있는 방법은 Comparison을 하지 않는 것

```

- 단점 : 배열 사이즈 N 만큼 돌 때, 증가시켜주는 Counting 배열의 크기가 큼. (메모리 낭비가 심함)

`참고자료`
- https://gyoogle.dev/blog/algorithm/Counting%20Sort.html