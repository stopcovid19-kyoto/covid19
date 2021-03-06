# 京都府 非公式 新型冠狀病毒疫情中心

![](https://github.com/stopcovid19-kyoto/covid19/workflows/production%20deploy/badge.svg)

[![京都府 非公式 新型冠狀病毒疫情中心](https://stopcovid19-kyoto.netlify.com/ogp.png)](https://stopcovid19-kyoto.netlify.com/)

### [日本語](./README.md) | [English](./README_EN.md) | [Spanish](./README_ES.md) | [Korean](./README_KO.md) | [Chinese (Taiwan)](./README_ZH_TW.md) | [Chinese (Simplified)](./README_ZH_CN.md) | [Vietnamese](./README_VI.md) | [Thai](./README_TH.md)


## 如何貢獻
如果您能對 Issues 中做出各式各樣的修正協助，我們將不勝感激。

詳情請洽[如何貢獻](./.github/CONTRIBUTING_ZH_TW.md)。


## 行動原則
詳情請洽[建立網站的行動原則](./.github/CODE_OF_CONDUCT_ZH_TW.md)。

## 授權
本軟體採 [MIT 授權條款](./LICENSE.txt)釋出。

## 從這個網站衍生出來的東西

請參考[此連結](https://github.com/codeforsapporo/covid19)

## 給開發者的資訊

### 開發環境建置

- Node.js 版本最低需求：10.19.0 以上

**使用 yarn 的做法**
```bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev
```

**使用 docker compose 的做法**
```bash
# serve with hot reload at localhost:3000
$ docker-compose up --build
```

### 被 `Cannot find module ****` 卡住時

**使用 yarn 的做法**
```
$ yarn install
```

**使用 docker compose 的做法**
```bash
$ docker-compose run --rm app yarn install
```
### 生產環境/其他環境的判定

關於 `process.env.GENERATE_ENV` 這個值 ,生產環境為 `'production'` ，除此之外為 `'development'` 。
如果只想要在測試環境中執行的話，請利用這個值作為參考。

### Deploy 到 Staging 環境以及正式環境的方法

當 `master` 分支被更新時，HTML 檔案將會在 `production` 分支中被 build 起來，然後正式版網站 https://stopcovid19-kyoto.netlify.com/ 會被更新。

當 `staging` 分支被更新時，HTML 檔案將會在 `gh-pages` 分支中被 build 起來，然後 Staging 版網站 https://stg-stopcovid19-kyoto.netlify.com/ 會被更新。

當 `development` 分支被更新時，HTML 檔案將會在 `dev-pages` 分支中被 build 起來，然後開發版網站 https://dev-stopcovid19-kyoto.netlify.com/ 會被更新。
