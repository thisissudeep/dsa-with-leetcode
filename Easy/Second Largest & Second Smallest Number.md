You have been given an array ‘a’ of ‘n’ unique non-negative integers.

Find the second largest and second smallest element from the array.

Sample Input 1 :

4
3 4 5 2

Sample Output 1 :

4 3

Sample Input 2 :

5
4 5 3 6 7

Sample Output 2 :

6 4

## Code:

``` java
public class Solution {
          public static int findSecondLargest(int n,int[] a)
          {
              int largest=Integer.MIN_VALUE;
              int secondLargest=Integer.MIN_VALUE;
              for(int i=0;i<n;i++)
              {
                  if(a[i]>largest)
                  {
                      secondLargest=largest;
                      largest=a[i];
                  }
                  else if(a[i]>secondLargest && a[i]!=largest)
                  {
                      secondLargest=a[i];
                  }
              }
              return secondLargest;
          }
          public static int findSecondSmallest(int n,int[] a)
          {
              int smallest=Integer.MAX_VALUE;
              int secondSmallest=Integer.MAX_VALUE;
              for(int i=0;i<n;i++)
              {
                  if(a[i]<smallest)
                  {
                      secondSmallest=smallest;
                      smallest=a[i];
                  }
                  else if(a[i]<secondSmallest && a[i]!=smallest)
                  {
                      secondSmallest=a[i];
                  }
              }
              return secondSmallest;
          }
}
```
