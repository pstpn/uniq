# uniq

A Go implementation of the `uniq` utility. It collapses runs of adjacent duplicate lines,
reading from `stdin` and writing to `stdout` unless files are given as positional
arguments.

```
uniq [-c | -d | -u] [-i] [-f num] [-s chars] [input_file [output_file]]
```

    -c        print the number of occurrences before each line
    -d        print only the lines that repeat
    -u        print only the lines that never repeat
    -i        ignore letter case when comparing
    -f num    skip the first num fields, a field being a run of characters between spaces
    -s num    skip the first num characters, counted after the fields skipped by -f

Since `-c`, `-d` and `-u` each choose what gets printed, they cannot be combined, and
passing more than one prints the usage instead.

## Example

```shell
$ cat input.txt
I love music.
I love music.
I love music.

I love music of Kartik.
I love music of Kartik.
Thanks.

$ go run uniq.go -c input.txt
3 I love music.
1 
2 I love music of Kartik.
1 Thanks.
```
