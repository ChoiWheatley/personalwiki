---
{"dg-publish":true,"permalink":"/docs/bind(2)/","title":"bind(2)"}
---


<https://man7.org/linux/man-pages/man2/bind.2.html>
___

```c
#include <sys/socket.h>
int bind(int sockfd, const struct sockaddr *addr,
		 socklen_t addrlen);
```

[[docs/sockaddr(3type)\|sockaddr(3type)]]

```c
struct sockaddr {
	sa_family_t sa_family;
	char        sa_data[14];
}
```

소켓에 이름을 부여하는 작업. [[accept(2)\|accept(2)]]를 통해 커넥션을 체결하기 전에 필요하다. 
