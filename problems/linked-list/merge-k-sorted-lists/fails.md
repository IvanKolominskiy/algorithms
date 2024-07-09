### Ошибка 1 - Решение не работает с пустыми списками

    class Solution:
        def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
            dummy_node = ListNode()

            curr = dummy_node

            while len(lists) != 0:
                min_node = float('inf')
                min_index = None

                for i in range(len(lists)):
                    if lists[i].val < min_node:
                        min_node = lists[i].val
                        min_index = i

                curr.next = lists[min_index]
                curr = lists[min_index]
                lists[min_index] = lists[min_index].next

                if lists[min_index] is None:
                    lists.pop(min_index)

            return dummy_node.next
