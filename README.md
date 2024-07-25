# VisualBasic_DSA
---

## Data Structures in VB.NET

### 1. Arrays

**Description:**  
An array is a fixed-size collection of elements of the same type. The size of an array must be specified at the time of creation, and each element is accessed by its index, starting from 0.

**Use Case:**  
Arrays are used when you know the number of elements in advance and need fast access to elements by index.

**Example:**
```vbnet
' Declare and initialize an array of integers
Dim numbers(4) As Integer
numbers(0) = 10
numbers(1) = 20
numbers(2) = 30
numbers(3) = 40
numbers(4) = 50

' Accessing elements
For i As Integer = 0 To numbers.Length - 1
    Console.WriteLine(numbers(i))
Next
```

### 2. Lists

**Description:**  
A `List(Of T)` is a dynamic array that can grow and shrink in size. It is part of the `System.Collections.Generic` namespace and provides methods for adding, removing, and accessing elements.

**Use Case:**  
Lists are useful when you need a collection that can change size dynamically.

**Example:**
```vbnet
' Create a list of strings
Dim fruits As New List(Of String)()
fruits.Add("Apple")
fruits.Add("Banana")
fruits.Add("Cherry")

' Iterate through the list
For Each fruit In fruits
    Console.WriteLine(fruit)
Next

' Remove an item
fruits.Remove("Banana")
Console.WriteLine("After removal:")
For Each fruit In fruits
    Console.WriteLine(fruit)
Next
```

### 3. Dictionaries

**Description:**  
A `Dictionary(Of TKey, TValue)` is a collection of key-value pairs, where each key is unique. It allows for fast retrieval of values based on keys.

**Use Case:**  
Dictionaries are ideal for scenarios where you need to map a unique key to a value, like a phone book or a product catalog.

**Example:**
```vbnet
' Create a dictionary to store phone numbers
Dim phoneBook As New Dictionary(Of String, String)()
phoneBook("Alice") = "123-456-7890"
phoneBook("Bob") = "987-654-3210"

' Access a value using a key
Console.WriteLine("Alice's phone number: " & phoneBook("Alice"))

' Check if a key exists
If phoneBook.ContainsKey("Charlie") Then
    Console.WriteLine("Charlie's phone number: " & phoneBook("Charlie"))
Else
    Console.WriteLine("Charlie is not in the phone book.")
End If
```

### 4. Stacks

**Description:**  
A stack is a Last-In-First-Out (LIFO) collection. You can only add or remove elements from the top of the stack. The main operations are `Push` (to add) and `Pop` (to remove).

**Use Case:**  
Stacks are used in scenarios like undo mechanisms, expression evaluation, and depth-first search algorithms.

**Example:**
```vbnet
' Create a stack of integers
Dim stack As New Stack(Of Integer)()
stack.Push(1)
stack.Push(2)
stack.Push(3)

' Pop elements from the stack
While stack.Count > 0
    Console.WriteLine(stack.Pop())
End While
```

### 5. Queues

**Description:**  
A queue is a First-In-First-Out (FIFO) collection. Elements are added at the back and removed from the front. The main operations are `Enqueue` (to add) and `Dequeue` (to remove).

**Use Case:**  
Queues are used in scenarios like task scheduling, managing requests in a system, and breadth-first search algorithms.

**Example:**
```vbnet
' Create a queue of integers
Dim queue As New Queue(Of Integer)()
queue.Enqueue(1)
queue.Enqueue(2)
queue.Enqueue(3)

' Dequeue elements from the queue
While queue.Count > 0
    Console.WriteLine(queue.Dequeue())
End While
```

### 6. Linked Lists

**Description:**  
A linked list is a collection of nodes, where each node contains data and a reference to the next node. There are different types of linked lists, such as singly linked lists and doubly linked lists.

**Use Case:**  
Linked lists are useful when you need a dynamic collection with efficient insertion and deletion of elements at any position.

**Example of a Singly Linked List:**
```vbnet
Public Class Node
    Public Property Data As Integer
    Public Property NextNode As Node

    Public Sub New(data As Integer)
        Me.Data = data
        Me.NextNode = Nothing
    End Sub
End Class

Public Class LinkedList
    Public Property Head As Node

    Public Sub Add(data As Integer)
        Dim newNode As New Node(data)
        If Head Is Nothing Then
            Head = newNode
        Else
            Dim current As Node = Head
            While current.NextNode IsNot Nothing
                current = current.NextNode
            End While
            current.NextNode = newNode
        End If
    End Sub

    Public Sub Display()
        Dim current As Node = Head
        While current IsNot Nothing
            Console.WriteLine(current.Data)
            current = current.NextNode
        End While
    End Sub
End Class

' Usage
Dim linkedList As New LinkedList()
linkedList.Add(1)
linkedList.Add(2)
linkedList.Add(3)
linkedList.Display()
```

### 7. HashSets

**Description:**  
A `HashSet(Of T)` is an unordered collection that contains unique elements. It provides efficient methods for adding, removing, and checking for the presence of elements.

**Use Case:**  
HashSets are useful for maintaining a collection of unique items and performing operations like intersection, union, and difference.

**Example:**
```vbnet
' Create a HashSet of integers
Dim uniqueNumbers As New HashSet(Of Integer)()
uniqueNumbers.Add(1)
uniqueNumbers.Add(2)
uniqueNumbers.Add(1) ' Duplicate, will not be added

' Display unique numbers
For Each num In uniqueNumbers
    Console.WriteLine(num)
Next

' Check if a number is in the HashSet
If uniqueNumbers.Contains(2) Then
    Console.WriteLine("2 is in the set.")
Else
    Console.WriteLine("2 is not in the set.")
End If
```

### 8. Trees

**Description:**  
A tree is a hierarchical data structure consisting of nodes, where each node has a value and children. The top node is called the root, and nodes with no children are called leaves. A binary tree is a tree where each node has at most two children.

**Use Case:**  
Trees are used in scenarios like representing hierarchical data (e.g., file systems), search algorithms (e.g., binary search trees), and data compression (e.g., Huffman coding).

**Example of a Binary Tree:**
```vbnet
Public Class TreeNode
    Public Property Value As Integer
    Public Property Left As TreeNode
    Public Property Right As TreeNode

    Public Sub New(value As Integer)
        Me.Value = value
        Me.Left = Nothing
        Me.Right = Nothing
    End Sub
End Class

Public Class BinaryTree
    Public Property Root As TreeNode

    Public Sub New(value As Integer)
        Root = New TreeNode(value)
    End Sub

    ' In-order traversal
    Public Sub InOrderTraversal(node As TreeNode)
        If node IsNot Nothing Then
            InOrderTraversal(node.Left)
            Console.WriteLine(node.Value)
            InOrderTraversal(node.Right)
        End If
    End Sub
End Class

' Usage
Dim tree As New BinaryTree(5)
tree.Root.Left = New TreeNode(3)
tree.Root.Right = New TreeNode(7)
tree.Root.Left.Left = New TreeNode(2)
tree.Root.Left.Right = New TreeNode(4)
tree.InOrderTraversal(tree.Root)
```

### 9. Graphs

**Description:**  
A graph is a collection of vertices (nodes) and edges (connections) that connect pairs of vertices. Graphs can be directed or undirected and may have weights associated with edges.

**Use Case:**  
Graphs are used to represent networks like social networks, transportation systems, and web page links.

**Example of an Adjacency List Representation:**
```vbnet
Public Class Graph
    Private adjacencyList As New Dictionary(Of Integer, List(Of Integer))()

    Public Sub AddEdge(vertex1 As Integer, vertex2 As Integer)
        If Not adjacencyList.ContainsKey(vertex1) Then
            adjacencyList(vertex1) = New List(Of Integer)()
        End If
        adjacencyList(vertex1).Add(vertex2)
    End Sub

    Public Sub Display()
        For Each vertex In adjacencyList.Keys
            Console.Write(vertex & " -> ")
            For Each neighbor In adjacencyList(vertex)
                Console.Write(neighbor & " ")
            Next
            Console.WriteLine()
        Next
    End Sub
End Class

' Usage
Dim graph As New Graph()
graph.AddEdge(0, 1)
graph.AddEdge(0, 2)
graph.AddEdge(1, 2)
graph.AddEdge(2, 0)
graph.AddEdge(2, 3)
graph.Display()
```

---

These Markdown-formatted sections provide clear descriptions, use cases, and examples for each data structure. Let me know if you'd like more details or specific additions!
