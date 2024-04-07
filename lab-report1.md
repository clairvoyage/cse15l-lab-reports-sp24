# Lab report 1
## `cd`
### no arguments:
```
  merlin@Merlins-MacBook-Air lecture1 % cd
  merlin@Merlins-MacBook-Air ~ % 
```
**Absolute Path:** `/Users/merlin/Documents/coding/CSE15L/lecture1`

**Explanation:** Without an argument, `cd` changes the working directory to the home directory.

**Error?** No

---

### directory as argument:
```
  merlin@Merlins-MacBook-Air lecture1 % cd messages/
  merlin@Merlins-MacBook-Air messages % 
```
**Absolute Path:** `/Users/merlin/Documents/coding/CSE15L/lecture1`

**Explanation:** `cd messages/` changed the working directory to `lecture1/messages`.

**Error?** No

---

### path to file as argument:
```
  merlin@Merlins-MacBook-Air messages % cd en-us.txt 
  cd: not a directory: en-us.txt
```
**Absolute Path:** `/Users/merlin/Documents/coding/CSE15L/lecture1/messages`

**Explanation:** `cd` only changes to directories, not files.

**Error?** Yes, `cd` cannot change working directory to a file.


## `ls`
### no arguments:
```
  merlin@Merlins-MacBook-Air lecture1 % ls
  Hello.class     Hello.java      README          messages
```
**Absolute Path:** `/Users/merlin/Documents/coding/CSE15L/lecture1`

**Explanation:** `ls` listed all files and directories in `lecture1`

**Error?** No

---

### directory as argument:
```
  merlin@Merlins-MacBook-Air lecture1 % ls messages/
  en-us.txt       es-mx.txt       zh-cn.txt
```
**Absolute Path:** `/Users/merlin/Documents/coding/CSE15L/lecture1`

**Explanation:** `ls messages` listed all files and directories in `lecture1/messages`

**Error?** No

---

### path to file as argument:
```
  merlin@Merlins-MacBook-Air lecture1 % ls messages/en-us.txt
  messages/en-us.txt
```
**Absolute Path:** `/Users/merlin/Documents/coding/CSE15L/lecture1`

**Explanation:** `ls messages/en-us.txt` printed the entered path for `en-us.txt`.

**Error?** No

## `cat`
### no arguments:
```
  merlin@Merlins-MacBook-Air lecture1 % cat
  silly
  silly
```
**Absolute Path:** `/Users/merlin/Documents/coding/CSE15L/lecture1`

**Explanation:** `cat` prints the contents of a file. Without a file as an argument, it copies 
what you typed into the terminal until you exit the command.

**Error?** No

---

### directory as argument:
```
  merlin@Merlins-MacBook-Air lecture1 % cat messages/
  cat: messages/: Is a directory
```
**Absolute Path:** `/Users/merlin/Documents/coding/CSE15L/lecture1`

**Explanation:** `cat` only prints file contents, not a directory.

**Error?** Yes, `cat` only works to edit files.

---

### path to file as argument:
```
  merlin@Merlins-MacBook-Air lecture1 % cat messages/en-us.txt
  Hello World!
```
**Absolute Path:** `/Users/merlin/Documents/coding/CSE15L/lecture1`

**Explanation:** `cat` printed the contents of `en-us.txt`.

**Error?** No

