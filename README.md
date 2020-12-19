# main
class Node:

    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:

    def __init__(self):
        self.head = None

    def printList(self):
        temp = self.head
        while(temp):
            print(temp.data)
            temp = temp.next

    def push(self, newData):
        newNode = Node(newData)
        newNode.next = self.head
        self.head = newNode

    def insertAfter(self, prevNode, newData):
        if prevNode is None:
            print("The given node must be in the linked list")
            return
        newNode = Node(newData)
        newNode.next = prevNode.next
        prevNode.next = newNode

    def append(self, newData):
        newNode = Node(newData)
        if self.head is None:
            self.head = newNode
            return
        last = self.head
        while(last.next):
            last = last.next
        last.next = newNode
    def deleteNode(self, key):
        temp = self.head
        if(temp is not None):
            if(temp.data == key):
                self.head = temp.next
                temp = None
                return
        while(temp is not None):
            if temp.data == key:
                break
            prev = temp
            temp = temp.next
        if(temp == None):
            return
        prev.next = temp.next
        temp = None

    def __repr__(self):
        return 'LinkedList(%s)' % str(self)

    def __iter__(self):
        current = self.head
        while current:
            yield current.data
            current = current.next

    def __str__(self):
        return '[%s]' % ', '.join([x for x in self])


if __name__ == '__main__':
    list = LinkedList()

    while True:
        print("1. Add an element")
        print("2. Delete an element")
        print("3. Push an element")
        print("4. Insert after an element")
        print("5. Print the list")
        menu = int(input("Choose a number: "))

        if menu == 1:
            add = input("Add an element: ")
            list.append(add)
        elif menu == 2:
            delete = input("Add an existing element to delete: ")
            list.deleteNode(delete)
        elif menu == 3:
            push = input("Push an element: ")
            list.push(push)
        elif menu == 4:
            prevNode = next("Add an element to insert after[Previous Node]: ")
            newData = next("Add an element to insert after[New Data]: ")
            list.insertAfter(prevNode, newData)
        elif menu == 5:
            print(list)
        else:
            print("Wrong input try again. ")
