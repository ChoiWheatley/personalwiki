---
{"dg-publish":true,"permalink":"/docs/vim selectively find and replace text/","title":"vim selectively find and replace text"}
---

Yes, Vim provides an interactive way to perform search and replace. You can use the following command:

```
:%s/old_text/new_text/gc
```

This command initiates an interactive search and replace operation, where Vim will prompt you for each occurrence of “old_text” found in the file, allowing you to confirm whether to replace it with “new_text”. You can then choose to replace or skip each occurrence individually.
