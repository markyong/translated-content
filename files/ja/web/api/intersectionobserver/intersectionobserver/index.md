---
title: IntersectionObserver.IntersectionObserver()
slug: Web/API/IntersectionObserver/IntersectionObserver
---

{{APIRef("Intersection Observer API")}}

**`IntersectionObserver()`** コンストラクターは、新しい {{domxref("IntersectionObserver")}} オブジェクトを生成します。 `rootMargin` は、指定されていた場合は構文が正しいかが確認され、閾値は、0.0 から 1.0 の間であるか確認され、閾値のリストは昇順に並べ替えられます。閾値のリストが空の場合、 \[0.0] の配列に設定されます。

## 構文

```
var observer = new IntersectionObserver(callback[, options]);
```

### パラメーター

- `callback`

  - : 対象の要素が見えている割合が、表示されて閾値を越えたときに実行します。コールバックは 2 つの引数を受け取ります。

    - `entries`
      - : {{domxref("IntersectionObserverEntry")}} オブジェクトの配列で、それぞれの要素が閾値となります。これは、見えている割合が下から上に、または上から下にその値を越える時に callback が呼ばれるよう指定するものです。
    - `observer`
      - : コールバックが呼び出される {{domxref("IntersectionObserver")}} です。

- `options` {{optional_inline}}

  - : オブザーバをカスタマイズするためのオプションオブジェクトです。 もし `options` に何も指定されていない場合、オブザーバーはルートとして、余白の無い、閾値 0% のドキュメントビューポートを使用します（つまり、1px でもドキュメントビューポート内に入ればコールバックが実行されます）。次のオプションから任意の組み合わせを利用できます。

    - `root`
      - : {{domxref("Element")}} または {{domxref("Document")}} オブジェクトは、対象の祖先要素であり、これらの矩形はビューポートとみなされます。 `root` の可視領域に見えていない部分はいずれも、見えているとみなされません。
    - `rootMargin`
      - : 交差状態を計算するときに root の {{Glossary('bounding_box')}} に適用されるオフセットのセットを指定する文字列で、計算のために root を効果的に縮小または拡大させます。構文は概ね CSS の {{cssxref("margin")}} プロパティのものと同じです。margin のしくみと構文について詳しくは {{SectionOnPage("/ja/docs/Web/API/Intersection_Observer_API", "The root element and root margin")}} を御覧ください。デフォルト値は "0px 0px 0px 0px" です。
    - `threshold`
      - : 1 つの数値か、または 0.0 と 1.0 の間の数字の配列で指定し、監視対象の矩形の総面積に対する交差領域の比率を指定します。 0.0 に指定された場合、1px でも交差領域に入ったらその対象要素は表示されたとみなされます。threshold がどのように使われるかについては、 {{SectionOnPage("/ja/docs/Web/API/Intersection_Observer_API", "Thresholds")}} でより詳しく説明されています。 デフォルトの値は 0.0 です。

### 戻り値

新しい {{domxref("IntersectionObserver")}} は、対象要素が指定された `root` 内で `threshold` の可視閾値を越えて表示されたかどうかを監視するために使用することができます。対象要素の表示の変更を監視し始めるには、 {{domxref("IntersectionObserver.observe", "observe()")}} メソッドを呼び出します。

### 例外

- `SyntaxError`
  - : 指定した `rootMargin` は無効な値です。
- `RangeError`
  - : `threshold` の値のうち 1 つまたは 1 つ以上の値が 0.0 から 1.0 の範囲に当てはまりません。

## 例

この例では、監視されている要素の可視範囲が 10% を越える毎に `myObserverCallback` を呼び出すような新しい intersection observer を生成しています。

```js
let observer = new IntersectionObserver(myObserverCallback,
                   {threshold: 0.1});
```

## 仕様

{{Specifications}}

## ブラウザー実装状況

{{Compat("api.IntersectionObserver.IntersectionObserver")}}
