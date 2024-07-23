Given an Undirected Graph having unit weight, find the shortest path from the source to all other nodes in this graph. In this problem statement, we have assumed the source vertex to be ‘0’. If a vertex is unreachable from the source node, then return -1 for that vertex.

Example 1:


Input:
n = 9, m = 10
edges = [[0,1],[0,3],[3,4],[4 ,5],[5, 6],[1,2],[2,6],[6,7],[7,8],[6,8]]
src=0 

Output: 0 1 2 1 2 3 3 4 4

Explanation:
The above output array shows the shortest path to all 
the nodes from the source vertex (0), Dist[0] = 0, 
Dist[1] = 1 , Dist[2] = 2 , …. Dist[8] = 4 
Where Dist[node] is the shortest path between src and 
the node. For a node, if the value of Dist[node]= -1, 
then we conclude that the node is unreachable from 
the src node.
## Code:

``` java
public int[] findAllMinReachableDistance(List<List<Integer>> graph)
    {
        int[] distance=new int[graph.size()];
        boolean[] visited=new boolean[graph.size()];
        Queue<Integer> q=new LinkedList<>();
        
        q.add(0);
        distance[0]=0;
        visited[0]=true;
        while(!q.isEmpty())
        {
            int vertex=q.poll();
            for(int edge:graph.get(vertex))
            {
                if(visited[edge]==false)
                {
                    visited[edge]=true;
                    distance[edge]=distance[vertex]+1;
                    q.add(edge);
                }
            }
        }
        return distance;
    }
    ```