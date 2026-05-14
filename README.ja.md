# <img src="docs_app/src/assets/images/logos/Rx_Logo_S.png" alt="RxJS Logo" width="86" height="86"> RxJS: Reactive Extensions For JavaScript

![CI](https://github.com/reactivex/rxjs/workflows/CI/badge.svg)
[![npm version](https://badge.fury.io/js/rxjs.svg)](http://badge.fury.io/js/rxjs)
[![Join the chat at https://gitter.im/Reactive-Extensions/RxJS](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/Reactive-Extensions/RxJS?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

# RxJS 7 から 8 へのロードマップ

RxJSの今後の展開にご興味がありますか？[Issue 6367](https://github.com/ReactiveX/rxjs/issues/6367) をフォローして最新情報を確認してください。

# RxJS 7

### 6.x については [6.x ブランチ](https://github.com/ReactiveX/rxjs/tree/6.x) を参照してください

JavaScript向けのReactive Extensionsライブラリです。これは [Reactive-Extensions/RxJS](https://github.com/Reactive-Extensions/RxJS) の書き直しであり、本番環境で利用可能なRxJSの最新バージョンです。この書き直しは、より優れたパフォーマンス、モジュール性、デバッグしやすいコールスタックを提供することを目的としています。また、APIの表面積を減らすためのいくつかの破壊的変更を伴いますが、大部分において後方互換性を維持しています。

[Apache 2.0 License](LICENSE.txt)

- [行動規範](CODE_OF_CONDUCT.md)
- [コントリビューションガイドライン](CONTRIBUTING.md)
- [メンテナーガイドライン](docs_app/content/maintainer-guidelines.md)
- [APIドキュメント](https://rxjs.dev/)

## このリポジトリ内のバージョン

- [master](https://github.com/ReactiveX/rxjs/commits/master) - 現在のすべての開発作業が含まれており、現在はRxJS v7を対象としています。
- [6.x](https://github.com/ReactiveX/rxjs/tree/6.x) - バージョン6.x用のブランチです。

ほとんどのPRは **master** に対して作成してください。

## 重要

このリポジトリのIssueに貢献したりコメントしたりする場合、読んだかどうかにかかわらず、[コントリビューター行動規範](CODE_OF_CONDUCT.md)に同意したものとみなされます。交通ルールと同様に、知らなかったからといって免責されることはありません。

## インストールと使用方法

### ES モジュール

```JavaScript
import { range, filter, map } from "https://code4fukui.github.io/rxjs-es/rxjs.js";

range(1, 200)
  .pipe(
    filter(x => x % 2 === 1),
    map(x => x + x)
  )
  .subscribe(x => console.log(x));
```

### npm 経由の ES6

```shell
npm install rxjs
```

以下の `range` の例のように、必要なObservable生成メソッドは `'rxjs'` から直接インポートすることが推奨されます。
RxJSバージョン7.2以上を使用している場合は、必要なすべてのオペレーターも同じ `'rxjs'` からインポートできます。

```ts
import { range, filter, map } from 'rxjs';

range(1, 200)
  .pipe(
    filter((x) => x % 2 === 1),
    map((x) => x + x)
  )
  .subscribe((x) => console.log(x));
```

RxJSバージョン7.2未満を使用している場合は、必要なオペレーターを `'rxjs/operators'` からインポートできます。

```ts
import { range } from 'rxjs';
import { filter, map } from 'rxjs/operators';

range(1, 200)
  .pipe(
    filter((x) => x % 2 === 1),
    map((x) => x + x)
  )
  .subscribe((x) => console.log(x));
```

### CDN

CDNを利用する場合は、[unpkg](https://unpkg.com/) を使用できます。

[https://unpkg.com/rxjs@^7/dist/bundles/rxjs.umd.min.js](https://unpkg.com/rxjs@%5E7/dist/bundles/rxjs.umd.min.js)

RxJSのグローバル名前空間は `rxjs` です。

```js
const { range } = rxjs;
const { filter, map } = rxjs.operators;

range(1, 200)
  .pipe(
    filter((x) => x % 2 === 1),
    map((x) => x + x)
  )
  .subscribe((x) => console.log(x));
```

## 目標

- 全体的なバンドルサイズを縮小する
- 以前のバージョンのRxJSよりも優れたパフォーマンスを提供する
- Observableを [Observable Spec Proposal](https://github.com/zenparsing/es-observable) に基づいてモデル化・準拠させる
- さまざまなフォーマットでよりモジュール化されたファイル構造を提供する
- 以前のバージョンのRxJSよりもデバッグしやすいコールスタックを提供する

## ビルド/テスト

- `npm run compile` : すべてをビルドする
- `npm test` : テストを実行する
- `npm run dtslint` : dtslintテストを実行する

## ドキュメントの追加

いかなる形式であれ、ドキュメントへの貢献を歓迎します。ドキュメントアプリをローカルで立ち上げて実行するために必要なすべての情報や、貢献の方法については、[ドキュメントディレクトリ](./docs_app) を参照してください。
