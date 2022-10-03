# Sieve of erasthosthenes

 This algorthm is used to find primes numbers till N

 ## Explanation -
 We'll initialize the values SPF[i] with zeros, which means that we assume all numbers are prime. During the algorithm execution this array will be filled gradually.<br/>

 Now we'll go through the numbers from 2 to n. We have two cases for the current number :<br/>

 1) SPF[i] = 0 - that means that i is prime, i.e. we haven't found any smaller factors for it.Hence we assign SPF[i] = i and add i to end of vector prime. <br/>

 2) SPF[i] != 0 - that means i is composite, and its miniimum prime factor is SPF[i];<br/>

 In both cases we update values of SPF[i] for the numbers that are divisible by i. However, our goal is to learn to do so as to set a value SPF[i] at most once for every number. We can do it as follows: <br/>

 Let's consider numbers x = i*p where p are all prime numbers less than or equal to SPF[i](this is why we need to store the list of all prime numbers).
 We'll set new values SPF[x] = p for all numbers of this form.<br/>

 References - Gries,Misra(1978) <br/>

