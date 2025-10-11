# Data Manipulation

This module covers common data-processing utilities (`tr`, `head`, `cut`, `sort`) and shows how to manipulate piped input, delete characters, remove newlines, extract lines or fields, and sort data.

---

## Translating Characters

**Flag**

```
pwn.college{s2yVGXntaAg6lciXVdb7f0GIazW.01MxEzNxwSNxIzNzEzW}
```

**Solution / Terminal session**

```bash
hacker@data~translating-characters:~$ /challenge/run | tr 'A-Za-z' 'a-zA-Z'
yOUR CASE-SWAPPED FLAG:
pwn.college{s2yVGXntaAg6lciXVdb7f0GIazW.01MxEzNxwSNxIzNzEzW}
```

**What I learned**

* `tr` translates character sets; here it swaps letter case.

**Reference**

* pwn.college

---

## Deleting Characters

**Flag**

```
pwn.college{84upJ7B4UP47rON8sErFZfnUZk9.0FNxEzNxwSNxIzNzEzW}
```

**Solution / Terminal session**

```bash
hacker@data~deleting-characters:~$ /challenge/run | tr -d '^%'
Your character-stuffed flag:
pwn.college{84upJ7B4UP47rON8sErFZfnUZk9.0FNxEzNxwSNxIzNzEzW}
```

**What I learned**

* `tr -d` deletes characters from the input stream.

**Reference**

* pwn.college

---

## Deleting Newlines

**Flag**

```
pwn.college{UVVIag3lKnUaBw6cH74zGXximEF.0VNxEzNxwSNxIzNzEzW}
```

**Solution / Terminal session**

```bash
hacker@data~deleting-newlines:~$ /challenge/run | tr -d '\n'
Your line-split flag: pwn.college{UVVIag3lKnUaBw6cH74zGXximEF.0VNxEzNxwSNxIzNzEzW}hacker@data~deleting-newlines:~$
```

**What I learned**

* Use `tr -d '\n'` to join multiple lines into a single line.

**Reference**

* pwn.college

---

## Extracting The First Lines With Head

**Flag**

```
pwn.college{4tthFM2Az-veZgWAuFWUO79SY4E.0lNxEzNxwSNxIzNzEzW}
```

**Solution / Terminal session**

```bash
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{4tthFM2Az-veZgWAuFWUO79SY4E.0lNxEzNxwSNxIzNzEzW}
```

**What I learned**

* `head -n N` prints the first N lines of its input; useful to limit verbose output.

**Reference**

* pwn.college

---

## Extracting Specific Sections Of Text

**Flag**

```
pwn.college{4eqhztpROS62uuX0COr4VshaIcQ.01NxEzNxwSNxIzNzEzW}
```

**Solution / Terminal session**

```bash
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d ' ' -f 2 | tr -d '\n'
pwn.college{4eqhztpROS62uuX0COr4VshaIcQ.01NxEzNxwSNxIzNzEzW}hacker@data~extracting-specific-sections-of-text:~$
```

**What I learned**

* `cut -d 'DELIM' -f N` extracts the Nth field using DELIM as separator. Combine with `tr -d '\n'` to join characters into one line.

**Reference**

* pwn.college

---

## Sorting Data

**Flag**

```
pwn.college{oUarL6F1ED5xZXqscCu-l3Tyehb.0FM0MDOxwSNxIzNzEzW}
```

**Solution / Terminal session**

```bash
hacker@data~sorting-data:~$ sort /challenge/flags.txt | tail -n 1
pwn.college{oUarL6F1ED5xZXqscCu-l3Tyehb.0FM0MDOxwSNxIzNzEzW}
```

**What I learned**

* `sort` orders lines lexicographically; combine with `head`/`tail` to choose extremes.

**Reference**

* pwn.college

---

