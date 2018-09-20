# vue + webpack フロント開発環境

## 環境セットアップ

### nodenvセットアップ
```
$ brew install nodenv
$ nodenv init
$ nodenv install 8.11.4
```

### node設定
```
$ nodenv local 8.11.4
$ npm init
This utility will walk you through creating a package.json file.
...
```

### webpack, vue, sassなど関連パッケージインストール
```
$ npm install --save vue
$ npm install --save-dev webpack webpack-cli webpack-dev-server
$ npm install --save-dev vue-loader vue-template-compiler css-loader
$ npm install --save-dev babel-loader babel babel-core babel-preset-es2015
$ npm install --save-dev sass-loader node-sass style-loader postcss-loader
```

### scssをwebpackでビルドする
webpack4系ではmini-css-extract-pluginを利用する。
(extract-text-webpack-pluginはwebpack3まで)

```
$ npm install --save-dev mini-css-extract-plugin
```

### トラブルシュート

#### webpackを実行して、以下のエラー
```
ERROR in ./assets/javascripts/Top.vue
Module Error (from ./node_modules/vue-loader/lib/entry.js):
vue-loader was used without the corresponding plugin. Make sure to include VueLoaderPlugin in your webpack config.
```

webpack.config.jsに以下の記述を追加
```
const VueLoaderPlugin = require('vue-loader/lib/plugin')
...
    plugins: [
        new VueLoaderPlugin()
    ]
...
```