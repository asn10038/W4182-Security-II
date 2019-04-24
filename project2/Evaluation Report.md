# Evaluation Report

Evaluated by Group 4 (Anthony Saieva && Qing Teng)

Evaluation for Group 3 (Sophia Yao && Yoongbok Lee)

Link to project: <https://github.com/sophiay98/4182_fuzzer>

------

[TOC]

## Part 0: Summary

Here are the ratings we assigned for each criteria. You can find more specific explanations in Part 1 to 5. In Part 6, we modified the code to add logging features for both the fuzzer and the server.

| Criteria                     | Rating  |
| ---------------------------- | ------- |
| Installation                 | 9/10    |
| User Guide                   | 9/10    |
| Program functionality        | TODO/50 |
| Error handling               | TODO/20 |
| Clarity of the code/comments | 10/10   |

## Part 1: Installation

We cloned the repo and followed the instructions in `installation_guide.md`. We are installing the fuzzer on a Ubuntu 18.04 Desktop running in a VirtualBox VM. To ensure that the dependencies are fully listed in the installation guide, we are starting from a clean virtual environment.

The installation works per the instructions with no problems. We are able to copy and paste most of the commands without modifying anything. The only exception was step 9, which is "run the client by `sudo python3 *src* *dst* *sport* *dport*`". We believe the command should be `sudo python3 client.py *src* *dst* *sport* *dport*`, so we are **deducting .5 points**.

The instructions are mostly clear, being specific shell commands, with the exception of "using net-tools, find the ipv4 address of the server VM". While this is clear enough to people who are familiar with net-tools, we believe the instruction could be made more friendly to the general user by directing listing the `ifconfig` command, so we are **deducting .5 points**.

Overall we are assigning a rating of 9 for installation, with .5 points deducted for each of the two issues mentioned above.

## Part 2: User Guide

We followed the instructions in `user_guide.md`.

The user guide includes instructions on how to run default tests on the IP layer, including how to specify which fields to fuzz. An example is included, though there is a typo in the example. We will not deduct any points for this minor issue.

The user guide includes instructions on how to run tests on the IP layer when values are read from a file, including how to specify the file name and the format of the csv file. An example file, `ip.csv`, is provided, and the fuzzer works when running with the example file.

The user guide includes instructions on how to run default tests on the TCP layer, including how to specify which fields to fuzz. An example is included, though specific values are not given.

The user guide includes instructions on how to run tests on the TCP layer when values are read from a file, including how to specify the file name and the format of the csv file. An example for the file is provided, and the fuzzer works when running with the example.

The user guide includes instructions on how to run default tests on the application layer, including how to specify the range of payload size (or exact size) and the number of tests. An example is included, though specific values are not given.

The user guide includes instructions on how to run tests on the application layer when payloads are read from a file, including how to specify the file name and the number of tests. There is a default payload file, though it is not mentioned in the user guide. We will not deduct any points for this minor issue.

The user guide includes how to specify the destination of the packets.

The user guide includes comments on the server, including where to specify the pattern. However, we believe this part could be better organized. There is no example of how to run the server (though it is included in `installation_guide.md`). For these reasons we are **deducting 1 point**.

Overall, the fuzzer instructions are clear and cover each layer and most of them include examples. The instructions for how to use the server and specify the pattern are less clear and do not include examples. The program works per the instructions with no problems. Therefore, we are assigning 9 for user guide.

## Part 3: Program Functionality

TODO

\<Summary of tests performed\>
\<The following types of tests passed with no issues or minor issues (and explain the issues).\>
\<The following tests failed. Include exact inputs and relevant output.\>

### Fuzzer

We performed a series of tests on the fuzzer. First, we tested the general functionality, which included specifying the destination address and port and including a default payload. Second, we tested the IP, TCP and application layers separately. The specific tests are described below in detail. We are only providing screenshots for some of the tests due to space restrictions.

The following types of tests passed with no issues or minor issues:

**(1) General: specifying the destination address and port.**

Command: ``

Result: 

**(2) General: including a default payload.**

Command:

Result:

(3) IP layer: fuzzing all fields.

Command:

Result:

In general, this fuzzer was able to pass most of the tests we performed.

## Part 4: Error Handling

TODO

\<The following types of tests passed with no issues or minor issues (and explain the issues).\>
\<The following tests failed along with exact inputs and relevant output.\>

## Part 5: Clarity of the Code/Comments

The code is well organized and well commented.

For the fuzzer, the code for the IP, TCP and application layers are distinctively separated into the files `ip_fuzzer.py`, `tcp_fuzzer.py` and `app_fuzzer.py` and represented by the classes `IPFuzzer`, `TCPFuzzer` and `APPFuzzer`. We believe this shows good practice.

Inside each class, different functionalities are also separated into different methods, such as `_get_payload`, `_fuzz_from_file` and `_fuzz_by_fields`. As we can see, the names of the methods are very representative and they make the code very readable.

Ample comments are provided and it is easy to understand what the code is doing. Here is an example from `src/ip_fuzzer.py`:

```python
try:
    f = open(self._payload_addr, "r")
    payloads = f.readlines()
    if len(payloads) < 1:
				f.close()
        raise IOError

    # try parsing the first line as hex
    try:
    		payload = bytes.fromhex(payloads[0]) # only reads the first line of the file
        print("using payload: 0x" + payloads[0])
    except ValueError:
        # if cannot be parsed as hex, raise exception
        print("%s cannot be parsed as hex" % (payloads[0]))
        raise FieldAttributeException
except IOError:
        #file cannot be read. Create with 0x00
    		...
```

Server code is relatively short and it is also easy to understand. We do recommend moving `fuzz.py` to `src/` for better organization. Also `src/fuzzer-main.py` and `src/server2.py` do not seem to be needed. In general, we did not find any reasons to deduct points for this part, so we are assigning a 10.

## Part 6: Code Modification

### Adding Logging Information to the Server
#### Before
```
# server had no command line arguments
```
#### After 
* Adding the command line argument parsing
```
log_file = None
if len(sys.argv) > 2 and sys.argv[1] == '-L':
    log_file = sys.argv[2]
```
* Printing the information to the file
```
#send valid/invalid
                if pattern in data[:len(pattern)]:
                    print("valid!")
                    valid += 1
                    conn.sendall(b"0x000x000x000x00")
                else:
                    print("invalid!")
                    invalid += 1
                    conn.sendall(b"0xff0xff0xff0xff")
############ ADDITIONAL CODE ###################
                if log_file is not None:
                    with open(log_file, "wa"):
                        log_file.write(pattern)
################################################

                #data parsing
                if not data:
                    break
                if not data.endswith('\r\n'):
                    continue
                lines = data.split('\r\n')
                for line in lines:
                    print(line)
                data = ''

```

\<comments, reason for point deductions, required code snippets, inputs and outputs to show the
modifications and that they worked\>





Requirements for report:

A report consisting entirely incomplete sentences, typing/spelling/grammatical errors and mostly bullet lists in plain text format will receive no or little credit.

A nicely formatted report clearly and thoroughly explaining the reason for each rating/point deduction, what was tested and what code changes were made will receive most or all credit. Consider including tables indicating each test and the result, and including copies or screenshots of terminal output showing correct results or errors.
