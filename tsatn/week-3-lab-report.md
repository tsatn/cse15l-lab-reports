# CSE 15L Lab 2 

Teresa Tian,  A16878664

# Part One (Week 2)
## Code for SearchEngine.java

```
    import java.io.IOException;
    import java.net.URI;
    import java.util.*;

    class Handler implements URLHandler {
        List<String> strList = new ArrayList<String>();
        public String handleRequest(URI url) {
            if (url.getPath().contains("/")) {
                if (url.getPath().contains("add")) {
                    String[] parameters = url.getQuery().split("=");
                    if (parameters[0].contains("s")) {
                        if (parameters[1].contains("anewstringtoadd")) {
                            strList = new ArrayList<String>();
                            return String.format("%s", strList);
                        } else {
                            strList.add(parameters[1]);
                            return String.format("%s", strList);
                        }
                    } else {
                        return "404 Not Found!";
                    }
                } else if (url.getPath().contains("search")) {
                    String[] parameters = url.getQuery().split("=");
                    List<String> found = new ArrayList<String>();

                    if (parameters[0].contains("s")) {

                        for (String str : strList) {
                            if (str.contains(parameters[1])) {
                                found.add(str);
                            }
                        }
                    }
                    return String.format("%s", found);
                } else {
                    return String.format("%s", strList);
                }
            }
            return "404 Not Found!";
        }
    }

        class NumberServer {
            public static void main(String[] args) throws IOException {
                if(args.length == 0){
                    System.out.println("Missing port number! Try any number between 1024 to 49151");
                    return;
                }

                int port = Integer.parseInt(args[0]);

                Server.start(port, new Handler());
            }
        }
```

## Terminal commands

<img width="859" alt="Screen Shot 2022-10-14 at 10 41 51 PM" src="https://user-images.githubusercontent.com/114328188/195971083-5209f055-9081-4dd0-be03-7ccdb7954bf4.png">

> After having these code in the SearchEngine.java file, open a new terminal and execute the two commands above to compile and run the code. 
> This block of code determines that the number of the server. The random number 4020 that I typed in the terminal commands will later appear in my web server's path.
```
        class NumberServer {
            public static void main(String[] args) throws IOException {
                if(args.length == 0){
                    System.out.println("Missing port number! Try any number between 1024 to 49151");
                    return;
                }

                int port = Integer.parseInt(args[0]);

                Server.start(port, new Handler());
            }
        }
```
> After seeing the message that the server has started, click on the link in the terminal. Once you see the website below, it means that you have successfully implemented a web server, which tracks the list of strings. 

> The code in the file SearchEngine.java shown above would support you to edit the path and add strings to an empty list.

<img width="789" alt="Screen Shot 2022-10-14 at 10 42 27 PM" src="https://user-images.githubusercontent.com/114328188/195971085-ba8cc505-5eef-4b56-ab6a-9593edc26678.png">

> type the querie **/add?s=pineapple** in the path to add a new string "pineapple" to the empty list.

> This block of code below supports this function.

```                
} else {
    strList.add(parameters[1]);
    return String.format("%s", strList);
}                        
```

<img width="788" alt="Screen Shot 2022-10-17 at 7 03 25 AM" src="https://user-images.githubusercontent.com/114328188/196198627-1e82619f-1988-446d-8e13-6936d71f8724.png">

> Type in the command in the same style to add more strings to the list.

<img width="789" alt="Screen Shot 2022-10-17 at 7 03 43 AM" src="https://user-images.githubusercontent.com/114328188/196198655-0d345582-39df-4cb1-8e8f-7c8fda914a79.png">

> the command **/add?s=anewstringtoadd** empties the current string from view.

<img width="787" alt="Screen Shot 2022-10-17 at 7 03 55 AM" src="https://user-images.githubusercontent.com/114328188/196198689-0b995d8c-117b-430f-b735-202a20557284.png">

> the command **/search?s=app** allows you to search for strings that contains "app" in the stored memory. The returned string will be "pineapple" in this example.

> This block of code below supports this function.

```
} else if (url.getPath().contains("search")) {
    String[] parameters = url.getQuery().split("=");
    List<String> found = new ArrayList<String>();

    if (parameters[0].contains("s")) {

        for (String str : strList) {
            if (str.contains(parameters[1])) {
                found.add(str);
            }
        }
    }
    return String.format("%s", found);
} 
```  

<img width="894" alt="Screen Shot 2022-10-14 at 10 58 43 PM" src="https://user-images.githubusercontent.com/114328188/195971528-db6c27c3-c9cd-4672-ba88-ede7e7d45b91.png">

---

# Part Two (Week 3)
## Bugs and Symptoms

**Bug 1 (ArrayExamples.java)**

1) The failure-inducing input (the code of the test)
> In the file ArrayExamples.java, there exist bugs in the method called reverseInPlace in the ArrayExamples class.
> The test that fails under this method, named testManyNums(), is shown below: 

```
@Test 
  public void testManyNums() {
    int[] input2 = {0, 3, 4, 7, 2};
    assertArrayEquals(new int[]{2, 7, 4, 3, 0}, ArrayExamples.reversed(input2));
  }
```

> When the program runs, any similar tests wishing for transforming an array of multiple inputs will fail due to the existence of the bug.

2) The symptom (the failing test output)

>Terminal output from running the code.

<img width="1243" alt="Screen Shot 2022-10-15 at 8 28 53 PM" src="https://user-images.githubusercontent.com/114328188/196016588-fee790b9-5cc3-4350-bcf8-e98713af8bee.png">

3) The bug (the code fix needed)

>Buggy code of the method reverseInPlace that causes the test to fail

```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

>code fix: fixed method, which uses a variable to store the integer value at the front index, switches the back index value to the front, then updates the the back index as the old front value. 

```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length / 2; i += 1) {
      int tempV = arr[i];
      arr[i] = arr[arr.length - i - 1]; //assigns the back v to the front 
      arr[arr.length - i - 1] = tempV; //assigns the front value to the back
    }
  }
 ```
 
4) The connection between the symptom and the bug. Why does the bug cause that particular symptom for that particular input?

> Observing the error output message from the terminal, we can see that the test does not pass since values are not being swapped. 

> There are two bugs causing the program to fail on this test: 

>  The first one is that the for loop **for(int i = 0; i < arr.length; i += 1) {** loops through the entire array when it should only loop through half of the array, changing the values from the first half in the front to the back. Looping through the entire array from the first index to the last will be done switiching all of the values when it is half way through the array and switching them all back to the original positions.

>  The second one is at the line **arr[i] = arr[arr.length - i - 1]** where it only assigns the last value of the array to the front index, and does not have code responsible for putting the front value to the back of the array.

> Due to these bugs in the code, causing the program not being able to run correctly and switch the values from the front to back, the program has the first value to be 0 instead of 2, meaning that it fails to switch the front values with the back values.
---
**Bug 2 (ListExamples.java)**

1) The failure-inducing input (the code of the test)
> To test the code in the ListExamples.java, I wrote the test below in the file ListTests.java
```
 @Test
    public void testFilter() {
        List<String> arrIn = new ArrayList<>();
        List<String> expectedArr = new ArrayList<>();
        StringChecker sc = new StringCheck();
        arrIn.add("hi");
        arrIn.add("two");
        arrIn.add("bye");
        arrIn.add("pizzahut");
        arrIn.add("communication");
        expectedArr.add("hi");
        expectedArr.add("two");
        expectedArr.add("bye");
        assertEquals(expectedArr, ListExamples.filter(arrIn, sc));
    }
```

> when the program runs, we are expecting it to take an input list and return a new list, which contains all the elements checked and returned true by the StringChecker. the order of the elements in the new array should be the same as the old.

2) The symptom (the failing test output)

<img width="963" alt="Screen Shot 2022-10-17 at 6 12 53 AM" src="https://user-images.githubusercontent.com/114328188/196186306-d7dab2f7-faa6-402b-b1eb-1cbf32074e6b.png">

3) The bug (the code fix needed)

>Buggy code that causes the test to fail

```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
  }
```

>code fix: 

```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { 
  boolean checkString(String s); 
}

class StringCheck implements StringChecker {
  public boolean checkString(String s) {
    if (s.length() < 5) {
      return true;
    } else {
      return false;
    }
  }
}
```
> In order to fix the buggy code, we added a class named StringCheck which implements the StringChecker interface.

4) The connection between the symptom and the bug. Why does the bug cause that particular symptom for that particular input?
> the terminal output when running the program shows the message that it could not find the class ListTests. 
> This is caused by the bug that the code did not implements the interface called StringChecker, therefore, we would need to create a new class that implements this interface.
> there is a bug in the filter method, the problem is that the strings being added are only added to index 0.
> the is also a bug in the merge method, the problem is that if list2 is longer than list1, the program only increments index1 of the first list and not the second.
