## OA 1

https://aonecode.com/amazon-online-assessment-debugging-questions#cp2

You are required to fiix all the logical error in the given code. You can click *Compile & Run* anytime to check the compilation/execution status of the program. You can use *System.out.print()* to debug your code. The submitted code should be logically/syntactically correct and pass all testcases. Do not write the *main()* function as it is not required.

**Code Approach:** For this questions, you will need to complete the code as in given implementation. We **do not** expect you to modify the approach.



### compareProduct

The function/method ***compareProduct*** accepts on argument: *num*, an integer representing the number.

The function/method returns a Boolean value "true" if the product of digits at the even and odd places of a number are equal. Otherwise it returns "false".

The code compiles successfully but fails to return the desired result for some test cases because of an incorrect implementation of the function/method **compareProduct**. Your task is to fix the code so that it passes all the test cases.



```java
class Solution
{
  boolean compareProduct(int num)
  {
    if (num < 10)
      return false; 
    int oddProdValue = 1, evenProdValue = 1;
    
    while (num > 0)
    {
      int digit = num / 10;
      oddProdValue *= digit;
      num = num / 10;
      if (num == 0)
        break;
      digit = num / 10;
      evenProdValue *= digit;
      num = num / 10;
    }
    if (evenProdValue == oddProdValue)
      return true;
    return false;
  }
}
```



- Replace `int digit = num / 10;` by `int digit = num % 10;` 



### countRotations

The function/method ***countRotations*** accepts two arguments: *size*, an integer representing the size of the input list; *list*, representing the list of integers.

The given sorted list of distinct integers is rotated clockwise k times. The function returns an integer representing the value k by which the list is rotated.

The function/method uses another function ***countRotationsUtill*** which accepts three arguments - *list*, a sorted list of distinct integers; *low*, an integer representing the first value of the list and *high*, an integer representing the last value of the list. The function calculates the value k and returns it to function ***countRotations***.

```java
class Rotation
{
  int countRotationsUntil(int list[], int low, int high)
  {
    if (high < low)
      return 0;
    if (high == low)
      return low;
    
    int mid = low + (high - low)/2;
    
    if (mid < high && list[mid+1] < list[mid])
      return (mid + 1);
    
    if (mid > low && list[mid] < list[mid - 1])
      return mid - 1;
    
    if (list[high] > list[mid])
      return countRotationsUntil(list, low, mid);
    
    return countRotationsUntil(list, mid, high);
  }
  
  int countRotations(int size, int list[])
  {
    int res = countRotationsUntil(list, 0, size-1);
    return res;
  }
}
```

- Replace `return mid - 1;` by `return mid;` 



### Calculate Sum Of Numbers In String

The following function returns a positive integer representing the sum of numbers in the inputString.

```java
public class Solution {
    public int calculateSumOfNumbersInString(String inputString) {
        String temp = "";
        int sum = 0;
        for(int i = 0; i < inputString.length(); i++) {
            char ch = inputString.charAt(i);
            if(Character.isDigit(ch))
                temp += ch;
            else
                sum += Integer.parseInt(temp);
            temp = "0";
        }
        return sum + Integer.parseInt(temp);
    }
}
```



### Check Pair Sum Exists

The following function returns a boolean value representing if there is a pair with given sum exists in the array.

```java
public class Solution {
    public boolean checkPairSumExists(int rows, int cols, int[][] arr, int sum) {
        Set<Integer> set = new HashSet<Integer>();
        for(int i = 0; i < rows; i++) {
            for(int j = 0; j < cols; j++) {
                if(set.contains(sum - arr[i][j])) {
                    return true;
                } else {
                    set.add(sum);
                }
            }
        }
        return false;
    }
}
```



### Remove Consecutive Vowels

The following function returns a string value representing the string left after removing consecutive vowels from the string.

```java
public class Solution {
    boolean is_vowel(char ch) {
        return (ch == 'a') || (ch == 'e') ||
                (ch == 'i') || (ch == 'o') ||
                (ch == 'u');
    }

    public String removeConsecutiveVowels(String str) {
        String str1 = "";
        str1 = str1+str.charAt(0);
        for(int i = 1; i < str.length(); i++)
            if((!is_vowel(str.charAt(i - 1))) &&
                    (!is_vowel(str.charAt(i)))) {
                char ch = str.charAt(i);
                str1 = str1 + ch;
            }
        return str1;
    }

}
```



### Reverse Alphabet Chars Only

The following function returns a string representing the reversed string in such a way that the position fo the special chars are not affected. 

```java
public class Solution {
    public String reverseAlphabetCharsOnly(String inputString) {
        char[] inputChar = inputString.toCharArray();
        int right = inputString.length() - 1;
        int left = 0;
        while(left < right) {
            if(!Character.isAlphabetic(inputChar[left]))
                left++;
            else if(!Character.isAlphabetic(inputChar[right]))
                right--;
            else {
                char temp = inputChar[left];
                inputChar[left] = inputChar[right];
                inputChar[right] = temp;
            }
            left++;
            right--;
        }
        return new String(inputChar);
    }
}
```



### Count Triplet Sum Permutations

The following function countTripletSumPermutations returns an integer representing the number of triplets from the list whose product is equal to the given tripletSum. 

```java
public class Solution {
    public int countTripletSumPermutations(int size, int[] arr, int tripletSum)
    {
        int count = 0;
        for(int i = 0; i < size - 2; i++)
        {
            if(tripletSum % arr[i] == 0)
            {
                for(int j = 0; j < size - 1; j++)
                {
                    if(tripletSum % (arr[i] * arr[j]) == 0)
                    {
                        int value = tripletSum / (arr[i] * arr[j]);
                        for(int k = j + 1; k < size; k++)
                            if(arr[k] == value)
                                count++;
                    }
                }
            }

        }
        return count;
    }
}
```

