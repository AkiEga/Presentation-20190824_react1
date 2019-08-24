# 【初心者向け】みんなで学ぼうReact 勉強会
## 自己紹介
- 出身&来歴: 
```
AD198x: 千葉に生まれる
AD2007: 大学@東京 
AD2011: 大学院@東京 
AD2013: とある自動車部品メーカー@愛知に就職 
AD2019: 東京🗼へ転勤　←いまココ 
```
<br>

- 守備範囲: 
  - 組み込み(C/C++, RTOS, ハードウェア(少々))、
  - 並列処理(CUDA, OpenMP)、
  - 画像処理(OpenCV, OpenGL)、
  - Web系(javascript/AltJS, Electron, React/Vue, node.js)

- 趣味
  - キーボード収集&自作
  
## この勉強会について
### 対象者
↓こんな方々(自分も含む)
- "どこから手を付ければ良いか分からない"
- ”勉強してみたいけど、一人だと中々身に入らない"
- "環境構築で躓いてふて寝した"
  
### 参加者へのお願い事
- なるべく会話しながら進めてゆきたいです。途中での質問大歓迎です！  
  "自分の疑問はみんなの疑問" 是非共有させてください。
- 
    
## 本題(React 勉強会)
### 1. Reactとは?
Reactはfacebook製の世界的にフロントエンドフレームワークの一つです。  

#### 1.1 フロントエンドとは?
そもそもに**フロントエンド**とは何でしょうか?

webアプリケーションの世界において下記構図の様に  
ユーザー側PCとサーバー側PCが協調し実現されます。

```js
ユーザー側PC // フロントエンド  
  ↑  
  ↓  
サーバー側PC // バックエンド
```

この時ユーザー側PCとサーバー側PCを フロントエンド、バックエンドと称します。

#### 1.1 フロントエンドの発展
例えば、みなさんがブラウザを何気なくアクセスする時下記の処理がなされています

**&lt;登場人物&gt;**
- ユーザー側PC
  - browser

- サーバー側PC
  - backend program

**&lt;流れ&gt;**
```
// Webサイトアクセス開始
browser->backend program: .html, .js, .cssファイル送信

// ログイン画面表示
browser->browser: 受信したファイルを元にレンダリング


// ログイン実施
browser->backend program: ログイン情報送信(id, pass)
backend program->backend program: ログイン情報照会

// ログイン成功
browser->backend program: .html, .js, .cssファイル送信

browser->backend program: ユーザー操作
browser->backend program: .html, .js, .cssファイル送信
// 以降ループ
// :
```

元々2000年前半までは、バックエンド側が頑張って演算し、リッチで大量なhtmlファイル等を配信していました。  
しかし、上記の様にユーザー操作のたびに何度もファイルを送受信するのは帯域やレスポンス的に手間です。  
  
なのでユーザー側である程度自前で演算しhtmlファイルを動的に変化させるSPA(Single Page Application)というトレンドができました。  
  
このSPAをフロントエンド側で実現させるにあたり効率的に行う手段が **フロントエンドフレームワーク** です。  

#### 1.2 フロントエンドフレームワークの登場
フロントエンドフレームワークは下記３つがあります

- [Angular](https://angular.jp/): 大規模にガッツリとやりたい人向け
  - google製フレームワーク。
  - 幅広い機能がサポートされているが、その分実装コストも大きい

- [Vue.js](https://jp.vuejs.org/): 比較的コンパクトにとサックリやりたい人向け
  - [OSSコミュニティ](https://jp.vuejs.org/v2/guide/team.html)で発展したフレームワーク。
  - 日本語ドキュメントが豊富
  - Angularと比較して機能は絞られているが、その分実装コストは小さい

- [React](https://ja.reactjs.org/): 上記2つの中間 **←今回はコレ!**
  - facebook製フレームワーク。
  - 一番対応コンポーネントが世の中に出てる印象
    [19 Best React UI Component Libraries / Frameworks for 2019](https://www.codeinwp.com/blog/react-ui-component-libraries-frameworks/)

### 2. 環境構築
0. 開発環境用意  
  下記サイトから最新版をdownload & install  
  [Visual Studio Code – コード エディター | Microsoft Azure](https://azure.microsoft.com/ja-jp/products/visual-studio-code/)

1. node.js  
  下記サイトからLTS(Long Term Support) 版をdownload & install  
  [Node.js](https://nodejs.org/ja/)   

2. Reactアプリ作成ツール(create-react-app)  
  下記サイトの要領でcreate-react-appを導入   
  [新しい React アプリを作る – React](https://ja.reactjs.org/docs/create-a-new-react-app.html)

### 3. サンプルアプリによるReact体験
まずははじめに触ってみましょう♪

```shell
cd <Reactアプリケーションを作りたいお好みの場所>
npx create-react-app <アプリケーション名>
npm start
```

#### 3.1 中身ではどうやっているのか
上記手順で作成した[サンプルアプリケーション](https://github.com/AkiEga/Presentation-20190824_react1_Appendix1_hello_react) をベースに解説します
処理の流れは下記です。

**処理の流れ**
- Step1. html表示  
  file: [./public/index.html](https://github.com/AkiEga/Presentation-20190824_react1_Appendix1_hello_react/blob/master/public/index.html)  
  ```html
  <div id="root"></div>
  ```
↓
- Step2. htmlに紐付けられたjs実行→React製コンポーネント起動  
  file: [./src/index.js](https://github.com/AkiEga/Presentation-20190824_react1_Appendix1_hello_react/blob/master/src/index.js)  
  ```js
  ReactDOM.render(<App />, document.getElementById('root'));
  ```
↓
- Step3. React製コンポーネントの描画実施  
  file: [./src/App.js](https://github.com/AkiEga/Presentation-20190824_react1_Appendix1_hello_react/blob/master/src/App.js)  
  ```js
  function App() {
    return (
      <div className="App">
        <header className="App-header">
          <img src={logo} className="App-logo" alt="logo" />
          <p>
            Edit <code>src/App.js</code> and save to reload.
          </p>
          <a
            className="App-link"
            href="https://reactjs.org"
            target="_blank"
            rel="noopener noreferrer"
          >
            Learn React
          </a>
        </header>
      </div>
    );
  }
  ```

ちなみにロゴがくるくる回っているのは  

file: [./src/App.js](https://github.com/AkiEga/Presentation-20190824_react1_Appendix1_hello_react/blob/master/src/App.js)  
```js
import './App.css';
```
↓  
file: [./src/App.css](https://github.com/AkiEga/Presentation-20190824_react1_Appendix1_hello_react/blob/master/src/App.css)  
```css
.App-logo {
  animation: App-logo-spin infinite 20s linear;
  height: 40vmin;
  pointer-events: none;
}
```
と書かれているからです

### 4. React用コンポーネント自作
3章で雰囲気はつかめたと思うので、ここからはReact公式サイトのチュートリアルから説明してゆきます  
  
[チュートリアル：React の導入 – React](https://ja.reactjs.org/tutorial/tutorial.html)
    
