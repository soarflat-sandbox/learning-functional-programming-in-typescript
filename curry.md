# カリー化

[JavaScript ( 時々 TypeScript ) で学ぶ関数型プログラミングの基礎の基礎 #2 - カリー化について](https://tech.recruit-mp.co.jp/front-end/post-15885/)

## （関数の）カリー化とは

期待される数より少ない引数で関数を呼び出した場合、呼び出された関数が足りない引数を補完するために別の関数を返すような関数にすること。

たとえば、`f(a, b, c)`関数があるとする。

この関数を`f(a)`で実行すると、足りない引数`b`、`c`を引数に持つ`g(b, c)`関数を返す。

```ts
// 第二引数に渡されたオブジェクトに対して第一引数に渡されたメソッドを即座に実行する関数
function rightAwayInvoker(method: Function, ...targets: any[]) {
  const target = targets.shift();

  return method.apply(target, targets);
}

rightAwayInvoker(Array.prototype.reverse, [1, 2, 3]);
// => [3, 2, 1]
```
