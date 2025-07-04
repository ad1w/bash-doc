# bash-tips
some tips on bash shell. Just a personal documentation

## remove  character
```
sed 's/character //'
```
for example:
```
~ $ cat text.txt
Cantarel Bold 14

to get "Cantarel 14" you can use:
~ $ cat text.txt | sed 's/Bold //'
Cantarel 14
```

## get character separated by something
```
cut -d 'something' -f column
```
for example:
```
~ $ cat text.txt
gtk-font-name=Cantarel, 14

to get "Cantarel, 14" you can use:
~ $ cat text.txt | cut -d '=' -f 2
Cantarel, 14
```

## get characters on a specific line
```
awk 'NR==linenumber'
```
for example:
```
~ $ cat text.txt
ABCD
EFGH
IJKL

to get "EFGH" you can use:
~ $ cat text.txt | awk 'NR==2'
EFGH
```

## get characters on a specific column
```
awk '{print $numbercolumn}'
```
for example:
```
~ $ cat text.txt
ABCD EFGH IJKL

to get "EFGH" you can use:
~ $ cat text.txt | awk '{print $2}'
EFGH
```

## add file or directory on bash script
```
export PATH="${PATH}:/location"
```
for example:
you want to add some files on your script directory, you can add this line in your bash script
```
#!/bin/bash
export PATH="${PATH}:/script"
```
