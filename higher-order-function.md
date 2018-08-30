# 高階関数

[JavaScript ( 時々 TypeScript ) で学ぶ関数型プログラミングの基礎の基礎 #1 - 高階関数について](https://tech.recruit-mp.co.jp/front-end/post-15867/)

## 高階関数

関数を「引数」、もしくは「戻り値」として扱う関数のこと。

`Array.prototype.forEach()`なども高階関数である。

```ts
const stones = ['mick', 'keith', 'ronnie', 'charlie'];

stones.forEach(member => console.log(member));
```

配列の各アイテムを引数に持つ関数（`member => console.log(member)`）が`forEach()`に引数として渡されている。

他にも`map`、`filter`なども高階関数である。

### 簡単な高階関数を自作してみる

数値と値を引数に取り、その値を数値の数だけ格納された配列を返す関数`repeat`を作成してみる（高階関数ではない）。

```ts
import * as _ from 'lodash';

function repeat(times: number, value: any): any[] {
  return _.map(_.range(times), () => value);
}

repeat(3, 'foo');
//=> [foo", "foo", "foo"]
```

これをより抽象度が高い「ある計算を繰り返す」関数に修正してみる。

```ts
import * as _ from 'lodash';

function repeatedly(times: numer, f: (value: any) => any): any[] {
  return _.map(_.range(times), f);
}

repeatedly(3, Math.random() * 10 + 1);
//=> [6.440716057227879, 4.58105440499825, 4.298355912680706]

repeatedly(3, () => 'bar');
//=> ['bar', 'bar', 'bar']
```

値ではなく、関数を引数として受け取り、その結果を配列に格納するようになった。つまり、この関数を高階関数に修正した。

修正前`repart`のように固定の処理の結果（値）を配列に格納して返すのではなく、任意の処理の結果（値）を配列に格納して返せるようになった。

### 戻り値として他の関数を返す関数

### なぜ関数を返す関数を利用するのか（存在するのか）
