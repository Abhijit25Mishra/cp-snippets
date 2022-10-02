# KMP Algorithm           

It is a pattern searching algorithm, in which we try to find a patter in a string.

## Explanation -
Pattern searching methods are used to display the search results when we perform a string search in a database, browser, or notepad/word file.  The Naive algorithm's worst-case complexity is O(m(n-m+1)). In contrast to this, in a worst case scenario, the KMP (Knuth Morris Pratt) Pattern Searching algorithm has a time complexity of O(n). <br/>

The degenerating property of the pattern, which is when the same sub-patterns appear more than once in the pattern, is used by the KMP matching algorithm to increase the worst case complexity to O. (n). The fundamental tenet of KMP's method is that we already know some of the letters in the text of the following window if we see a discrepancy (after a few matches). By using this knowledge, we can avoid matching characters that we know will already match. <br/>