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

The installation works per the instructions with no problems. We are able to copy and paste most of the commands without modifying anything. The only exception was step 9, which is "run the client by `sudo python3 *src* *dst* *sport* *dport*`". We believe the command should be `sudo python3 client.py *src* *dst* *sport* *dport*`, so we are **deducting .5 points**.

The instructions are mostly clear, being specific shell commands, with the exception of "using net-tools, find the ipv4 address of the server VM". While this is clear enough to people who are familiar with net-tools, we believe the instruction could be made more friendly to the general user by directing listing the `ifconfig` command, so we are **deducting .5 points**.

Overall we are assigning a rating of 9 for installation, with .5 points deducted for each of the two issues mentioned above.

## Part 2: User Guide

TODO

\<comments, reason for point deductions\>

We followed the instructions in `user_guide.md`.

The user guide includes instructions on how to run default tests on the IP layer, including how to specify which fields to fuzz. An example is included, though there is a typo in the example. We will not deduct any points for this minor issue.

The user guide includes instructions on how to run tests on the IP layer when values are read from a file, including how to specify the file name and the format of the csv file. An example file, `ip.csv`, is provided, and the fuzzer works when running with the example file.

The user guide includes instructions on how to run default tests on the TCP layer, including how to specify which fields to fuzz. No example is included, so we will **deduct .5 points**.

The user guide includes instructions on how to run tests on the TCP layer when values are read from a file, including how to specify the file name and the format of the csv file. An example file is provided, and the fuzzer works when running with the example provided.

Overall, the fuzzer instructions are clear and cover each layer and most of them include examples. The instructions for how to use the server and specify the pattern are clear and include examples (?). The program works per the instructions with no problems. Therefore, we are assigning 9.5 for user guide.

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