# BingoGame

Object-Oriented Programming
Software Workshop 1
Assignment 2:
Bingo!
Set by
Brian Mitchell and Jacqueline Chetty
Early Testing Deadline:
Tuesday16thNovember20212pmGMT
Final Submission Deadline:
Sunday21stNovember20215pmGMT
This assignment is worth
35 % (thirty-fivepercent)
of the overall course mark
You must use OpenJDK11


Overview
1 Introduction 1
2 Important points 1
3 Marking scheme 3
4 Coding tasks 3
5 Non-functional requirements 10
6 Assignment IntelliJ project 11
7 Testing your code 11
A General tips 12
B Rules 16
C Feedback reports 17
D Submission instructions 18


Table of contents
1 Introduction 1
2 Important points 1
3 Marking scheme 3
4 Coding tasks 3
4.1 Overall functional requirements . . . . . . . . . . . . . . . . . . . . . . . . . . 4
4.2 BingoRunner . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 6
4.3 Toolkit . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 6
4.4 Defaults . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 7
4.5 BingoController . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 7
4.6 BingoCard . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 8
5 Non-functional requirements 10
5.1 Code requirements . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 10
5.2 Submission requirements . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 10
6 Assignment IntelliJ project 11
6.1 Obtaining the assignment project . . . . . . . . . . . . . . . . . . . . . . . . . . 11
6.2 Structure of the assignment project . . . . . . . . . . . . . . . . . . . . . . . . . 11
6.3 Loading the assignment project . . . . . . . . . . . . . . . . . . . . . . . . . . . 11
7 Testing your code 11
A General tips 12
A.1 Before you begin coding . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 12
A.2 While you are coding . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 15
B Rules 16
C Feedback reports 17
D Submission instructions 18
D.1 Before you submit . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 18
D.2 How to submit . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 19
D.3 Missing the deadline . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 19
D.4 Early test deadline . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 20
D.5 Extensions for welfare reasons . . . . . . . . . . . . . . . . . . . . . . . . . . . 20
D.6 Assignment cut-off dates . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 20
List of figures
1 Setting the run configuration . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 13
2 Viewing differences between output . . . . . . . . . . . . . . . . . . . . . . . . . . . . 14
i
2 Important points



1 Introduction
You must complete a menu-driven text-based limited implementation of a
bingo game. In real life, bingo1 is a competitive game of chance where numbers
are repeatedly drawn in a true random sequence from a pre-determined set
by a person, known as a ‘caller’, or by a machine. Fresh numbers are drawn 5
until the first player to realise they have matched a winning pattern on their
bingo card announces this win aloud, typically shouting ‘house’ or ‘bingo.’ If
multiple players complete a winning pattern simultaneously, the winner is the
first to shout out. A bingo card, also known as a ‘ticket,’ is a grid of (mostly) non-
consecutive numbers. The actual configuration of bingo cards varies between 10
different versions of bingo games, so the configuration of cards used in this
assignment might differ from cards you have seen before.
To keep the size of the assignment manageable and so it can be auto-marked
reliably, you will not be implementing a full bingo game — in particular there
will be no randomisation of numbers, definitely no shouting out, and no prizes 15
for winning, although there are assignment marks to be ‘won’.
A complete and correct assignment will be able to:
1. set the dimensions of the bingo cards (rows by columns);
2. set the numbers contained on every bingo card in the game;
3. process sequences of numbers to be ‘called’; 20
4. mark matched numbers on all bingo cards currently in use;
5. test whether a bingo card is a fullhouse winner.
Descriptions of the overall requirements are given in §4 Coding tasks and
§5.1 Code requirements but specifics of these requirements are generally left to
‘TODO’ comments in the skeleton code (use IntelliJ’s TODO tab) plus analysing 25
differences between your version’s output against a set of ExpectedOutput files
provided in the assignment pack.


2 Important points
Starting your assignment by typing code will go wrong and waste a lot of time.
We recommend the following approach: 30
1. read this document quickly to see the big picture;
2. load the skeleton code into IntelliJ and use these plugins:
Call Graph (Chentai Kao) to visualise which methods call each other,
SequenceDiagram (VanStudio) for a different visualisation of methods
calling each other, 35
1 https://en.wikipedia.org/wiki/Bingo_(British_version)
↖Contents ↖Figures ↘Tips ↘Rules ↘Submission 1
2 Important points
UMLGenerator (Alessandro Caldonazzi) to visualise class relationships;
3. study those diagrams even though they are of incomplete code and think
what extra connections and sequences your completed code will probably
need based on the assignment requirements;
4. study and understand the names of methods and constants and decide 40
when and how the author intended them to be used;
5. analyse the relationship between the provided input files and their cor-
responding expected output as this helps you decide and design the steps
needed to convert input to output;
6. study IntelliJ’s TODO tab and relate the list to the assignment requirements; 45
7. re-read this assignment document in more detail for the requirements and
relate the information to the TODO list, the expected outputs (from their
respective inputs), and the diagrams;
8. put multiple designs on paper and consider which parts of which designs
are more (or less) suitable — be creative here and consider attempting 50
tasks ‘backwards’ or from an opposing perspective;
9. transform parts of your design into Java code, probably starting with
something from the final stages (for example printing some calculated
output) and working forwards (for example towards the raw inputs needed
to produce that calculated output); 55
10. use an end-to-end approach and make something work from beginning to
end for a simple case before making your code more flexible, more robust,
more efficient, or more elegant;
11. re-test your code after every two or three lines you write or change: baby
steps are fastest overall. 60
But first of all please take a moment to remind yourself of the rules §B Rules and
§D Submission instructions as well as the School’s and the University’s require-
ments for good academic practice. In particular:
1. you are encouraged to discuss the design of your program but you must
not share actual program code otherwise you risk plagiarism charges; 65
2. you are expected to work out for yourself the details of what your code
must do from analysing this document, the skeleton code, and especially
any ExpectedOutput files we give you;
3. should there be any apparent contradictions between this document and
either the skeleton code or ExpectedOutput, then specifications in the 70
skeleton code and output in the ExpectedOutput take precedence;
4. your code must compile as submitted otherwise you will score zero, no
matter how trivial a change is needed to make it compile;
5. your code must run on our system — whether it runs on yours does not
count. 75
↖Contents ↖Figures ↘Tips ↘Rules ↘Submission 2
4 Coding tasks
3 Marking scheme
Question Description Marks
1 Toolkit 12
2 BingoRunner 8
3 BingoCard 40
4 BingoController 40
Total 100
The marks listed are for submissions which correctly do everything required
and which produce output exactly matching the expected output. It is not
feasible to specify the exact break-down of marks within each item in the table 80
and we keep some of the tests secret until after the deadline to hamper attempts
to game the system.
Generally speaking, if your submissions meets all the requirements in
§4 Coding tasks and §5.1 Code requirements in the must and must not lists, then it
will probably obtain a reasonable pass mark — deductions for late penalties and 85
rule-breaking notwithstanding. To obtain a higher mark, your submission must
also meet the requirements listed under should and should not.
Adding functionality not specified in the assignment can lose you marks
— especially if it prints anything not required by this assignment — and might
be interpreted as an attempt to cheat if it looks like you used code originally 90
written for a different program.
4 Coding tasks
This section details the coding tasks. You do not have to attempt the tasks in
the order listed. Nor is it necessary to finish one task before starting another.
Cycling between tasks is expected and indeed encouraged. 95
Each subsection below says what a particular part of the code must or must
not or should or should not do. The difference matters. Functionality defined
by must (not) are core requirements: the minimum a client paying you for
this software would accept. Successfully meeting only these requirements will
probably limit you to a reasonable overall mark, penalties notwithstanding. 100
Higher marks can be unlocked by fulfilling the lists of should (not).
↖Contents ↖Figures ↘Tips ↘Rules ↘Submission 3
4 Coding tasks
Breaking requirements marked with a dagger†could result in a zero score
for the entire assignment. Breaking any requirement marked with a double
dagger‡ will definitely result in a zero score for the entire assignment.
4.1 Overall functional requirements 105
Additional to the requirements below, if your program is a mixture of ‘advanced’
code with basic bits that are badly programmed, we reserve the right to ques-
tion you on the ‘advanced’ parts and deduct marks — possibly all of them — if
we are not satisfied by your ability to explain them. This is to discourage you
from just copying or adapting code simply for the sake of scoring marks: it is 110
far, far more important to your academic development that you understand
what you are doing, even if your code is currently clumsy. If you do not learn
to understand programming at this stage, you will struggle even more with
subsequent modules.
Overall, your program must: 115
1. †only ever use one Scanner to read from the keyboard;2
2. follow the requirements (positive and negative) set out in this document;
3. account for any official changes to the assignment after the assignment
has been released.
Overall, your program must NOT: 120
1. ‡ import any other libraries apart from the ones that are allowed;
2. ‡ change any signatures of classes, class fields, or methods;
3. ‡ remove any required methods;
4. ‡ remove any classes;
5. ‡ add any new classes; 125
6. ‡ add any new methods;
7. †crash when given well-formed correct input;
8. †print any extra output beyond what is officially specified;
9. †add any extra functionality beyond what is officially specified;
10. †create any new Scanners. 130
Overall, your program should:
1. †only import items that are explicitly included in the skeleton;
2. †work correctly if the content of items in Defaults.java are changed;
3. exhibit consistent and predictable behaviour;
4. tolerate some mildly inappropriate input such as extraneous white space 135
or an int outside the required range;
2 The one to use is provided in the skeleton code.
↖Contents ↖Figures ↘Tips ↘Rules ↘Submission 4
4.1 Overall functional requirements 4 Coding tasks
5. be efficient in terms of execution speed3 mainly by not performing un-
necessary steps or calculations, though this is less important than the
program working correctly.
With respect to Item 1, a definitive list of allowed imports will be maintained 140
on the Canvas assignment page. The only permitted way to seek adjustments
to this list is to email the shared mailbox for the course with a compelling
justification for your request. Emailing someone directly or asking them in
person is not allowed because there are serious implications to the viability
of the assignment if import restrictions are changed, hence these must be 145
considered by multiple people involved with different aspects of the assignment.
Please expect in advance that your request is likely to be denied.
Overall, your program should NOT:
1. ‡ crash when given badly formatted input of the correct type, such as
multiple spaces between ints when there should be only a single space; 150
2. ‡ crash if input is of the correct type but inappropriate content, such as an
int out of range or a String containing leading or trailing white space.
Exclamation-circle We will test all your classes individually and then substitute them in
some, probably most, tests with our own versions. This is to try to
avoid penalising you multiple times for the same error. But it means
your code must work within the boundaries set by the assignment
and not have any additional, unwarranted functionality. This also
means you absolutely must not add or remove any methods or class
fields to these classes, nor modify the signatures of any provided
methods and fields. If your program cannot function without all but
one of the classes substituted at any one time, then you will probably
score zero overall.
3 We test this by limiting the amount of time your code program is allowed to run for.
↖Contents ↖Figures ↘Tips ↘Rules ↘Submission 5
