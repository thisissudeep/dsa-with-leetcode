Given an array ‘arr’ of size ‘n’ find the largest element in the array.


Sample input 1:

6
4 7 8 6 7 6 

Sample output 1:

8

Constraints :

1 <= 'n' <= 10^5
1 <= 'arr[i]' <= 10^9

## Code:
- Optimal Solution:
``` java

public class Solution {

    static int largestElement(int[] arr, int n) {
        int largest=arr[0];
        for(int i=1;i<n;i++)
        {
            if(arr[i]>n) largest=arr[i];
        }
        return largest;
    }
}
```
