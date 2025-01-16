---
{"dg-publish":true,"permalink":"/docs/docker --filter flag/","title":"docker --filter flag"}
---


> how to change view for docker ps? I want to see only CONTAINER ID, NAME column

You can customize the output of docker ps using the --format option. To display only the CONTAINER ID and NAME columns, use the following command:

```
 docker ps --format "table {{.ID}}\t{{.Names}}"
```

This command formats the output as a table with the specified columns. If you want a simpler output without the table format, you can use:

```
 docker ps --format "{{.ID}} {{.Names}}"
```
