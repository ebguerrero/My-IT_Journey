# Linux Commands Notes
**Date:** 11/27/2025

---

## 📝 nano
**Purpose:** Edit text files directly from the command line.

**Usage:**
```bash
nano myfile.txt
````

---

## 📦 du — Disk Usage

*(du --help, man du)*

**Purpose:**
`du` (disk usage) shows how much space files and directories consume on disk.
By default, `du`:

* shows size in **kilobytes (KB)**
* lists **directories only** (not files)
* walks recursively through subdirectories

---

### 🔧 Flags

| Flag       | Description                                           |
| ---------- | ----------------------------------------------------- |
| `-a`       | List **all files and directories**, not just folders  |
| `-h`       | Human-readable sizes (1K, 4M, 2G)                     |
| `-c`       | Show a **grand total** at the end                     |
| `-d <num>` | Limit directory depth (e.g., `-d 1` = top-level only) |
| `--time`   | Show last modification timestamp                      |

---

### 🧪 Examples

#### List every file inside /home with its size:

```bash
du -a /home/
```

#### Filter results using grep (example: match "user"):

```bash
du -a /home/ | grep user
```

#### Human-readable units:

```bash
du -h /var/log
```

#### Show directory sizes up to depth 2:

```bash
du -h -d 2 /etc
```

#### Show modification timestamps (depth 1):

```bash
du --time -d 1 .
```

---

### 📘 Output Example

Running:

```bash
du ./Documents
```

You may see:

```
3409    ./Documents
9182    ./Downloads
```

Each line shows:

* size
* path
* **sizes represent disk blocks unless `-h` is used**

---

## 🔍 grep — Pattern Searching

*(grep --help, man grep)*

**Purpose:**
`grep` searches text for matching patterns. It is used to quickly extract relevant lines from files, outputs, and directories.

---

### 🔧 Flags

| Flag | Description                                     |
| ---- | ----------------------------------------------- |
| `-i` | Case-insensitive search                         |
| `-v` | Invert match (show lines *without* the pattern) |
| `-n` | Show line numbers for matches                   |
| `-R` | Recursive search through directories            |

---

### 🧪 Examples

#### Search for the word "error" in a file:

```bash
grep "error" logfile.txt
```

#### Case-insensitive search:

```bash
grep -i "error" logfile.txt
```

#### Recursive search in current directory:

```bash
grep -R "example_word" .
```

#### Search a specific directory and subdirectories:

```bash
grep -R "error_code" /var/log
```

#### Combine flags: recursive + case-insensitive:

```bash
grep -Ri "search_term" /home/user/documents
```

---

## 📘 Bonus: Check file owner and metadata

Use `stat` when you need owner, permissions, timestamps, or inode details:

```bash
stat filename.txt
```
Absolutely — this is a **great lesson to formalize properly** because your original text mixes good info with confusing wording. I’ll do **two things**:

1. ✅ **Teach / clarify the concepts in plain English**
2. ✅ **Convert the lesson into a clean, GitHub-ready Markdown file**, consistent with the style of your other notes.

---

---

## 🔎 What is `grep`?

`grep` is a Linux tool that **searches text** and prints only the lines that match a pattern.

Think of it as:

> **Filter everything → show only what matches**

Basic example:

```bash
grep "error" logfile.txt
```

Meaning:

* Look inside `logfile.txt`
* Find lines containing `"error"`
* Print those lines only

---

---

## 🌳 The Grep Family — `grep`, `egrep`, `fgrep`

There are **three related tools**:

| Tool    | Purpose                                               |
| ------- | ----------------------------------------------------- |
| `grep`  | Default tool – basic regex                            |
| `egrep` | Uses **extended regex**                               |
| `fgrep` | Searches for **literal text only** (no regex symbols) |

But today:

> `egrep` and `fgrep` are **deprecated aliases** for special `grep` modes.

Instead of using them, we now use:

```bash
grep -E   # extended regex mode (same as egrep)
grep -F   # fixed-string mode (same as fgrep)
```

---

### ✅ Equivalent Commands

| Old Way                | New Way                  |
| ---------------------- | ------------------------ |
| `egrep "pattern" file` | `grep -E "pattern" file` |
| `fgrep "text" file`    | `grep -F "text" file`    |

---

---

## ✨ The Modes Explained

---

### 🔹 Normal `grep` (BRE = Basic Regex)

This is the default.

* Simple matching:

  * words
  * basic regex wildcards

Example:

```bash
grep "sun" poem.txt
```

---

---

### 🔹 `grep -E` (ERE = Extended Regex)

This lets you use **full regex syntax**:

* `+` (one or more)
* `?` (optional)
* `|` (OR logic)
* grouping `( )`

Example:

```bash
grep -E "(sun|moon)" poem.txt
```

Matches lines containing:

* sun
* moon

Without `-E`, this would **not work** unless you heavily escaped characters.

---

---

### 🔹 `grep -F` (Fixed String Search)

This searches for **literal text only** — regex symbols are ignored.

Example:

```bash
grep -F "hello.*world" file.txt
```

This looks for the **exact string**:

```
hello.*world
```

It DOES NOT treat `.*` as wildcards.

---

✅ Use `grep -F` when:

* Searching large logs quickly
* You want **zero regex interpretation**
* You're matching known strings (IPs, hashes, filenames)

---

---

---

## 🧠 Summary of Regex Modes

| Mode      | Regex Allowed? | Use Case                |
| --------- | -------------- | ----------------------- |
| `grep`    | Basic regex    | Simple string matching  |
| `grep -E` | Extended regex | Complex regex filtering |
| `grep -F` | ❌ No regex     | Literal fast searching  |

---

---

---

## 🏷️ Important Grep Flags Explained

| Flag | Description                                |
| ---- | ------------------------------------------ |
| `-R` | Search **recursively** through directories |
| `-h` | Hide filename prefixes                     |
| `-c` | Show **count only** (not matches)          |
| `-i` | Ignore case                                |
| `-l` | Show filenames only                        |
| `-n` | Show line numbers                          |
| `-v` | Invert match (show non-matching lines)     |
| `-E` | Enable **extended regex**                  |
| `-F` | Enable **fixed (literal) search**          |
| `-e` | Specify **multiple patterns**              |

---

---

### 🔹 `-e` vs `-E` (COMMON CONFUSION)

---

#### ✅ `-e` → Multiple patterns

Use when you want to match **more than one pattern**:

```bash
grep -e "error" -e "fail" logfile.txt
```

This matches lines containing:

* `error`
* OR `fail`

---

#### ✅ `-E` → Extended Regex

Use when your **single pattern uses advanced regex syntax**

```bash
grep -E "(error|fail)" logfile.txt
```

This does the same thing — but uses REGEX grouping instead of multiple flags.

---

### ✅ The Real Difference

| Feature    | `-e`              | `-E`                  |
| ---------- | ----------------- | --------------------- |
| Purpose    | Multiple patterns | Enable advanced regex |
| Use count  | Yes, repeatable   | No need to repeat     |
| Regex type | BRE               | ERE                   |

---

---

---

## 📌 BRE vs ERE (Simple Explanation)

| Type    | Meaning                                                |                                      |
| ------- | ------------------------------------------------------ | ------------------------------------ |
| **BRE** | Basic Regular Expressions — limited syntax             |                                      |
| **ERE** | Extended Regular Expressions — modern regex with OR (` | `), repetition (`+`), grouping `( )` |

---

### Examples

#### Basic regex

```bash
grep "sun" poem.txt
```

---

#### Extended regex

```bash
grep -E "^s.*n$" poem.txt
```

Matches any word:

* starting with `s`
* ending with `n`

Examples:

* sun
* sandston
* shin

---

---

---

# ✅ PART 2 — **READY-TO-USE MARKDOWN FILE**

---

## **`Grep_Egrep_Fgrep.md`**

Copy/Paste into your repo:

````md
# 🔎 Grep, Egrep, and Fgrep Notes

---

## 🧠 Introduction

`grep` is a Linux filtering tool used to search files or command output for specific patterns and return only matching lines.

```bash
grep "PATTERN" file.txt
````

---

---

## 🌳 The Grep Family

Historically there were 3 tools:

| Tool      | Function               |
| --------- | ---------------------- |
| **grep**  | Basic pattern matching |
| **egrep** | Extended regex         |
| **fgrep** | Fixed-string search    |

---

### ✅ Modern Usage

Today they are replaced by flags:

```bash
grep -E   # same as egrep
grep -F   # same as fgrep
```

---

---

## 🔍 Modes of Searching

### 🔹 Basic Grep (BRE)

```bash
grep "sun" poem.txt
```

Matches basic strings and simple regex.

---

### 🔹 Extended Regex Mode

```bash
grep -E "(sun|moon)" poem.txt
```

Allows:

* Grouping `( )`
* OR `|`
* Optional `?`
* One-or-more `+`

---

---

### 🔹 Fixed String Mode

```bash
grep -F "hello.*world" file.txt
```

Treats everything literally — no regex interpretation.

---

---

## ✅ Summary Table

| Mode      | Regex Allowed | When To Use             |
| --------- | ------------- | ----------------------- |
| `grep`    | ✅ Basic       | Simple string filtering |
| `grep -E` | ✅ Extended    | Complex regex           |
| `grep -F` | ❌ None        | Fast literal searches   |

---

---

## 🚩 Important Flags

| Flag | Description                |
| ---- | -------------------------- |
| `-R` | Recursive directory search |
| `-h` | Suppress filename output   |
| `-c` | Count matching lines only  |
| `-i` | Ignore case                |
| `-l` | Show only filenames        |
| `-n` | Add line numbers           |
| `-v` | Invert match               |
| `-E` | Enable extended regex      |
| `-F` | Literal-only search        |
| `-e` | Multiple search patterns   |

---

---

## ⚔️ `-e` vs `-E`

---

#### Multiple Patterns (`-e`)

```bash
grep -e "error" -e "fail" logfile.txt
```

---

#### Extended Regex (`-E`)

```bash
grep -E "(error|fail)" logfile.txt
```

---

## 📘 Regex Types

| Type | Meaning                      |
| ---- | ---------------------------- |
| BRE  | Basic regular expressions    |
| ERE  | Extended regular expressions |

---

### BRE Example

```bash
grep "sun" poem.txt
```

---

### ERE Example

```bash
grep -E "^s.*n$" poem.txt
```

Matches words starting with `s` and ending with `n`.

---

---

## ✅ Final Notes

* Use `grep -F` when searching for literal strings fast.
* Use `grep -E` when doing complex pattern matching.
* Use `-e` if matching more than one pattern at once.

---
