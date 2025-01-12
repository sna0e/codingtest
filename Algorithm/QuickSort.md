# Quick Sort
![Wikipedia - Quick Sort](assets/gif_quicksort.gif)
## Quick Sort 구현하기
### Key Point
1. Divide and Conquer 분할정복
2. 배열에서 pivot (기준) 정하기
3. Divide : pivot 보다 작은 집합과 큰 집합으로 나누기
4. pivot 을 두 집합 사이로 위치
5. Conquer : 2-4 번을 재귀호출 하여 정렬
6. 정렬 후 결과 합치기
7. 특징 : 이미 정렬된 경우 O(n^2), 절반씩 이쁘게 쪼개지는 경우 O(NlogN)
```python
def quicksort (arr, start, end) :

    if start > end :
        return

    i = start - 1
    pivot = arr[end]
    for j in range (start, end) :
        if arr[j] < pivot :
            i += 1 # arr[j] 를 작은 값 집합으로 포함시키기 위한 영역 확장
            arr[i], arr[j] = arr[j], arr[i]
            # arr[i] 까지는 pivot 보다 작은 값 집합 & 정렬 완료, arr[j] 는 지금 확인하는 값
            # 그런데 arr[j] < pivot 이라는 것은 arr[j] 를 작은 값 집합에 추가해야 한다는 뜻
            # 즉, arr[j] 를 작은 값 집합에 추가 하기 위한 자리 교환

    arr[i+1], arr[end] = arr[end], arr[i+1] # i + 1 == pivot 이 최종적으로 위치할 index

    quicksort(arr, start, i)
    quicksort(arr, i+2, end)
    
    return arr
```
#### 부연 설명
i : pivot 보다 작은 값이 모여 있는 경계 인덱스  
i + 1 = 최종적으로 pivot 자리  
j : 배열의 요소와 pivot 의 값을 비교하기 위한 인덱스