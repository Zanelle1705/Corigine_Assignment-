# Corigine_Assignment2022

This README file describes my (Zanelle Vorster) program for the Corigine Recruitment Technical Assignment. 

To extract the compressed tarball, please run the following command:

```bash
tar -xzvf zanellevorster.tar.gz
```
Next, change directory to the *corig* file with the following command:
```bash
cd corig
```
Then you have to build the docker image:
```bash
docker build -t corig .
```

Finally, it is packaged and executable as a Docker container so in order to run it according to the assignment instructions, use the following command where *corig* is the image name and *N* is input to the algorithmic problem:

```bash
docker run --rm corig N
```
### Program Description

I have attempted four ways to solve the numerical algorithmic problem which I will discuss and also the reasons why I have selected the final method for my submission. In my actual script *(fibonacci-term.py)* all four algorithms are present; However, the methods' which I am not using are commented out. Additionally, comments are used to clearly label the methods.

Firstly, in order to pass *N* in on the command line, the `sys` module provided in Python is imported and `sys.argv` is used. The first argument from the command line will be the name of the file and therefore the second argument is taken as the input to the python script (i.e, *N*). The `numpy` package is added to the *requirements.txt* file within the Docker container. Furthermore, within the *Dockerfile*, `ENTRYPOINT ["python", "fibonacci-term.py"]` is added. 


The first method solves for *n* in  **Binet's Formula** and checks when the number of digits in the Fib number is equal to the input *N* while accumulating an index number. This method fails when *N* becomes larger than approximately 300 as the value is too large for the 'power' in NumPy to handle, causing overflow to occur. 

The second method uses an iterative approach to finding the Fib sequence; However, it requires the number to be casted to a string in order to find the string length and compare to the *N* value. The assignment suggested to avoid casting variables if possible. Additionally, when *N* gets larger, the execution time is longer than the last two methods described below. 

The third method is my final chosen method and uses the inverse of **Binet's Formula** to find the index of the first term in the Fib sequence to contain *N* digits. The `ceil()` function is used to return the smallest integer greater than or equal to the solution of the inverse formula. This method is fast and can take very large *N* values. (Tested for 100 000 000)

The final method also iterates over every Fib number in order to find the first index. It works with the principle that 1000 digits satisfies *1e1000 <= Fib < 1e1001* and therefore the calculated Fib numbers are bounded and comapred to *10^(N-1)* while accumulating an index number. This method is faster than the second method, but not faster than the third (chosen) method. It also fails when trying to compute for a *N* value of 100 000 000. 

Thank you for the opportunity to challenge myself and learn new skills!
