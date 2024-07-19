### Reachability
React Developer Community is a community of React developers. It allows developers to reach
out to others and discuss various topics around JS programming. This community has been
modelled as a directed social network graph.
Find Reachability
JS newbie A wants to check if he can reach out to a React expert B using his network.
### Input Format :
total members in React Developer Community
memberId1
MemberId2..........................MemberIdN
Total possible edges
.............................
Follower
Following
### Output Format :
"0" OR "1"
### Sample Testcase :
4
2
5
7
9
4
2 9
7 2
7 9
9 5
### Start and end :
7 5
### Testcase Output :
1
### Code :
``` java
public boolean isReachable(Map<Integer,List<Integer>> graph,int source ,int destination)
    {
       int maxVertix=Collections.max(graph.keySet());
       boolean[] visited=new boolean[maxVertix+1];
       Queue<Integer> q=new LinkedList<>();
       q.add(source);
       visited[source]=true;
       while(!q.isEmpty())
       {
           int cur=q.poll();
           if(cur==destination) return true;
           for(int neighbor:graph.get(cur))
           {
               if(visited[neighbor]==false)
               {
                   visited[neighbor]=true;
                   q.add(neighbor);
               }
           }
           
       }
       return false;
    }
```