# Insertion Sort
![Wikipedia-Insertion Sort](gif_insertionsort.gif)
## Insertion Sort 구현하기
### Key Point
1. 맨 첫번째 요소만 정렬된 상태로 간주
2. 이미 정렬된 부분 뒤의 데이터를 올바른 위치에 삽입하여 정렬 유지
3. 2.부터 배열 끝까지 반복
```python
def insertionsort (arr) :
    for n in range (len(arr) - 1) :
        for current in range(n+1, 0, -1) :
            if arr[current-1] > arr[current] :
                arr[current-1], arr[current] = arr[current], arr[current-1]
            else :
                break
    return arr
 ```