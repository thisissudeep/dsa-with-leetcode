    Given a number N, the task is to convert every digit of the number into words.
    Examples: 
    Input: N = 1234 
    Output: One Two Three Four 
    Explanation: 
    Every digit of the given number has been converted into its corresponding word.

    Input: N = 567 
    Output: Five Six Seven 

## Code:
- Solved using Recursion:
``` java
import java.util.*;
public class Main {
  private static String [] words={"zero","one","two","three","four","five","six","seven","eight","nine"};
  public static void numToWords(int num)
  {
    if(num==0) return;
    numToWords(num/10);
    System.out.print(words[num%10] +" ");
  }
  public static void main(String[] args) {
    Scanner sc=new Scanner(System.in);
    int num=sc.nextInt();
    numToWords(num);
  }
}
```
