Given an integer k and a queue of integers, The task is to reverse the order of the first k elements of the queue, leaving the other elements in the same relative order.

Only following standard operations are allowed on queue. 

    enqueue(x) : Add an item x to rear of queue
    dequeue() : Remove an item from front of queue
    size() : Returns number of elements in queue.
    front() : Finds front item.
## Code:
``` java
import java.util.Queue;
import java.util.LinkedList;
import java.util.List;
import java.util.ArrayList;
import java.util.*;
public class Main {
  public static void main(String[] args) {
    Scanner sc=new Scanner(System.in);
    int k=sc.nextInt();
    sc.nextLine();
    String[] input=sc.nextLine().split(" ");
    Queue<Integer> queue=new LinkedList<>();
    for(int i=0;i<input.length;i++) queue.add(Integer.parseInt(input[i]));
    List<Integer> reversed= reverseQueue(queue,k);
  	for(int element:reversed) System.out.print(element+" ");
  }
  
  public static List<Integer> reverseQueue(Queue<Integer> queue,int k)
  {
    List<Integer> reversed=new ArrayList<>();
    while(k!=0)  {reversed.add(queue.remove());k--;}
    Collections.reverse(reversed);
  	while(!queue.isEmpty())  reversed.add(queue.remove());
    return reversed;
  }
}
```
