# Lab Report 5

## Part 1 - Debugging Scenario

**Student:** Hi, we have just learned bash script couple days ago and I think it was very cool. In today's lab, I was trying to run the JUnit test in bash script. The testing file contains 3 tests so I expected to see the JUnit run through three tests and pass all the test cases. However, when I use bash script to run the JUnit tests it did not detect any test case I wrote. Can you please take a look and help me out?

* <img width="583" alt="image" src="https://github.com/Sam110120/cse15l-lab-report5/assets/71369089/e876d6aa-7ce8-4b61-812a-9e0c0c97beaf">

**TA:** Ah I see, so you want to test out your test case in your test file. The question is, how do you make sure that the JUnit knows which file you want to test out in your bash script? I suggest you to modify the last line of your bash script.

**Student:** Oh I see what you mean, I have modified the bash script by putting the target java testing file to the JUnit test command. It run through all the test cases successfully.

* <img width="615" alt="image" src="https://github.com/Sam110120/cse15l-lab-report5/assets/71369089/44dc7b82-dec5-40a8-a103-d23c669da305">

However one of my cases(test2) failed, but I was not sure why it failed the test case it supposed to put the last value of an ArrayList. Below are the screenshot of the test case and method implementation asscociate with it.

* <img width="258" alt="image" src="https://github.com/Sam110120/cse15l-lab-report5/assets/71369089/bae13b23-57f7-4df2-96b4-54c039cbe7a1">

* <img width="485" alt="image" src="https://github.com/Sam110120/cse15l-lab-report5/assets/71369089/49ce8f06-b1b4-4db4-acf5-2d2a48c3d108">

Can you give me some hints please?

**TA:** It 

**Summary for step 4:**

* The file & directory structure needed
  * The directory is **Cse15L_lab4** and inside of this directory it contains following files:
    * **testMac.sh**, **ListExamples.java**, **ArrayTests.java**, and a **lib** directory which contains the JUnit test file (hamcrest-core-1.3.jar and junit-4.13.2.jar)

* The contents of each file before fixing the bug
  * testMac.sh:
    * <img width="585" alt="image" src="https://github.com/Sam110120/cse15l-lab-report5/assets/71369089/16b044d5-d5f9-47c4-8674-0ed000a3d143">
  * ArrayTests.java:
    * <img width="268" alt="image" src="https://github.com/Sam110120/cse15l-lab-report5/assets/71369089/c9d5433c-640f-40fa-82d5-bd21e384ab17">


 

* The full command line (or lines) you ran to trigger the bug

* A description of what to edit to fix the bug
  * For the first bug in bash script, I put the target java file(ArrayTests) at the end of ```java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore``` so that JUnit will know which java file to test for.
  * The second 

## Part 2 - Relection

Reflecting on the second half of this quarter's lab experience, I gained valuable insights into two specific areas: bash scripting and Vim. Prior to these labs, my understanding of bash scripting was quite limited. I learned the power and efficiency it brings to automating tasks in a Linux environment, which was both enlightening and immensely practical. This knowledge has opened up new possibilities for streamlining my workflow, especially in managing files and executing repetitive tasks. I was so surprised that I dont have to enter command line one by one in the terminal which saved so much time for me！

Similarly, my experience with Vim was transformative. Before this course, I viewed Vim as just another text editor like I have do download another platform like vscode, but I've since discovered its robust capabilities. The modal nature of Vim, with its various modes for editing, inserting, and navigating, was a novel concept for me. I've learned numerous shortcuts and commands that have significantly improved my efficiency in coding and text editing. This exploration of Vim was not just about learning a tool, but about adopting a more thoughtful and efficient approach to coding. I was able to access the file directly without actually open the file itself, and I was also able to made changes and save it. It's also very cool.
