# Computational Theory

*Link to [problems.ipynb](./problems.ipynb) file.*

## 1. Project Overview

This repository contains my submission for the **Computational Theory** assessment for *Winter 2025/26.*
The work focuses on implementing and analysing core components of the **Secure Hash Standard (FIPS 180-4)** using *Python* and *NumPy*, supported by clear explanations, reproducible code, and ongoing revision through consistent commits.

The assessment requires all problems to be completed in one **Jupyter notebook** called ``problems.ipynb``. This notebook needs to be organised in a way suitable for review and testing. It also must maintain consistent version control and structure.

The structure and requirements of this project follow the official assessment instructions and guidance provided by the module’s [GitHub repository](https://github.com/ianmcloughlin/computational-theory/tree/main).

### 1. Purpose of Project

The primary goal of this project is to demonstrate a strong practical **understanding of the computational and mathematical foundations** behind the **SHA-256 hashing algorithm**, including:

- Binary word operations

- Bitwise functions and rotation logic

- Prime-based constant derivation

- Cryptographic padding rules

- Block-based message processing

- Iterative hash computation and compression functions

- Password hashing, weaknesses, and mitigation strategies

The project goes beyond simply solving each question: it **documents the theory behind each concept**, applies testing, references appropriate sources, and structures the work so it can be rerun cleanly on any machine.

### 2. Respository Structure
The project structure is quite simple and only contains the ``README.md`` and the ``problems.ipynb``. My repository also contains a .``vscode`` file which just contains JSON settings configuration file but it is not particularly relevant to this assignment.
```
computational-theory/
│
├── .gitignore
├── problems.ipynb              
├── README.md  
├── requirements.txt           
```

- **README.md**: Provides a general overview of the [problems.ipynb](./problems.ipynb) notebook. 
- **problems.ipynb**: Contains the five problems from the *computational theory* module and follows the module's requirements. 
- .**gitignore**: Prevents certain files from being committed to the [computational-theory](https://github.com/fionnmcgoldrick123/computational-theory) GitHub repository.
- **requirements.txt**: Stores dependencies for easy installation in set up.

### 3. How to Run the Notebooks

To run `problems.ipynb`, clone the repository and set up a Python environment with the required dependencies.

### Clone the Repository
**With HTTPS:** 
```
git clone https://github.com/fionnmcgoldrick123/computational-theory.git
cd computational-theory
```

**With SSH:**
```
git clone git@github.com:fionnmcgoldrick123/computational-theory.git
cd computational-theory
```

### Create and Activate a Virtual Environment
It is recommended to use a virtual environment to keep dependencies isolated.
```
python3 -m venv venv
source venv/bin/activate        # macOS / Linux
venv\Scripts\activate           # Windows
```

### Install Dependencies
Install NumPy dependency.
```
pip install numpy
```

### Open the Project in Visual Studio Code
```
code . 
```

### Select your Python Interpreter
**In Visual Studio Code:**

1. Press **Ctrl+Shift+P**
2. Type **Python: Select Interpreter**
3. Choose the interpreter from your ``.venv`` folder

This ensures the notebook uses the correct environment.

### Run the Notebook

Open ``problems.ipynb`` and click the run / play button on any given cell.

**NOTE:** *Ensure the first cell containing the NumPy and hashlib imports is run before executing later cells.*

### 4. Dependencies

This project requires only two external **Python** packages: **NumPy** & **hashlib**.

### Required Packages:
- **NumPy** — used for 32-bit integer operations, bitwise functions, and numerical calculations required by the Secure Hash Standard.

**Install NumPy using:**

```
pip install numpy
```

*hashlib is a built-in standard library in Python*

```python
import hashlib
```

### 5. Core Theoretical Concepts Explained

This section explains the key **low-level computational concepts** used throughout SHA-256 and your notebook. These ideas appear repeatedly throughout the notebook and are essential for understanding how each component of the **Secure Hash Standard (FIPS 180-4)** works internally. 

### 32-Bit Words and Modulo 2<sup>32</sup> Arithmetic

**SHA-256** operates exclusively on **32-bit unsigned integers (also called words).**
A 32-bit word can represent values in the range:

``0 ≤ x < 2``<sup>``32``</sup>

All additions in **SHA-256** use **modulo 2<sup>32</sup>** arithmetic, meaning that if a result exceeds the maximum 32-bit value, it wraps around, discarding overflow bits:

*Example*
```python
0xFFFFFFFF + 0x02 = 0x00000001   (overflow ignored)
```

This wrap-around behaviour is fundamental to the **hash design**.
In the notebook, **NumPy’s** ``np.uint32()`` is used to enforce **32-bit boundaries** consistently, ensuring all intermediate values remain valid **SHA-256 words**.


### Bitwise Operations Notations
| Symbol | Name | Operation Description | Example `(x = 0b1100, y = 0b1010)`| 
|:-:|:-:|:-:|:-----------------:|
| & | Bitwise AND | Compares each bit of two numbers. Bit is *1* only if both bits are *1*. | `x & y = 0b1000` | 
| ` | Bitwise OR |Compares each bit of two numbers. Bit is *1* if either bit is *1*. | ``x ` y = 0b1110`` | 
| ^ | Bitwise XOR | Bit is 1 if the two bits are *different*. | `x ^ y = 0b0110` | 
| ~ | Bitwise NOT | Flips every bit *(1 > 0, 0 > 1)*. Works as *-(x+1)* in Python due to two’s complement. | `~x = -0b1101` |
| << | Left Shift | Shifts bits to the left by *n* places. Fills in zeros on the right. | `x << 2 = 0b110000` | 
| >> | Right Shift | Shift bits to the right by *n* places. Fills in the zeros on the left. | `x >> 2 = 0b0011` |  




### 6. Resources & References

This section contains each source that I used both universally throughout the assignment, and the ones I used for each individual problem.

### Universal References

- [Computational Theory GitHub Repo](https://github.com/ianmcloughlin/computational-theory) - *Base resource for the notebook. Used for understanding the notebook and problem requirements. Also, for notes on understanding many concepts relevant to this notebook.*  

- [NIST (Secure Hash Standard)](https://csrc.nist.gov/pubs/fips/180-2/final) - *Used for getting the necessary formulas to complete the problems.* 

- [NumPy Docs](https://numpy.org/doc/) - *Used to understand NumPy functionalities, use cases, and also for NumPy syntax.*

- [numpydoc](https://numpydoc.readthedocs.io/en/latest/format.html) - *Helpful for planning out Docstring structure*

- [Real Python](https://realpython.com/) - *Used for understanding new Python concepts I was not aware of.*

- [SHA: Secure Hashing Algorithm - Computerphile](https://www.youtube.com/watch?v=DMtFhACPnTY) - *YouTube video used for understang SHA general knowledge.*

- [W3Schools - Python](https://www.w3schools.com/python/) - *Used for understanding anything python. Syntax, built-in functions, data structures, ect...*

- [ChatGPT](https://chatgpt.com/) - *Used for a personalised explanation of concepts that I could not find helpful sources on. Also used for assistance with grammar, spelling mistakes, and scientific structure in the markdown.*

- [Claude](https://claude.ai/new) - *Used for help in debugging Python code if I could not find the issues myself or online.*

- [StackOverflow](https://stackoverflow.com/questions) - *Often used to find correct or improved implementations of my code.* 

- [Sha Algorithm - Visualisation](https://sha256algorithm.com/) - *Massive help for visualising SHA-256 concepts.*

### Problem 1 References

- [Bitwise Operators in Python](https://realpython.com/python-bitwise-operators/) - *To get a understand bitwise operations further.*

- [Bitwise Operation](https://en.wikipedia.org/wiki/Bitwise_operation) - *To obtain a deeper understanding of bitwise operations.*

### Problem 2 References

- [List of prime numbers](https://en.wikipedia.org/wiki/List_of_prime_numbers) - *Used for reaffirming prime function output.*

- [Cuberoot Root Calculator](https://www.calculatorsoup.com/calculators/algebra/cuberoots.php) - *Checking if function outputting correct primes.*

- [Cuberoot Wikepedia](https://en.wikipedia.org/wiki/Cube_root) - *Information on cuberoots*

- [How to represent fractional numbers in Binary](https://www.luisllamas.es/en/represent-fractional-numbers-in-binary/) - *Used for understanding how to represent fractional numbers in binary.*

- [Hexadeximal Wiki](https://en.wikipedia.org/wiki/Hexadecimal) - *Information on hexadecimal representation.* 

### Problem 3 References

- [Real Python - Generators](https://realpython.com/introduction-to-python-generators/) - *Used to better understand how generators work and their applications.*

- [Real Python - Byte Objects](https://realpython.com/python-bytes/) - *Understand byte object better.*

- [MojoAuth - MD5 vs MD4](https://mojoauth.com/compare-hashing-algorithms/) - *Researching MD5 & MD4 cryptographic functions.* 

- [Wikipedia - Guido van Rossum](https://en.wikipedia.org/wiki/Guido_van_Rossum) - *Researching Python history for discussion section.*

- [Python Enhancement Proposals](https://peps.python.org/pep-0225/) - *Used for understanding the PEP 225 proposals for the discussion section.*

- [Wikipedia - Endianness](https://en.wikipedia.org/wiki/Endianness) - *For understanding endianness.*

- [W3Schools - Python Built in Functions](https://www.w3schools.com/python/python_ref_functions.asp) - *For finding functions I will need for this problem and how they work.*

### Problem 4 References

- [Hash function](https://en.wikipedia.org/wiki/Hash_function) - *Better understanding of hash functions.*

- [SHA-256 | COMPLETE Step-By-Step Explanation - RedBlockBlue](https://www.youtube.com/watch?v=orIgy2MjqrA) - *Useful YouTube video. Watched onward from **4:27** for this problem.*

- [CS255 - Stanford: Introduction to Cryptography](https://crypto.stanford.edu/~dabo/cs255/) - *Taught how iterative hashing worked and why internal state is updated block by block.*

- [SHA256 - Online Tools](https://emn178.github.io/online-tools/sha256.html) - *Used for visualisation of hashing and experimenting with input and hashed output. Also used to test my implementation functionality.*

- [Simplil Learn: A Definitive Guide to Learn The SHA-256 (Secure Hash Algorithms)](https://www.simplilearn.com/tutorials/cyber-security-tutorial/sha-256-algorithm) - *Extremely good graphics for explaining hashing and SHA-256 concepts.*

### Problem 5 References

- [UTF-8 - Wikepedia](https://en.wikipedia.org/wiki/UTF-8) - *To consolidate my understanding of the UTF-8 format*

- [UTF-8, Explained Simply - Nic Barker](https://www.youtube.com/watch?v=vpSkBV5vydg) - *More theory and background behind UTF-8 encoding.*

- [The Unicode Standard](https://www.unicode.org/standard/standard.html) - *Used for learning about the Unicode Standard deeper.*

- [ASCII Code](https://www.ascii-code.com/) - *To compare UTF-8 to ASCII encoding.*

- [Nord Pass](https://nordpass.com/most-common-passwords-list/) - *For finding a list of the top 200 most common passwords.*

- [Real Python - hashlib](https://realpython.com/ref/stdlib/hashlib/#:~:text=The%20Python%20hashlib%20module%20provides,%2C%20password%20storage%2C%20and%20more.) - *Researching libraries to help with this problem.*

- [Python assert Keyword](https://www.w3schools.com/python/ref_keyword_assert.asp) - *Used for understanding assert keyword in Python before using it in test cases.*

- [bcrypt - Wikipedia](https://en.wikipedia.org/wiki/Bcrypt) - *Reading up on bcrypt for discussion section.*

- [PBKDF2 - Wikipedia](https://en.wikipedia.org/wiki/PBKDF2) - *Reading up on PBKDF2 for discussion section of this problem.*

- [Argon2 - Wikipedia](https://en.wikipedia.org/wiki/Argon2) - *Read up on Argon2 definition for discussion section.*

- [What is a Dictionary Attack? - Kaspersky](https://www.kaspersky.com/resource-center/definitions/what-is-a-dictionary-attack) - *Understanding how a dictionary attack works.*

## 7. Assessment Requirements Checklist

This project has been implemented to meet the requirements of the Computational Theory assessment as described in the module repository.


- [x] Implemented all required **SHA-256** components specified in the assignment, including the padding algorithm, message block parsing, message schedule expansion (`W[0..63]`), and the full **SHA-256** compression function (`hash(current, block)`) as described in **FIPS 180-4**.
- [x] Completed all problem statements from the assessment brief, including the implementation of the helper functions (bitwise operations, rotations, choice/majority functions, σ and Σ functions) and the construction of the working variables for each compression round.
- [x] Developed a working SHA-256 hashing pipeline capable of hashing **UTF-8** encoded strings.
- [x] Successfully implemented the password-cracking task using the SHA-256 function, a dictionary of common passwords, and hash comparison.
- [x] Added explanations, docstrings, and comments to document how each part of the implementation works and how it relates to the Secure Hash Standard.
- [x] Included test cases validating correctness, determinism, avalanche behaviour, and correct 32-bit word handling.
- [x] Provided a discussion of results, interpretation of the approach, and improvements to password hashing (e.g., salting, slow KDFs, stronger password policies).
- [ ] Finish all sections to the ``README.md`` in a cohesive and professional way.
- [ ] Ensure that the ``problems.ipynb`` is well structured and consistent while reading in an exciting and interesting way.
- [ ] Explore multiple different approaches to implementations of the problems in the notebook. 



## 8. Testing / Verification Notes

All components of the project were tested using a combination of unit-level checks, manual verification, and comparisons with known **SHA-256 outputs**. Each problem was validated in its own appropriate way to ensure correctness, consistency, and alignment with the **FIPS 180-4 specification**.

The full hashing pipeline was cross-checked against official test vectors and external **SHA-256** calculators (which are referenced), and repeated runs confirmed deterministic behaviour. The password-cracking task was also tested with controlled inputs to ensure the logic worked as intended. Overall, the project’s results were verified to be accurate and reproducible.

## 9. Author
This repo was designed and written by *Fionn McGoldrick*.

G00422349@atu.ie

