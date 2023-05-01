Download Link: https://assignmentchef.com/product/solved-cs211-project2-balanced-symbol-checker
<br>
<h1></h1>

For this lab, write a C program that will determine whether input is given with properly balanced symbols. We will often use symbols together to specify the beginning and ending of an item, such as the use of parentheses in a mathematic expression or the use of curly braces in a C, C++ or Java program. For this program, we will be checking the following symbol pairs:

<ul>

 <li>parentheses: ( )</li>

 <li>curly braces: { }</li>

 <li>square brackets: [ ]</li>

 <li>angle brackets: &lt; &gt;</li>

</ul>




This program will require the use of a stack implemented in a dynamic array. This dynamic array is to grow to a larger size when a push operation would be done to a full array causing an array overflow. For this program, your dynamic array MUST start with 2 positions in the array. When the array needs to grow, it size MUST grow by 2 additional positions each time (note the array to grow in size from 2 to 4 to 6 to 8 to 10 to …).




The <strong>push</strong> operation is now defined as follows:  if (the stack array if full)  grow the array

add the value to the stack array

increment the top-of-stack value




The <strong>grow</strong> operation is defined as follows:

Create a temporary pointer to the current stack array

Allocate a new dynamic array of the larger size and Have the stack array variable refer/point to the new dynamic array

Copy the existing values from the current stack array to the new dynamic array

Deallocate the current stack array

Update the maximum stack size variable

<h1>Input</h1>

The input for this program will come from standard input. Each line of input will be a single expression that is to be checked for balanced symbols. You may assume that each line of input is less than 300 characters long.  The program must loop to read in multiple lines of input.  If the input on the line contains only the letter q or Q, quit the program.




Since we have limited the length of the input and are trying to process one line of input at a time, the best way to read the input is the <strong>fgets()</strong> function in the &lt;stdio.h&gt; library.  Since we are reading from standard input, you are to use the value of <strong>stdin</strong> for the third parameter of <strong>fgets().</strong>  This causes fgets() to read input from the standard input.  <strong>You MUST use fgets() for this programming project to read in the input</strong>. See the base code to see how this is done.  If you are not familiar with the fgets() functions, do a Google search and read.  The <u>cplusplus.com</u> website has a <u>good reference page on</u> <u>fgets()</u>.







<h1>Stack Use Algorithm</h1>

To check for balance symbols in an expression, the expression is inspected from left to right after the entire line is read in.  The algorithm only cares about opening symbols, closing symbols and the end of the expression.  Any other input is ignored.  The stack must be empty at the start of the expression.

When an opening symbol is encountered, this symbol is pushed onto the stack. The opening symbols are: ( { [ and &lt;.

When a closing symbol is encountered, check the symbol at the top of the stack.

<ul>

 <li>If the symbol on the top of the stack is the corresponding opening symbol, pop the stack and continue.</li>

 <li>If the symbol on the top of the stack is NOT the corresponding opening symbol, the expression is NOT balanced and the wrong closing symbol was encountered. (Error #1)</li>

 <li>If the stack is empty, the expression is NOT balanced and there is a missing opening symbol. (Error #2)</li>

</ul>




When the end of the expression is encountered (i.e. the end of the input line), check to see if the stack is empty.

<ul>

 <li>If the stack is empty, then the expression was balanced.</li>

 <li>If the stack is NOT empty, the expression was not balanced and there is a missing closing symbol. (Error #3)</li>

</ul>

Since the only input we really care about are the 8 characters that form the 4 symbol pairs and determining when the “end of the expression” is reached, any other input on the line can be ignored.




<h1>Output</h1>

For each line of input, your program should display the input and specify whether the expression

<ul>

 <li>is balanced</li>

 <li>is unbalanced because it is <strong>expecting a different closing symbol</strong> (the wrong closing symbol is on the top of the stack) (Error #1)</li>

 <li>is unbalanced because it is <strong>missing an opening symbol</strong> (stack is empty when a closing symbol is encountered) (Error # 2)</li>

 <li>is unbalanced because it is <strong>missing a closing symbol</strong> (line ends while the stack is not empty)</li>

</ul>

(Error # 3)




For the unbalanced expression, print the “up arrow” character at the place where the unbalanced error occurred with a message. Only report the first error encountered in any line of input.  The following are some examples output showing the 4 possible outcomes:




( ( a a ) &lt; &gt; [ [ [ { [ x ] } ]]] &lt;&gt;)

Expression is balanced




( ( a a ) &lt; &gt; [ [ [ { [ x ] ]]] &lt;&gt;)

^ expecting }




( ( a a ) ) &lt; &gt; &gt; [ [ [ { [ x ] } ]]] &lt;&gt;)

^ missing &lt;




( ( a a ) &lt; &gt; [ [ [ { [ x ] } ]]]

^ missing )

<strong> </strong>

<h2>Use of C struct and C functions</h2>

When writing your code, you MUST place all of the data items needed for the stack in a C struct called “stack”. These data items must include the following (and may include others if needed).

<ul>

 <li>the pointer to the dynamic array that actually holds the stack</li>

 <li>the integer variable specifying the current size of the dynamic array</li>

 <li>the integer variable specifying the top of the stack</li>

</ul>




The instance of this struct MUST be declared locally in main(). It may NOT be global.  (Note: If you want it to be declared locally in some other function other than main(), that is also OK.)




<strong>In your program, you MUST write functions for</strong>:

<ul>

 <li>initializing the stack (typically named: init( ) ),</li>

 <li>checking if the stack is empty (typically named: is_empty( ) ),</li>

 <li>pushing/adding an element onto the stack (typically named: push( ) ),</li>

 <li>popping/removing an element off of the stack (typically named: pop( ) ),</li>

 <li>accessing/returning the top element on the stack (typically named: top( ) ), and</li>

 <li>clear the stack so that it is empty and ready to be used again (typically named: clear( ) ).</li>

</ul>




All of these functions MUST take <strong>as their first parameter</strong> a pointer to the struct that contains the instance of the stack that is being used. The only exception to this is that the initializing function may return a newly created instance and return a pointer to this instance.




<h1>Coding Style</h1>

Don’t forget to use good coding style when writing your program.  Good coding style makes your program easier to be read by other people as the compiler ignores these parts/differences in your code.  Elements of good code style include (but may not be limited to):

<ul>

 <li>Meaningful variable names</li>

 <li>Use of functions/methods</li>

 <li>Proper indentation</li>

 <li>Use of blank lines between code sections</li>

 <li>In-line comments</li>

 <li>Function/method header comments</li>

 <li>File header comments</li>

</ul>

The Code Review Checklist also hints at other elements of good coding style.

<h2>Command Line Argument: Debug Mode</h2>

Your program is to be able to take one optional command line argument, the -d flag. When this flag is given, your program is to run in “debug” mode. When in this mode, your program is to display a message whenever an item is pushed or popped from the stack.  This message must include the character being pushed or popped. Also, when the stack grows, you are to explicitly state the old and new size of the dynamic array for the stack as well as indicate the number of values copies from the current to the new dynamic array.

When the flag is not given, this debugging information should not be displayed. One simple way to set up a “debugging” mode is to use a “Boolean” variable which is set to true when debugging mode is turned on but false otherwise. This debugging mode variable can be set up as a global variable if desired.  Then using a simple if statement controls whether information should be output or not.

if ( debugMode == TRUE )  printf (” Debugging Information 
”);