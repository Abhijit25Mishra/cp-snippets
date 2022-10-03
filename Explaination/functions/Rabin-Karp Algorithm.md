# Rabin-Karp Algorithm       

It implements on the functionality of **Rolling Hash** <br />
The Rabin-Karp algorithm uses a hash function to search for and match patterns in text. Instead of going through every character in the initial phase like the Naive String Matching Algorithm does, it filters out the characters that don't match before performing the comparison.


## Explanation -
The Naive String Matching algorithm gradually shifts the pattern. Characters at the current shift are checked one by one after each slide, and if they all match, the match is printed. <br />
The Rabin-Karp algorithm slides the pattern one by one, just like the Naive Algorithm. The Rabin Karp algorithm, in contrast to the Naive approach, compares the pattern's hash value to the hash value of the currently-selected substring of text, and only begins matching individual characters if the hash values match. Therefore, the following strings require hash values to be calculated via the Rabin-Karp algorithm -
* All the substrings of the text of length equals to pattern
* Pattern itself

## Time Complexity: O(length of main string + length of pattern)
## Space Complexity: O(1) 
<br />

![Rabin-Karp Algorithm](https://user-images.githubusercontent.com/80835305/193504950-72d8ef62-99ab-4c46-9458-14d26071bd88.png)


## Steps of Algorithm

1. Create a function “rabinKarpSearch()’ for implementing the Rabin Karp algorithm, that will accept the two parameters - the given string ‘S’ and the given pattern ‘P’. First, calculate the lengths of ‘S’ and ‘P’.

2. Now, we have to choose a prime number and a value for taking modulus while calculating the hash values. For minimizing the hashing collision, we have to take the value of the prime number close to the number of characters used in the string and pattern. Assuming that the given ‘S’ and ‘P’ consist of only lower alphabets, the total number of characters will be 26, so take prime = 31. Now a value for taking modulus should be very large and prime so, take mod = 1e +9.

3.  The hash function that we have used here is:
    ```cpp
     hash(S) = (Σ((S[i] - ‘a’ + 1) * (P^(i)))) % mod
    ```

4. Create a vector to store the powers of “prime” and store (prime ^ 0) to (prime ^ Ns). Now calculate the hash value of the given pattern and the first window of the string ‘S’.

5. Now one by one, slide the given pattern and calculate the hash value of the corresponding substring and compare it with the hash value of the pattern. If found the same, print the occurrence of the pattern at that index.

## author - @flow6979(https://github.com/flow6979)
