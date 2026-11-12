## OverTheWire Bandit Levels

## LEVEL 0

First level! So we all know how to ssh something in the default port 22, but what about custom port? we can use -p, which stands for port! and the rest are like the default command!

ssh -p [port number] user@ip/domain

![alt text](<Level 0.png>)

## Level 0 -> 1

This was easy. There is a file named readme in home directory. We need to read it. so we can use ls to see the file first, then use cat to see the content of the file.

cat readme

![alt text](<Level 0 - 1.png>)

Password: 6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR

## Level 1 -> 2

For file name such as hyphen (-), cat it doesnt work. We can use ./ before it, where . (dot) means current directory.

cat ./-

![alt text](<Level 1 - 2.png>)

Password: PK8fYLZg2hnHSz83plBL1iEPKdD3QToB

## Level 2 -> 3

When file names have space in them, it needs the \ (backslash) before it. Because lets say the file name is "file have space.txt". If we cat it, it will think there is three things, file, have and space.txt, so we need \ before space to say, it is a space.

cat ./--spaces\ in\ this\ filename--

![alt text](<Level 2 - 3.png>)

Password: 7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME

## Level 3 -> 4

Many files can be hidden in linux. To find them we can use ls with -a option, which show every files, hidden and non hidden one.

ls -la

![alt text](<Level 3 - 4.png>)

Password: xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq

## Level 4 -> 5

Many files can be binary, which cant be read normally. In this problem, out of 9 files, 1 file is only human readable. For finding the readable file, I just bruteforced it, with using cat to all files.

![alt text](<Level 4 - 5.png>)

Password: 6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG

## Level 5 -> 6

To effectivly find files, we can use the find command, with several options. find command wants a path, here ./ means current directory. -type helps finding file or directory, -type f means file. -size can help finding specific or in a certain range. Here -size 1033c means 1033 byte. ! -executable means not executable.

find ./ -type f -size 1033c ! -executable

![alt text](<Level 5 - 6.png>)

Password: pXa26xhMWaC2SvDotA4r9EgZkulOeSBW

## Level 6 -> 7

To find files from anywhere, we need to use only / . Then it will match the conditions and find every directory with /. Also we can find files with specific user and group using -user and -group.

find / -user bandit7 -group bandit6 -size 33c

![alt text](<Level 6 - 7 .1.png>)
![alt text](<Level 6 - 7 .2.png>)

Password: Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3

## Level 7 -> 8

We can find something in file using grep command. As the password is next to a word, we can use the grep command with the word.

cat data.txt | grep "millionth"

![alt text](<Level 7 - 8.png>)

Password: VR1ljMayciFxbnUokuQmJFw6QC9VKtub

## Level 8 -> 9

When texts are repeated many times, and we have to find unique text, we need to sort the files first. After that, we can use unique command with -u to find the unique text.

sort data.txt | uniq -u

![alt text](<Level 8 - 9.png>)

Password: EjmOSvuAu7sGAHqHVcBDPirRe9T03kxl

## Level 9 -> 10

In binary file, we can read the data section with strings -d. Now if charcters have a pattern, and we want to find any pattern that matches it, we can use grep with -E, which find any extended pattern it is given.

strings -d data.txt | grep -E ==

![alt text](<Level 9 - 10.png>)

Password: B0s2khmbT9u0geKuOoVGW3JZKhndE3BG

## Level 10 -> 11

Many text can be in base64. We can decode these to find out actual texts. To decode the base64, we can use base64 -d

cat data.txt | base64 -d

![alt text](<Level 10- 11.png>)

Password: pYfOY6HwUsDj5rL9UvyhU7MCmv8vN5Ro

## Level 11 -> 12
