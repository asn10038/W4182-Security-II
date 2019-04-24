# Evaluation Report

Evaluated by Group 4 (Anthony Saieva && Qing Teng)

Evaluation for Group 3 (Sophia Yao && Yoongbok Lee)

Link to project: <https://github.com/sophiay98/4182_fuzzer>

------

[TOC]

## Part 0: Summary

TODO: Write a few sentences.

| Criteria                     | Rating  |
| ---------------------------- | ------- |
| Installation                 | 9/10    |
| User Guide                   | TODO/10 |
| Program functionality        | TODO/50 |
| Error handling               | TODO/20 |
| Clarity of the code/comments | TODO/10 |

## Part 1: Installation

We cloned the repo and followed the instructions in `installation_guide.md`. We are installing the fuzzer on a Ubuntu 18.04 Desktop running in a VirtualBox VM. To ensure that the dependencies are fully listed in the installation guide, we are starting from a clean virtual environment.

The installation works per the instructions with no problems. We are able to copy and paste most of the commands without modifying anything. The only exception was step 9, which is "run the client by `sudo python3 *src* *dst* *sport* *dport*`". We believe the command should be `sudo python3 client.py *src* *dst* *sport* *dport*`.

The instructions are mostly clear, being specific shell commands, with the exception of "using net-tools, find the ipv4 address of the server VM". While this is clear enough to people who are familiar with net-tools, we believe the instruction could be made more friendly to the general user by directing listing the `ifconfig` command.

Overall we are assigning a rating of 9 for installation, with .5 points deducted for each of the two issues mentioned above.

## Part 2: User Guide

TODO

\<comments, reason for point deductions\>

We followed the instructions in `user_guide.md`.

## Part 3: Program Functionality

TODO

\<Summary of tests performed\>
\<The following types of tests passed with no issues or minor issues (and explain the issues).\>
\<The following tests failed. Include exact inputs and relevant output.\>

## Part 4: Error Handling

TODO

\<The following types of tests passed with no issues or minor issues (and explain the issues).\>
\<The following tests failed along with exact inputs and relevant output.\>

## Part 5: Clarity of the Code/Comments

TODO

\<comments, reason for point deductions, required code snippets, inputs and outputs to show the
modifications and that they worked\>

## Part 6: Code Modification

TODO





Requirements for report:

A report consisting entirely incomplete sentences, typing/spelling/grammatical errors and mostly bullet lists in plain text format will receive no or little credit.

A nicely formatted report clearly and thoroughly explaining the reason for each rating/point deduction, what was tested and what code changes were made will receive most or all credit. Consider including tables indicating each test and the result, and including copies or screenshots of terminal output showing correct results or errors.