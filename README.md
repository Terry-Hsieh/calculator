# calculator

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm test
```
## 疑難雜症
``` bash
**vue 使用ngrok 跳出 Invalid Host Header 
則解決辦法為在 在webpack.dev.conf.js的devServer配置中添加disableHostCheck: true
devServer: {
   ...
    disableHostCheck: true,
  },
其原因為因為安全考量，默認檢查hostname，如果不是配置內的，將取消訪問

indexof 如果裡面沒有 . 就會回傳-1 為了不要太多點
(a,b) => a / b = function(a,b){ return a/b;} 箭頭函數
${}會等於串聯,- + this current
=== 嚴格相等 this.current.charAt(0) === '-' 就做接下來的事

.mymouse{ #滑鼠樣式
  cursor: help;
}


```
For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
