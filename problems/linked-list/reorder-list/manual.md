### Решение

    class Solution:
        def find_middle(self, head):
            fast = head
            slow = head

            while fast and fast.next:
                slow = slow.next
                fast = fast.next.next

            return slow

        def reverse(self, head):
            p1 = None
            p2 = head

            while p2:
                tmp = p2.next

                p2.next = p1

                p1 = p2
                p2 = tmp

            return p1

        def reorderList(self, head: Optional[ListNode]) -> None:
            """
            Do not return anything, modify head in-place instead.
            """

            middle = self.find_middle(head)

            start = head
            end = self.reverse(middle)

            while start is not end:
                tmp = start.next

                start.next = end

                start = end
                end = tmp

### Оценка по времени: O(n), где n - размер связного списка

Объяснения: Найти середину - O(n), Развернуть список - O(n), Связать значения - O(n). Общая сложность O(n).

### Оценка по памяти: O(1)

### Описание решения

Для начала ищем середину. Затем от середины список разворачиваем. Далее решаем задачу с помощью указателя на начало и конец. На каждой итерации связываем указатель на начало с указателем на конец, затем указатель на конец свдигаем на next указателя на начало, а указатель на начало сдвигаем на место указателя на конец. В итоге оба указателя окажутся в одной вершине - здесь мы завершаем работу.
