### Решение

    class Solution:
        def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
            if head is None:
                return head

            p1 = None
            p2 = head

            while p2 is not None:
                tmp = p2.next

                p2.next = p1

                p1 = p2
                p2 = tmp

            return p1

### Оценка по времени: O(n), где n - размер связного списка

Объяснения: для того чтобы развернуть все связи у нод, нужно пройти по всему списку размера n.

### Оценка по памяти: O(1)

### Описание решения

Решается с помощью 2-ух указателей - p1 и p2. Для начала сохраняем next ноды, на которую указывает p2 указатель. Затем связываем p1 и p2 ноду. Далее сдвигаем указатели - p1 на место p2, p2 на сохраненный next.
