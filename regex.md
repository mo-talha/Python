# Regex
`.` - Any character except new line, tab spaces etc
`*` - 0 or more repetetions of characters
`+` - 1 or more repetetions of characters
`\` - Used to get a specific character, ex: \m, needs to have m
`^` - Start matching at the begining of the string
`$` - Start matching at the end of the string i.e. until a new line, a tab space etc.
`?` - 0 or 1 repetition
`{m}` - m repetitions
`{m, n}` - m - n repetitions
ex:
```
re.search(".+@[a-zA-Z0-9]+\.com$", email)
```
re will search for .com until a new line, tab space etc
`[]` - Used to declare a set
`[^]` - Used to escape characters except, ex: [^@] - This means every character except the @ char
`\w` - word character as well as numbers and the underscore
```
Instead of using,
re.search(".+@[a-zA-Z0-9]+\.com$", email)

we can just do,
re.search(".+@\w+\.com$", email) 

This means after @ any word or character, + means at least one or more characters, followed by a . (\.) this means specfifically a dot, and followed by characters com.
```
`\W` - not a word character
`\d` - means any decimal digit
`\D` - not a decimal digit
`\s` - whitespace characters
`\S` - not a whitespace
`|` - or, can be used as a|b, A|B
`()` - used to group, ex: `[\w]+@[\w]+\.(com|in|edu|org)` this will find emails that will end with com, in, edu or org

## Flags
- re.IGNORECASE
- re.MULTILINE
- re.DOTALL

these can can be used inside `re.search()` as an argument, in place of flags. Lets say we do re.IGNORECASE it will treat the email addresses in lower case even if the user enters it all in uppercase.

### What if the email is talha@koinbasket.bitbuddy.in
```
re.search(r"\w+@\w+\.in")
```
this would make the above email invalid as the regex is searching for a pattern where there are 1 or more characters followed by a .in, we can fix this in multiple ways,

**fix-1**
```
re.search(r"\w+@\w+\.bitbuddy\.in")
```
But this is very restrictive, meaning the email needs to have bitbuddy to be valid.

**fix-2**
```
re.search(r"\w+@\w+\.\w+\.in")
```
This means any word to the right of @ followed by a dot, followed by a word and .in

## re.match(), re.fullmatch()
***re.match()*** helps in matching the stringfrom the start, i.e. we can avoid using `^`. 
***re.fullmatch()*** helps in matching the string from the start and match it from the end, i.e. we can avoid using both `^` and `$`. 


```
name = "Talha, Mohammed"
matches = re.search(r"(\w+), (\w+)", name)

first_name = matches.group(2)
last_name = matches.group(1)
print(f"{first_name} {last}")
```
In the above code we can see that, with grouping () we can get the matching values in variables and use them.