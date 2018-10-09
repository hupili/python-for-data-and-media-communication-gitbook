# File IO FAQ

## Do not see the content in file after successful .write statement

This is usually due to [File I/O buffer, or Data buffer](https://en.wikipedia.org/wiki/Data_buffer). Computer systems use buffer to avoid frequent I/O operations because those operations are usually costly. Producer side (in our case, Python program) keeps writing to the buffer. When buffer is flushed, the consumer side (in our case, the file on disk) can see the content. File buffer is usually flushed at two events:

- When you `.close()` a file. That is why we ask you not to forget closing a file after using it.
- When the cache is full. To know the default size of the cache, use the following script:

```python
>>> import io
>>> io.DEFAULT_BUFFER_SIZE
8192
```

## Write to closed file

This error message is direct: `ValueError : I/O operation on closed file.`.

You can not `.write()` or `.read()` after closing a file. You can re-`.open()` this file and try again.