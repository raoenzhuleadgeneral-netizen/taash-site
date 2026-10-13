# Taash Guide — SEO 实验站

印度纸牌游戏规则与概率站。纯静态，全平级文件，零构建依赖。

## 文件

```
index.html         首页（URL: /）
teen-patti.html    Teen Patti 规则页（URL: /teen-patti，Cloudflare 自动去掉 .html）
sitemap.xml
robots.txt
build.py           生成器：算概率 + 生成上面的 html（部署不依赖它，保留作方法记录）
README.md
```

## 改域名后重新生成（可选）

打开 `build.py`，把第 1 节的 `SITE_URL` 改成你的真实域名（结尾不带斜杠），
然后 `python3 build.py`，把 `dist/` 里新生成的 html 覆盖上传。

## 部署到 Cloudflare Pages（无需构建）

1. 这些文件已在 GitHub 仓库根目录
2. Cloudflare → Workers & Pages → Create → Pages → 连接仓库
3. 构建设置：
   - Framework preset: **None**
   - Build command: **留空**
   - Build output directory: **/**
4. 部署后用 `*.pages.dev` 临时域名验证，再在 Custom domains 绑定真实域名

## 之后扩展

加新游戏 = 在 `build.py` 里仿照 `build_teen_patti()` 写一个页面函数，
加进 `main()` 的文件列表，本地跑一次，把新 html 上传。

## 原则

- 概率一律在 `build.py` 里用代码算，不手写数字。
- 每页必须有独有价值。
- 不放任何真钱平台链接，纯规则与数学。
