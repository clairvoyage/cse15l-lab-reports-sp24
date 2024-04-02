# Lab report 1
### `cd`
- no arguments:
```
  merlin@Merlins-MacBook-Air lecture1 % cd
  merlin@Merlins-MacBook-Air ~ % 
```
- directory as argument:
```
  merlin@Merlins-MacBook-Air lecture1 % cd messages/
  merlin@Merlins-MacBook-Air messages % 
```
- path to file as argument:
```
  merlin@Merlins-MacBook-Air messages % cd en-us.txt 
  cd: not a directory: en-us.txt
```

### `ls`
- no arguments:
```
  merlin@Merlins-MacBook-Air lecture1 % ls
  Hello.class     Hello.java      README          messages
```
- directory as argument:
```
  merlin@Merlins-MacBook-Air lecture1 % ls messages/
  en-us.txt       es-mx.txt       zh-cn.txt
```
- path to file as argument:
```
  merlin@Merlins-MacBook-Air lecture1 % ls messages/en-us.txt
  messages/en-us.txt
```

### `cat`
- no arguments:
```
  merlin@Merlins-MacBook-Air lecture1 % cat
  
  
  ^C
```
- directory as argument:
```
  merlin@Merlins-MacBook-Air lecture1 % cat messages/
  cat: messages/: Is a directory
```
- path to file as argument:
```
  merlin@Merlins-MacBook-Air lecture1 % cat messages/en-us.txt
  Hello World!
```
