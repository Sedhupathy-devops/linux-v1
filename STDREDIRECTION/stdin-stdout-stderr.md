# STDIN-STDOUT-STDERR

In Linux, stdin is the standard input stream. This accepts text as its input. Text output from the command to the shell is delivered via the stdout (standard out) stream. Error messages from the command are sent through the stderr (standard error) stream.

````TEXT
These values are always used for stdin, stdout, and stderr:

0: stdin
1: stdout
2: stderr
````

## Redirecting stdout
```TEXT
To explicitly redirect  stdout, use this redirection instruction:

1>

examples:
    ./error.sh 1> capture.txt
```

## Redirecting stderr

```TEXT
To explicitly redirect  stderr, use this redirection instruction:

2>

examples:
    ./error.sh 2> capture.txt
```

## Redirecting Both stdout and stderr

```TEXT
./error.sh 1> capture.txt 2> error.txt #to seprate files

./error.sh > capture.txt 2>&1 #to same file
```

## Redirecting stdin

```TEXT
./input.sh < dummy.txt
```

## Redirect stdout to stdout

```TEXT
echo "hello there" >&1
hello there
```

## Redirect stdout to stderr

```TEXT
echo "hello there" >&2
hello there
```
