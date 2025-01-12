# Selection Sort 
![Wikipedia - Selection Sort](assets/gif_selectionsort.gif)
## Selection Sort 구현하기
### key Point
1. 데이터를 순회하며 가장 작은 데이터 찾기
2. 가장 작은 데이터와 맨 앞 자리 교체
3. 맨 앞에 제외하고 1. 부터 다시 시작하여 배열 끝까지 반복
   - 맨 앞엔 항상 가장 작은 데이터가 위치
```python
def selectionsort (arr) :

    for n in range (len(arr) - 1) :
        min = n
        for current in range (n+1, len(arr)) :
            if arr[current] < arr[min] :
                min = current

        if min != n :
            arr[n], arr[min] = arr[min], arr[n]

    return arr
```