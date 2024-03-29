---
title: 맥 OS에서 백틱(`)입력하기
---

# 맥 OS에서 백틱(`)입력하기  
맥을 하이 시에라(High Sierra)로 올리고 나니 어느 순간부터 백틱이 원화(₩)로 표시되기 시작했다.  
어쩔 땐 백틱이 입력되고, 어쩔 땐 원화가 입력되서 고민을 하던 찰나 아래 링크를 확인해보니 한글 입력 상태일 때만 해당 현상이 발생했다.
[macOS Sierra에서 원화(₩) 대신 백 쿼트 입력하기](https://ani2life.com/wp/?p=1753)  
따라서 한글일 때는 옵션 + 백틱 키를 눌러야 원화가 아닌 백틱이 나왔는데 이는 매우 귀챠니즘한 일이다.  
따라서 위 링크를 참고해서 아래 커맨드를 입력하면 된다.  
```bash
cd ~/Library
mkdir KeyBindings
vim DefaultkeyBinding.dict
```

그리고 아래와 같은 내용을 추가하고 IDE 등등을 재시작 해보면 한글 상태에서도 백틱이 잘 먹히는 걸 볼 수 있다.  
```
{
    "₩" = ("insertText:", "`");
}
```

위 과정이 귀찮은 사람은 한큐에 실행할 수 있는 명령어가 있다.  
```bash
if ! [ -f ~/Library/KeyBindings/DefaultkeyBinding.dict ]; then mkdir -p ~/Library/KeyBindings && echo '{"₩" = ("insertText:", "\`");}' > ~/Library/KeyBindings/DefaultkeyBinding.dict; fi
```

## 참조 링크
* [macOS Sierra에서 원화(₩) 대신 백 쿼트(`) 입력하기](https://ani2life.com/wp/?p=1753)  
* [kr_won_to_backquote.sh](https://gist.github.com/redism/43bc51cab62269fa97a220a7bb5e1103)