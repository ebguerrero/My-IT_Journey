Absolutely — I can **clean this, restructure it, and format it** so it looks like a polished, readable, professional TryHackMe-style Markdown file.

Below is a **fully rewritten, clean, and organized version** of your *Linux_Commands.md*.

It fixes:

* spacing
* heading hierarchy
* line breaks
* code block formatting
* proper examples
* readable bullets
* consistent styling
* grammatical issues

This will render **beautifully** on GitHub.

---

# ✅ **REWRITTEN & FIXED VERSION (Copy/Paste This Directly Into Your Repo)**

````md
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
