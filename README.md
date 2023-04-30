Download Link: https://assignmentchef.com/product/solved-ensf594-principles-of-software-development-ii-lab-assignment-4
<br>
Application of Stack

Note:

You should use the Stack implementation. It’s up to you whether you want to use Array-based or linked list based. Don’t use predefined Stack available in Java. You can use class code after citing.

<h1>Q1. Brackets matching – The Delimiters on the Stack   (5 marks)</h1>




Write a java program that determines whether the given set of delimiters (in our case, it will be parenthesis such as <em>( and )</em> ) is validate or not.

Input:

Your program should read the input set of parenthesis from the user.

Output:

You would write on the console whether a given set of parenthesis is valid or not.




Sample Run:

Enter a String: ()

This is valid




Another run:

Enter a String: )(

This is invalid




Another run:

Enter a String: (())

This is valid




<strong>Note: For question 2 and question 3, you can assume that all the expressions contains only single digits number. There will not be any parenthesis in the expression. The operator will be +, -, * and /. </strong>

<h1>Q2. Convert from Infix to Postfix   (5 marks)</h1>

We write expression with an operator (+, -, * and /) places between the operands. This is called infix notation because operator is placed between the operands. In postfix notation, operator follows the two operands. For Example A + B becaosme AB+. Below table describe Infix expression to postfix expression.




<table width="480">

 <tbody>

  <tr>

   <td width="271"><strong>Infix </strong></td>

   <td width="208"><strong>Postfix </strong></td>

  </tr>

  <tr>

   <td width="271">A + B – C</td>

   <td width="208">AB+C-</td>

  </tr>

  <tr>

   <td width="271">A * B / C</td>

   <td width="208">AB*C/</td>

  </tr>

  <tr>

   <td width="271">A + B * C</td>

   <td width="208">AB*C+</td>

  </tr>

  <tr>

   <td width="271">A * B + C</td>

   <td width="208">ABC+*</td>

  </tr>

  <tr>

   <td width="271">A * B + C * D</td>

   <td width="208">AB*CD*+</td>

  </tr>

 </tbody>

</table>




Below table describe how we can convert an expression from infix to post.  Infix: A + B – C, Postfix: AB+C-

<table width="623">

 <tbody>

  <tr>

   <td width="175">Character Read from Infix Expression</td>

   <td width="175">Infix expression parsed so far</td>

   <td width="137">Postfix Expression</td>

   <td width="137">Comment</td>

  </tr>

  <tr>

   <td width="175">A</td>

   <td width="175">A</td>

   <td width="137">A</td>

   <td width="137"> </td>

  </tr>

  <tr>

   <td width="175">+</td>

   <td width="175">A+</td>

   <td width="137">A</td>

   <td width="137"> </td>

  </tr>

  <tr>

   <td width="175">B</td>

   <td width="175">A+B</td>

   <td width="137">AB</td>

   <td width="137"> </td>

  </tr>

  <tr>

   <td width="175">–</td>

   <td width="175">A+B-</td>

   <td width="137">AB+</td>

   <td width="137">When you see the -, you can copy the + to the postfix string</td>

  </tr>

  <tr>

   <td width="175">C</td>

   <td width="175">A+B-C</td>

   <td width="137">AB+C</td>

   <td width="137"> </td>

  </tr>

  <tr>

   <td width="175">End</td>

   <td width="175">A+B-C</td>

   <td width="137">AB+C-</td>

   <td width="137">When you reach at the end of the expression, you can copy the –</td>

  </tr>

 </tbody>

</table>




Now consider another example
















<table width="623">

 <tbody>

  <tr>

   <td width="175">Character Read from Infix Expression</td>

   <td width="175">Infix expression parsed so far</td>

   <td width="137">Postfix Expression</td>

   <td width="137">Comment</td>

  </tr>

  <tr>

   <td width="175">A</td>

   <td width="175">A</td>

   <td width="137">A</td>

   <td width="137"> </td>

  </tr>

  <tr>

   <td width="175">+</td>

   <td width="175">A+</td>

   <td width="137">A</td>

   <td width="137"> </td>

  </tr>

  <tr>

   <td width="175">B</td>

   <td width="175">A+B</td>

   <td width="137">AB</td>

   <td width="137"> </td>

  </tr>

  <tr>

   <td width="175">*</td>

   <td width="175">A+B*</td>

   <td width="137">AB</td>

   <td width="137">You cannot copy + because * has higher precedence</td>

  </tr>

  <tr>

   <td width="175">C</td>

   <td width="175">A+B*C</td>

   <td width="137">AB+C</td>

   <td width="137">When you see theC, you can copy the *</td>

  </tr>

  <tr>

   <td width="175"> </td>

   <td width="175">A+B*C </td>

   <td width="137">ABC*</td>

   <td width="137"> </td>

  </tr>

  <tr>

   <td width="175">End</td>

   <td width="175">A+B*C</td>

   <td width="137">ABC*+</td>

   <td width="137">When you see end of the expression,, you can copy the +</td>

  </tr>

 </tbody>

</table>




Below are the input to postfix transition rules:




<table width="623">

 <tbody>

  <tr>

   <td width="312"><strong>Item Read from Input </strong></td>

   <td width="312"><strong>Action (infix) </strong></td>

  </tr>

  <tr>

   <td width="312">Operand</td>

   <td width="312">Write it to output</td>

  </tr>

  <tr>

   <td width="312">Operator(opThis)</td>

   <td width="312">If stack is empty, push opThisOtherwise, while stack not empty, repeat:Pop an itemIf item is an operator(opTop) andIf opTop &lt; opThis, push opTopIf opTop &gt;= opThis, output opTopQuit loop if opTOP &lt; opThisPush opThis</td>

  </tr>

  <tr>

   <td width="312">No more items</td>

   <td width="312">While stack not empty, Pop item, output it</td>

  </tr>

 </tbody>

</table>




In the above table, &lt; and &gt;= symbols refers to the operator precedence. The opThis operator has just been read from the infix input, while opTop operator has just been popped off the stack




You can follow these transition rules in our first two table.

Write a java program that read an infix expression from the user (console), and convert that expression in the postfix expression.




Sample Run:

Enter infix: 2+3*4

Postfix is: 234*


<h1>Q3. Evaluating expression   (4 marks)</h1>




Below algorithm describe the evaluating postfix expression

<ul>

 <li>If item read from postfix expression is an operand, then push that item onto the stack</li>

 <li>If item read from postfix expression is an operator, pop the top two operands from the stack and apply the operator to them. Push the result.</li>

</ul>




When you are done, pop the stack to obtain the answer.




Sample Run:

Enter Postfix: 57


Evaluates to 12







Submit electronically via D2L:

<ol>

 <li>Your source code files. Your TA will run your program to verify that it works correctly. Make sure your Java program compiles and runs without issues.</li>

 <li>For Q1, the main file name should be Q1_LastName_FirstName.java. Same pattern will be for Q2 and Q3.</li>

</ol>

<strong> </strong>

Grading Rubric:

<strong> </strong>

<strong> </strong>

<table width="472">

 <tbody>

  <tr>

   <td width="472"><strong>Functionality</strong>: produces correct output:•        Produce correct output for Q1    (5 marks)•        Convert infix expression to postfix     ( 5 marks)•        Evaluate the expression      (4 marks)</td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<strong> </strong>

<strong>Reference: </strong>

<strong>Some of the contents of the assignment has been adapted from Data Structures and Algorithm in Java, 2<sup>nd</sup> Edition by Robert Lafore </strong>

<strong> </strong>

<strong>Other Source: </strong>

<strong>Following will be extra resources to read if you are interested.  </strong><a href="https://introcs.cs.princeton.edu/java/43stack/"><strong>https://introcs.cs.princeton.edu/java/43stack/</strong></a> <a href="https://eecs.wsu.edu/~nroy/courses/cpts122/labs/Infix2Postfix.pdf"><strong>https://eecs.wsu.edu/~nroy/courses/cpts122/labs/Infix2Postfix.pdf</strong></a>

<strong> </strong>