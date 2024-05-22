# Lab report 4 - Vim (Week 7)

## Step 4:

(1) Screenshot:

![Untitled](https://lh3.googleusercontent.com/pw/AP1GczNyZ85lnm81tIld0GdoaXF3-oxuJSoql4a_m0DhiVVph7YefCsyEq2JjikwV3mRgl0oif-JMgQlV-JseT5sOn4zXnoMqA21-flU4KWw7tDweFlKp9oTSDOq6FKmGm4pKt0kSemPrvXkZOC-EM0zX60_=w1271-h831-s-no?authuser=0)

(2) Keys pressed: `<up><enter>`

(3) The `ssh aqho@ieng6@ucsd.edu` command was already in my history, so I could press the `<up>` key once to re enter it. I ran `ssh` + my user ID for the remote computer in the UCSD basement. I pressed `<enter>` to run the command. `ssh` stands for Secure Shell, which is used to do remote login and command-line execution like I am doing here. I am now connected to `ieng6` on this terminal, and I can now run terminal commands on the remote computer.

## Step 5:

(1) Screenshot: 

![Untitled](https://lh3.googleusercontent.com/pw/AP1GczOPQt1qMZu_lCsn4K7ekLaLj3d-Axa2RSk4ElXoTQyy1mtzTC-HA7dm--sR1fUcxWU22-lHPIVyO07up0EYR1z0DGAZjB1a4Tc0-I6bnj4XXkPKfJvkrtokxKOzxSBgve5NIAJMNVn7O9zXkJYSTEzy=w1271-h494-s-no?authuser=0)

(2) Keys pressed: `git clone <ctrl+v> <enter>`

(3) Prior to typing the git clone command into the terminal, I first went to the webpage of my fork of the repository and copied the ssh URL. Afterwards, I ran `git clone`, which creates a local copy of the remote repository onto your device. In this case, I am copying my fork of the repository onto the remote computer, ieng6. 

## Step 6:

(1) Screenshot: 

![Untitled](https://lh3.googleusercontent.com/pw/AP1GczOgXxG9Cn1ki6GLuM_WMSaTdyrrL3SWa3kWZKdlzGZk8_b8LUWglC4h9j2ihDayYZrRk4Bas1sOkqg5sHRuXus1U1j1WSfmiH8xaAg7xQ5-9_KqpAvy_pjb5DQC2qiira4ZtyNdasGnTL6WP3Y3ulEA=w1271-h1003-s-no?authuser=0)

(2) Keys pressed: `cd la<tab><enter> ls<enter> bash tes<tab><enter>`

(3) First, I ran `cd`, which changes the current directory to the one specified. In this case, I wanted to go to `lab7/`. This directory contains the cloned fork that I am working with. To make things easier, I typed `cd la<tab>` instead of `cd lab7/` because typing `<tab>` autofills the rest of the line to what the command line predicts I will type. In this case, it predicted correctly that I was trying to change my directory to `lab7/`.

Afterwards, I ran `ls<enter>`. `ls` lists all the files and directories in the working directory. I ran this command to make sure I knew what the name of the file that runs the test is.

Lastly, I ran `bash tes<tab>`. This command runs a bash file. I typed `tes<tab>` because the terminal will autofill the rest of the argument for my bash command to `test.sh`, which is the name of the file I am trying to run. I run the test and the output is the results of the test. According to the output, of the two tests run, one of them failed. It shows that the error occured on line 19 of `ListExamplesTests.java`, which stopped at line 42 from `ListExamples.java`. This means I should check `ListExamples.java` around line 42 to see where the bug is. 

## Step 7:

(1) Screenshot: 

![Untitled](https://lh3.googleusercontent.com/pw/AP1GczNj75INRDV3Wx9beSsxdIGWRYq4ZoDA69RDb125jfaBjaK2aHzX-4wuVUmRHmmNiVbJz544N1rWRGvPWzTC65ZqYL9IzPNMEvNhUS1s9hAqPzqE6NOhuBmRlNXs8zsQmeRATIG2kiOWeAVpDRTEiSmD=w1142-h122-s-no?authuser=0)

![Untitled](https://lh3.googleusercontent.com/pw/AP1GczOABXecDDAabcr2vGtpyu9Y3WvSMdzMazC1qdzpNvsh4gzRkaNCmynv20kpC1ocqzT5VA-c3CZ2z1zgIpGT7NmCDMcdoMT7IwhT08zSbpfwykYXdfc-ReoGy-N1Zb8EABiplTQmYXWIStmcpnJ4M4hr=w1271-h1193-s-no?authuser=0)

![Untitled](https://lh3.googleusercontent.com/pw/AP1GczM9jypQEcBOqXhrbQi7Hutlg8yQiqfvV4BCXPD-yAE3y8pKY8vZdTAfdeEFRx6WjDT8TEIjd1BIgpgjh7lL6tR-mkff6TNMdf_57d42I_8F69V-TDehhRspM0VO0tFkXP9Qf0Yx9vlhbbvob-go6btT=w1271-h451-s-no?authuser=0)

(2) Keys pressed: `vim Lis<tab>.java<enter> :set number<enter>20j20jjjj ^whhr2<esc> :wq<enter>`

(3) I am going to check `ListExamples.java` to try to find the bug that failed the test. First, I typed `vim Lis<tab>.java<enter>` to edit the [`ListExamples.java`](http://ListExamples.java) file using vim. I typed `<tab>` to autofill the rest of `ListExamples` using just `Lis`. 

Afterwards, I typed `:set number<enter>` to add numbers to the side of my vim viewer so I can more easily tell where to jump to in the file to make my edits. I type `20j` twice to hop a total of 40 lines down to see more of the file. 

At last, I see the line I have to change. There is a comment above line 44 indicating this is the line where there is a bug, and that I should change `index1` in this line to `index2`.

I type `jjj` to move another three lines down to land exactly on the line I need to edit and type `^` to move to the start of the first non-blank character of my line. I then type `w` to jump to the end of the word I am changing, `index1,` and type `hh` to move my cursor on top of the character `1` to change the incorrect variable `index1` to `index2`. My cursor is on top of the `1` in `index1`, so I type `r2` to replace `1` with `2` to get `index2`. 

I type `<esc>` to make sure I am still in command mode and then type `:wq` to save and quit editing the file.

## Step 8

(1) Screenshot: 

![Untitled](https://lh3.googleusercontent.com/pw/AP1GczMEoIZH3El63M4vNXa6LN--IWQDnz4NJCGmFf6Mlq6PMOrehe4-Wov-aJpcn9ooC0TDPvTlHYxoGqemDizR2gaaEdgwzSAQNnNySsI3o7sYJVbiEuLEz4-a20lBZu20Bw7miDtqpmgjxYbh1-v_kGPp=w858-h412-s-no?authuser=0)

(2) Key presses: `bash te<tab><enter>`

(3) To test the file again, I type `bash te<tab>`, with the tab to autofill `te` to `test.sh`. I then press `<enter>` to run the command, and the test runs are printed to the command line. The line `OK (2 tests)` indicates that both of my two tests ran successfully. 

## Step 9

(1) Screenshot: 

![Untitled](https://lh3.googleusercontent.com/pw/AP1GczNr-bB6zHKGAXlx-Dx9LAS9k82yApy51YU96iqClxMlzokDc_MCQtj_yrm9QvphUr25s8wZF8KcbSYPe-8eXMOalI-xf7Cqe9UGx2a1E61UECIhy037uThWMnFN8UJfiCiJThdyHIhiM-eBly4twWE8=w1155-h1330-s-no?authuser=0)

(2) Key presses: `git add * -f<enter>git commit -m "yippee fixed ListExamples.java"<enter>git push origin main<enter>`

(3) I typed `git add * -f` to stage all my files. They are now ready to be committed. I added `*` to stage all the new and untracked files, and I added `-f` to the end to make sure I still add the files that would be ignore by one of my `.gitignore` files. 

I then typed `git commit -m` and then the message I wanted to include with my commit. In this case, the message was `“yippee fixed ListExamples.java”`. `git commit` creates a save point of my repository, and `-m` adds a message to indicate what was changed in that save point.

Lastly, I typed `git push origin main`. This pushes my changes to the main branch of my fork of the repository. In other words, the fork I created of the remote repository is now updated to what I have changed just now.
