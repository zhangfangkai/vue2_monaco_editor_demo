# edit_pro2

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
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).


```
npm install monaco-editor@0.25.2 --save-dev 
npm install monaco-editor-webpack-plugin@4.1.1 --save-dev


首先注意monaco版本，以下版本可行
"monaco-editor": "^0.25.2",
"monaco-editor-webpack-plugin": "^4.1.1",


问题1：
引入的包如果换成 import * as monaco from "monaco-editor" 会有Error: Unexpected usage at EditorSimpleWorker.loadForeignModule，
换成'monaco-editor/esm/vs/editor/editor.api' 该错误消失，但是没有了高亮以及 editor.action.formatDocument 方法
解决办法：添加worker，参考https://github.com/microsoft/monaco-editor/blob/main/docs/integrate-esm.md#option-2-using-plain-webpack
self.MonacoEnvironment = {
    getWorkerUrl: function (moduleId, label) {
        return './json.worker.bundle.js';
	}
};
同时修改webpack.base.conf.js 
entry添加 'json.worker.bundle': 'monaco-editor/esm/vs/language/json/json.worker',

问题2：
一直报错 window is not defined window["webpackHotUpdate"]
修改webpack版本：
"webpack": "^3.5.1",
"webpack-dev-server": "^2.11.0",
```