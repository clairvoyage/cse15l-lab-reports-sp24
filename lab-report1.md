# Lab report 1
### `cd`
- no arguments:
```
  merlin@Merlins-MacBook-Air lecture1 % cd
  merlin@Merlins-MacBook-Air ~ % 
```
absolute path: `/Users/merlin/Documents/coding/CSE15L/lecture1`
explanation: Without an argument, cd changes the working directory to the home directory.
error? No

- directory as argument:
```
  merlin@Merlins-MacBook-Air lecture1 % cd messages/
  merlin@Merlins-MacBook-Air messages % 
```
absolute path: `/Users/merlin/Documents/coding/CSE15L/lecture1`
explanation: Changed working directory to lecture1/messages.
error? No

- path to file as argument:
```
  merlin@Merlins-MacBook-Air messages % cd en-us.txt 
  cd: not a directory: en-us.txt
```
absolute path: `/Users/merlin/Documents/coding/CSE15L/lecture1/messages`
explanation: `cd` only changes to directories, not files.
error? Yes, `cd` cannot change working directory to a file.

### `ls`
- no arguments:
```
  merlin@Merlins-MacBook-Air lecture1 % ls
  Hello.class     Hello.java      README          messages
```
absolute path: `/Users/merlin/Documents/coding/CSE15L/lecture1`
explanation: Listed all files and directories in lecture1
error? No

- directory as argument:
```
  merlin@Merlins-MacBook-Air lecture1 % ls messages/
  en-us.txt       es-mx.txt       zh-cn.txt
```
absolute path: `/Users/merlin/Documents/coding/CSE15L/lecture1`
explanation: Listed all files and directories in lecture1/messages
error? No

- path to file as argument:
```
  merlin@Merlins-MacBook-Air lecture1 % ls messages/en-us.txt
  messages/en-us.txt
```
absolute path: `/Users/merlin/Documents/coding/CSE15L/lecture1`
explanation: Listed file's relative path.
error? No

### `cat`
- no arguments:
```
  merlin@Merlins-MacBook-Air lecture1 % cat
  silly
  silly
```
absolute path: `/Users/merlin/Documents/coding/CSE15L/lecture1`
explanation: `cat` prints the contents of a file. Without a file as an argument, it copies what you typed into the terminal until you exit the command.
error? No

- directory as argument:
```
  merlin@Merlins-MacBook-Air lecture1 % cat messages/
  cat: messages/: Is a directory
```
absolute path: `/Users/merlin/Documents/coding/CSE15L/lecture1`
explanation: Only prints file contents, not a directory
error? Yes, `cat` only works to edit files.

- path to file as argument:
```
  merlin@Merlins-MacBook-Air lecture1 % cat messages/en-us.txt
  Hello World!
```
absolute path: `/Users/merlin/Documents/coding/CSE15L/lecture1`
explanation: Printed contents of en-us.txt.
error? No

