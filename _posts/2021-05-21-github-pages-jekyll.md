---
layout: post
title: "github pages + jekyll 搭建博客"
subtitle: "github pages + jekyll 搭建博客"
date: 2021-05-21
author: "WaHaoo"
header-img: "img/post/post-bg-miui6.jpg"
mathjax: false
tags:
    - github pages
    - jekyll
---


# github pages + jekyll 搭建博客

> [维基百科](https://zh.wikipedia.org/wiki/GitHub_Pages)：GitHub Pages是GitHub提供的一个网页寄存服务，于2008年推出。可以用于存放静态网页，包括博客、项目文档甚至整本书。Jekyll软件可以用于将文档转换成静态网页，该软件提供了将网页上传到GitHub Pages的功能。一般GitHub Pages的网站使用github.io的子域名，但是用户也可以使用第三方域名。

## github pages

### 新建一个username.github.io仓库

- `username`一定要与github的用户名`相同`，不能任意选取
- 仓库属性选择Public，Private需要付费
- readme文件：仓库的描述信息
- .gitignore：此文件内容为需要忽略的本地文件路径
- license：开源许可证

![](https://waha-note.oss-cn-beijing.aliyuncs.com/PicGo/20210521144645.png)

### 选择一个主题

在仓库页面中点击settings

![image-20210521144746764](https://waha-note.oss-cn-beijing.aliyuncs.com/PicGo/20210521144746.png)

然后点击pages中的choose a theme

![image-20210521144817813](https://waha-note.oss-cn-beijing.aliyuncs.com/PicGo/20210521144817.png)

选择想要的主题

<img src="https://waha-note.oss-cn-beijing.aliyuncs.com/PicGo/20210521145011.png" alt="image-20210521145011478" style="zoom:50%;" />

提交选择主题的更改到github

<img src="https://waha-note.oss-cn-beijing.aliyuncs.com/PicGo/20210521145128.png" alt="image-20210521145128098" style="zoom:50%;" />

### 效果

此时github pages 已经运行成功了，访问https://username.github.io/，即可看见网站主页内容。但是此时功能十分简陋，通常还远远未满足我们的需求，我们需要利用静态模板系统来让生产接管你博客的文章的生成，让你把更多的经历投入在创作里。下面就用到了 GitHub 官方推荐的 Jekyll 工具。

<img src="https://waha-note.oss-cn-beijing.aliyuncs.com/PicGo/20210521145450.png" alt="image-20210521145450533" style="zoom:50%;" />

## jekyll

Jekyll是一个简单的，可识别博客的静态网站生成器，非常适合个人项目或组织网站。无需考虑所有复杂性，使得使用者只需要关注创作即可。Jekyll是GitHub Pages的引擎，您可以使用它直接在GitHub存储库中托管网站。

### windows安装

1. 下载安装[Ruby+Devkit](https://rubyinstaller.org/downloads/),选项全部默认即可

- 安装目录`不要有空格、中文`,例如常用的Program Files安装目录就不可以

2. 最后一步`ridk install`一定要勾选，随后弹出一个cmd窗口，选择3即可

![image-20210521151056035](https://waha-note.oss-cn-beijing.aliyuncs.com/PicGo/20210521151056.png)

![image-20210521151334178](https://waha-note.oss-cn-beijing.aliyuncs.com/PicGo/20210521151334.png)

然后验证是否安装成功，打开命令窗口，输入`ruby -v`和`gem -v`如果能够查询到版本表示安装成功

```shell
C:\Users\wa_ha>ruby -v
ruby 2.7.3p183 (2021-04-05 revision 6847ee089d) [x64-mingw32]

C:\Users\wa_ha>gem -v
3.1.6
```

3. 安装jekyll、bundler

- 打开命令窗口输入`gem install jekyll bundler`
- 如果超时，可以先尝试更改gem源为[国内源](https://gems.ruby-china.com/)
- 如果更改源也不行，则有可能是ipv6的原因，需要禁用网络ipv6，禁用方法参考[Win10关闭IPv6协议的方法](https://windows10.pro/win10-turn-off-ipv6/)

```shell
C:\Users\wa_ha>gem install jekyll bundler
Successfully installed jekyll-4.2.0
Parsing documentation for jekyll-4.2.0
Done installing documentation for jekyll after 0 seconds
Successfully installed bundler-2.2.17
Parsing documentation for bundler-2.2.17
Done installing documentation for bundler after 2 seconds
2 gems installed
```

### 使用方法

1. 克隆github pages远程仓库

```shell
git clone https://github.com/username/username.github.io
cd username.github.io/
```

2. `jekyll new . --force`

- 最重要的文件夹就是`_posts`，增加新的博客文章就是向此文件夹添加新的markdown文件即可。

```shell
(base) PS D:\Workspace\Git\wahaoo-dev.github.io> ls


    目录: D:\Workspace\Git\wahaoo-dev.github.io


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----         2021/5/21     15:53                _posts
-a----         2021/5/21     15:53             56 .gitignore
-a----         2021/5/21     15:53            419 404.html
-a----         2021/5/21     15:53            539 about.markdown
-a----         2021/5/21     15:53           1155 Gemfile
-a----         2021/5/21     15:53           2039 Gemfile.lock
-a----         2021/5/21     15:53            175 index.markdown
-a----         2021/5/21     15:30          11558 LICENSE
-a----         2021/5/21     15:30           1348 README.md
-a----         2021/5/21     15:53           2080 _config.yml
```



3. 本地运行：`bundle exec jekyll serve`，打开http://127.0.0.1:4000/即可看到jekyll默认的博客主题

```shell
(base) PS D:\Workspace\Git\wahaoo-dev.github.io> bundle exec jekyll serve
Configuration file: D:/Workspace/Git/wahaoo-dev.github.io/_config.yml
            Source: D:/Workspace/Git/wahaoo-dev.github.io
       Destination: D:/Workspace/Git/wahaoo-dev.github.io/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
       Jekyll Feed: Generating feed for posts
                    done in 0.666 seconds.
 Auto-regeneration: enabled for 'D:/Workspace/Git/wahaoo-dev.github.io'
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
```

### 修改配置文件_config.yml

- 配置文件因选择的主题而有所不同，常见的有主页标题，email，描述等信息

```yaml
title: Your awesome title
email: your-email@example.com
description: >- # this means to ignore newlines until "baseurl:"
  Write an awesome description for your new site here. You can edit this
  line in _config.yml. It will appear in your document head meta (for
  Google search results) and in your feed.xml site description.
baseurl: "" # the subpath of your site, e.g. /blog
url: "" # the base hostname & protocol for your site, e.g. http://example.com

twitter_username: jekyllrb
github_username:  jekyll
```



### 添加博客

只需要按照规则`YYYY-MM-DD-name.md`添加文件到_post文件夹即可，例如2021-05-21-test.md

```markdown
---
layout: post
title:  "test!"
date:   2021-05-21 15:53:53 +0800
categories: jekyll update
---
# test

> this is test
```

然后刷新网页，即可在主页中看到相应的博客标题

![image-20210521160539030](https://waha-note.oss-cn-beijing.aliyuncs.com/PicGo/20210521160539.png)

点进去可以看到博客完全内容

![image-20210521160552285](https://waha-note.oss-cn-beijing.aliyuncs.com/PicGo/20210521160552.png)

此时只是在本地中可以看到，如果对效果满意则直接git push 到远程仓库，即可通过https://username.github.io访问主页。

### 更改主题

1. 选取主题，[jekyll主题网站](http://jekyllthemes.org/)
2. 替换本地仓库username.github.io中的文件
3. 修改_config.yml配置文件

