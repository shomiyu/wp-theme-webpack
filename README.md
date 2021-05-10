# wp-theme-webpack

このリポジトリは Webpack を使用する WordPress 開発用テーマです。下記を使用します。

```
- yarn
```

## パッケージ

```
- fortawesome
- ress
- babel
- autoprefixer
- node-sass
- webpack
```

## セットアップ

### プロジェクトインストール

**WordPress の themes 直下**に、下記のコマンドでリポジトリをクローンします。`project-theme-name`の部分はプロジェクトに合わせて変更してください。

```sh
git clone https://github.com/shomiyu/wp-theme-webpack.git project-theme-name
```

クローンができたらディレクトリ内に移動し、package.json に従って各モジュールのインストールをします。

```sh
cd project-theme-name
yarn install
```

### 初期設定

あとから変更すると管理画面にアクセスできなくなるなどのトラブルになりかねないので事前に修正します。

#### 納品フォルダ名の編集

最終的に納品するフォルダの名称を修正します。`project-theme-name`の部分をプロジェクトに合わせて変更してください。

```sh
mv theme-name project-theme-name
```

Webpack によりバンドルされるファイルの吐き出し先の指定を修正します。`/project.json`を開き、先ほどリネームしたディレクトリ名に修正します。

```json
{
  "paths": {
    "dist": "project-theme-name"
  }
}
```

### 開発環境立ち上げ

WordPress の管理画面から 外観 > テーマ と進み、テーマを有効化します。

下記のコマンドで開発環境のプロジェクトを立ち上げます。立ち上げ後はファイルを更新してリロードする度に反映されます。

```sh
yarn dev
```

`control + C`で開発環境を停止します。

### 納品・デプロイ

開発環境を立ち上げている場合は停止し、minify 版を出力するためビルドします。

```sh
yarn build
```

`./theme-name` を zip で固めるか FTP か CI ツールでアップロードします。

## プロジェクトツリー

```
.
├── README.md
├── webpack.config.js
├── project.json
├── postcss.config.js
├── package.json
├── src
│   ├── js
│   │    ├── modules
│   │    └── project.js
│   └── scss
│        ├── foundation
│        ├── inc
│        ├── layout
│        ├── object
│        └── project.scss
└── theme-name
    ├── index.php
    ├── style.css
    ├── editor-style.css
    ├── screenshot.png
    ├── functions.php
    ├── functions
    └── assets
         ├── images
         └── build
```
