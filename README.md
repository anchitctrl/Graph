# Graph

## Table of Contents:
* [Implementation of Graph Using Adjacency List](#implementation-of-graph-using-adjacency-list)
* [Implementation of Graph Using Adjacency Matrix](#implementation-of-graph-using-adjacency-matrix)
* [Breadth First Search Using Adjacency List](#breadth-first-search-using-adjacency-list)
* [Depth First Search Using Adjacency List](#depth-first-search-using-adjacency-list)

<a name="implementation-of-graph-using-adjacency-list"></a>
## Implementation of Graph Using Adjacency List

```java
class Graph {
      
    // A utility function to add an edge in an
    // undirected graph
    static void addEdge(ArrayList<ArrayList<Integer> > adj,
                        int u, int v)
    {
        adj.get(u).add(v);
        adj.get(v).add(u);
    }
  
    // A utility function to print the adjacency list
    // representation of graph
    static void printGraph(ArrayList<ArrayList<Integer> > adj)
    {
        for (int i = 0; i < adj.size(); i++) {
            System.out.println("\nAdjacency list of vertex" + i);
            System.out.print("head");
            for (int j = 0; j < adj.get(i).size(); j++) {
                System.out.print(" -> "+adj.get(i).get(j));
            }
            System.out.println();
        }
    }
  
    // Driver Code
    public static void main(String[] args)
    {
        // Creating a graph with 5 vertices
        int V = 5;
        ArrayList<ArrayList<Integer> > adj 
                    = new ArrayList<ArrayList<Integer> >(V);
          
        for (int i = 0; i < V; i++)
            adj.add(new ArrayList<Integer>());
  
        // Adding edges one by one
        addEdge(adj, 0, 1);
        addEdge(adj, 0, 4);
        addEdge(adj, 1, 2);
        addEdge(adj, 1, 3);
        addEdge(adj, 1, 4);
        addEdge(adj, 2, 3);
        addEdge(adj, 3, 4);
          
        printGraph(adj);
    }
}
```

<a name="implementation-of-using-adjacency-matrix"></a>
## Implementation of Graph Using Adjacency Matrix

> Instead of Using a 2D Array List we can use a 2D Array only

<a name="breadth-first-search-using-adjacency-list"></a>
## Breadth First Search Using Adjacency List

```java
import java.io.*;
import java.util.*;
class Graph
{
	private int V; // No. of vertices
	private LinkedList<Integer> adj[]; //Adjacency Lists

	// Constructor
	Graph(int v)
	{
		V = v;
		adj = new LinkedList[v];
		for (int i=0; i<v; ++i)
			adj[i] = new LinkedList();
	}
	void addEdge(int v,int w)
	{
		adj[v].add(w);
	}
	void BFS(int s)
	{
		boolean visited[] = new boolean[V];
		LinkedList<Integer> queue = new LinkedList<Integer>();
		visited[s]=true;
		queue.add(s);

		while (queue.size() != 0)
		{
			s = queue.poll();
			System.out.print(s+" ");
			Iterator<Integer> i = adj[s].listIterator();
			while (i.hasNext())
			{
				int n = i.next();
				if (!visited[n])
				{
					visited[n] = true;
					queue.add(n);
				}
			}
		}
	}
	public static void main(String args[])
	{
		Graph g = new Graph(4);
		g.addEdge(0, 1);
		g.addEdge(0, 2);
		g.addEdge(1, 2);
		g.addEdge(2, 0);
		g.addEdge(2, 3);
		g.addEdge(3, 3);
      
        g.BFS(2);
	}
}
```

<a name="depth-first-search-using-adjacency-list"></a>
## Depth First Search Using Adjacency List

```java
void DFSUtil(int v, boolean visited[])
    {
        // Mark the current node as visited and print it
        visited[v] = true;
        System.out.print(v + " ");
  
        // Recur for all the vertices adjacent to this
        // vertex
        Iterator<Integer> i = adj[v].listIterator();
        while (i.hasNext()) 
        {
            int n = i.next();
            if (!visited[n])
                DFSUtil(n, visited);
        }
    }
```
