---
{"dg-publish":true,"permalink":"/docs/stat(2)/","title":"stat(2)"}
---

- <https://www.man7.org/linux/man-pages/man2/stat.2.html>
- [[docs/index/0017 C 🍎\|0017 C 🍎]]
- [[docs/10. System-Level IO {CSAPP}#10.6. Readig File Metadata\|10. System-Level IO {CSAPP}#10.6. Readig File Metadata]] 참조
___

```c
       #include <sys/stat.h>

       int stat(const char *restrict pathname,
                struct stat *restrict statbuf);
       int fstat(int fd, struct stat *statbuf);
       int lstat(const char *restrict pathname,
                struct stat *restrict statbuf);

       #include <fcntl.h>           /* Definition of AT_* constants */
       #include <sys/stat.h>

       int fstatat(int dirfd, const char *restrict pathname,
                struct stat *restrict statbuf, int flags);
```

## description

information about a file
