---
title: reset 취소, stash drop 취소하기
---

# reset 취소, stash drop 취소하기

```bash
git reflog
```

위 명령어를 치면 여태까지의 이동한 커밋 로그와 헤드가 전부 다 나온다.  

```bash
git reset --hard HEAD@{1}
git reset --hard 커밋로그
```

뭘 쳐도 된다.

```bash
git fsck --no-reflog | awk '/dangling commit/ {print $3}'
```
stash들이 전부 다 나오는 거 같다.  
가장 상위에 나오는 게 최근에 push한 stash인 듯...

## 참조 링크
* [(GIT) reset 한거 취소하는 방법](http://88240.tistory.com/284)  
* [How to recover a dropped stash in Git?](https://stackoverflow.com/questions/89332/how-to-recover-a-dropped-stash-in-git)
