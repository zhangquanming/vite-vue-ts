# Vue 3 + Typescript + Vite 构建

## 全局安装

```bash
npm i -g create-vite-app
```

## 创建项目

```bash
# npm 6.x
npm init @vitejs/app vite_vue3_ts --template

# npm 7+, 需要额外的双横线：
npm init @vitejs/app vite_vue3_ts -- --template

# yarn
yarn create @vitejs/app vite_vue3_ts --template
```

> 选择 vue 回车 => vue-ts 回车

## Eslint 支持

```bash
# eslint 安装
yarn add eslint --dev

# eslint 插件安装
yarn add eslint-plugin-vue --dev

yarn add @typescript-eslint/eslint-plugin --dev

yarn add eslint-plugin-prettier --dev

# typescript parser
yarn add @typescript-eslint/parser --dev
```

注意: 如果 eslint 安装报错,可以尝试运行

```bash
yarn config set ignore-engines true
```

> 解决 ESLint 中的样式规范和 prettier 中样式规范的冲突，以 prettier 的样式规范为准，使 ESLint 中的样式规范自动失效。

```bash
# 安装 prettier
yarn add prettier --dev
# 安装插件 eslint-config-prettier
yarn add eslint-config-prettier --dev
```

### 项目下新建 .eslintrc.js

> 配置 eslint 校验规则:

```js
module.exports = {
  root: true,
  env: {
    browser: true,
    node: true,
    es2021: true,
  },
  parser: 'vue-eslint-parser',
  extends: [
    'eslint:recommended',
    'plugin:vue/vue3-recommended',
    'plugin:@typescript-eslint/recommended',
    'plugin:prettier/recommended',
    // eslint-config-prettier 的缩写
    'prettier',
  ],
  parserOptions: {
    ecmaVersion: 12,
    parser: '@typescript-eslint/parser',
    sourceType: 'module',
    ecmaFeatures: {
      jsx: true,
    },
  },
  // eslint-plugin-vue @typescript-eslint/eslint-plugin eslint-plugin-prettier的缩写
  plugins: ['vue', '@typescript-eslint', 'prettier'],
  rules: {
    // "@typescript-eslint/ban-ts-ignore": "off",
    // "@typescript-eslint/no-unused-vars": "off",
    // "@typescript-eslint/explicit-function-return-type": "off",
    // "@typescript-eslint/no-explicit-any": "off",
    // "@typescript-eslint/no-var-requires": "off",
    // "@typescript-eslint/no-empty-function": "off",
    // "@typescript-eslint/no-use-before-define": "off",
    // "@typescript-eslint/ban-ts-comment": "off",
    // "@typescript-eslint/ban-types": "off",
    // "@typescript-eslint/no-non-null-assertion": "off",
    // "@typescript-eslint/explicit-module-boundary-types": "off",
    // "no-var": "error",
    // // 结尾去分号
    'prettier/prettier': [
      'error',
      {
        semi: false,
      },
    ],
    // // 禁止出现console
    // "no-console": "warn",
    // // 禁用debugger
    // "no-debugger": "warn",
    // // 禁止出现重复的 case 标签
    // "no-duplicate-case": "warn",
    // // 禁止出现空语句块
    // "no-empty": "warn",
    // // 禁止不必要的括号
    // "no-extra-parens": "off",
    // // 禁止对 function 声明重新赋值
    // "no-func-assign": "warn",
    // // 禁止在 return、throw、continue 和 break 语句之后出现不可达代码
    // "no-unreachable": "warn",
    // // 强制所有控制语句使用一致的括号风格
    // curly: "warn",
    // // 要求 switch 语句中有 default 分支
    // "default-case": "warn",
    // // 强制尽可能地使用点号
    // "dot-notation": "warn",
    // // 要求使用 === 和 !==
    // eqeqeq: "warn",
    // // 禁止 if 语句中 return 语句之后有 else 块
    // "no-else-return": "warn",
    // // 禁止出现空函数
    // "no-empty-function": "warn",
    // // 禁用不必要的嵌套块
    // "no-lone-blocks": "warn",
    // // 禁止使用多个空格
    // "no-multi-spaces": "warn",
    // // 禁止多次声明同一变量
    // "no-redeclare": "warn",
    // // 禁止在 return 语句中使用赋值语句
    // "no-return-assign": "warn",
    // // 禁用不必要的 return await
    // "no-return-await": "warn",
    // // 禁止自我赋值
    // "no-self-assign": "warn",
    // // 禁止自身比较
    // "no-self-compare": "warn",
    // // 禁止不必要的 catch 子句
    // "no-useless-catch": "warn",
    // // 禁止多余的 return 语句
    // "no-useless-return": "warn",
    // // 禁止变量声明与外层作用域的变量同名
    // "no-shadow": "off",
    // // 允许delete变量
    // "no-delete-var": "off",
    // // 强制数组方括号中使用一致的空格
    // "array-bracket-spacing": "warn",
    // // 强制在代码块中使用一致的大括号风格
    // "brace-style": "warn",
    // // 强制使用骆驼拼写法命名约定
    // camelcase: "warn",
    // // 强制使用一致的缩进
    // indent: "off",
    // // 强制在 JSX 属性中一致地使用双引号或单引号
    // // 'jsx-quotes': 'warn',
    // // 强制可嵌套的块的最大深度4
    // "max-depth": "warn",
    // // 强制最大行数 300
    // // "max-lines": ["warn", { "max": 1200 }],
    // // 强制函数最大代码行数 50
    // // 'max-lines-per-function': ['warn', { max: 70 }],
    // // 强制函数块最多允许的的语句数量20
    // "max-statements": ["warn", 100],
    // // 强制回调函数最大嵌套深度
    // "max-nested-callbacks": ["warn", 3],
    // // 强制函数定义中最多允许的参数数量
    // "max-params": ["warn", 3],
    // // 强制每一行中所允许的最大语句数量
    // "max-statements-per-line": ["warn", { max: 1 }],
    // // 要求方法链中每个调用都有一个换行符
    // "newline-per-chained-call": ["warn", { ignoreChainWithDepth: 3 }],
    // // 禁止 if 作为唯一的语句出现在 else 语句中
    // "no-lonely-if": "warn",
    // // 禁止空格和 tab 的混合缩进
    // "no-mixed-spaces-and-tabs": "warn",
    // // 禁止出现多行空行
    // "no-multiple-empty-lines": "warn",
    // // 禁止出现;
    // semi: ["error", "never"],
    // // 强制在块之前使用一致的空格
    // "space-before-blocks": "warn",
    // // 强制在 function的左括号之前使用一致的空格
    // // 'space-before-function-paren': ['warn', 'never'],
    // // 强制在圆括号内使用一致的空格
    // "space-in-parens": "warn",
    // // 要求操作符周围有空格
    // "space-infix-ops": "warn",
    // // 强制在一元操作符前后使用一致的空格
    // "space-unary-ops": "warn",
    // // 强制在注释中 // 或 /* 使用一致的空格
    // // "spaced-comment": "warn",
    // // 强制在 switch 的冒号左右有空格
    // "switch-colon-spacing": "warn",
    // // 强制箭头函数的箭头前后使用一致的空格
    // "arrow-spacing": "warn",
    // "prefer-const": "warn",
    // "prefer-rest-params": "warn",
    // "no-useless-escape": "warn",
    // "no-irregular-whitespace": "warn",
    // "no-prototype-builtins": "warn",
    // "no-fallthrough": "warn",
    // "no-extra-boolean-cast": "warn",
    // "no-case-declarations": "warn",
    // "no-async-promise-executor": "warn",
  },
  globals: {
    defineProps: 'readonly',
    defineEmits: 'readonly',
    defineExpose: 'readonly',
    withDefaults: 'readonly',
  },
}
```

### 项目下新建 .eslintignore

```bash
# eslint 忽略检查 (根据项目需要自行添加)
node_modules
dist
```

### 项目下新建 .prettierrc.js

> 配置 prettier 格式化规则:

```js
module.exports = {
  tabWidth: 2,
  semi: false,
  arrowParens: 'always',
  printWidth: 100,
  tabWidth: 2,
  useTabs: false,
  semi: false, // 未尾逗号
  vueIndentScriptAndStyle: true,
  singleQuote: true, // 单引号
  quoteProps: 'as-needed',
  bracketSpacing: true,
  trailingComma: 'none', // 未尾分号
  jsxBracketSameLine: false,
  jsxSingleQuote: false,
  arrowParens: 'always',
  insertPragma: false,
  requirePragma: false,
  proseWrap: 'never',
  htmlWhitespaceSensitivity: 'strict',
  endOfLine: 'lf',
}
```

### 项目下新建 .prettierignore

```bash
# 忽略格式化文件 (根据项目需要自行添加)
node_modules
dist
```

### package.json 配置:

```json
{
  "script": {
    "lint": "eslint src --fix --ext .ts,.tsx,.vue,.js,.jsx",
    "prettier": "prettier --write ."
  }
}
```

上面配置完成后，可以运行以下命令测试下代码检查个格式化效果:

```bash
# eslint 检查
yarn lint
# prettier 自动格式化
yarn prettier
```

### 配置文件引用别名 alias

> 直接修改 vite.config.ts 文件配置:

```ts
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'
import * as path from 'path'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [vue()],
  resolve: {
    alias: {
      '@': path.resolve(__dirname, 'src'),
    },
  },
})
```

> ts：找不到模块“path”或其相应的类型声明，安装 node 类型文件

```bash
yarn add @types/node —D
```

> 修改 tsconfig.json

```js
{
  "compilerOptions": {
    // ...
    "paths": {
      "@/*": ["src/*"]
    }
  }
}
```

## 配置 css 预处理器 scss

### 安装

```bash
yarn add dart-sass --dev
yarn add sass --dev
```

### 配置全局 scss 样式文件

新建文件 `src/assets/styles/common.scss`

```scss
$test-color: red;
```

全局注入，配置 Vite:

```json
css:{
    preprocessorOptions:{
      scss:{
        additionalData:'@import "@/assets/style/mian.scss";'
      }
    }
  },
```

然后不需要任何引入可以直接使用全局 scss 定义的变量。

```scss
color: $test-color;
```

## 路由

```bash
# 安装路由
yarn add vue-router@4
```

在 `src` 文件下新增 `router` 文件夹 => `index.ts` 文件

```ts
import { createRouter, createWebHistory, RouteRecordRaw } from 'vue-router'

const routes: RouteRecordRaw[] = [
  {
    path: '/',
    name: 'Home',
    component: () => import('@/pages/home/Home.vue'),
  },
  {
    path: '/login',
    name: 'Login',
    component: () => import('@/pages/login/Login.vue'), // 注意这里要带上 文件后缀.vue
  },
]

const router = createRouter({
  history: createWebHistory(),
  routes,
})

export default router
```

修改入口文件 `main.ts` :

```ts
import { createApp } from 'vue'
import App from './App.vue'
import router from '@/router/index'

const app = createApp(App)
app.use(router).mount('#app')
```

`vue-router4.x` 支持 `typescript`，配置路由的类型是 `RouteRecordRaw`，这里 `meta` 可以让我们有更多的发挥空间，这里提供一些参考：

- `title:string`; 页面标题，通常必选。
- `icon?:string`; 图标，一般配合菜单使用。
- `auth?:boolean`; 是否需要登录权限。
- `ignoreAuth?:boolean`; 是否忽略权限。
- `roles?:RoleEnum[]`; 可以访问的角色
- `keepAlive?:boolean`; 是否开启页面缓存
- `hideMenu?:boolean`; 有些路由我们并不想在菜单中显示，比如某些编辑页面。
- `order?:number`; 菜单排序。
- `frameUrl?:string`; 嵌套外链。

## 封装请求

安装

```bash
# 安装 axios
yarn add axios
# 安装 nprogress 用于请求 loading
# 也可以根据项目需求自定义其它 loading
yarn add nprogress
# 类型声明，或者添加一个包含 `declare module 'nprogress'
yarn add @types/nprogress --dev
```

新增 `service` 文件夹，`service` 下新增 `http.ts` 文件以及 `api` 文件夹:

```ts
// http.ts
import axios, { AxiosRequestConfig } from 'axios'
import NProgress from 'nprogress'

// 设置请求头和请求路径
axios.defaults.baseURL = '/api'
axios.defaults.timeout = 10000
axios.defaults.headers.post['Content-Type'] = 'application/json;charset=UTF-8'

axios.interceptors.request.use(
  (config): AxiosRequestConfig<any> => {
    const token = window.sessionStorage.getItem('token')
    if (token) {
      config.headers.token = token
    }
    return config
  },
  (error) => {
    return error
  }
)
// 响应拦截
axios.interceptors.response.use((res) => {
  if (res.data.code === 111) {
    sessionStorage.setItem('token', '')
    // token过期操作
  }
  return res
})

interface ResType<T> {
  code: number
  data?: T
  msg: string
  err?: string
}
interface Http {
  get<T>(url: string, params?: unknown): Promise<ResType<T>>
  post<T>(url: string, params?: unknown): Promise<ResType<T>>
  upload<T>(url: string, params: unknown): Promise<ResType<T>>
  download(url: string): void
}

const http: Http = {
  get(url, params) {
    return new Promise((resolve, reject) => {
      NProgress.start()
      axios
        .get(url, { params })
        .then((res) => {
          NProgress.done()
          resolve(res.data)
        })
        .catch((err) => {
          NProgress.done()
          reject(err.data)
        })
    })
  },
  post(url, params) {
    return new Promise((resolve, reject) => {
      NProgress.start()
      axios
        .post(url, JSON.stringify(params))
        .then((res) => {
          NProgress.done()
          resolve(res.data)
        })
        .catch((err) => {
          NProgress.done()
          reject(err.data)
        })
    })
  },
  upload(url, file) {
    return new Promise((resolve, reject) => {
      NProgress.start()
      axios
        .post(url, file, {
          headers: { 'Content-Type': 'multipart/form-data' }
        })
        .then((res) => {
          NProgress.done()
          resolve(res.data)
        })
        .catch((err) => {
          NProgress.done()
          reject(err.data)
        })
    })
  },
  download(url) {
    const iframe = document.createElement('iframe')
    iframe.style.display = 'none'
    iframe.src = url
    iframe.onload = function () {
      document.body.removeChild(iframe)
    }
    document.body.appendChild(iframe)
  }
}
export default http
```

在 `api` 文件下新增 `login` 文件夹,用于存放登录模块的请求接口,`login` 文件夹下分别新增 `login.ts` 

```ts
// login.ts
import http from '@/service/http'
import * as T from './types'

const loginApi: T.ILoginApi = {
    login(params){
        return http.post('/login', params)
    }

}
export default loginApi
```

```ts
// types.ts
export interface ILoginParams {
    userName: string
    passWord: string | number
}
export interface ILoginApi {
    login: (params: ILoginParams)=> Promise<any>
}
```

## 状态管理 pinia

> 由于 vuex 4 对 typescript 的支持让人感到难过，所以状态管理弃用了 vuex 而采取了 pinia. pinia 的作者是 Vue 核心团队成员，尤大好像说 pinia 可能会代替 vuex。

## 环境变量

> vite 提供了两种模式：具有开发服务器的开发模式（development）和生产模式（production）

`.env.development`
```env
NODE_ENV=development
VITE_APP_WEB_URL= 'YOUR WEB URL'
```

 `.env.production`
```env
NODE_ENV=production
VITE_APP_WEB_URL= 'YOUR WEB URL'
```

组件中使用：
```js
console.log(import.meta.env.VITE_APP_WEB_URL)
```

配置 `package.json`:

> 打包区分开发环境和生产环境

```json
"build:dev": "vite build --mode development",
"build:pro": "vite build --mode production",
```

## Vite 常用基础配置

`运行` `代理` 和 `打包` 配置

```js
server: {
    host: '0.0.0.0',
    port: 3000,
    open: true,
    https: false,
    proxy: {}
},
```

生产环境去除 `console` 、`debugger`

```js
build:{
  // ...
  terserOptions: {
      compress: {
        drop_console: true,
        drop_debugger: true
      }
  }
}
```

### 生产环境生成 .gz 文件

> 开启 `gzip` 可以极大的压缩静态资源，对页面加载的速度起到了显著的作用。

使用 `vite-plugin-compression` 可以 `gzip` 或 `brotli` 的方式来压缩资源，这一步需要服务器端的配合，`vite` 只能帮你打包出 `.gz` 文件。此插件使用简单，你甚至无需配置参数，引入即可。

```bash
# 安装
yarn add --dev vite-plugin-compression
```

plugins 中添加：

```js
import viteCompression from 'vite-plugin-compression'

// gzip压缩 生产环境生成 .gz 文件
plugins: [
  // ...
  viteCompression({
    verbose: true,
    disable: false,
    threshold: 10240,
    algorithm: 'gzip',
    ext: '.gz',
  }),
]
```

## 参考文献

[Vite2 + Vue3 + TypeScript + Pinia 搭建一套企业级的开发脚手架](https://juejin.cn/post/7036745610954801166)
