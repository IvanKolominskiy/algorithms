### Решение

    class Solution:
        def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
            slow = head
            fast = head

            while fast is not None and fast.next is not None:
                slow = slow.next
                fast = fast.next.next

            return slow

### Оценка по времени: O(n), где n - размер связного списка

Объяснения: чтобы дойти до середины нам нужно сделать n/2 операций

### Оценка по памяти: O(1)

### Описание решения

Используются 2 указателя - fast и slow. Fast указатель на каждой итерации проходит на 2 шага вперед. Идем по списку пока не достигнем nil ноды, либо пока fast.next не является nil нодой. В итоге середина связного списка будет находится в slow указателе.
