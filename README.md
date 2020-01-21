# JavaScriptで出来ること

===

## 1. はじめに

---

### 1-1. 構成
1. はじめに
2. 様々なJavaScriptの用途
3. 様々なJavaScriptの用途 @ Webブラウザ
4. おわりに

---

### 1-2. 目的
* ❌ JavaScriptの文法を習得する
* ⭕ JavaScriptで出来ることを知る
  * たくさんある！

notes:
* 文法はドキュメントを読めば理解できる。
* それを使って何が出来るのかがわからないと、学習意欲がわかない。例: 数学
* JavaScriptを使ってなにか出来るのかを体験して、ワクワクしてもらいたい。

===

## 2. 様々なJavaScriptの用途

notes:
* どのように使われているか見ていくことで、何が出来るかを知る。

---

### 2-1. Webブラウザ
* ブラウザの様々な操作
* 3章で一部くわしく紹介

notes:
* 表示内容に変化を与えたり、ページ遷移や外部データ取得など、様々なブラウザの機能を扱ったりできる。
* Webブラウザで、特別な準備なしに動作するプログラミング言語は、長らくJavaScriptのみだった。
* いまではWebAssemblyも動作するが、これは単独ではなく、JavaScriptと共に使用するもの。
* Webブラウザ上でのプログラミングには、JavaScriptが必須。

---

### 2-2. Node.js
1. リモートマシンでの用途
2. ローカルマシンでの用途

notes:
* Node.jsは、Webブラウザ（Chrome）のJavaScript実行エンジン（V8）を、OS上で動作するようにしたもの。
* パソコンでも動作するし、VPSサーバーの様な手元にないリモートマシンでも動作する。

---

#### 1. リモートマシンでの用途 | 2-2. Node.js
* Webサーバー
* アプリケーションサーバー
* FaaS（Function as a Service）

notes:
* HTMLや画像など、静的なデータを配信するWebサーバーとして、動作させることができる。
* リクエストに応じて動的にデータを返すアプリケーションサーバーとして、動作させることができる。
* Faas: 関数だけ書けば、その実行受付と結果送信を行ってくれるサービス。例: AWS Lambda
  * 現在は多くの言語で記述可能だが、Node.jsは最初期からサポートされていた。
* リモートマシンでNode.jsを使用している事例
  * タップル https://tapple.me/
  * グランブルーファンタジー https://granbluefantasy.jp/
  * Amebaピグ https://s.life.pigg.ameba.jp/

---

#### 2. ローカルマシンでの用途 | 2-2. Node.js
* タスクランナー
* ネイティブアプリ開発環境
* デスクトップアプリエンジン
* IoT

notes:
* コードの最小化や画像サイズ削減など、面倒な作業を人に代わって実行するタスクランナーとして利用できる。例: Gulp, Webpack
* スマートフォンアプリを開発できる。1つのコードから、iOSとAndroid両方のために書き出すことができる。例: React Native
* エディタやチャットアプリなどの、デスクトップアプリの実行エンジンとして利用できる。例: Electron
  * Node.jsを内蔵したアプリケーションをビルドできる
* Raspberry Piなどの小型マシン上で動作させ、ランプやセンサーなどを操作できる。
* ローカルマシンでNode.jsを使用している事例
  * ReactNativeを使用して開発されたスマートフォンアプリ
    * Facebook, Instagram, Airbnb, Skype
  * Electronを実行エンジンとして起動デスクトップアプリ
    * Slack, Visual Studio Code, Atom
  * IoT
    * LEDチカチカから、Webサーバーとして稼働まで


===

## 3. 様々なJavaScriptの用途<br>＠Webブラウザ

notes:
* JavaScriptの様々な用途の中から、Webブラウザでの用途に焦点を絞る。
* 学校やオンラインの講座で一般的に教えられているのがこの用途。
* それを学んだ先で、何が出来るようになるかを知る。
* 基本、重要、頻出と思われる概念を、一部抜き出して紹介する。
* 各項目とも実例のCodePenを用意してある。
* 体験版の方は、あと肝となる部分だけを追記すれば、完成する状態。
* まずは完成版を見て何を目指すか理解してもらい、その後は添えてある参考情報をもとに体験版から完成させてみてほしい。

---

### 3-1. イベントハンドリング
* イベントと関数を結びつけることができる。
  * **イベント**: クリック、スクロール、HTML読込完了など
  * 👉 **任意のタイミングで自由な処理を実行できる！**

notes:
* イベントと処理の結びつけは、JavaScriptプログラミングでは必ず発生する基本の概念。
* 全ての処理は何かのイベントを引き金として実行されている。
* ボタンを作るなら、クリックと処理を結びつけることになるし、
* スクロールに応じた演出を作るなら、スクロールと処理を結びつけることになるし、
* 最初に実行されるコードも、コードの取得完了と結びついていると言える。

---

#### 体験してみよう | 3-1. イベントハンドリング
* <a href="https://codepen.io/dsktschy/pen/rNaxBvZ" target="_blank">体験版CodePen</a>
  * 参考

```js

/**
 * Element # addEventListener()
 * 要素で発生する任意のイベントに、関数を結びつける。
 * 
 * 例: target要素の、clickイベントに、listener関数を結びつける。
 */
target.addEventListener('click', listener)


```

* <a href="https://codepen.io/dsktschy/pen/PowPgKL" target="_blank">完成版CodePen</a>

notes:
* 実際には、addEventListenerという関数で、イベントハンドリングが実現される。
* jQueryでいうところのon関数。
* 要素と関数は用意してあるので、addEventListenerでそれらを結びつけてほしい。
* 結びつけたら、円形をクリックしてみてほしい。
* 円形を震わせる処理が、クリックに結びついている。

---

### 3-2. DOMを扱う
* DOMを扱い、表示内容を変更することが出来る。
  * **DOM**（Document Object Model）:<br>HTML文書をJavaScriptから扱えるオブジェクトで表したもの
  * 👉 **アコーディオンやスライダーなど様々なUIを実現できる！**

notes:
* DOMを扱うことで、表示内容を自由に変更することができる。
* HTMLのclass属性を書き換えて、表示/非表示や位置を変化させられる。（例: 表示非表示->アコーディオン, 位置->スライダー）
* 要素を作成、挿入したり、削除したりもできる。
* イベントハンドリングと組み合わせて、任意のタイミングで実行できる。

---

#### 体験してみよう | 3-2. DOMを扱う
* <a href="https://codepen.io/dsktschy/pen/dyPGbKb" target="_blank">体験版CodePen</a>
  * 参考

```js

/**
 * Element # appendChild()
 * 対象要素の最後の子要素として、別の要素を挿入する。
 * 
 * 例: target要素の最後の子要素として、element要素を挿入する。
 */
target.appendChild(element)


```

* <a href="https://codepen.io/dsktschy/pen/NWPGmaK" target="_blank">完成版CodePen</a>

notes:
* DOM操作の一例として、要素挿入のappendChildを使用してみる。
* jQueryでいうところのappend関数。
* appendChildを使用して、コメントで指定された通りに、要素を要素に挿入してほしい。
* 挿入処理が書けたら、画面をクリックしてみてほしい。
* 複製された円形が、画面に追加されていく。

---

### 3-3. Ajax
* 任意のタイミングで、サーバーから情報を取得することが出来る。
  * **Ajax**（Asynchronous JavaScript + XML）:<br>JavaScriptによって、サーバーと情報の送受信を行う手法
    * 簡単にしてくれるライブラリもある（例: Axios）
  * 👉 **サーバーと連携ができる！**
  * 👉 **ここまでの概念の組み合わせでSPAも実現できる！**

notes:
* HTML上のlinkタグやscriptタグだけでなく、JavaScriptでも外部から情報を取得できる。
* 新しい表示内容を取得して、現在の表示内容と置き換えたり、
* 取得とは逆に、ユーザーの入力を外部に送信したりもできる。
* イベントハンドリングと組み合わせて、任意のタイミングで実行できる。

---

#### 体験してみよう | 3-3. Ajax
* <a href="https://codepen.io/dsktschy/pen/RwNrbJW" target="_blank">体験版CodePen</a>
  * 参考

```js

/**
 * fetch()
 * 指定されたURLに対してリクエストを送信する。
 * 
 * 例: https://sample.com/api/ に対してリクエストを送信する。
 *     成功した場合はonSuccess関数を実行し、
 *     失敗した場合はonFail関数を実行する。
 */
fetch('https://sample.com/api/')
  .then(onSuccess)
  .catch(onFail)


```

* <a href="https://codepen.io/dsktschy/pen/yLyYrzO" target="_blank">完成版CodePen</a>

notes:
* fetch関数を使用して、Ajaxを実現してみる。
* jQueryでいうところのajax関数。
* 後ろにthen関数とcatch関数をつなげ、成功時と失敗時に実行される関数を決める。
* コメントで指定されたとおりに、fetch関数を実行してみてほしい。
* 記述が完了したら、画面下のフォームに、適当な画像URLを入力し、右のApplyボタンを押してみてほしい。
* 次のページの画像を使用してくれてもかまわない。
* カラーパレット抽出サービスに画像URLを送信し、その結果を円形の色に反映している。

---

#### 画像URLサンプル | 3-3. Ajax

![プールで麻雀](https://liginc.co.jp/wp-content/themes/ligtheme/assets/images/introduction-media-contentcreation.jpg)

https://liginc.co.jp/wp-content/themes/ligtheme/assets/images/introduction-media-contentcreation.jpg

---

### 3-4. Canvas
* 2D、3Dのグラフィックの描画、画像の解析ができる。
  * **Canvas**: <br>グラフィックを扱うHTML要素。JavaScriptから操作する。
    * 簡単にしてくれるライブラリもある（例: PixiJS, three.js）
  * 👉 **かっこいい演出や、ゲームも実現できる！**

notes:
* HTMLのcanvas要素の範囲内に、自由に2D,3Dのグラフィックを描ける。
* 他のHTML要素と違い、複数の図形をcanvas要素1つで描画できる。
* ピクセル単位の細かな描画指示ができる。
* 描画とは逆に、画像を解析し、ピクセル単位の色情報を取得することもできる。
* イベントハンドリングと組み合わせて、任意のタイミングで実行できる。

---

#### 体験してみよう | 3-4. Canvas
* <a href="https://codepen.io/dsktschy/pen/BayjBVp" target="_blank">体験版CodePen</a>
  * 参考

```js

/**
 * HTMLCanvasElement # getContext()
 * canvas要素から、RenderingContextオブジェクトを生成する。
 * 
 * 例: canvas要素から、2dモードで、RenderingContextオブジェクトを生成し、
 *     生成されたオブジェクトを変数ctxに格納する。
 */
const ctx = canvas.getContext('2d')


```

* <a href="https://codepen.io/dsktschy/pen/povoJdm" target="_blank">完成版CodePen</a>

notes:
* Canvasを2dモードで利用開始してみる。
* コメントのとおりに、CanvasのRenderingContextオブジェクトを生成してみてほしい。
* 記述が完了したら、画面をクリックしてみてほしい。
* Canvasによって、モナリザの絵から1ピクセル毎の色情報が解析され、それを元に円形でモナリザが再現されていく。

---

### 3-5. WebAudioAPI（おまけ）
* 音の再生、生成、解析ができる。
  * **WebAudioAPI**: <br>音声を扱うための機能。JavaScriptから操作する。
    * 2020年1月現在、まだ標準化の途中。
  * 👉 **効果音再生や、音声を引き金とした処理の実行ができる！**

notes:
* これについては重要、必須というわけではないが、ここまで出来るという例として紹介しておく。
* 音声ファイルの再生、加工、解析ができる。
* 音声の生成も可能で、その生成物も再生、加工、解析できる。
* 既に広く利用されているが、まだ標準化しておらず、今後も仕様変更が予想されるため、注意が必要。
* イベントハンドリングと組み合わせて、任意のタイミングで実行できる。

---

#### 体験してみよう | 3-5. WebAudioAPI（おまけ）
* <a href="https://codepen.io/dsktschy/pen/wvBvKzV" target="_blank">完成版</a>
  * 参考

```js

/**
 * new AudioContext()
 * AudioContextオブジェクトを生成する。
 * 
 * 例: AudioContextオブジェクトを生成し、生成されたオブジェクトを変数ctxに格納する。
 */
const ctx = new AudioContext()


```

notes:
* CodePenをひらき、一度画面をクリックしたあと、拍手してみてほしい。
* WebAudioAPIの機能によって、音量が解析され、その大きさに応じて徐々に画像が描かれていく。

===

## 4. おわりに

---

### 4-1. まとめ
* JavaScriptで出来ることは、とても多い！
  * 👉 **JavaScript1つで、様々なことが実現できる！**
  * 👉 **JavaScript1つで、様々な分野に活躍のチャンスがある！**
* 👉👉👉👉👉👉👉👉 **JavaScriptは、楽しい！** 👈👈👈👈👈👈👈👈

notes:
* それ一つを習得するだけで、これだけ多くを実現できる言語は、いまのところ他にないと思います。
* JavaScriptに精通していれば、Webフロントエンドに限らず、サーバーサイドや、ネイティブアプリ開発など、様々な分野で活躍できる可能性がある。
* JavaScriptは、可能性を、短い期間で大きく広げてくれる、楽しい言語。

---

### 4-2. 注意
* ❌ JavaScriptさえあれば、他言語は不要。**ではない！**

notes:
* 実現内容によって、何を採用することが最適解なのかは異なる。
* JavaScriptに限らず、広く手段を持っている開発者の方が、更に可能性は広がる。

---

### 4-3. 次のステップ
* 3章の各コードを読解してみよう
* Node.jsを動かしてみよう

notes:
* 興味があれば、CodePenで一部だけ編集したコードについて、全体を読解してみる。
* Webブラウザ外のJavaScriptに触れるため、Node.jsで何かを作ってみる。
