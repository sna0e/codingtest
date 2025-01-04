# BFS
Breadth First Search
![image](gif_BFS.gif)

## BFS 구현하기
### Key Point
1. 인접 노드 부터 방문
2. Queue 유사

```python
from collections import deque

def bfs_queue(graph, start) :
    visited = [start]
    deq = deque([start]) # 방문할 곳


    while deq :
        node = deq.popleft()
        for adjacent in graph[node] :
            if adjacent not in visited :
                deq.append(adjacent) # 방문 예정
                visited.append(adjacent) # 방문 함

    return visited
```

## 예시 문제 - 섬의 개수
```python
from collections import deque

def island_bfs(grid) :

    count = 0
    deq = deque()
    rows = len(grid)
    cols = len(grid[0])
    direction_row = [-1, 1, 0, 0]
    direction_col = [0, 0, -1, 1]

    for r in range (rows) :
        for c in range (cols) :
            if grid[r][c] != "1" :
                continue

            count += 1
            deq.append((r, c))

            while deq :
                x, y = deq.popleft()

                for i in range (4) :
                    nx = x + direction_row[i]
                    ny = y + direction_col[i]

                    if nx < 0 or nx >= rows or ny < 0 or ny >= cols or grid[nx][ny] != "1" :
                        continue

                    grid[nx][ny] = "0"
                    deq.append((nx, ny))

    return count
```