# tiny-oss

用于浏览器端的阿里云 OSS 极简版 SDK。小于 10kb (min+gzipped)

**[English](README.md) | 简体中文**

## 安装

Npm

```sh
npm install tiny-oss
```

Yarn

```sh
yarn add tiny-oss
```

## 使用

```js
const oss = new TinyOSS({
  accessKeyId: 'your accessKeyId',
  accessKeySecret: 'your accessKeySecret',
  region: 'oss-cn-beijing',
  bucket: 'your bucket'
});

const blob = new Blob(['hello world'], { type: 'text/plain' });

// 上传
oss.put('hello-world', blob);
```

## 兼容性

这个包依赖一些现代 Web APIs，比如 [Blob](https://developer.mozilla.org/zh-CN/docs/Web/API/Blob), [Uint8Array](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Uint8Array), [FileReader](https://developer.mozilla.org/zh-CN/docs/Web/API/FileReader), [Promise](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise).

所以应该在下面浏览器当中都能正常运行。

* Chrome >= 20
* Edge >= 12
* IE >= 10
* Firefox >= 4
* Safari >= 8
* Opera >= 11
* Android >= 4.4.4
* iOS >= 8

**对于 IE 和低版本 Firefox（<= 28），你需要引入 Promise polyfill，比如 [es6-promise](https://github.com/stefanpenner/es6-promise)**。

## 接口

```js
new TinyOSS(options)
```

### options

请参考[Browser.js 官方文档](https://help.aliyun.com/document_detail/64095.html?spm=a2c4g.11186623.6.1122.27976928XhTpTr)关于配置项的说明。

* accessKeyId
* accessKeySecret
* bucket
* endpoint
* region
* internal
* secure
* timeout

### put(objectName, blob)

上传。

#### 参数

* **objectName (String)**：对象名称。
* **blob (Blob|File)**: 被上传的对象。

#### 返回值

* **(Promise)**

### signatureUrl(objectName, options)

获取一个签名的 URL，可用于下载文件。

#### 参数

* **objectName (String)**: 对象名称。
* **[options (Object)]**:
  + **[options.expires (Number)]**: URL 过期时间（单位：秒）。

#### 返回值

* **(String)**

## 许可证协议

MIT