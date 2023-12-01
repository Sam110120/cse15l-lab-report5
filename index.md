# Lab Report 5

## Part 1 - Debugging Scenario

**Student:** Hi, we just learned bash script a couple of days ago and I think it was very cool. In today's lab, I was trying to run the JUnit test in the bash script. The testing file contains 3 tests so I expected to see the JUnit run through three tests and pass all the test cases. However, when I used the bash script to run the JUnit tests it did not detect any test case I wrote. Can you please take a look and help me out?

* <img width="583" alt="image" src="https://github.com/Sam110120/cse15l-lab-report5/assets/71369089/e876d6aa-7ce8-4b61-812a-9e0c0c97beaf">

**TA:** Ah I see, so you want to test out your test case in your test file. The question is, how do you make sure that the JUnit knows which file you want to test out in your bash script? I suggest you modify the last line of your bash script.

**Student:** Oh I see what you mean, I have modified the bash script by putting the target java testing file to the JUnit test command. So without putting the target testing file, the JUnit will not know which file will be used. Now it detects all the test cases and runs through them successfully.

* <img width="615" alt="image" src="https://github.com/Sam110120/cse15l-lab-report5/assets/71369089/44dc7b82-dec5-40a8-a103-d23c669da305">

* <img width="652" alt="image" src="https://github.com/Sam110120/cse15l-lab-report5/assets/71369089/9d79bb93-d105-4150-9c75-2042e2e510bc">

However one of my cases(test2) failed, but I was not sure why it failed the test case. The method was supposed to reverse the input list but it turns out the elements did not change after I applied the method to the input list. Below are the screenshots of the test case and method implementation associated with it.

* <img width="258" alt="image" src="https://github.com/Sam110120/cse15l-lab-report5/assets/71369089/bae13b23-57f7-4df2-96b4-54c039cbe7a1">

* <img width="485" alt="image" src="https://github.com/Sam110120/cse15l-lab-report5/assets/71369089/49ce8f06-b1b4-4db4-acf5-2d2a48c3d108">

Can you give me some hints please?

**TA:** Yeah sure, so you are wondering why if your function is not working as intended. I suggest you try to print out the input list before and after the method and see if you notice anything.

**Student:** Ohhh the input list does not change after I use the method! Since the method will return the modified list, I have to update(reassign) to the input list. Otherwise, the input list will just stay the same. So I need to reassign the output of the method to the input list. I have fixed the bug and all the test cases are passed!

* <img width="266" alt="image" src="https://github.com/Sam110120/cse15l-lab-report5/assets/71369089/1f877ba9-a077-42b3-b043-afe56aa5fed5">

* <img width="360" alt="image" src="https://github.com/Sam110120/cse15l-lab-report5/assets/71369089/33d7502b-bd1a-49c8-aa31-47068fdd0c52">

Thank you so much!

**TA:** No problem!

**Summary for step 4:**

* The file & directory structure needed
  * The directory is **Cse15L_lab4** and inside of this directory it contains following files:
    * **testMac.sh**, **ListExamples.java**, **ArrayTests.java**, and a **lib** directory which contains the JUnit test file (**hamcrest-core-1.3.jar** and **junit-4.13.2.jar**)

* The contents of each file before fixing the bug:

* testMac.sh (it contains the JUnit test command):

```
set -e

javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore
```

  * ArrayTests.java (it contains the test cases for ListExamples.java but screenshot contains the bug case before fixing):

```

import static org.junit.Assert.*;

import java.beans.Transient;

import org.junit.*;

public class ArrayTests {
	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}

  @Test
  public void test1(){
    int[] input = {1,2,3,4,5,6};
    int[] output = {6,5,4,3,2,1};
    ArrayExamples.reverseInPlace(input);
    assertArrayEquals(output, input);
  }

  @Test 
  public void test2(){
    int[] input = {1,2,3,4};
    int[] output = {4,3,2,1};
    ArrayExamples.reversed(input);
    assertArrayEquals(output, input);
  }
}
```

  * ListExamples.java (it contains the method implementations):
```
public class ArrayExamples {

  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i += 1) {
      int temp = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = temp;
    }
  }

  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[arr.length - i - 1] = arr[i];
    }
    return newArray;
  }

  // Averages the numbers in the array (takes the mean), but leaves out the
  // lowest number when calculating. Returns 0 if there are no elements or just
  // 1 element in the array
  static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }
}
```

* The full command line (or lines) you ran to trigger the bug
	* for both bugs it was ```bash testMac.sh``` to trigger the bug.

* A description of what to edit to fix the bug
  * For fixing the first bug in bash script, I put the target java file(ArrayTests) at the end of ```java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore``` so that JUnit will know which java file to test for.
  * To fix the second bug I put the variable ```input = ```in front of ```ArrayExamples.reversed(input)```to hold the modified list from the method. So it would update the value of the list and match the expected list.

## Part 2 - Relection

Reflecting on the second half of this quarter's lab experience, I gained valuable insights into two specific areas: bash scripting and Vim. Prior to these labs, my understanding of bash scripting was quite limited. I learned the power and efficiency it brings to automating tasks in a Linux environment, which was both enlightening and immensely practical. This knowledge has opened up new possibilities for streamlining my workflow, especially in managing files and executing repetitive tasks. I was so surprised that I dont have to enter command line one by one in the terminal which saved so much time for me！

Similarly, my experience with Vim was transformative. Before this course, I viewed Vim as just another text editor like I have do download another platform like vscode, but I've since discovered its robust capabilities. The modal nature of Vim, with its various modes for editing, inserting, and navigating, was a novel concept for me. I've learned numerous shortcuts and commands that have significantly improved my efficiency in coding and text editing. This exploration of Vim was not just about learning a tool, but about adopting a more thoughtful and efficient approach to coding. I was able to access the file directly without actually open the file itself, and I was also able to made changes and save it. It's also very cool.

