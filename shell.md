# shell cheatsheet

This will create a file `greetings.txt` with two lines in it, the first being `line 1` and the second being `line 2`:

```bash
cat <<EOT >> greetings.txt
line 1
line 2
EOT
```

## References:

1. [How to append multiple lines to a file on UNIX StackExchange](https://unix.stackexchange.com/a/77278/107124)
