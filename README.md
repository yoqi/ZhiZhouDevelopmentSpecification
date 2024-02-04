# [ZhiZhou Development Specification](https://git.yoqi.me/zhizhou/ZhiZhouDevelopmentSpecification)


本项目根据十多年来的开发经验，总结目前在使用的各种编程语言的开发规范，并提供代码片段（vscode 代码提示）。


## 开发规范

通过 md 格式构建 vue docs pdf 等项目。

## 代码片段

## 参考：

https://developer.android.com/guide/index.html


## Develop

```
cd node_modules/gitbook-cli/node_modules/npm/node_modules/
npm install graceful-fs@latest --save
npm install -g gitbook-cli
gitbook fetch "4.0.0-alpha.6"
gitbook fetch "3.2.3"

gitbook init
gitbook install
gitbook build
- gitbook pdf .
- gitbook epub .
- gitbook mobi .

docker run -it --rm -v /workspace:/workspace -p 4000:4000 onejar99/gitbook:light_20200617 /bin/bash
cd /workspace/docs
yarn serve

```

## License

Copyright (c) 2021 [liuyuqi.gov@msn.cn](mailto:liuyuqi.gov@msn.cn). All rights reserved.

Licensed under the [Apache 2.0](LICENSE.md) license.


## Reference



