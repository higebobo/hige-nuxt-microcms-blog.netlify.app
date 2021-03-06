# buta7-nuxt-microcms-blog.netlify.app

* 以下をベースに作成
    * [microCMS \+ NuxtでJamstackブログを作ってみよう](https://microcms.io/blog/microcms-nuxt-jamstack-blog/)
    * [NuxtのJamstack構成におけるページングの実装](https://microcms.io/blog/nuxt-jamstack-paging/)
* microcms:hige-blog:blog

## Build Setup

```shell
# create project
npx create-nuxt-app hige-nuxt-microcms-blog.netlify.app

cd hige-nuxt-microcms-blog.netlify.app

# serve with hot reload at localhost:3000
npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
npm run generate
```

追加モジュール

```shell
npm install --save axios
npm install --save node-sass sass-loader
npm install --save-dev @nuxtjs/dotenv
```

## 設定

### Microcms

* サービス登録
    * サービス名: hige-blog
    * サービスID: hige-blog.microcms.io
* APIの基本情報
    * API名: ブログ
    * エンドポイント: https://hige-blog.microcms.io/api/v1/blog
    * APIの型を選択: リスト形式
    * APIスキーマ
        * title/タイトル/テキストフィールド
        * body/本文/リッチエディタ

### Netlify

* Build settings
    * Repository: github
    * Build command: npm run generate
    * Publish directory: dist 
* 環境変数(.envも同様)
    * `API_KEY`: microcmsのAPI-KEY
    * `API_BASE_URL`: https://hige-blog.microcms.io/api/v1
* Webhook設定

### Microcms + Netlify

* NetlifyのWebhook(前述)を登録
    * API設定＞Webhook>Netlify

### カテゴリー実装

* APIの基本情報
    * API名: カテゴリー
    * エンドポイント: https://hige-blog.microcms.io/api/v1/categories
    * APIの型を選択: リスト形式
    * APIスキーマ
        * title/タイトル/テキストフィールド
        * body/本文/リッチエディタ

* ブログに上記を追加
    * APIスキーマ>追加
        * category/カテゴリー/コンテンツ参照・カテゴリー

## Link

* [最近話題のヘッドレスCMS「microCMS」\+Nuxtでサイトを作った話 \- Qiita](https://qiita.com/yutopia898/items/653068aa3d8237f3e89a)
* [NuxtのJamstack構成におけるAPIキーの隠蔽方法について](https://microcms.io/blog/nuxt-secure-api-key/)
    * ローカルで生成したものにはAPK_KEY等含まれるがデプロイしたものからは排除されている
