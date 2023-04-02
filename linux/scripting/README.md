# `Shell Scripting`

## Defining a variable

- spaces are important when working with bash
- spaces are reserved for shells

```bash
jasondevers@Js-M1:~$ foo=bar
jasondevers@Js-M1:~$ echo $foo
bar
```

- here, we created a variable called foo and we accessed it through using `$`

```bash
foo = bar
```

- this is a wrong example, this is saying
- 1.  run the program `foo`
- 2. with arguments `=` and `bar`

## Defining strings

- can use single or double quotes

```bash
echo "World"
World
echo 'World'
World
```

- however, they're not the same

```bash
echo "Value is $foo"
Value is bar
echo 'Value is $foo'
Value is $foo
```

- double quotes should be using for the above (same in python)

## Defining functions

```bash
mcd () {
    mkdir -p "$1"
    cd "$1"
}
```

- can do this through the shell or we can create a file and edit there
- when defining a file, it would have a `.sh` extension (for shell)
- you then would do `source <filename>.sh`

## Reserved `$<value>`

- `$0` is reserved for the name of the script
- `$1` access the first argument
- `$2 ... $9` will be the second to the ninth arguments
- `$?` will get the error code from the previous command
- `$_` last argument of previous command

## `Bang Bang`

- you try a command and get a permission denied

```bash
mkdir /mnt/new
permission denied
sudo !! 
sudo /mnt/new
```

- replaces the previous denied command

## Standard Errors

```bash
echo "Hello"
Hello
echo $?
0
```

- there were no errors, so we got a return value of `0` (same in C, everything went well)

```bash
grep foobar mcd.sh
echo $?
1
```

- we tried to search for a foobar string in `mcd.sh`, but it wasn't there so it returns 1

```bash
jasondevers@Js-M1:~$ true
jasondevers@Js-M1:~$ echo $?
0
jasondevers@Js-M1:~$ false
jasondevers@Js-M1:~$ echo $?
1
```

```bash
jasondevers@Js-M1:~$ false || echo "Oops fail"
Oops fail
```

- bash (like any other language) will try to that `false` and if it's ... well `false` then we try the next statement (bc we use `OR` logical operator)

```bash
jasondevers@Js-M1:~$ true || echo "Will not be printed"
jasondevers@Js-M1:~$ 
```

- here, `true` will always evaluate to `true` so it doesn't get to the second statement

```bash
jasondevers@Js-M1:~$ echo true && echo "Things went well"
Things went well
jasondevers@Js-M1:~$ false && echo "This will not print"
```

- above is using the same logic with the `AND` operator (both have to be true)

```bash
jasondevers@Js-M1:~$ false ; echo "This will always print"
```

- we can concatenate commands together using a `;` like we did above and that will always combine the two commands

## Getting output of a command in variable

```bash
jasondevers@Js-M1:~$ foo=$(pwd)
jasondevers@Js-M1:~$ echo $foo
<will print result of pwd>
```

- this gets the output of the `pwd` command and stores it in the variable `foo` and this is accessed by using `$`

```bash
echo "We are in $(pwd)"
We are in <result of pwd>
```

## Process substitution

```bash
cat <(ls) <(ls ..)
```

- we're `ls`'ing the directory, putting it in a temp file
- doing the same thing with the parent folder and we concat both of them together

## Example

```bash
echo "Starting a program at $(date)"

echo "Running program $0 with $# arguments with pid $$"

for file in "$@"; do
    grep foobar "$file" > /dev/null 2> /dev/null
    # when pattern is not found, grep has exit status
    # redirect STDOUT and STDERR to a null register 
    if [["$?" - ne 0 ]]; then
    echo "File $file does not have any foobar, adding one"
    echo "# foobar" >> "$file"
    fi
done
```

- tells what the date is based on `$(date)`
- says what the name of program we're running is based on `$0`
- `$#` is the number of arguments
- `$$` process id of the command that is running
- `$@` is going to expand to all the arguments
- 1. for example `$1 $2 $3` instead of typing all these out
- redirect the output of this `grep foobar` into `/dev/null`
- the `2>` represents standard error because those two streams are different
- `if [["$?" - ne 0]]; then` is saying if the exit code is nonzero, we enter this if
- `echo "File $file does not ..."`
- `>>` append at the end of a file

## Globbing

```bash
ls
example.sh image.png mcd.sh project1 script.py
ls *.sh
example.sh mcd.sh
```

- shows only `.sh` files

```bash
ls
example.sh mcd.sh project1 project2 project42 script.py
ls project?
project1:
src

project2:
src
```

- there are 3 "project" directories, but we only show two
- the `?` extension only checks by one extra character

## Using `{}`

```bash
convert image.png image.jpg
convert image.{png,jpg}
```

- the curly braces will basically help eliminate repeated work or having to type out the same thing again and again

-----
`Start`

```bash
touch foo{,1,2,10}
```

this will turn into when you run it as

```bash
touch foo foo1 foo2 foo10
```

`End`

-----

`Start`

```bash
cp project{1, 2
touch project{1,2}/src/test/test/{1,2,3}.py
```

will turn into

```bash
touch project1/src/test/test1.py project1/src/test/test2.py project1/src/test/test3.py project2/src/test/test1.py  project2/src/test/test2.py project2/src/test/test3.py 
```

- takes the cartesian products of the tw

`End`

-----

`Start`

```bash
mkdir foo bar
touch {foo,bar}/{a..j}
```

- this is going to expand from `foo/a, bar/a, foo/b, bar/b, foo/c, bar/c, ... , fooj, bar/j`

`End`

-----

```bash
touch foo/x bar/y
diff <(ls foo) <(ls bar)
11c11
< x
---
> y
```

## Consider a python script

```python
#! /usr/local/bin/python
import sys
for arg in reversed(sys.argv[1:]):
    print(arg)
```

- the first line is called a `shebang`, it tells bash the path
- this script basically prints whatever command in reversed order

```bash
python3 script.py a b c
c
b
a
```

- having the `#! /usr/local/bin/python` (`shebang`) is what allows us run this program as `./script.py a b c`
- you can also do `#! /usr/env python`

## Debugging in bash `shellcheck`

- `shellcheck` will give better error messages
- can install `tldr` that will examples that explain

## `find`

```bash
find . -name src -type d
```

- `find` in the `.` current directory
- `-name src` name being src
- `-type d` type being a directory

```bash
find . path '**/test/*.py' -type f
```

- look for python files within test folder
- `**` means doesn't really care about the start of the path

```bash
find . -mtime -1
```

- `-mtime` is modified time
- `-1` modified in the past day

```bash
find . -name "*.tmp"
./project1/src/test/test2.tmp
./project1/src/test/test3.tmp
./project1/src/test/test1.tmp
./project2/src/test/test2.tmp
./project2/src/test/test3.tmp
./project2/src/test/test1.tmp
find . -name "*.tmp" -exec rm {} \;
find . -name "*.tmp"
```

- we can use find and run other commands
- above we basically delete all the temp files
- when we search for them again, they aren't there

```bash
find . -name "*.tmp"
fd ".*py"
```

- the two commands above will do the same thing

```bash
grep -R foobar
```

- `-R` flag will go through the entire directory

```bash
rg "import requests" -t py
```

- this will show through all the files where this string `import requests` shows up

```bash
rg "import requests" -t py -C 5 ~/scratch
```

- `-C` will provide context, it will show 5 lines after where the string is, which is awesome

```bash
rg -u --files-without-match "^#\!" -t sh
```

- `u` is don't ignore hidden files
- `--files-without-match` print files without match `"^#\!` (`shebang`)
- `-t` type is `sh`

```bash
rg "import requests" -t py -C 5 --stats ~/scratch
```

- will give stats about the command

## `history`

```bash
history 1 | 
```

- prints everything since the beginning

```bash
history | grep convert
```

- show everything related to "convert"
- `ctrl + R` is backward search

## `fzf`

```bash
cat example.sh | fzf
```

- this is really neat, it will allow us to scan through this file, only filtering on things that we are looking for as we start typing

## quick listing

```bash
ls -R
```

- `-R` recursively list structure
