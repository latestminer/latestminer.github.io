# Latest Miner

## 建站历程

### 初始化项目

```sh
$ hexo init latestminer
```

### 本地运行

```sh
$ cd latestminer # 切换到目录
$ yarn install # 安装依赖
$ yarn server # 运行项目
```

### 自动部署

懂得都懂，基于 GitHub Action 即可实现自动部署。

```yml
name: github pages
on:
  push:
    branches:
      - main # default branch
jobs:
  deploy:
    runs-on: ubuntu-18.04
    steps:
      - uses: actions/checkout@v2
        with:
          submodules: true # Checkout private submodules(themes or something else).
      - uses: c-hive/gha-yarn-cache@v2
      - run: yarn install
      - run: yarn build
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

## 站点基础配置

`_config.yml` 中是站点的配置，改了什么请参考 http://tny.im/4jBq。

## 插件配置

### baidu-sitemap