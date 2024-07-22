## Find all Reachables of a vertex in a graph

``` java

public List<Integer> findReachables(int vertix,Map<Integer,List<Integer>> graph)
    {
        List<Integer> edgeReachables=new ArrayList<>();
        int max=Collections.max(graph.keySet());
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
```