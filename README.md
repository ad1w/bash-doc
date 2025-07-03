# bash-tips
some tips on bash shell. Just a personal documentation

## remove  character
```
~ $ sed 's/character //'
```
for example:
```
~ $ Cantarel Bold 14

to get "Cantarel 14" you can use:
~ $ sed 's/Bold //'

the result will be:
~ $ Cantarel 14
```
## get character separated by something
```
~ $ cut -d 'something' -f column
```
for example:
```
~ $ gtk-font-name=Cantarel, 14

to get "Cantarel, 14" you can use:
~ $ cut -d '=' -f 2

the result will be:
~ $ Cantarel, 14
```
