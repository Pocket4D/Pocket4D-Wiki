# Comparison of different solutions


## Hybrid solutions between Native+HTML/React-Native/Vue-Native/Flutter

| Characteristics   | Native+HTML             | React-Native      | Vue-Native        | Flutter     |
| :---------------- | :---------------------- | :---------------- | :---------------- | :---------- |
| Cross-platform    | Platform specific       | Yes               | Yes               | Yes         |
| Rendering Engine  | Web                     | Platform specific | Platform specific | Skia        |
| FPS               | about 30                | 30 - 60,45 avg    | 30 - 60,45 avg    | 60          |
| Plugins System    | No                      | Npm               | Npm               | Pub         |
| Script Language   | Native+JS               | Native+React      | Native+Vue        | Native+Dart |
| Dev Friendly      | Bad                     | Average           | Average           | Good        |
| Combatibilities   | Bad                     | Average           | Average           | Excellent   |
| Javascript Engine | Webview or Dev's choice | javascriptcore    | javascriptcore    | Not Embbed  |
| Dynamic Update    | No                      | No                | No                | No          |


## Mini-Program solutions between Wechat/Alibaba/Meituan/uni-app/Pocket4D

| Characteristics        | Wechat          | Alibaba         | Meituan         | ByteDance       | uni-app        | Pocket4D           |
| :--------------------- | :-------------- | :-------------- | :-------------- | :-------------- | :------------- | :----------------- |
| # Technical            | --              | --              | --              | --              | --             | --                 |
| Actual JSEngine        | V8/Jscore       | V8/Jscore       | V8/Jscore       | V8/Jscore       | V8/Jscore      | QuickJS/Jscore     |
| Rendering Engine       | WebView/Flutter | WebView/Flutter | WebView/Flutter | WebView         | Webview        | Flutter            |
| Flutter Interop        | DartNative      | FFI             | FFI             | --              | --             | FFI                |
| Core Open Source       | No              | No              | No              | No              | No             | Yes                |
| FrontEnd Style         | Vue/React       | Vue/React       | Vue/React       | Vue/React       | Vue/React      | Vue/React          |
| FrontEnd Open Source   | Yes             | Yes             | Yes             | Yes             | Yes            | Yes                |
| FrontEnd Storage       | Tencent Cloud   | Alibaba Cloud   | Meituan Cloud   | ByteDance Cloud | DCloud         | Private/Blockchain |
| Backend Provider       | Tencent Cloud   | Alibaba Cloud   | Meituan Cloud   | ByteDance Cloud | Private/DCloud | Private/Blockchain |
| Crypto Support         | No              | No              | No              | No              | No             | Yes                |
| # Eco-system && Market | --              | --              | --              | --              | --             | --                 |
| Dev Friendly           | Good            | Good            | Unknown         | Good            | Good           | Unknown            |
| Devs Number            | 200k            | 100k            | Small           | 100k            | Small          | Unknown            |
| Payment System         | WechatPay       | AliPay          | Multi           | Multi           | Multi          | Multi              |
| Market Region          | China           | China           | China           | Global          | China          | Global             |
| Bussiness Region       | All kinds       | All kinds       | E-Commerce      | Entertainment   | All kinds      | All kinds          |
| # Authorities          | --              | --              | --              | --              | --             | --                 |
| Regulatory Authority   | Wechat          | Alibaba         | Meituan         | ByteDance       | Unknown        | None               |
| Censorship             | Government      | Government      | Government      | Government      | Government     | None               |









