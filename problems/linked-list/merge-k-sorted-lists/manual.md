### Решение

    class Solution:
        def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
            dummy_node = ListNode()

            curr = dummy_node

            while True:
                min_node = float('inf')
                min_index = None

                for i in range(len(lists)):
                    if lists[i] is None:
                        continue

                    if lists[i].val < min_node:
                        min_node = lists[i].val
                        min_index = i

                if min_node == float('inf'):
                    break

                curr.next = lists[min_index]
                curr = lists[min_index]
                lists[min_index] = lists[min_index].next

            return dummy_node.next

### Оценка по времени: O(n \* k), где n - суммарный размер всех списков, k - количество списков

Объяснения: Для того чтобы смерджить все списки нужно зайти в каждую вершину каждого списка.

### Оценка по памяти: O(1)

### Описание решения

Для начала создаем dummy_node чтобы не нужно было разбираться с какой вершины начинать составлять наш смердженный список. Далее сравниваем значения из всех данных списков списков, выбираем минимальное, присоединяем её к текущей вершине, делаем эту вершину текущей и свдигаем указатель в том списке откуда мы взяли эту вершину. Алгоритм завершается когда во всех списках мы дошли до nil ноды.
