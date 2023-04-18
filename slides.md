---
layout: cover
---

# page1

Hello, World!  23232323
```
console.log('aaa')
```

```ts { 2,3 }
function add(
  a: Ref<number> | number,
  b: Ref<number> | number
) {
  return computed(() => unref(a) + unref(b))
}
```
指定修改的行
```ts {2,3 | 5 }
function add(
  a: Ref<number> | number,
  b: Ref<number> | number
) {
  return computed(() => unref(a) + unref(b))
}
```


---

# Page 2
这是第二页

在线修改
```ts {monaco}
console.log('HelloWorld')
```

![Remote Image](<https://sli.dev/favicon.png>)

---

# 第三页
这是第三页

<div v-click>Hello</div>
<div v-after>World</div>



<!-- 这是一条备注 -->