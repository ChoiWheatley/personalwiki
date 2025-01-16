---
{"dg-publish":true,"permalink":"/docs/chmod 400과 동일한 파워셸 powershell 커맨드/","title":"chmod 400과 동일한 파워셸 powershell 커맨드"}
---

https://www.youtube.com/watch?v=P1erVo5X3Bs

```powershell
icacls.exe filename /reset
icacls.exe filename /grant:r "$($env:username):(r)"
icacls.exe filename /inheritance:r
```
