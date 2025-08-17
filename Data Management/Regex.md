
## Character Classes
*Predefined shorthand notations for commonly used character sets.*

- `.` – Any character except newline  
  _Example_: `a.c` matches `'abc'`, `'axc'`

- `\d` – Digit `[0-9]`  
  _Example_: `\d+` matches `'123'` in `'abc123'`

- `\D` – Non-digit `[^0-9]`  
  _Example_: `\D+` matches `'abc'` in `'abc123'`

- `\w` – Word character `[A-Za-z0-9_]`  
  _Example_: `\w+` matches `'word_1'`

- `\W` – Non-word character  
  _Example_: `\W` matches `'#'` in `'word#'`

- `\s` – Whitespace  
  _Example_: `\s` matches `' '` in `'a b'`

- `\S` – Non-whitespace  
  _Example_: `\S` matches `'a'` in `' a'`

---

##  Bracket Expressions
*Match specific characters or ranges using square brackets.*

- `[adf]` – Match `'a'`, `'d'`, or `'f'`  
  _Example_: `b[aeiou]t` matches `'bat'`, `'bet'`

- `[^adf]` – Exclude `'a'`, `'d'`, or `'f'`  
  _Example_: `[^0-9]` matches non-digit

- `[a-f]` – Match lowercase range  
  _Example_: `[a-c]` matches `'b'` in `'bat'`

- `[A-F]` – Match uppercase range  
  _Example_: `[A-C]` matches `'B'`

- `[0-9]` – Match digits  
  _Example_: `[0-9]+` matches `'123'`

---

##  Anchors
*Match positions, not characters.*

- `^` – Start of string or line  
  _Example_: `^abc` matches `'abc'` at start

- `$` – End of string or line  
  _Example_: `abc$` matches `'abc'` at end

- `\b` – Word boundary  
  _Example_: `\bcat\b` matches `'cat'` not `'catalog'`

- `\B` – Not a word boundary  
  _Example_: `\Bcat\B` matches `'educate'`

---

##  Groups & Backreferences
*Group patterns and refer back to them.*

- `(foo)` – Capturing group  
  _Example_: `(ab)+` matches `'abab'`

- `(?:foo)` – Non-capturing group  
  _Example_: `(?:ab)+` matches `'abab'`

- `(?<name>foo)` – Named group  
  _Example_: `(?<word>\w+)`

- `\1`, `\2`, etc. – Backreference to group  
  _Example_: `(\w+)\s\1` matches `'hello hello'`

- `$1`, `${name}` – Backreference in replacement  
  _Example_: replace `(\w+)` with `$1_`

---

##  Quantifiers
*Specify how many times an element must occur.*

- `*` – 0 or more (greedy)  
  _Example_: `a*` matches `''`, `'a'`, `'aaa'`

- `+?` – 1 or more (lazy)  
  _Example_: `a+?` matches shortest match

- `?` – 0 or 1 (greedy)  
  _Example_: `colou?r` matches `'color'` and `'colour'`

- `{2,4}` – Between 2 and 4 times  
  _Example_: `a{2,4}` matches `'aa'`, `'aaa'`

---

##  Special Characters
*Escape characters and control sequences.*

- `\n` – Newline  
  _Example_: matches line break

- `\t` – Tab  
  _Example_: matches horizontal tab

- `\\` – Backslash  
  _Example_: matches literal `\`

- `\.` – Literal dot  
  _Example_: matches `'.'`

---

##  Assertions
*Conditional matching using lookahead and lookbehind.*

- `foo(?=bar)` – Match `'foo'` if followed by `'bar'`  
  _Example_: matches `'foo'` in `'foobar'`

- `foo(?!bar)` – Match `'foo'` if not followed by `'bar'`  
  _Example_: matches `'foo'` in `'foobaz'`

- `(?<=foo)bar` – Match `'bar'` if preceded by `'foo'`  
  _Example_: matches `'bar'` in `'foobar'`

- `(?<!foo)bar` – Match `'bar'` if not preceded by `'foo'`  
  _Example_: matches `'bar'` in `'bazbar'`

---

##  POSIX Character Classes
*Used within brackets for broad matching, e.g., `[[:digit:]]`.*

- `[:alpha:]` – Letters  
  _Example_: `[[:alpha:]]` matches `'a'`, `'Z'`

- `[:digit:]` – Digits  
  _Example_: `[[:digit:]]` matches `'0'`–`'9'`

- `[:space:]` – Whitespace  
  _Example_: `[[:space:]]` matches space, tab

- `[:punct:]` – Punctuation  
  _Example_: `[[:punct:]]` matches `'!'`, `'?'`

---

##  Modifiers
*Inline options to change RegEx behavior.*

- `(?i)` – Case insensitive  
  _Example_: `(?i)abc` matches `'ABC'`

- `(?m)` – Multi-line mode  
  _Example_: `^abc` matches start of each line

- `(?s)` – Dot matches newline  
  _Example_: `.` matches newline too

---

##  Expression Flags
*Set outside the pattern (e.g., in JavaScript: `/pattern/flags`).*

- `g` – Global match  
  _Example_: `/word/g` finds all occurrences

- `i` – Case insensitive  
  _Example_: `/abc/i` matches `'ABC'`

- `s` – Dot matches newline  
  _Example_: `/./s` matches newline

- `u` – Unicode support  
  _Example_: Properly matches emoji, etc.