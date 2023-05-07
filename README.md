Download Link: https://assignmentchef.com/product/solved-max-scrabble-score
<br>
The board game Scrabble works by assigning points to wooden tiles arranged in cells on a board. It’s described here: Scrabble on Wikipedia.

For this project, you will write code that computes the Scrabble score for each line of text in a file and reports the line with the maximal Scrabble score and that score.

Learning Objectives

<ol>

 <li>Use inheritance to leverage the code provided in a superclass to perform a task (opening and reading in the lines of a text file).</li>

 <li>Writing code that conforms to a specification.</li>

 <li>Developing code that will work with existing code.</li>

 <li>Creating code that correctly implements an algorithm as specified.</li>

 <li>Making essential use of a data structure (array) in your code to implement an algorithm.</li>

 <li>Gaining further experience developing code incrementally: writing a small amount of code and then testing.</li>

 <li>Gain further experience writing modular code: writing methods that perform small tasks in service of the larger task.</li>

</ol>

Computing the Scrabble Score

The Scrabble score for a line of text is the sum of the scores for all of the individual characters in that line. The Scrabble score for a single character is computed as follows:

<ol>

 <li>For each character in the line:If the character is a letter, get the letter score. If it is not a letter, its score is zero. The case of the letter (upper/lower case) does not matter.</li>

 <li>If the position of the character (position is its index- the first character is position 0) is divisible by 4, the score is doubled.</li>

 <li>If the position of the character is divisible by 9, the score is tripled.</li>

 <li>If the position of the character is divisible by 4 and 9, the score is doubled.</li>

</ol>

This table lists the Scrabble letter scores:

A-1

B-3

C-3

D-2

E-1

F-4

G-2

H-4

I-1

J-8

K-5

L-1

M-3

N-1

O-1

P-3

Q-10

R-1

S-1

T-1

U-1

V-4

W-4

X-8

Y-4

Z-10

For example, given this line of text:

Dave, I am afraid.

The Scrabble score for that line would be: 38

Note that the first position of the input string is zero, which is divisible by 4 and 9, so the character score for the first letter, D, which is 2, is doubled.

Another example: this line:

now is the time

has a Scrabble score of 29.

Required Code Structure

This project utilizes three source files: A driver class called ScrabbleDriver, a class that opens the file and uses a Scanner to access the lines of text called TextFileAccessor, and the MaxScrabbleScore class- which you will write for this project.

The MaxScrabbleScore class must extend the TextFileAccessor class.

import java.util.Scanner;

import java.io.IOException;

public class ScrabbleDriver{

public static void main(String args[])

{

try{

Scanner s = new Scanner(System.in);

System.out.println(“Enter the file name:”);

String fileName = s.nextLine();

TextFileAccessor scrab = new MaxScrabbleScore();

scrab.openFile(fileName);

scrab.processFile();

System.out.println(scrab.getReportStr());

}

catch(IOException ioex)

{System.out.println(ioex);}

}

}

——————————————————————————————

import java.util.Scanner;

import java.io.IOException;

import java.io.FileReader;

public abstract class TextFileAccessor {

protected String fileName;

protected Scanner scan;




// throws a FileNotFoundException if can’t open file

public void openFile(String fn)throws IOException {

fileName = fn;

scan = new Scanner(new FileReader(fileName));

}

public void processFile() {

while (scan.hasNext()) {

processLine(scan.nextLine());

}

scan.close();

}




protected abstract void processLine(String line);




public abstract String getReportStr();

}

————————————————————————————————

public class MaxScrabbleScore extends TextFileAccessor {

//declare variables

public MaxScrabbleScore(){

//initialise variables in constructor

}

protected void processLine(String curLine) {

// process each character from the current line

//calculate sum of the scores for characters in that line

}

private int getScrabbleScore(char c, int pos){

//helper method to return the score for the character

}

public String getReportStr(){

//returns the score and the string that was entered

}

}//end class

Testing Your Code

Strongly Suggested:

<ol>

 <li>Don’t start this project by coding!</li>

 <li>Plan the algorithm you will develop for computing the scrabble score without worrying about the added complexity of Java syntax.</li>

 <li>Plan the steps of your algorithm- plan the helper methods you would write so that you are not doing all of the work in one big block.</li>

 <li>Coding: Make a project in jGrasp for this code. Work in the project to manage your code.</li>

 <li>Don’t focus on the inheritance and file IO at the start. Work on developing the scrabble score algorithm first. Use the debugger to see what your code is doing on one word.</li>

 <li>Start by doing simple tests: one word. When you can correctly compute one word’s score, move on to several words.</li>

 <li>Once you have tested the algorithm, add the file IO and read from the simplest text file.</li>

</ol>

<strong>PROJECT REQUIREMENTS</strong>

<ol>

 <li>Your MaxScrabbleScore class must properly extend the TextFileAccessor class. There must not be any unnecessary duplication of superclass code in MaxScrabbleScore.</li>

 <li>Your MaxScrabbleScore class must define one and only one constructor with an empty parameter list. The body of the constructor initializes any variables you declare as members of the class.</li>

 <li>Your MaxScrabbleScore class may not import any Java package or libraries.</li>

 <li>Your MaxScrabbleScore class must compile and run with the other two source files provided with this project: TextFileAccessor.java and ScrabbleDriver.java. You may not modify these files.</li>

 <li>Your MaxScrabbleScore class must produce the output in the same format as shown in the above section Testing Your Code. Points off if your values are correct but you don’t match the output as shown above.</li>

 <li>Your MaxScrabbleScore class must provide definitions for the processLine and getReportStr methods.</li>

 <li>Your solution must use an int array to store the letter scores given in the table to compute the individual letter scores in the lines of text.</li>

</ol>