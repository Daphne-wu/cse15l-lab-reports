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
```
211c211
< []
---
> [url]
```
This means that on line 211 of the results.txt in the CSE15L-RoseateSpoonbill directory, the line contained `[]`, while on line 211 of the markdown-parse/results.txt directory, the line contained `[url]`.  If we look at line 211, in those files, that’s the test output for the file 194.md. 
 

 > 

[Foo*bar\]]:my_(url) 'title (with parens)'

[Foo*bar\]]
