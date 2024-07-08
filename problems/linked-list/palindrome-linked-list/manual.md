### Решение

    class Solution:
        def find_middle(self, head):
            slow = head
            fast = head

            while fast and fast.next:
                slow = slow.next
                fast = fast.next.next

            return slow

        def reverse_list(self, head):
            p1 = None
            p2 = head

            while p2:
                tmp = p2.next

                p2.next = p1

                p1 = p2
                p2 = tmp

            return p1

        def isPalindrome(self, head: Optional[ListNode]) -> bool:
            middle = self.find_middle(head)

            start = head
            end = reverse_list(middle)

            while end:
                if start.val != end.val:
                    return False

                start = start.next
                end = end.next

            return True

### Оценка по времени: O(n), где n - размер связного списка

Объяснения: Нахождение середины, реверс связного списка и проход по списку для сравнения значений - все это O(n), соответственно общая оценка O(n)

### Оценка по памяти: O(1)

### Описание решения

Для начала находится середина связного списка. Затем от середины список переворачивается. Далее мы итеративно сравниваем значения, которые содержатся в 2-ух указателях - на начало и конец. И сравнием до тех пор, пока указатель на конец не достигнет nil ноды.
