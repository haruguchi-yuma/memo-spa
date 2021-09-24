# Memo App
Vue CLIで実装したSPA版のメモ管理アプリケーションです。

# 使い方
このアプリケーションではメモの一覧表示・詳細表示・追加・編集・削除ができます。

## 一覧表示モード
一覧表示モードではメモの最初の1行がリスト形式で表示されます。
また、「＋」をクリックすることで「新規メモ」という名前のメモが作成され後述するメモ編集モードに移行します。
https://gyazo.com/4f36ac05255dc7ab85133185dfe806f0

## 編集モード
メモをクリックすると編集モードになります。
メモの編集モードではメモの編集、削除ができます。

https://gyazo.com/24e74a29b9b15568a1a2b66e9422594d

# ローカル環境での実行方法
```bash
$ git clone https://github.com/haruguchi-yuma/memo-spa
$ cd memo-spa
$ npm run serve

ブラウザでhttp://localhost:8080へアクセス
```

