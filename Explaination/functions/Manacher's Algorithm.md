# Manacher's Algorithm       

It find all the pairs in a string such that its substring  is a palindrome. <br />
It is very famous algorithm to solve Longest Palindromic Subsequence (LPS) problem in linear time complexity.

## Explanation -
At first appearance, it appears that there is no linear approach for this problem. In the worst situation, a string may have up to palindromic substrings.
The fact that this approach is sufficiently simpler to compute these "palindromity arrays" in linear time is a surprise.

Assume the given String Shas a length of N,S = "abababa". Create a string Q of length 2*N+1 , by inserting any letter that doesn't appear in the input string (call it special character for the purpose of this article), 
in the spaces between any 2 characters. Also, insert this special character in the beginning and the end of the string.If "#" is chosen as special character then the new string Q would look like "#a#b#a#b#a#b#a#".

Calculate the longest palindromic substring in each center. Expand around each character i in the new string, then store the number of letters, in the longest palindromic substring with character  as the center, divided by 2.
The stored number is divided by 2 because the palindromic substring has it's 2 same parts around the center.

Above process would yield an array P=[0,1,0,3,0,5,0,7,0,5,0,3,0,1,0].
Each number m, in the array P, indicates that there are m corresponding letters in both sides around a center i. So the palindromic substring = m letters in the left side + center + m letters in right side.

### Time Complexity: O(n)
### Space Complexity: O(1)
<br />

![image](https://user-images.githubusercontent.com/80835305/193578282-57c1abe0-e08e-4fad-af92-a4718587b8ae.png)


## Trivial algorithm-

### Time complexity of trivial algorithm- O(n^2)
```cpp
vector<int> manacher_odd(string s) {
    int n = s.size();
    s = "$" + s + "^";
    vector<int> p(n + 2);
    for(int i = 1; i <= n; i++) {
        while(s[i - p[i]] == s[i + p[i]]) {
            p[i]++;
        }
    }
    return vector<int>(begin(p) + 1, end(p) - 1);
}
```

Terminal characters $ and ^ were used to avoid dealing with ends of the string separately.



## Implementation of Manacher's algorithm

Odd- and even-length palindromes are individually accounted for as d1[i] and d2[i]. If the two central characters in a palindrome are s[i] and s[i-1], we assume that they are centred in position I for palindromes of even length.

for ODD-

```cpp
vector<int> manacher_odd(string s) {
    int n = s.size();
    s = "$" + s + "^";
    vector<int> p(n + 2);
    int l = 1, r = 1;
    for(int i = 1; i <= n; i++) {
        p[i] = max(0, min(r - i, p[l + (r - i)]));
        while(s[i - p[i]] == s[i + p[i]]) {
            p[i]++;
        }
        if(i + p[i] > r) {
            l = i - p[i], r = i + p[i];
        }
    }
    return vector<int>(begin(p) + 1, end(p) - 1);
}
```


for EVEN-

Even though Manacher's technique may be implemented separately for odd and even lengths, the implementation of the version for even lengths is sometimes seen to be more challenging since it feels less natural and is more prone to off-by-one errors. To lessen this, the entire issue can be reduced to the scenario in which we only deal with palindromes of odd length. To accomplish this, we can insert an extra # character at the start and end of the string, as well as between each letter in the string.

![image](https://user-images.githubusercontent.com/80835305/193577578-c78efccc-76b8-49e9-be63-b1093c4ca201.png)

However, even-length palindromes of the original string are now odd-length palindromes of the new string centred in # characters, while the odd-length palindromes of the original string remain centred in the characters of the first string.

The reduction is implemented in the following way:

```cpp
vector<int> manacher(string s) {
    string t;
    for(auto c: s) {
        t += string("#") + c;
    }
    auto res = manacher_odd(t + "#");
    return vector<int>(begin(res) + 1, end(res) - 1);
}
```
For the sake of simplicity, the array's explicit division into d1 and d2 as well as their calculation are left out.

## author - @flow6979(https://github.com/flow6979)
