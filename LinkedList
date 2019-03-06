
enum LinkedListError : Error {
    case tailDoesNotExist
    case emptyList
    case keyNotfound
}

class LinkedListNode<Type> {
    
    var key : Type
    
    var next : LinkedListNode?
    weak var prev : LinkedListNode?
    
    init(key : Type) {
        self.key = key
    }
}


class LinkedList<Type> {
    
    typealias Node = LinkedListNode<Type>
    
    var head : Node?
    var tail : Node?
    var count = 0;
    
    var first : Node? {
        return head
    }
    
    var last : Node? {
        return tail
    }
    
    var nodeCount : Int {
        return count
    }
    
    //Appends a new node to the tail of the linked list
    func append(_ element : Type ) {
        
        let newNode = LinkedListNode(key: element)
        
        if let tail = self.tail{
            tail.next = newNode
            newNode.prev = tail
        }else {
            self.head = newNode
        }
        
        self.tail = newNode
        count += 1
    }
    
    
    //Iterate through list and print values
    func printLinkedList() {
        if var node = head {
            while(node.next != nil) {
                print(node.key)
                node = node.next!
            }
            print(node.key)
        }
    }
    
    //Returns a node at the specified index
    func node(atIndex index: Int) -> LinkedListNode<Type>? {
        
        var counter = 0
        
        if var node = head {
            while (node.next != nil) {
                if(counter == index) { return node}
                counter += 1
                node = node.next!
            }
        }
        return nil
    }
    
    //Inserts an element at a specific index
    func insert(_ element : Type, atIndex index : Int) {
        
        let insertionNode = LinkedListNode(key: element)
        let nodeAtIndex = node(atIndex: index)
        let nodeBeforeIndex = nodeAtIndex?.prev
        
        if(nodeAtIndex == nil && nodeBeforeIndex == nil){
            append(element)
        }else {
            nodeBeforeIndex?.next = insertionNode
            nodeAtIndex?.prev = insertionNode
            
            insertionNode.prev = nodeBeforeIndex
            insertionNode.next = nodeAtIndex
            count += 1
        }

    }
    
    //Removes a node at the specified index.
    func remove(at index: Int) throws{
        
       var counter = 0
        
        let node = head
        while(node?.next != nil){
        
            if (index == counter && self.nodeCount > 1){
                
                let prevNode = node?.prev
                let nextNode = node?.next
                
                prevNode?.next = nextNode
                nextNode?.prev = prevNode
                count -= 1
                break
            }else if(index == counter){
                removeHead()
                count -= 1
                break
            }
            counter += 1
        }
        if(counter > index) {
            throw LinkedListError.keyNotfound
        }
        
    }
    
    
    //Removes tail from the linked list
    func removeTail() throws{
        guard let tail = self.tail else {
            throw LinkedListError.tailDoesNotExist
        }
        
        guard let tailPrev = tail.prev else {
            throw LinkedListError.emptyList
        }
        
        let newTail = tailPrev
        newTail.next = nil
        count -= 1
    }
    
    //Removes the head of the linked list.
    func removeHead() {
        
        if(self.nodeCount > 1){
            head = head?.next
        }else {
            head = nil
        }
        count -= 1
    }

}
    






