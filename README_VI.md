# Cổng thông tin chống dịch CoVid-19 của TP Tokyo

![](https://github.com/stopcovid19-kyoto/covid19/workflows/production%20deploy/badge.svg)

[![Cổng thông tin chống dịch CoVid-19 của TP Kyoto unofficial](https://stopcovid19-kyoto.netlify.com/ogp.png)](https://stopcovid19-kyoto.netlify.com/)

### [日本語](./README.md) | [English](./README_EN.md) | [Spanish](./README_ES.md) | [Korean](./README_KO.md) | [Chinese (Taiwan)](./README_ZH_TW.md) | [Chinese (Simplified)](./README_ZH_CN.md) | [Vietnamese](./README_VI.md) | [Thai](./README_TH.md)

## Làm thế nào để đóng góp
Mọi đóng góp của các bạn đều được chào đón.
Xin vui lòng đọc [tại đây](./.github/CONTRIBUTING_VI.md) để biết thêm chi tiết.


## Quy tắc ứng xử
Chi tiết vui lòng xem [tại đây](./.github/CODE_OF_CONDUCT_VI.md)

## Giấy phép
Phần mềm này được phân phối dưới giấy phép [MIT](./LICENSE.txt)

## Thông tin cho nhà phát triển

### Xây dựng môi trường

- Node.js phiên bản: 10.19.0 hoặc cao hơn

**Nếu dùng yarn**
```bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev
```

**Nếu dùng docker compose**
```bash
# serve with hot reload at localhost:3000
$ docker-compose up --build
```
### Detect procition/others environment (translate me!)

On the production environment, `'production'` is assigned to `process.env.GENERATE_ENV` variable, on the other case `'development'` is assigned to the variable.
Please use the variable to detect which enviroinment is used at the runtime.

### Triển khai lên môi trường staging và production

Khi nhánh `master` được cập nhật, file HTML sẽ tự động được build dựa trên nhánh `production`. Sau đó https://stopcovid19-kyoto.netlify.com/ sẽ được cập nhật.

Khi nhánh `staging` được cập nhật, file HTML sẽ tự động được build dựa trên nhánh `gh-pages`. Sau đó https://stg-stopcovid19-kyoto.netlify.com/ sẽ được cập nhật.

Khi nhánh `development` được cập nhật, file HTML sẽ tự động được build dựa trên nhánh `dev-pages`. Sau đó https://dev-stopcovid19-kyoto.netlify.com/ sẽ được cập nhật.
