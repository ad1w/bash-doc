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
you want to add some files on your <i>script</i> directory, you can add this line in your bash script
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
for example, you can create a new file (ex: text.txt) then you add this line:
```
#!/bin/bash
cat <<EOF
Hello World
EOF

then if you run, the result will be:
~ $ bash text.txt
Hello World
```

## add the colors
```
tput setaf <0-15>
```
for example, you can create a new file (ex: text.txt) then you add this line:
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

then if you run, the result will be:
~ $ bash text.txt
Hello World (with red color)
```
