Given an undirected graph and a set of vertices, find all reachable nodes from every vertex present in the given set.

Consider below undirected graph with 2 disconnected components. 

GraphEx1 

arr[] = {1 , 2 , 5}
Reachable nodes from 1 are  1, 2, 3, 4
Reachable nodes from 2 are 1, 2, 3, 4
Reachable nodes from 5 are 5, 6, 7


## Code:
``` java
public Map<Integer,List<Integer>> findAllReachables(List<Integer> vertices,Map<Integer,List<Integer>> graph)
    {
        Map<Integer,List<Integer>> allReachables=new HashMap<>();
        int max=Collections.max(graph.keySet());
        boolean[] visited=new boolean[max+1];
        
        for(int vertex:vertices)
        {
            if(visited[vertex]==false)
            {
                List<Integer> vertexReachables=new ArrayList<>();
                visited[vertex]=true;
                vertexReachables.add(vertex);   
                for(int edge:graph.getOrDefault(vertex,new ArrayList<>()))
                {
                    if(visited[edge]==false)
                    {
                       visited[edge]=true;
                       List<Integer> edgeReachables=findReachables(edge,graph, max);
                       allReachables.put(edge,edgeReachables);
                       addUniques(vertexReachables,edgeReachables);
                    }
                    else addUniques(vertexReachables,allReachables.get(edge));
                }
                allReachables.put(vertex,vertexReachables);
            }
        }
        return allReachables;
    }
    public List<Integer> findReachables(int vertix,Map<Integer,List<Integer>> graph,int max)
    {
        List<Integer> edgeReachables=new ArrayList<>();
        boolean[] visit=new boolean[max+1];
        Queue<Integer> q=new LinkedList<>();
        q.add(vertix);
        visit[vertix]=true;
        edgeReachables.add(vertix);
        while(!q.isEmpty())
        {
        int curVertix=q.poll();
        for(int edge:graph.get(curVertix))
        {
            if(visit[edge]==false)
                {
                    visit[edge]=true;
                    q.add(edge);
                    edgeReachables.add(edge);
                }
        }
        }
        return edgeReachables;
    }
    public void addUniques(List<Integer> list1,List<Integer> list2)
    {
        Set<Integer> set=new HashSet<>(list1);
        for(int element:list2)
            if(!set.contains(element))
                list1.add(element);
    }
    ```