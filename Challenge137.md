## picoCTF Challenge137 writeup

First use wget to import the .gz file
```shell
altregal@altREGAL:~/ctf/pico/challenge137$ wget https://mercury.picoctf.net/static/626abf12c976b994999f77eec3138a22/dds2-alpine.flag.img.gz
```

Then use gzip -d to unpack the file
```shell
altregal@altREGAL:~/ctf/pico/challenge137$ gzip -d dds2-alpine.flag.img
```

Use mmls to find the start value of the last partition
```shell
altregal@altREGAL:~/ctf/pico/challenge137$ mmls dds2-alpine.flag.img
```

Use fls to inspect the root of the partition by supplying start value to offset value in fls

```shell
altregal@altREGAL:~/ctf/pico/challenge137$ fls -o 2048 dds2-alpine.flag.img
```

Inspect the root note by supplying fls the inode number
```shell
altregal@altREGAL:~/ctf/pico/challenge137$ fls -o 2048 dds2-alpine.flag.img 18290
```

Since the root node has "down-at-bottom.txt" extract the contents of the file with icat
```shell
altregal@altREGAL:~/ctf/pico/challenge137$ icat -o 2048 dds2-alpine.flag.img 18291
```


