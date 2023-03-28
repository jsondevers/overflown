# [`The Shell`](https://missing.csail.mit.edu/2020/course-shell/)

## What is the shell?

- Allow programmers to take full advantage of tools on computer
- Bourne Again SHell = BASH

## Using the shell

```bash
jasondevers@Js-M1:~$
```

- `~`  is for home
- `$` means you're not the root user

```bash
jsondev:~$ date
```

- `date` command
- we can pass arguments into commands

```bash
jasondevers@Js-M1:~$ echo hello
```

- `echo` is the command
- `hello` is the argument

```bash
jasondevers@Js-M1:~$ echo "hello world"
```

- here we still pass one argument as one literal string `"hello world"`

This is equivalent to:

```bash
jasondevers@Js-M1:~$ echo hello\ world
```

## How does the shell know these commands?

- it ships with the computer
- shell has a way to know/run/search these programs through an environment variable
- bash is basically a way programming language of its own

## Navigating the shell

```bash
jasondevers@Js-M1:~$ echo $PATH
```

- will return all paths that the shell will search for programs
- shown as a list, separated by a colon `(:)`
- look in each directory for a program/file whose name matches the command eg. `date` or `echo` and run it

```bash
jasondevers@Js-M1:~$ which echo 
/usr/bin/echo
```

- which program it actually runs
- if we were to run a program called `echo` which basically shows which program we're calling

## `Paths`

- Paths are a way to name the location of a file on computer
- separated by slashes `/` (on windows it's `\`)
- `root` directory is the start of the directory/top of the file system
- in the above example, we have the first `/` that represents the root then directory `usr` then `bin` then run `echo`
- everything lives under root in mac/linux (under one namespace)
- windows each partition has a root
- absolute paths are paths that fully determine the location of a file
- relative paths are paths relevant to where we currently are

```bash
jasondevers@Js-M1:~$ pwd
/Users/jasondevers
```

- `pwd` is print working directory, the current path we're in

```bash
jasondevers@Js-M1:~$ cd /Users
jasondevers@Js-M1:/Users$ pwd
/Users
```

- from root we go into `/Users`

## `Directories`

- `.` is the current directory
- `..` is the parent directory

```bash
jasondevers@Js-M1:/Users$ pwd
/Users
jasondevers@Js-M1:/Users$ cd ..
jasondevers@Js-M1:/$ pwd
/
```

- here we switched into the root directory from users

```bash
jasondevers@Js-M1:~$ pwd
/Users/jasondevers
jasondevers@Js-M1:~$ which echo
/bin/echo
```

- we see where the echo command is located

```bash
jasondevers@Js-M1:~$ ../../bin/echo "this is me using the echo command"
this is me using the echo command
jasondevers@Js-M1:~$ 
```

- here we ran the same `echo` command by directly accessing it
- through environment variables, we don't always have to give the full path like we just did in order to run a command like `echo`

```bash
jasondevers@Js-M1:~$ ls
Desktop/                Movies/                 bin/
Documents/              Music/                  go/
Downloads/              Pictures/               iCloud Drive (Archive)/
Library/                Public/
```

- shows files in the current directory

```bash
jasondevers@Js-M1:~$ ls ../../
Applications/ Volumes/      etc@          sbin/
Library/      bin/          home@         tmp@
System/       cores/        opt/          usr/
Users/        dev/          private/      var@
jasondevers@Js-M1:~$ 
```

- shows files in the root directory
- `ls /` could have also done the same thing

`~` (tilde) this is the home directory and can always take us there through `cd ~`

```bash
jasondevers@Js-M1:~$ cd -
```

- `cd -` will take us back to our previous directory, not our parent directory but the directory we were last in, meaning we can massively change back and forth between key directories

## `Running Programs`

- when we run programs, they're going to be in the current working directory

## `Flags & Options`

- we can implement flags/options through `-` that will allow us to add arguments

```bash
jasondevers@Js-M1:~$ lsof -help
```

- on macOS we have to add the `of` along with `-help`
- on linux it would just be `ls --help`

```bash
jasondevers@Js-M1:~$ ls -l
total 0
drwx------@  13 jasondevers  staff   416B Dec 27 20:11 Desktop/
drwx------+   7 jasondevers  staff   224B Dec  2 12:00 Documents/
drwx------@  23 jasondevers  staff   736B Dec 26 22:08 Downloads/
drwx------@  90 jasondevers  staff   2.8K Dec 
```

- these say read/write details as well as other information about the files
- it says who owns the file (me)
- this looks different for linux
- these are all directories, but it would look different for others

### `read permissions (r)`

- basically means you're allowed to lists the contents of this file

### `write permissions (w)`

- basically means you're allowed to create, rename, and remove files within that directory, however you cannot delete the directory itself, you can basically remove all of its contents, but not actually remove

### `execute permissions (x)`

- on directories is what is known as `search` basically means are you allowed to enter this directory, if you want to get to a file, read/open/write to it (basically `cd` into a directory), you must have the `x` permission on all parent directories of that directory and the directory itself

### `root`

- for a lot of things in `root` we would have a lot of `x's` that mean they're executable because anyone should be able to write those commands
- if the permissions just have a `-`, a dash, this means that you do not have the permission, for example `r-x` means you have read and execute but you do not have write (`-` is where `w` should be)

### `mv` move

- allows us to rename files (for example change the name of the file but not the directory)

```bash
mv [path/file to be 'moved'] [renamed path/file]
```

### `cp` copy

```bash
cp [path/file to copy 'from' ] [path/file 'to']
```

### `rm` remove

```bash
rm [path/file to removed 'from' ] 
```

below is a recursive removal `-rf`

```bash
rm -rf[path/file to removed 'from' ] 
```

- `rmdir` only lets you remove a directory if that directory is empty

### `mkdir` make directory

```bash
mkdir dir1 dir2 dir3
```

- creates three separate directories

```bash
mkdir "dir1 dir2 dir3"
```

- creates one directory

### `man`

- displays more information about a command

```bash
man [command]
```

- press `q` to quit this program, it can be hard to break out of this

### `cleaning`

- `ctrl + l` will clear the terminal up to the top
- `cmd + l` will clear the last command
- `clear` will clear your terminal (start from the top again)

### `power of the shell`

- combining these different programs
- chain multiple programs through the notion of streams

### `every program has two primary streams`

1. input stream (keyboard/terminal)
2. output stream (terminal)

- with the shell we can use `<` and `>`
- `<` means rewire the inputs of this program to be the contents of this file
- `>` means rewire the output of the preceding into this file

```bash
echo hello > hello.txt
```

- this stores the output/contents of the `echo hello` command in the contents of the hello.txt file (this can also be a path)
- as a result of this, nothing will be outputted when we run this `echo hello` command via the terminal
- we can use `cat` to see the contents of this hello.txt file to show the "hello" by doing

```bash
cat hello.txt
```

- then we can do something like `cat < hello.txt` to display to the terminal the contents of the file (the same as doing `echo hello`)
- we can then combine these input/output redirects

```bash
cat < hello.txt > hello2.txt
```

- if we were to do `cat hello2.txt` after this, it would again, just show "hello" via the shell
- the cat program does not know anything about this redirection, it's just doing its thing and showing the contents of a file
- i'm telling the shell to do these programs/commands with these redirections

### `>>` append

- using the above example if we ran

```bash
cat < hello.txt >> hello2.txt
```

- if we were to do `cat hello2.txt` after this, it would now show

```bash
hello
hello
```

### `|` pipe

- pipe means take the output of the program to the left and make it in the input of the program to the right
- let's do an example

```bash
ls -l 
```

this is going to show a bunch of files, let's say we only wanted the last line of the result of this command

- `tail` prints the last `n` lines of its inputs
- we can add a flag `n1` where `n` is the number of lines, so this just means print the last line

```bash
tail -n1
```

we can wire all these programs together

```bash
ls -l / | tail -n1
```

- `ls` does not know about `tail`
- `tail` does not know about `ls`
- it's the shell redirecting/combining programs via the pipe

### examples from lecture

```bash
curl --head --silent google.com | grep -i content-length | cut --delimiter=' ' -f2
```

- `curl --head --silent google.com` gives all the http headers for google.com
- `grep -i content-length` is saying the content length as a result of the headers that were generated
- `cut --delimiter=' ' -f2` is saying cut the program on a space, and we want the second field (`-f2`)
- chaining these together can really help
- pipes are not just for text, they can do binary images and you can chain binaries together
- can stream a video by having the last command in your pipe being a chromecast command

### `using the terminal better`

- `root`: is sort of like the administrator on windows and has user ID zero, it lets you do whatever, a `super` user, we're not usually user (it can be dangerous)
- when we need to have `root` access, we can use the `sudo` command that says act as a "super user" or `sudo` and we can say do the following program as if you were the `root` user

#### when would we use `sudo`?

- many special file systems on a computer, but on linux, we can access the `sysfs`

```bash
cd /sys
```

- access the `sys` directory from the root directory
- this is a whole new world
- these are file systems that are not part of your computer file system
- these files are parameters for your `kernel` which is the core of your computer
- means we're able to access these `kernel` parameters through the view as a file system
- we can use all the tools from above for this
- we can alter the backlight on our computer through access via the shell in this sub system

```bash
echo 500 > brightness
permission denied
sudo echo > brightness
permission denied
```

- would change our `brightness` to 500
- in order to change things in the `kernel`, you have to be the administrator
- `sudo` still doesn't work because these pipes don't know about each other
- we're telling our shell currently to run the program `sudo` with the following arguments `echo 500` and send its output to file called `brightness`
- however, the shell is what is what is opening the brightness file, not the `sudo`

### if you were setting up a firewall, you might do something like

```bash
# echo 1 > /sys/net/ipv4_forward
```

- the `#` means to run this as `root`
- when we are `root` user, we will see `#` instead of `$`

### to get around our problem earlier, we can do

```bash
sudo su 
```

- `su` is a very complicated command that gets us a shell as the super user
- now we're a `root` user

### as not the root user, we could instead

```bash
echo 500 > brightness | sudo tee brightness
```

- above is saying run the `tee` as `root` and have `tee` write into the brightness file
- the `tee` command takes its inputs and writes it to a file, but also to the standard output (terminal)
- the `tee` is what is opening the file
- real world use: log file, you want to save the logs and put it in a file, but you also want to see it

### there is also another command `xdg-open`

- on macOS it's just `open`
- this command will open the program you give it in its respective program
