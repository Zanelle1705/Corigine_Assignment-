# Corigine_Assignment2022

This README file describes my program for Corigine's Recruitment Technical Assignment. 

To extract the compressed tarball, please run the following command:

```bash
tar -xzvf zanellevorster.tar.gz
```

It is packaged and executable as a Docker container so in order to run it according to the assignment instructions, use the following command where *corig* is the image name and *N* is input to the algorithmic problem:

```bash
docker run --rm corig N
```
### Program Description

I have attempted four ways to solve the numerical algorithmic problem which I will discuss and also the reasons why I have selected the final method for my submission. In my actual script *(fibonacci-term.py)* all four algorithms are present; However, the methods' which I am not using are commented out. Additionally, comments are used to clearly label the methods.

Firstly, in orde to pass *N* in on the command line, the `sys` module provided in Python is imported and `sys.argv` is used. The first argument from the command line will be the name of the file and therefore the second argument is taken as the input to the python script (i.e, *N*). 

The first method solves for *n* in  **Binet's Formula** and checks when the number of digits in the Fib number is equal to the input *N* while accumulating an index number. This method fails when *N* becomes larger than approximately 300 as the value is too large for the 'power' in NumPy to handle, causing overflow to occur. 

The second method uses an iterative approach to finding the fib sequence; However, it requires the number to be casted to a string in order to find the string length and compare to the *N* value. The assignment suggested to avoid casting variables if possible. Additionally, when *N* gets larger, the execution time is longer than the next two methods. 

The third method is my final chosen method and also uses the inverse of **Binet's Formula** to find the index of the first term in the Fib sequence to contain *N* digits.
