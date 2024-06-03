---
title: Scripting
search: true
---

# Scripting

<!-- TOC -->
* [Scripting](#scripting)
  * [Fundamentals](#fundamentals)
  * [If Statements](#if-statements)
    * [Conditions](#conditions)
  * [Case Statements](#case-statements)
  * [Loops](#loops)
    * [For Loops](#for-loops)
    * [While Loops](#while-loops)
    * [Until Loops](#until-loops)
  * [Functions](#functions)
<!-- TOC -->

## Fundamentals

Shebang (first line of file) for shell (`.sh`) files: `#!/bin/sh` or `#!/bin/bash`

Shell arguments: `$1`, `$2` ... `$9`; `$@` (all arguments)

## If Statements

```bash
if condition1; then
    command1a
    command1b
elif condition2; then
    command2
else
    command3
fi
```

### Conditions

`test $# -ne 2` or `[ $# -ne 2 ]` (spaces are required!)

## Case Statements

```bash
echo -n "yes/no? "
read answer
case $answer in
    y | yes ) echo "yes";;
    n | no ) echo "no";;
    *) echo "invalid input";;
esac
```

## Loops

### For Loops

```bash
for i in a b c; do
  echo $i
done
```

```bash
IFS=$'\n' # Internal Field Separator (needed to allow spaces in filenames)
for file in $*; do
  cp "$file" "$file.bak"
done
```

### While Loops

```bash
i=1
while [ $i -le 5 ]; do 
  echo $i; i=$(($i+1))
done
```

### Until Loops

```bash
i=1
until [ $i -gt 5 ]; do
  echo $i; i=$(($i+1))
done
```

## Functions

```bash
function myFunc {
  echo "Hello World, $1!"
}
myfunc "Linux"
```

```bash
myFunc() {
  echo "Hello World, $1!"
}
myfunc "Linux"
```