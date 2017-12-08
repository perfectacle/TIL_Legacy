---
title: 함수형 패러다임의 예
---

# 함수형 패러다임의 예
```javascript
function ignoreAssets(mw) {
  return async function(ctx, next) {
    if (/(\.js|\.css|\.ico)$/.test(ctx.path)) {
      await next();
    } else {
      // must .call() to explicitly set the receiver
      await mw.call(this, ctx, next);
    }
  };
}
```

특정 코드를 보니까 위와 같이 돼있었다.  
왜 아래와 같이 안 되있는 걸까?  

```javascript
async function ignoreAssets(ctx, next) {
  if (/(\.js|\.css|\.ico)$/.test(ctx.path)) {
    await next();
  } else {
    // must .call() to explicitly set the receiver
    await mw().call(this, ctx, next);
  }
}
```

두 코드는 동일하게 동작한다.  
함수형 패러다임 때문에 맨 위와 같이 작성한 거라는데 mw 자체가 함수 코드 내부에서 다른 값으로 쓰일 수도 있고  
사이드 이펙트를 막기 위해, 좀 더 코드를 안전하고 견고하게 짜기 위한 함수형 프로그래밍의 패러다임인 것 같다.  
