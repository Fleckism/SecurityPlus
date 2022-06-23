syntax
Filtering a log to discover data points of interest usually involves some sort of string search, typically invoking [[regular expression (regex)]] syntax. A regular expression is a search pattern to match within a given string. The search pattern is built from the regex syntax. This syntax defines metacharacters that function as search operators, quantifiers, logic statements, and anchors/boundaries. The following list illustrates some commonly used elements of regex syntax:

-   [ … ] matches a single instance of a character within the brackets. This can include literals, ranges such as [a-z], and token matches, such as [\s] (white space) or [\d] (one digit).
-   + matches one or more occurrences. A quantifier is placed after the term to match; for example, \s+ matches one or more white space characters.
-   * matches zero or more times.
-   ? matches once or not at all.
-   {} matches a number of times. For example, {2} matches two times, {2,} matches two or more times, and {2,5} matches two to five times.

A complete description of regex syntax is beyond the scope of this course, but you can use an online reference such as [regexr.com](https://regexr.com/) or [rexegg.com](http://rexegg.com/) to learn it.

The grep command invokes simple string matching or regex syntax to search text files for specific strings. This enables you to search the entire contents of a text file for a specific pattern within each line and display that pattern on the screen or dump it to another file. A simple example of grep usage is as follows:

grep -F 192.168.1.254 access.log

This searches the text file access.log for all lines containing some variation of the literal string pattern 192.168.1.254 and prints only those lines to the terminal. The -F switch instructs grep to treat the pattern as a literal.

The following example searches for any IP address in the 192.168.1.0/24 subnet using regex syntax for the pattern (note that each period must be escaped) within any file in any directory from the current one. The -r option enables recursion, while the period in the target part indicates the current directory:

grep -r 192\.168\.1\.[\d]{1,3} ./*