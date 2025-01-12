# Heap Sort
![Wikipedia - Heap Sort](assets/gif_heapsort.gif)
## Heap Sort 구현하기
### Key Point
1. heap : 항상 최대값/최소값이 root 에 있는 complete binary tree
2. 최대값 / 최소값을 찾을 경우
```python
from structures import BinaryMinHeap

def heapsort(arr) :

    min_heap = BinaryMinHeap()

    for element in arr :
        min_heap.insert(element)

    return [min_heap.extract() for _ in range(len(arr))]
```
```python
class BinaryMinHeap :
    def __init__(self):
        self.items = [None]

    def insert(self, val):
        self.items.append(val)

        currentIdx = len(self.items) - 1
        parentIdx = currentIdx // 2

        while parentIdx > 0 :
            if self.items[currentIdx] < self.items[parentIdx] :
                self.items[currentIdx], self.items[parentIdx] = self.items[parentIdx], self.items[currentIdx]

            currentIdx = parentIdx
            parentIdx = currentIdx // 2

    def extract(self):

        if len(self.items ) < 2 :
            return None

        root = self.items[1]
        self.items[1] , self.items[-1] = self.items[-1] , self.items[1]
        self.items.pop()

        self._percolate_down(1)

        return root

    def _percolate_down(self, currentIdx):
        smallestIdx = currentIdx
        leftIdx = currentIdx * 2
        rightIdx = currentIdx * 2 + 1

        if leftIdx < len(self.items) and self.items[leftIdx] < self.items[smallestIdx] :
            smallestIdx = leftIdx
        if rightIdx < len(self.items) and self.items[rightIdx] < self.items[smallestIdx] :
            smallestIdx = rightIdx
        if smallestIdx != currentIdx :
            self.items[smallestIdx], self.items[currentIdx] = self.items[currentIdx], self.items[smallestIdx]
            self._percolate_down(smallestIdx)
```