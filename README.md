# Vue 3 + Typescript + Vite 构建

## 全局安装

```shell
npm i -g create-vite-app
```

## 创建项目

```shell
# npm 6.x
npm init @vitejs/app vite_vue3_ts --template

# npm 7+, 需要额外的双横线：
npm init @vitejs/app vite_vue3_ts -- --template

# yarn
yarn create @vitejs/app vite_vue3_ts --template
```

> 选择 vue 回车 => vue-ts 回车

## Eslint 支持

```shell
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

```shell
yarn config set ignore-engines true
```

> 解决 ESLint 中的样式规范和 prettier 中样式规范的冲突，以 prettier 的样式规范为准，使 ESLint 中的样式规范自动失效。

```shell
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
  parser: "vue-eslint-parser",
  extends: [
    "eslint:recommended",
    "plugin:vue/vue3-recommended",
    "plugin:@typescript-eslint/recommended",
    "plugin:prettier/recommended",
    // eslint-config-prettier 的缩写
    "prettier",
  ],
  parserOptions: {
    ecmaVersion: 12,
    parser: "@typescript-eslint/parser",
    sourceType: "module",
    ecmaFeatures: {
      jsx: true,
    },
  },
  // eslint-plugin-vue @typescript-eslint/eslint-plugin eslint-plugin-prettier的缩写
  plugins: ["vue", "@typescript-eslint", "prettier"],
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
    "prettier/prettier": ["error", { semi: false }],
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
    defineProps: "readonly",
    defineEmits: "readonly",
    defineExpose: "readonly",
    withDefaults: "readonly",
  },
}
```

### 项目下新建 .eslintignore

```shell
# eslint 忽略检查 (根据项目需要自行添加)
node_modules
dist
```

### 项目下新建 .prettier.js

> 配置 prettier 格式化规则:

```js
module.exports = {
  tabWidth: 2,
  jsxSingleQuote: true,
  jsxBracketSameLine: true,
  printWidth: 100,
  singleQuote: true,
  semi: false,
  overrides: [
    {
      files: "*.json",
      options: {
        printWidth: 200,
      },
    },
  ],
  arrowParens: "always",
}
```

### 项目下新建 .prettierignore

```shell
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

```shell
# eslint 检查
yarn lint
# prettier 自动格式化
yarn prettier
```