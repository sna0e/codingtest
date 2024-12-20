![img_2.png](../../2nd_week/img_2.png)
![img_1.png](../../2nd_week/img_1.png)

```python

class LinkedNode () :
    def __init__ (self, val=0, next=None) :
        self.val = val
        self.next = next

class LinkedList () :
    def __init__ (self):
        self.head = None
        
    def append(self, val):
        if self.head == None :
            self.head = LinkedNode(val)
            return 
        
        node = self.head
        while node.next :
            node = node.next
            
        node.next = LinkedNode(val)

```

## key point
1. 각 노드는 값을 가진다
2. 각 노드는 다음 가리키는 노드 정보를 가진다.
   - 끝 노드의 next = `None`
3. LinkedList 는 head 노드 정보를 가진다.
   - head 는 첫번째 노드