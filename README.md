Download Link: https://assignmentchef.com/product/solved-cs3210-project-2-lisp
<br>
<ol>

 <li>N Factorial.  Takes a positive integer and returns its factorial.</li>

 <li>Search.  A function that receives an integer and a list.  The list will have a mix of integers and words, and may have nested lists.  The function returns a count of how many times the integer value is found.</li>

 <li>Divide by 3 counter.  A function that receives a list of numbers, possibly nested, and returns a count of how many are divisible by 3.  Uses a helper predicate function that returns true if its numeric argument is evenly divisible by 3.</li>

</ol>

Sample:   (divide-by-3  ’(3 15 78 100 4 12))  ==&gt;  4

<ol>

 <li>Has duplicates.  Given a list of integers (order unknown, not nested), report whether the list has any duplicates (true) or not (false).</li>

 <li>Remove negatives.  A function that receives a list of integers, not nested, and returns a list with all negative values removed.</li>

 <li>Temperature conversion.  Receives a list containing two pieces of data, a number and a letter, where the number is a value for a temperature, and the letter is either C or F (meaning centigrade or Fahrenheit) and returns the converted value (not in a list).  Three functions: convert, which calls F-to-C or C-to-F as needed, based on the letter given.  Assumption: the numeric value is a legitimate integer, holding a valid temperature.</li>

</ol>

Sample:   (convert  ’(100 C))  ==&gt;  212

<ol>

 <li>Count groups.  Given a list of words and / or numbers, not nested, count the number of groups (a group is two or more identical adjacent items).</li>

</ol>

Examples:

(count-clumps ‘(a b c))  ==&gt;  0

(count-clumps ‘(here kitty kitty))  ==&gt;  1

(count-clumps ‘(happy happy joy joy))  ==&gt;  2

(count-clumps ‘(yes no no 23 -101 yes yes yes)  ==&gt;  2

(count-clumps ‘(7 7 7 7 7 7))  ==&gt;  1

<ol>

 <li>Sort by recency.  Takes a word and a list of words, not nested.  If the word is not in the list, it is added at the beginning of the list.  If the word is in the list, its position is changed to be first in the list.  In both cases, the word most recently added is now at the front of the list.  Assumption: the incoming list has no duplicates.</li>

</ol>

Examples:

(make-recent cat ‘(a cat came in))  ==&gt;  (cat a came in)

(make-recent boy ‘(cat dog tree))  ==&gt;  (boy cat dog tree)

<ol>

 <li>Enforce upper limit.  A function that receives a number (an upper limit) and a list of words and / or numbers, possibly nested.  The function produces a new list in which all values originally over the limit are replaced by the limit.  Assumption: the limit will be a number.</li>

</ol>

Examples:

(enforce-limit (5 ‘(6 2 kitty 5 -16))  ==&gt;  (5 2 kitty 5 -16)

(enforce-limit (8 ‘(1 66 2 kitty -16))  ==&gt;  (1 8 2 kitty -16)

(enforce-limit ‘(33 (20 (35 9) 7 100 2 () 2)))  ==&gt;  (20 (33 9) 7 33 2 () 2)

<ol>

 <li>Twin.  Receives a list, not nested, and doubles all elements.</li>

</ol>

Example:

(twin ’(dog 2 cat))  ==&gt;  (dog dog 2 2 cat cat)

(twin ’(3 3 4))  ==&gt;  (3 3 3 3 4 4)

<ol>

 <li>Expression syntax checker.  A function which checks the syntax of a (possibly nested) list of expressions with numeric operands and binary infix operators (the operators are the actual words): plus, minus, times, dividedby.  The checker returns nil if any of the following conditions are found, true otherwise: wrong number of tokens in an expression (i.e., not three), operands not numeric, invalid operator.  Do not consider any other errors.  Your main function should call three helper functions which each check one condition.</li>

</ol>

Examples of top-level function:

(checker  ‘(7 plus 11))  ==&gt;  T                                <em>(true, valid)</em>

(checker  ‘(25 minus (17 times 12)))  ==&gt;  T       <em>(true, valid)</em>

(checker  ’(-4 plus))  ==&gt;  nil                                  <em>(wrong number of tokens)</em>

(checker  ’(-4 plus (cat minus dog)))  ==&gt;  nil     <em>(operands not numeric)</em>

(checker  ’((7 + 3) minus 12))  ==&gt;  nil                 <em>(invalid operator “+”)</em>

(checker  ’(-4 plus (cat minus dog)))  ==&gt;  nil     <em>(operands not numeric)</em>







<strong>Lisp language subset                                                                                                                   </strong>

Do  not use any other Lisp functions than those listed below.

defun, cond

car, cdr

cons, append, list

numberp, listp, atom

length

+, -, *, /, mod

=, equal

&lt;, &gt;, &lt;=, &gt;=

and, or, not, null

setf (only as shown above, for setting names for test data)

load (shown above)

<h1>Specifications</h1>

<ol>

 <li>This project is a series of individual problems, each of which is solved using one or more Lisp functions.</li>

 <li>Begin by completing all the practice functions handed out in class.</li>

 <li>Testing.

  <ol>

   <li>Develop all test cases first; these should be independent of the implementation language, and should not consider the specific logic that may be used.</li>

   <li>Your solutions must corrrectly handle all the examples given in these specifications, however, do not include those as part of your submitted test data.  You should include test cases that fall in the same categories as the examples, plus more categories.</li>

   <li>Test plans should be thorough: include all obvious test cases.  (Suggestion: if you have not had much experience writing thorough test plans, come in for help).  Each test case must be in a different category of possible incoming data and must have a different specific description.</li>

   <li>All helper functions have their own description and test plan.</li>

   <li>Do not write test cases for data beyond the problem definition.</li>

   <li>See the example test plan below.</li>

   <li>Solutions without a test plan and solutions that fail an accompanying test case are not considered completed, and that problem will receive no credit.  The same will be true for solutions that fail an obvious test case even if it was not included in the test plan (for example, empty and singleton lists).  Test plans missing basic test cases will lose points.</li>

  </ol></li>

 <li>Documentation.

  <ol>

   <li>For each solution (possibly composed of more than one function), document each function as follows: briefly describe what the function does, explain each parameter, include any assumptions / limitations (i.e., conditions your code is not expected to handle), and list your entire test plan.  Notice that all documentation is commented out, so that the entire file can be loaded and run as is.</li>

   <li>Problems without documenation are not considered completed.</li>

   <li>Documentation example, for one function:</li>

  </ol></li>

</ol>




;;  Your Name – CS 3210 – Spring 2019

;;  ============================

;;  adder function: adds all elements of a given list

;;  parameters:

;;       lst – a list of numbers

;;  assumptions:

;;       1. no nested lists

;;       2. all list elements are integers

;;       3. list sum will not exceed maxint




&lt; Lisp code here &gt;




;;  test plan for adder:

;;  category / description                 data                expected result

;;  —————————————————————————————————-

;;  empty list                                       ( )                           0

;;  list with 1 element                        (6)                          6

;;  list sums to zero &amp; duplicates   (-2 1 0 1)               0

&lt;etc.&gt;




<ol>

 <li>Development.

  <ol>

   <li>testing: check test plans against specifications before coding, test as you go, add new test cases as needed, do regression testing after any change</li>

   <li>documentation: document as you go, check documentation against specifications, update documentation to reflect changes during development</li>

   <li>establish and stick to a development schedule</li>

   <li>develop logic in English before writing in Lisp</li>

   <li>don’t make assumptions on the specifications</li>

  </ol></li>

 <li>Your function signatures and return types must match those given here in the examples.</li>

 <li>Use lowercase for any textual data.  “word” as used in the problem descriptions means a string of letters only (e.g., not “x123”, not “a.?z”).</li>

 <li>Some problems specify more than one function.  On other problems, you may choose to use additional helper functions  Think of small compact functions with associated helper functions for subtasks.</li>

 <li>Place each problem’s solution (of one or more functions, plus documentation, plus test plan) in a separate file.</li>

 <li>Do not make assumptions about incoming data types (list or atom, list contents) beyond those given in the problems. Always consider the empty and singleton lists (unless otherwise specified): what would a reasonable result be for these lists?  If needed, explain any of your decisions in your cover letter.</li>

 <li>One way to develop these programs is to have a working file (blah.lsp) containing your code, plus setf’s for the data test cases.  You can then just call the function several times without typing in all the data.  Example problem file:</li>

</ol>

&lt;documented code here, as above&gt;

(setf  data1  ’(2 17 0))

(setf  data2  ’( ))

Use (load “blah.lsp”) in many interpreters, or find a menu choice named <em>load</em>, which will bring in the program function(s), and set up names for your test cases.  Then, at the prompt, type:

(somefunc data1)

<ol>

 <li>You may consult general Lisp references as needed, but do not look up these specific problems.  There is a Moodle Lisp forum for discussions of the Lisp exercises handed out and done in class.  You may also ask questions about specifications of this project but do not post any code or ask questions that give part of a solution (come to office hours instead).  Work together sparingly if at all; strive to master the functional paradigm.</li>

 <li>Lisp quiz.  There will be a Lisp quiz on the project’s due date.  You will have a quick reference sheet to use for the quiz..</li>

 <li>Do not include any enhancements that go beyond the problems as specified here (although you may show these in the cover letter if you’d like me to see them).  Do not hand in incomplete or non-working solutions; you may hand in a subset of problems that are working correctly.</li>

 <li>Project submission is your claim that all test cases ran as specified, and that the work is your own (other than a bit of brainstrming with classmates and consultations with me).</li>

 <li>Additional cover letter notes and questions to answer.

  <ol>

   <li>Had you worked in Lisp or a Lisp dialect before?  If so, how much?</li>

   <li>What development environment did you use?  If it’s other than LispWorks, include a link to the software’s main page.</li>

   <li>How much time had you spent working on the practice exercises before starting this assignment?</li>

   <li>How comfortable were you with recursion before beginning Lisp?  And now?</li>

  </ol></li>

 <li>Submission.  Post on Moodle and bring a paper copy to class:

  <ol>

   <li>for each problem, source code file (one or more functions)</li>

   <li>one cover page for the whole assignment</li>

  </ol></li>

</ol>


