### Ошибка 1 - Разворот списка вызван не от середины, а от head

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
            end = self.reverse(head) <- FAIL

            while start is not end:
                tmp = start.next

                start.next = end

                start = end
                end = tmp
