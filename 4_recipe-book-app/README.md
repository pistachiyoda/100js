# 4.recipe book app
レシピデータは楽天レシピ系APIを利用させてもらってます。
https://webservice.rakuten.co.jp/

.envファイルを作成し、楽天で作成したアプリケーションIDを設定すると情報を取得することができます。
```
VITE_APPLICATION_ID=1234567890
```

```js:App.vue
const applicationId = import.meta.env.VITE_APPLICATION_ID;
```


# Project Setup

```sh
npm install
npm run dev
npm run build
```