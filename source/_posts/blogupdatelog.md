---
title: blogupdatelog
date: 2020-03-31 16:11:53
categories: hexo
summary: 博客更新说明
comments: true
 # password: a665a45920422f9d417e4867efdc4fb8a04a1f3fff1fa07e998e86f7f7a27ae3
tags:
- html
- github
---


## v1.0.1    
 - `20200331`
 - 更新说明
  -【新增】自动化部署(github action)

 - 配置说明
   1. 配置公钥和私钥
      私钥：settings/secrets(你的项目)
      公钥：settings/keys(主页)

```yml
name: 自动部署 Hexo
on: 
  push:
    branches:
      - master
jobs:
  build:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        node-version: [10.x]

    steps:
      - name: 开始运行
        uses: actions/checkout@v1

      - name: 设置 Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v1
        with:
          node-version: ${{ matrix.node-version }}

      - name: 配置 Git 环境
        env:
          ACTION_DEPLOY_KEY: ${{secrets.HEXO_DEPLOY_PRIVATE_KEY}}
        run: |
          mkdir -p ~/.ssh/
          echo "$ACTION_DEPLOY_KEY" > ~/.ssh/id_rsa
          chmod 600 ~/.ssh/id_rsa
          ssh-keyscan github.com >> ~/.ssh/known_hosts
          git config --global user.name "linxueyang"
          git config --global user.email "584790982@qq.com"

      - name: 安装 Hexo CI
        run: |
          npm i -g hexo-cli
          npm i

      - name: 安装插件
        run: |
          npm install hexo-asset-image --save
          npm install hexo-generator-archive --save
          npm install hexo-generator-category --save
          npm install hexo-generator-feed --save
          npm install hexo-generator-index --save
          npm install hexo-generator-tag --save
          npm install hexo-generator-search --save
          npm install hexo-helper-live2d --save
          npm install hexo-permalink-pinyin --save
          npm install hexo-prism-plugin --save
          npm install hexo-renderer-ejs --save
          npm install hexo-renderer-marked --save
          npm install hexo-renderer-stylus --save
          npm install hexo-deployer-git --save
          npm install live2d-widget-model-haruto --save
          npm install hexo-wordcount --save

      - name: 部署博客
        run: |
          hexo generate && hexo deploy # 执行部署程序
```