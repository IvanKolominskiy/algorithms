### Решение

    class Solution:
        def get_val(self, node):
            if node:
                return node.val
            return 101

        def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
            dummy_node = ListNode()

            curr = dummy_node

            while list1 or list2:
                if self.get_val(list1) < self.get_val(list2):
                    curr.next = list1
                    curr = list1
                    list1 = list1.next
                else:
                    curr.next = list2
                    curr = list2
                    list2 = list2.next

            return dummy_node.next

### Оценка по времени: O(n), где n - суммарный размер 2-ух списков

Объяснения: Для того чтобы смерджить 2 списка нужно зайти в каждую вершину каждого списка.

### Оценка по памяти: O(1)

### Описание решения

Для начала создаем dummy_node чтобы не нужно было разбираться с какой вершины начинать составлять наш смердженный список. Далее сравниваем значения из 2-ух списков, выбираем минимальное, присоединяем её к текущей вершине, делаем эту вершину текущей и свдигаем указатель в том списке откуда мы взяли эту вершину. Если в какой то момент мы попадем в None, то функция get_val вернет значение, которое больше любого значения в списке.
