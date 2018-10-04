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

## Encoding of Python script

### Declare file encoding other than the default

By default, the `.py` file you write uses the system encoding. For MAC and Linux, this had long been unified by `utf-8`. Windows systems are usually a bit tricky. The Chinese version Windows could use one of some common encodings other than `utf-8`: `gbk` in mainland; `big5` in Hong Kong and Taiwan. That makes your script less portabel to other systems. Or you will meet problems, especially when string operation is heavily used in your program.

To declare an encoding other than the default one, a special comment line should be added as the first line of the file. the syntax is as follows:

```python
# coding={the codec name here}

# Remaining part of your Python script
```

For example, if you have Chinese characters in your code and your operating system is also Chinese version of Windows, it is better to declare the coding by writing the following as the first line in your source code file:

`# coding=utf-8` or `# -*- coding: utf-8 -*-`

There might be other situations and encoding format, and its a case by case situation, if you encounter more situation, please free feel to open an issue.