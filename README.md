# COMPSCI4016_CourseWork_FUNPL
COMPSCI4016 Programming Languages
Programming Languages H
Coursework Assignment
In this assignment you will extend the Fun compiler, using the compiler generation tool ANTLR. The assignment itself 
consists of three stages (to be submitted altogether as one): syntactic analysis, contextual analysis, and code generation. 
The assignment contributes 20% of the assessment for the PL(H) course.
Assignment: extending Fun with a repeat-until loop and a switch statement
The assignment is to design and implement two extensions to Fun.
(A) The first is a repeat-until command, which is a new form of loop. 
(B) The second extension is a switch command, analogous to that of Java and C.
Each extension consists of three stages.
1. Syntactic analysis: the definition of the grammar to specify the syntax of the new language feature.
2. Contextual analysis: the definition of scope and type checking rules for the new feature, and the extension of 
the visitor to implement them.
3. Code generation: the definition of code templates for the new feature, and the extension of the visitor to 
implement code generation.
Set up a new project, called FunExtended, and start by importing or copying the files from your version of Fun, which 
was extended with multiple parameters from the warm-up exercise.
Maintain the same structure of directory as it was given to you.
Add your own name and the date to the header comment in any file you modify. 
Additionally, clearly highlight all your modifications in the code, using comments such as
“// EXTENSION … //END OF EXTENSION”.
Extension A: the repeat-until command
Note the following points about the syntax, typing rules and semantics of the switch command.
• The repeat-until command should contain any sequence of commands in its body.
• The guard of until should be any general expression.
Extension B: the switch command
Note the following points about the syntax, typing rules and semantics of the switch command.
• The expression being tested (i.e. the expression that appears after the switch keyword) can be any integer or 
boolean expression.
• Each guard (i.e. the value or values that appear after a case keyword) has one of three possible forms. (1) An 
integer literal. (2) A boolean literal. (3) An integer range, such as 2..4 as in the first example; this case is 
selected when the value of n is either 2, 3 or 4. Note that only literal values, not arbitrary expressions, are 
allowed in guards.
• All of the guards must have the same type as the expression being tested.
• All of the guards must be non-overlapping. This means that guards of forms (1) and (2) must all have different 
values, and the ranges in guards of form (3) must not overlap with other ranges or with guards of form (1).
• There can be any number of cases.
• There must be exactly one default case.
• The code for each case can be any sequence of commands.
• There is no fall-through, therefore no need for a break keyword. At the end of the sequence of commands 
associated with a particular case, execution jumps to the end of the switch-command. This is true even if the 
sequence of commands is empty. 
Assignment stage 1: syntactic analysis
Add a suitable grammar definition for the repeat-until and switch commands to Fun.g4. Remember to extend 
the lexicon as necessary. Make sure your grammar is general enough.
Write at least two test Fun programs containing repeat-until and at least two tests containing switch. Test your extended 
syntactic analyser by running the simplified driver program FunParse (not FunRun) with each of these test programs. 
You can also use the ANTLR visualisation tool to check the syntax trees.
Assignment stage 2: contextual analysis
Add implementations of the missing methods in the FunCheckerVisitor class, so that all the necessary type 
checking is done.
For the switch command, you need to implement a check that there are no repeated or overlapping guards.
Test your extended contextual analyser by running FunCheck with each of your test programs, and see whether it 
correctly performs type checks and other analysis (for switch, including no repeated or overlapping guards). Your test 
programs should include one that violates the commands’ rules. 
Assignment stage 3: code generation
Extend the Fun code generator.
Start by designing a code template for a repeat-until and a switch command. Note: Include your code template as a 
comment in FunEncoderVisitor.java. This should be in a separate part of the file (e.g., top of the corresponding 
method), not interspersed between other code. You will receive marks for a reasonable code template even if your code 
generator does not work as intended. Note that the code template does not mean the Java code of a visit method. It 
means a schematic outline of the code that will be generated, showing the structure of tests and jumps. The lecture slides 
show code templates for the if statement and the while statement, for reference.
After the code template, define the missing methods in the FunEncoderVisitor class. 
Test your extended contextual analyser and code generator by running FunRun with each of your test programs, and 
see whether it performs proper scope/type checks and generates correct object code. 
There are two ways to verify whether the compiler generates correct object code – use both!
1. Visually inspect the object code.
2. See what happens when the object code is interpreted. If the object code’s behaviour is unexpected, your 
compiler must be generating incorrect object code.
Submission
Follow the submission instructions below. These are mandatory. If you do not follow these instructions, marks will 
be removed.
• Upload a zipped directory on Moodle in the Submit your coursework here area. Use your GUID (your student 
number followed by the first letter of your surname) as the directory name for the submission. As an example, 
if your GUID was 2021234x, you would run the following command to create the zip archive: 
zip -r 2021234x.zip 2021234x/
• The zipped directory must: 
i) Contain a folder named FunExtended, which in turn contains all the files for your modified Fun compiler, 
including the files that you have not changed. We want to be able to compile your compiler without needing 
to change anything in your directory. In the tests directory inside FunExtended you can put your own
test programs.
Recall: you must keep the same structure of the directory as the one that was given to you on Moodle for 
Fun in Fun.zip.
ii) Include in your top-level directory, a report called StatusReport (max 4 pages) describing in detail 
what you have done in each of the three stages of the coursework. Your report should include a heading 
stating your full name and your student number and clear instructions on how to run the code.
Note: the report contributes to your final mark.
Help and support
Your lecturer and tutors will be in the lab to assist.
You may collaborate with other students to familiarize yourself with ANTLR and the Fun compiler. However, 
assignment stages 1–3 must be your own unaided work.
Marking Criteria
Your work will be marked primarily for correctness. However, marks may be deducted for code that is clumsy, hard to 
read, or very inefficient. Marks will also be deducted for a missing or misleading status report. Your total mark will be 
converted to a percentage and then to a band on the 22-point scale. The assessment scheme will be:
