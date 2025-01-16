---
{"dg-publish":true,"permalink":"/docs/export to variables from .env file/","title":"export to variables from .env file"}
---

`#`를 무시하며 각 줄에 `Key=Value` 쌍을 포함하고 있는 .env 파일이 있을 경우, 한 번에 export 하는 방법에 관한 대화를 정리했습니다 ref: <https://stackoverflow.com/questions/19331497/set-environment-variables-from-file-of-key-value-pairs>

```sh
export $(grep -v '^#' .env | xargs)
```
