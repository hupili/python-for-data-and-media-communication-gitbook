# Encoding

## iconv

`iconv` is a convenient command line tool to convert between two different file encodings. Suppose you have a `file.txt` which is GBK encoded and want to have UTF-8 version, you can use the following command.

```shell
iconv -f gbk -t utf-8 file.txt
```

The converted result is sent to standard output by default. You can use `stdout` redirect to save that in a file called `output.txt`.

```shell
iconv -f gbk -t utf-8 file.txt > output.txt
```

Suppose you have original GBK encoded files in `orig/` and want to output UTF-8 encoded text files to `utf-8/`. Following command can help you do the batch conversion.

```bash
ls orig -1 | xargs -I{} sh -c 'iconv -f gbk -t utf-8 orig/"{}" > utf-8/"{}"'
```

MAC user can install iconv via `brew`.
