# BASH tips
Some tips on bash shell. Just a personal documentation

## Remove  character
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

## Get character separated by something
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

## Get characters on a specific line
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

## Get characters on a specific column
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

## Add file or directory on bash script
```
export PATH="${PATH}:/location"
```
for example:
you want to add some files on your ```script``` directory, you can add this line in your bash script
```
#!/bin/bash
export PATH="${PATH}:/script"
```

## Print character on bash script
```
#!/bin/bash
cat <<EOF
character
EOF
```
for example, you can create a new file ```text.txt``` then you add this line:
```
#!/bin/bash
cat <<EOF
Hello World
EOF
```
then if you run, the result will be:
```
~ $ bash text.txt
Hello World
```

## Add the colors
```
tput setaf <0-15>
```
for example, you can create a new file ```text.txt``` then you add this line:
```
#!/bin/bash
# Add colors
#normal
bla=$(tput setaf 0)
red=$(tput setaf 1)
gre=$(tput setaf 2)
yel=$(tput setaf 3)
blu=$(tput setaf 4)
mag=$(tput setaf 5)
cya=$(tput setaf 6)
whi=$(tput setaf 7)
#bright
bbla=$(tput setaf 8)
bred=$(tput setaf 9)
bgre=$(tput setaf 10)
byel=$(tput setaf 11)
bblu=$(tput setaf 12)
bmag=$(tput setaf 13)
bcya=$(tput setaf 14)
bwhi=$(tput setaf 15)

# Print result
cat <<EOF
$redHello World
EOF
```
then if you run, the result will be:
```
~ $ bash text.txt
Hello World (with red color)
```

## Add value option on bash
```
if [[ $1 = "value" ]]; then
  action
else
  action
fi
```
for example, in your ```text.txt``` you can add this line:
```
#!/bin/bash
val_1=Hello World
val_2=Hello There

if [[ $1 = "-1" ]]; then
  echo "$(val_1)"
else
  echo "$(val_2)"
fi
```
then if you run with "-1", the result will be:
```
~ $ bash text.txt -1
Hello World
```
if you run without "-1", the result will be:
```
~ $ bash text.txt
Hello There
```

## Add value option (number) on bash
```
if [[ $1 =~ ^[0-9]+$ ]]; then
  action
else
  action
fi
```
for example, in your ```text.txt``` you can add this line:
```
#!/bin/bash

if [[ $1 =~ ^[0-9]+$ ]]; then
  echo "the value is" $1
else
  echo "the value is -"  
fi
```
then if you run with "number", the result will be:
```
~ $ bash text.txt 9379
the value is 9379
```
if you run with "character", the result will be:
```
~ $ bash text.txt abcd
the value is -
```

## Arithmetic operations
```
eq=$(($1+$2))
echo $1 + $2 = $eq
```
for example, in your ```test.txt``` you can add this line:
```
#!/bin/bash

eq=$(($1+$2))
echo $1 + $2 = $eq
```
then if you run, the result will be:
```
~ $ bash test.txt 10 7
10 + 7 = 17
```
