> a graph is a **data structure** used to represent relationships or connections between entities.
> 

---

## **keywords**

directed graph: edges have a direction.

undirected graph: edges have no direction.

adjacency list: a data structure where each vertex is a key, and its neighbors are stored as a list.

adjacency matrix: a 2D array where the cells indicate whether there is an edge between the vertices.

edge: a connection between two vertices.

vertex (node): an entity in the graph.

---

## **how it works**

### **diagram**

image.png

---

### **code**

**initialization:**

```python
class Graph:
    def __init__(self):
        self.adj_list = {}
    
    def add_vertex(self, vertex):
        if vertex not in self.adj_list:
            self.adj_list[vertex] = []
```

**insertion:**

```python
    def add_edge(self, vertex1, vertex2, weight=None):
        if vertex1 in self.adj_list and vertex2 in self.adj_list:
            self.adj_list[vertex1].append((vertex2, weight))
            # for undirected graph, add the reverse connection
            # self.adj_list[vertex2].append((vertex1, weight))

```

**retrieval:**

```python
    def get_neighbors(self, vertex):
        return self.adj_list.get(vertex, [])

```

**deletion:**

```python

    def remove_edge(self, vertex1, vertex2):
        if vertex1 in self.adj_list:
            self.adj_list[vertex1] = [edge for edge in self.adj_list[vertex1] if edge[0] != vertex2]

    def remove_vertex(self, vertex):
        if vertex in self.adj_list:
            del self.adj_list[vertex]
            for v in self.adj_list:
                self.adj_list[v] = [edge for edge in self.adj_list[v] if edge[0] != vertex]

```

**display:**

```python
    def display(self):
        for vertex, edges in self.adj_list.items():
            print(f"{vertex}: {edges}")

```

---

**putting it together:**

1. initialize a graph instance.
2. add vertices and edges.
3. retrieve neighbors or display the graph structure.
4. remove edges or vertices as needed.

**main:**

```python
graph = Graph()

# adding vertices
graph.add_vertex('A')
graph.add_vertex('B')
graph.add_vertex('C')

# adding edges
graph.add_edge('A', 'B', weight=1)
graph.add_edge('B', 'C', weight=2)

# display the graph
graph.display()

# remove an edge and a vertex
graph.remove_edge('A', 'B')
graph.remove_vertex('C')

graph.display()

```

---

## **runtime complexity**

**insertion, retrieval, deletion:**

**best case:** O(1)

insertion and deletion in adjacency lists for sparse graphs.

**worst case:** O(vertexes) or O(edges)

insertion, deletion, or retrieval in adjacency matrixes for dense graphs due to resizing.

---

## **use cases**

best for representing relationships like social networks, maps, dependency graphs, and workflow systems.

---

## **resources**

https://www.youtube.com/watch?v=-VgHk7UMPP4