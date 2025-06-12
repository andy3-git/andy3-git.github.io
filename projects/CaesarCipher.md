---
layout: project
type: project
image: img/CipherDisk.jpg
title: "Simple Caesar Cipher in Python"
date: 2025
published: true
labels:
  - Python
  - GitHub
summary: "A simple Python Project, made during ICS 141 - Discrete Math"
---

<img src="/img/CaesarCipher.png" alt="Caesar Cipher Example" width="200" height="150">

## About

The Ceaser Cipher code is a basic form of encryption that shifts a specific number up or down the alphabet. 
For Example, if A is 1, B is 2 and so on. With the Cipher shifting by +3, then A becomes D, B becomes E and so on
This Cipher predates 58-50 BCE, used by Caesar to protect his messages from interception. 
Using Python, I have reconstructed this simple cipher through dictionaries, and a simple math formula
The formula used is E(x) = (x + k) modulo 26, where x represents numerical valu of the letter, k represents the numerical shift requested
and 26 represent the amount of letters in the alphabet.

## Code

The code down below uses two Python dictionaries in order to covert individual letters of a string into either its numerical form or alphabet form

```python
def intToChar (argument):
    Dict0 = {1: 'A', 2: 'B', 3: 'C', 4: 'D', 5: 'E', 6: 'F', 7: 'G', 8: 'H', 9: 'I', 10: 'J', 11: 'K', 12: 'L', 13: 'M', 
                14: 'N', 15: 'O', 16: 'P', 17: 'Q', 18: 'R', 19: 'S', 20: 'T', 21: 'U', 22: 'V', 23: 'W', 24: 'X', 25: 'Y', 26: 'Z'}
    return Dict0.get(argument)

def charToInt (argument):
    Dict1 = {'A': 1, 'B': 2, 'C': 3, 'D': 4, 'E': 5, 'F': 6, 'G': 7, 'H': 8, 'I': 9, 'J': 10, 'K': 11, 'L': 12, 'M': 13, 
                'N': 14, 'O': 15, 'P': 16, 'Q': 17, 'R': 18, 'S': 19, 'T': 20, 'U': 21, 'V': 22, 'W': 23, 'X': 24, 'Y': 25, 'Z': 26 }
    return Dict1.get(argument, argument)
```

These python definition utilizes the formula mentioned above to encrypt plaintext
It runs on a for loop that detects whether or not there is empty space.
If there it is no empty space, then the character goes through the charToInt dictionary that converts it an Integer
Else it goes through caesar's formula then joins the output.

definition shiftCipherDE3 is the same except the formula uses a negative sign instead of the positive sign


```python
def shiftCipherEN3(encrypt, K):
    output = ""
    for i in encrypt:
        if i != ' ':
            P = charToInt(i.upper())
            if P == i:
                output += output.join(i)
            else:
                shiftCipher = (P + K) % 26
                if shiftCipher == 0:
                    output += output.join(intToChar(P + K))
                else:
                    output += output.join(intToChar(shiftCipher))
        else:
            output += output.join(' ')
    return output

def shiftCipherDE3(decrypt, K):
    output = ""
    for i in decrypt:
        if i != ' ':
            P = charToInt(i.upper())
            if P == i:
                output += output.join(i)
            else:
                shiftCipher = (P - K) % 26
                if shiftCipher == 0:
                    output += output.join(intToChar(P + K))
                else:
                    output += output.join(intToChar(shiftCipher))
        else:
            output += output.join(' ')
    return output
```

Here are some test cases to try out in Python

```python
message1 = "Meet you in the par"
message2 = "I am reading a book on the history of glue. I just can not seem to put it down"
message3 = "I like ths class"
message4 = "Why do scientists not trust atoms? Because they make up everything."

print(shiftCipherEN3(message1, 3))
print(shiftCipherEN3(message2, 3))
print(shiftCipherEN3(message3, 3))
print(shiftCipherEN3(message4, 9))
```
