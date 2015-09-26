generate two files.

```
du@L64:~/work/m3_freertos$ dd if=/dev/zero of=zero64.bin bs=65536 count=1
1+0 records in
1+0 records out
65536 bytes (66 kB) copied, 0.0120669 s, 5.4 MB/s
du@L64:~/work/m3_freertos$ dd if=/dev/zero of=zero32.bin bs=32768 count=1
1+0 records in
1+0 records out
32768 bytes (33 kB) copied, 0.0202808 s, 1.6 MB/s
du@L64:~/work/m3_freertos$

```

use A2BU to patch them.

```

du@L64:~/work/m3_freertos$ head zero32.bin.sig  | hd
00000000  eb 10 90 00 03 00 00 0a  00 00 00 00 00 00 00 00  |................|
00000010  00 80 00 00 01 00 00 00  00 00 00 00 40 00 00 00  |............@...|
00000020  a0 a1 a2 a3 a4 a5 a6 a7  a8 a9 aa ab ac ad ae af  |................|
00000030  00 00 00 00 00 00 00 00  a6 fc 1f 01 d3 8e 49 9d  |..............I.|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00008040
du@L64:~/work/m3_freertos$ head zero64.bin.sig  | hd
00000000  eb 10 90 00 03 00 00 0a  00 00 00 00 00 00 00 00  |................|
00000010  00 00 01 00 01 00 00 00  00 00 00 00 40 00 00 00  |............@...|
00000020  a0 a1 a2 a3 a4 a5 a6 a7  a8 a9 aa ab ac ad ae af  |................|
00000030  00 00 00 00 00 00 00 00  eb 8e 97 d7 36 91 0d ce  |............6...|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00010040
du@L64:~/work/m3_freertos$

```

I guess the beginning of the second line is the file size, littile endian.
