# Lab Report 5 Week 10
 ## *Commonmark-spec Tests* 
 ----
 For this lab report, choose any two tests from the 652 commonmark-spec tests where your implementation (or a representative implementation from your group) had different answers than the implementation we provided for lab 9.

--------

## How I found the tests with different results:
To find the different results I used the command: `diff`.

Before doing so, I generated output from each implementation using the bash script and put the output into a results file using output redirection. I called this `results.txt`

To output the results from of running the bash script I used the command: `bash script.sh > results.txt`

Then to compare the different files I used the command:
`diff CSE15L-RoseateSpoonbill/results.txt markdown-parse/results.txt > diff.txt `
This outputs the differences between the two files to a file called `diff.txt`.

## Describe which implementation is correct:

**Test 1:**
------
```
211c211
< []
---
> [url]
```
This means that on line 211 of the results.txt in the CSE15L-RoseateSpoonbill directory, the line contained `[]`, while on line 211 of the markdown-parse/results.txt directory, the line contained `[url]`.  If we look at line 211, in those files, that’s the test output for the file 194.md. 
 

The contents of `file 194.md` are:
```
[Foo*bar\]]:my_(url) 'title (with parens)'

[Foo*bar\]]
```
I believe my or RoseateSpoonbill's implementation is correct in this case. The expected output from this file is `[]`, as there are no valid links in the file. The RoseateSpoonbill's implementation outputed `[]`, however, the markdown-parse implementation outputed `[url].

**The Bug:**
The markdown-parse implementation code does not check if the parenthesis holding a link is right after the closed bracket. In this case, there is is text between the closed bracket and open parenthesis. This makes it not a valid link. This bug can be fixed by checking for whether the next character after a closed bracket holding the title of the link is right next to the open parenthesis holding the link domain. 


**Test 2:**
------
```
871c871
< []
---
> [<b]
```
This means that on line 871 of the results.txt in the CSE15L-RoseateSpoonbill directory, the line contained `[]`, while on line 871 of the markdown-parse/results.txt directory, the line contained `[<b]`.  If we look at line 871, in those files, that’s the test output for the file 491.md. 
 

The contents of `file 491.md` are:
```
[a](<b)c>)
```
I believe markdown-parse's implementation is correct in this case. The expected output from this file is `[<b]`, as there is a valid link in the file. The markdown-parse's implementation outputed `[<b]`, however, my RoseateSpoonbill implementation outputed `[]`.

**The Bug:**
My implementation code has a bug where it looks explicity for a exclaimation point. It incorrected looks for if there is an exclaimaiton point before the first open bracket. If there is no exclaimation point then the link is not added. To fix this bug all I need to do is change the code from looking for an exclaimation point before the the open bracket, to looking for whether there is not an exclaimation point. This would be a simple code change on line 37 of my code from a `!=` to a `==`. 

