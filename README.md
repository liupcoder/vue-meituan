# vue-meituan
慕课Vue美团实战
## 实战准备
### 项目安装
```
npm install -g npx
```
```
npx create-nuxt-app project-name
```

![](https://raw.githubusercontent.com/liupcoder/PictureBed/master/img/20200111212323.png)
### Nuxt项目支持import写法的最新解决方案
* package.json 添加babel转换

```
--exec babel-node --presets @babel/env
```

* 根目录创建babel配置文件.babelrc

```
{
  "env": {
    "test": {
      "presets": [
        [
          "@babel/preset-env",
          {
            "targets": {
              "node": "current"
            }
          }
        ]
      ]
    }
  }
}
```

*  安装 babel-preset-es2015


```
npm install @babel/cli @babel/core @babel/preset-env @babel/node -D
```

* 重新执行 npn run dev 


```
npn run dev 
```

### 安装 Sass loader
```
npm i sass-loader node-sass
```

### 辅助工具安装
mongDB 
redis
robo 3T