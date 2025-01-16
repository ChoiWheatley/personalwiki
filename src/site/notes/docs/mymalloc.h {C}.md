---
{"dg-publish":true,"permalink":"/docs/mymalloc.h {C}/","title":"mymalloc.h {C}"}
---

말록 에러를 자동으로 관리해주는 친절한 매크로

```c
#pragma once
#include <stdio.h>
#include <stdlib.h>

#define MALLOC(p, s)                           \
  if (!((p) = malloc(s))) {                    \
    fprintf(stderr, "Insufficient memory!\n"); \
    exit(EXIT_FAILURE);                        \
  }
```
