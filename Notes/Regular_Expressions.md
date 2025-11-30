

# ✅ **`Regular_Expressions.md`**

````md
# 🔍 Regular Expressions (Regex) Notes

---

## 🧠 Introduction

### What are Regular Expressions?
Regular expressions (Regex) are **text patterns** used to search, match, and manipulate strings. They allow you to locate text based on **patterns**, not just exact words.

---

### Why Learn Regex?

- Saves **time** searching through large datasets and logs
- Essential knowledge for **CTFs**
- Improves your pattern recognition skills
- Useful for scripting and development

---

### Testing Regex

There are two primary ways to test patterns:

#### ✅ Linux Method
```bash
egrep "<pattern>" <filename>
````

#### ✅ Online Editor

Use [https://regexr.com](https://regexr.com)

* Paste text in **Text** field
* Enter patterns in **Expression** field
* Live highlighting shows matches

✅ Recommended: **Online editor for practice**

---

---

## 🧩 Character Sets

Character sets use **square brackets `[ ]`** to match **one character from a group or range.**

### Examples

```regex
[abc]
```

Matches `a`, `b`, or `c`.

```regex
[abc]zz
```

Matches: `azz`, `bzz`, `czz`.

```regex
[a-c]zz
```

Matches the same as above using a range.

```regex
[a-cx-z]zz
```

Matches: `azz`, `bzz`, `czz`, `xzz`, `yzz`, `zzz`.

---

### Letters

```regex
[a-zA-Z]
```

Matches **any letter**, uppercase or lowercase.

---

### Numbers

```regex
file[1-3]
```

Matches: `file1`, `file2`, `file3`.

---

### Excluding Characters

Exclude matches with the **caret `^`** inside brackets:

```regex
[^k]ing
```

Matches anything ending in `ing` **except** `king`.

```regex
[^a-c]at
```

Matches `fat`, `hat` (not `bat` or `cat`).

---

### ⚠️ Notes on Charsets

* `[abc]` matches only **one character at a time**, not the full string `"abc"`.
* Answers should be:

  * **Specific** when narrow matching is required.
  * **General** when broader matching is simpler.

---

---

## ✅ Pop Quiz — Character Sets

| Goal                             | Regex          |
| -------------------------------- | -------------- |
| Match `c`, `o`, `g`              | `[cog]`        |
| Match `cat`, `fat`, `hat`        | `[cfh]at`      |
| Match `Cat`, `cat`, `Hat`, `hat` | `[CcHh]at`     |
| Match filenames                  | `[Ff]ile[1-9]` |
| Exclude `File7`                  | `[Ff]ile[^7]`  |

---

---

## 🌟 Wildcards & Optional Characters

### Wildcard

`.` matches **any single character**.

```regex
a.c
```

Matches `aac`, `a0c`, `a!c`.

---

### Optional Character

```regex
abc?
```

Matches `ab` and `abc`.

---

### Escaping Characters

Use `\` to escape special characters.

```regex
a\.c
```

Matches **only** `a.c`, not `abc`.

---

### ✅ Pop Quiz — Wildcards

| Goal                                       | Regex           |
| ------------------------------------------ | --------------- |
| `Cat`, `fat`, `hat`, `rat`                 | `.at`           |
| `Cat`, `cats`                              | `[Cc]ats?`      |
| Match `cat.xyz`                            | `cat\.xyz`      |
| Match `cat.xyz`, `cats.xyz`, `hats.xyz`    | `[ch]ats?\.xyz` |
| 4 chars not ending in n-z                  | `...[^n-z]`     |
| Match `bat`, `bats`, `hat`, `hats` not rat | `[^r]ats?`      |

---

---

## 🔠 Metacharacters

| Symbol | Meaning                   |
| ------ | ------------------------- |
| `\d`   | digit                     |
| `\D`   | non-digit                 |
| `\w`   | alphanumeric + underscore |
| `\W`   | non-alphanumeric          |
| `\s`   | whitespace                |
| `\S`   | non-whitespace            |

✅ `_` is included in `\w`

---

---

## 🔁 Repetition

| Operator | Meaning    |
| -------- | ---------- |
| `{12}`   | exactly 12 |
| `{1,5}`  | 1–5        |
| `{2,}`   | 2 or more  |
| `*`      | 0 or more  |
| `+`      | 1 or more  |

---

### ✅ Pop Quiz — Repetition

| Goal                                | Regex               |
| ----------------------------------- | ------------------- |
| `catssss`                           | `cats{4}`           |
| `Cat`, `cats`, `catsss`             | `[Cc]ats*`          |
| `regex go br`, `regex go brrrrrr`   | `regex go br+`      |
| Match filenames                     | `[abc]{1,3}[01]{4}` |
| `File01, File2, file12`             | `[Ff]ile\d{1,2}`    |
| `kali tools`, `kali    tools`       | `kali\s+tools`      |
| `notes~, stuff@`                    | `\w{5}\W`           |
| Match quoted text                   | `\S*\s*\S*`         |
| Any 9-char string not ending in `!` | `\S{8}[^!]`         |
| `.bash_rc`, long filename, note1    | `\.?\w+`            |

---

---

## 🔗 Anchors, Groups & OR Logic

### Line Anchors

| Symbol | Meaning       |
| ------ | ------------- |
| `^`    | start of line |
| `$`    | end of line   |

```regex
^abc    # starts with abc
xyz$    # ends with xyz
```

---

### Groups

Groups use **parentheses `( )`**:

```regex
(day|night)
```

Matches either `day` or `night`.

---

### Repeating Groups

```regex
(no){5}
```

Matches `nonononono`.

---

---

## ✅ Pop Quiz — Advanced

| Goal                            | Regex                   |       |
| ------------------------------- | ----------------------- | ----- |
| Password + 10 chars excluding 0 | `Password:[^0]{10}`     |       |
| Match username start            | `^username:\s`          |       |
| Line doesn't start w/ digit     | `^\D`                   |       |
| End-of-line match `EOF$`        | `EOF\$$`                |       |
| Match editor preference         | `I use (nano            | vim)` |
| Dollar lines                    | `\$\d\$\S+`             |       |
| Match IPv4                      | `(\d{1,3}\.){3}\d{1,3}` |       |
| Extract emails                  | `(\w+)@(\w+)\.com`      |       |

---

---

## ✅ Conclusion

Regular expressions are:

* Extremely powerful
* Highly practical in security and development
* Best learned through **practice and repetition**

Always remember:

> **Be precise — but not overly complex.**

When matching common formats (emails, URLs, IP addresses), reuse trusted expressions rather than reinventing them.

---

