---
{"dg-publish":true,"permalink":"/docs/github issue, pull request 활용하기/","title":"github issue, pull request 활용하기"}
---

- 

[PR 내 충돌 해결법](https://stackoverflow.com/questions/53346762/how-to-resolve-conflict-in-pull-request)

```
# clean your local working directory with a stash or commit

# update your local repo with the content of the remote branches
git fetch --all --prune

# checkout the release_v1 branch
git checkout release_v1 

# update the content if required
git pull origin release_v1 

# merge the desired branch
git merge origin/master
```
