# ts-lib-basic

使用 TypeScript 快速编写一个应用库，提供了一套基础项目骨架目录，集成了基础工具（编译、测试、文档托管）。[https://peacelovea.github.io/ts-lib-basic/](https://peacelovea.github.io/ts-lib-basic/)。

将本仓库 clone 到本地，可作为一个新的库骨架。

更多细节请参考博客 《[写一个完整的 JavaScript 库](https://tasaid.com/blog/2018122819513079.html)》。

----


## 快速开始

### 安装

```bash
npm i --save ts-lib-basic
# or
yarn add ts-lib-basic --save
```

### 使用

`app.ts`:

```ts
import * as express from 'express'

const app = express()
app.use(middleware)

app.get('/example', (req, res) => {
  res.send(res.locals)
})

ex.listen(3000, () => {
  console.log('Example app listening on port 3000!')
})

// 访问 localhost:3000/example 即可
```

## API


### default

`ts-lib-basic` 默认导出如下：

```ts
// es6 模块
import middleware from 'ts-lib-basic'
```

| 参数 | 类型 | 描述 |
| --- | --- | --- |
| xxxx | string | 参数详细描述 |


示例：

```ts
import middleware from 'ts-lib-basic'
import * as express from 'express'

const app = express()
app.use(middleware)

```


## bug 追踪

`ts-lib-basic` 使用了 [debug](https://github.com/visionmedia/debug) 模块来进行 bug 追踪，在运行 node 应用程序之前，在环境变量中注入 `DEBUG=ts-lib-basic*` 即可在终端 shell 中看到 debug 信息：

```bash
# 一般启动
$env:DEBUG='ts-lib-basic*';node app.js
# 或者
DEBUG=ts-lib-basic* node app.js


# ts-node
DEBUG=ts-lib-basic* ts-node app.ts
```

完整的 debug 命名空间参考：

| 命名空间 | 说明 |
| --- | --- |
| ts-lib-basic:app | 应用程序基本调试信息打开 |

如果 debug 信息较大，debug 信息较大，需要过滤层次，请设置 [DEBUG_DEPTH](https://github.com/visionmedia/debug#environment-variables)。

## 开发和编译

项目目录结构：

```bash
.
├── .vscode           # vscode 配置
│   └── launch.json   # vscode 调试配置
├── dist              # 编译产出目录，编译后才有
├── src               # 源码
├── tests             # 单元测试
├── .gitignore        # git 忽略文件
├── .npmrc            # npm 配置
├── .travis.yml       # 持续集成
├── LICENSE           # 开源协议
├── README.md         # README
├── package-lock.json # npm 锁定依赖
├── package.json      # npm
├── tsconfig.json     # typescript 配置
└── tslint.json       # tslint 校验
```

提供了多个编译脚本。

### 构建

```bash
# 构建产出 dist 包，用于发布
npm run build

# 监听 src 文件夹，并实时编译产出 dist 包
npm run build:w
```

### 开发测试

```bash
# 完整测试，并在 tests 目录下产出 coverage 目录（完整测试报告）
npm run test

# 监听 tests 文件夹并实时进行单元测试
npm run test:w

# 运行 tests/app.ts
npm run test:e
```

### 调试

两种调试方式：

- `npm run test:e` 运行 `test/app.ts`，直接运行程序
- 使用 vscode：`调试` => `启动调试(F5)`，支持断点


## 文档

在 `docs/` 文件夹下直接写 Markdown 文件即可。文档使用 [VuePress](https://vuepress.vuejs.org/zh/) 进行编译。执行 `npm run docs` 可以实时预览文档。

执行 `npm run docs:build` 可以编译产出最新文档，提交到 Github。

点击项目 `Setting` 中，在 GitHub Pages 中，将 **Source** 修改为 **master branch/docs folder**（选择 docs/ 作为目录）。

然后访问 `https://<USERNAME or GROUP>.gitlab.io/<REPO>/` 即可。

## 持续集成

默认配置了在 master 代码提交的时候自动执行 `npm run test`。

在 [travis-ci](https://travis-ci.org/) 可以打开持续集成服务。


----

更多细节请参考博客 《[写一个完整的 JavaScript 库](https://tasaid.com/blog/2018122819513079.html)》。


## Release history

### 2019-07-29 1.1.0

- [feature] 加入 `git commit` 规范

### 2018-12-27 1.0.0

正式发布

- [feature] 初始化项目骨架
- [feature] 初始化测试脚本
- [bugfix] xx bug(#0) 修复