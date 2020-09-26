# 小程序解决方案对比

## 混合开发方案对比：Native+HTML/React-Native/Vue-Native/Flutter

| 特点           | Native + HTML | React-Native    | Vue-Native      | Flutter       |
| :------------- | :------------ | :-------------- | :-------------- | :------------ |
| 跨平台         | 仅限特定平台  | 是              | 是              | 是            |
| 渲染系统       | Web           | 仅限特定平台    | 仅限特定平台    | Skia          |
| 帧率（FPS）    | 约30          | 30 - 60，平均45 | 30 - 60，平均45 | 60            |
| 插件系统       | 无            | Npm             | Npm             | Pub           |
| 开发语言       | Native + JS   | Native + React  | Native + Vue    | Native + Dart |
| 开发友好度     | 差            | 一般            | 一般            | 好            |
| 兼容性         | 差            | 一般            | 一般            | 极好          |
| JavaScript引擎 | Webview或其他 | JavaScriptCore  | JavaScriptCore  | 无嵌入        |



## 小程序解决方案对比：Wechat/Alibaba/Meituan/uni-app/Pocket4D

| 特点                | 微信            | 阿里巴巴        | 美团            | 字节跳动       | uni-app                 | Pocket4D          |
| :------------------ | :-------------- | :-------------- | :-------------- | :------------- | :---------------------- | :---------------- |
| # 技术              | --              | --              | --              | --             | --                      | --                |
| 内核引擎            | V8/Jscore       | V8/Jscore       | V8/Jscore       | V8/Jscore      | V8/Jscore               | QuickJS/Jscore    |
| 渲染引擎            | WebView/Flutter | WebView/Flutter | WebView/Flutter | WebView        | Webview                 | Flutter           |
| 与Flutter的互操作性 | DartNative      | FFI        | FFI        | --             | --                      | FFI          |
| 核心代码开源        | No              | 否              | 否              | 否             | 否                      | 是                |
| 前端样式            | Vue/React       | Vue/React       | Vue/React       | Vue/React      | Vue/React               | Vue/React         |
| 前端开源            | 是              | 是              | 是              | 是             | 是                      | 是                |
| 前端资源存储方式    | 腾讯云          | 阿里云          | 美团服务器      | 字节跳动服务器 | DCloud服务器            | 私有化部署/区块链 |
| 后端存储方式        | 腾讯云          | 阿里云          | 美团服务器      | 字节跳动服务器 | 私有化部署/DCloud服务器 | 私有化部署/区块链 |
| # 生态系统及市场    | --              | --              | --              | --             | --                      | --                |
| 开发友好度          | 好              | 好              | 未知            | 好             | 好                      | 有待公开          |
| 程序数量            | 20万            | 10万            | 少量            | 10万           | 少量                    | 未知              |
| 支付方式            | 微信支付        | 支付宝          | 多种方式        | 多种方式       | 多种方式                | 多种方式          |
| 支持加密币          | 不支持          | 不支持          | 不支持          | 不支持         | 不支持                  | 支持              |
| 市场区域            | 中国            | 中国            | 中国            | 全球           | 中国                    | 全球              |
| 行业                | 全行业          | 全行业          | 电商            | 媒体           | 全行业                  | 全行业            |
<!-- | 授权机构          | --              | --              | --              | --             | --                      | --                | -->
| 监管机构            | 微信            | 阿里巴巴        | 美团            | 字节跳动       | 未知                    | 无                |
| 审查机构            | 政府            | 政府            | 政府            | 政府           | 政府                    | 无                |
