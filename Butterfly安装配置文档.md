---
title: Butterfly安装配置文档
date: 2020-07-02 08:35:12
tags: butterfly
categories: 博客
keywords: 
description:
top_img: https://xtl-blog.oss-cn-beijing.aliyuncs.com/hexo/timg.png
cover: https://xtl-blog.oss-cn-beijing.aliyuncs.com/hexo/timg.png
---

# 快速安装

- hexo-theme-butterfly是基于Molunerfinn的hexo-theme-melody的基础上进行开发的。
文档也是在hexo-theme-melody的文档基础上修改。因为一些配置变更导致与原主题配置上有部分区别。故如果安装hexo-theme-butterfly主题，请参考这篇文档。

## 安装
### 稳定版【建议】
- 在你的博客根目录里

  ```Powershell
  git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
  ```
### 测试版
- 如果想要安装比较新的dev分支，可以

  ```Powershell
  git clone -b dev https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
  ```
## 应用主题
- 修改站点配置文件_config.yml，把主题改为butterfly

  ```Yaml
  theme: butterfly
  ```
  > 如果你没有 pug 以及 stylus 的渲染器，请下载安装： npm install hexo-renderer-pug hexo-renderer-stylus --save or yarn add hexo-renderer-pug hexo-renderer-stylus

## 平滑升级
- 为了主题的平滑升级, Butterfly 使用了 data files 特性。

- 推荐把主题默认的配置文件_config.yml复製到 Hexo 工作目录下的source/_data/butterfly.yml，如果source/_data的目录不存在那就创建一个。

> 注意，如果你创建了butterfly.yml, 它将会替换主题默认配置文件_config.yml里的配置项 (不是合併而是替换), 之后你就只需要通过git pull的方式就可以平滑地升级 theme-butterfly了。

> 由于主题在添加功能或者修復Bugs的情况下，可能会涉及到配置文件的修改。这时候，如果升级主题，需要把新增加的配置添加到butterfly.yml去，不然很大机会会出现报错。


# 主题页面
## Front-matter
- Front-matter 是档案最上方以 --- 分隔的区域，用于指定个别档案的变数。

> 如果标注可选的参数，可根据自己需要添加，不用全部都写在markdown里

### Page Front-matter
```Markdown
---
title:
date:
updated:
type:
comments:
description:
keywords:
top_img:
mathjax:
katex:
aside:
aplayer：
highlight_shrink：
```

 写法 | 解释 
 - | - 
title |【必需】页面标题
date |【必需】页面创建日期
type|【必需】标籤、分类和友情链接三个页面需要配置
updated |【可选】页面更新日期
description |【可选】页面描述
keywords |【可选】页面关键字
comments |【可选】显示页面评论模块(默认 true)
top_img |【可选】页面顶部图片
mathjax |【可选】显示mathjax(当设置mathjax的per_page: false时，才需要配置，默认 false)
katex |【可选】显示katex(当设置katex的per_page: false时，才需要配置，默认 false)
aside	|【可选】显示侧边栏 (默认 true)
aplayer	|【可选】在需要的页面加载aplayer的js和css,请参考文章下面的音乐 配置
highlight_shrink	|【可选】配置代码框是否展开(true/false)(默认为设置中highlight_shrink的配置)

### Post Front-matter

```Markdown
---
title:
date:
updated:
tags:
categories:
keywords:
description:
top_img:
comments：
cover:  
toc:  
toc_number:
auto_open:
copyright:
mathjax:
katex:
aplayer：
highlight_shrink：
---
```

写法 |	解释
- |-
title	|【必需】文章标题
date	|【必需】文章创建日期
updated|	【可选】文章更新日期
tags	|【可选】文章标籤
categories	|【可选】文章分类
keywords	|【可选】文章关键字
description	|【可选】文章描述
top_img	|【可选】文章顶部图片
cover	|【可选】文章缩略图(如果没有设置top_img,文章页顶部将显示缩略图，可设为false/图片地址/留空)
comments	|【可选】显示文章评论模块(默认 true)
toc	|【可选】显示文章TOC(默认为设置中toc的enable配置)
toc_number	|【可选】显示toc_number(默认为设置中toc的number配置)
auto_open	|【可选】是否自动打开TOC(默认为设置中toc的auto_open配置)
copyright	|【可选】显示文章版权模块(默认为设置中post_copyright的enable配置)
mathjax	|【可选】显示mathjax(当设置mathjax的per_page: false时，才需要配置，默认 false)
katex	|【可选】显示katex(当设置katex的per_page: false时，才需要配置，默认 false)
aplayer	|【可选】在需要的页面加载aplayer的js和css,请参考文章下面的音乐 配置
highlight_shrink	|【可选】配置代码框是否展开(true/false)(默认为设置中highlight_shrink的配置)


## 标签页
- 前往你的 Hexo 博客的根目录

- 输入hexo new page tags

- 你会找到source/tags/index.md这个文件

- 修改这个文件：

```Markdown
---
title: 标籤
date: 2018-01-05 00:00:00
type: "tags"
---
```

## 分类页
- 前往你的 Hexo 博客的根目录

- 输入hexo new page categories

- 你会找到source/categories/index.md这个文件

- 修改这个文件：

```Markdown
---
title: 分类
date: 2018-01-05 00:00:00
type: "categories"
---
```

## 友情链接
为你的博客创建一个友情链接！

### 创建友情链接页面
- 前往你的 Hexo 博客的根目录
- 输入 hexo new page link
- 你会找到source/link/index.md这个文件
- 修改这个文件：

```Markdown
---
title: 友情链接
date: 2018-06-07 22:17:49
type: "link"
---
```

### 友情链接添加
在Hexo博客目录中的source/_data，创建一个文件link.yml

```Yml
- class_name: 友情链接
  class_desc: 那些人，那些事
  link_list:
    - name: JerryC
      link: https://jerryc.me/
      avatar: https://jerryc.me/image/avatar.png
      descr: 今日事,今日毕
    - name: Hexo
      link: https://hexo.io/zh-tw/
      avatar: https://d33wubrfki0l68.cloudfront.net/6657ba50e702d84afb32fe846bed54fba1a77add/827ae/logo.svg
      descr: 快速、简单且强大的网誌框架

- class_name: 网站
  class_desc: 值得推荐的网站
  link_list:
    - name: Youtube
      link: https://www.youtube.com/
      avatar: https://i.loli.net/2020/05/14/9ZkGg8v3azHJfM1.png
      descr: 视频网站
    - name: Weibo
      link: https://www.weibo.com/
      avatar: https://i.loli.net/2020/05/14/TLJBum386vcnI1P.png
      descr: 中国最大社交分享平台
    - name: Twitter
      link: https://twitter.com/
      avatar: https://i.loli.net/2020/05/14/5VyHPQqR6LWF39a.png
      descr: 社交分享平台
```

class_name和class_desc支持html格式书写，如不需要，也可以留空。

### 友情链接界面设置
由 2.2.0起，友情链接界面可以由用户自己自定义，只需要在友情链接的md档设置就行，以普通的Markdown格式书写。

## 音乐
音乐界面使用了插件hexo-tag-aplayer。
使用方法请参考插件的文档。

音乐页面只是普通的page页，按普通页面操作生成就行。

- 以下内容可供选择配置

  插件会在每一个文件都插入js和css，为了避免这一情况，3.0版本内置了aplayer需要的css和js。

  首先在Hexo根目录_config里配置asset_inject为false

    ```Yaml
    aplayer:
    asset_inject: false
    ```

然后在你需要使用aplayer的页面Front-matter添加

```Markdown
aplayer: true
```

这样只会在需要aplayer的页面插入js和css。

## 电影
电影界面使用了插件hexo-douban。
使用方法请参考插件的文档。

注意：hexo-douban会主动生成页面，所以不需要自己创建。对应网页的top_img可以在butterfly.yml修改。

## 404页面
主题内置了一个简单的404页面，可在设置中开启

本地预览时，访问出错的网站是不会跳到404页面的。

如需本地预览，请访问http://localhost:4000/404.html

```Yaml
# A simple 404 page
error_404:
  enable: true
  subtitle: "页面没有找到"
  background:
```

# 主题配置一
配置文件説明

- 站点配置文件_config.yml是 hexo 工作目录下的主配置文件(还不知道是哪里的，自己google)
- butterfly.yml 是 Butterfly 的配置文件。它需要你手动将主题目录下的_config.yml文件复製到 hexo 工作目录的source/_data/butterfly.yml中。如果文件或者文件夹不存在，需要手动创建。

## 语言
修改站点配置文件 _config.yml

默认语言是 en

主题支持三种语言
- default(en)
- zh-CN (简体中文)
- zh-TW (繁体中文)

## 网站资料
修改网站各种资料，例如标题、副标题和邮箱等个人资料，请修改博客根目录的_config.yml

##导航菜单
配置butterfly.yml

```Yaml
menu:
  Home: / || fa fa-home
  Archives: /archives/ || fa fa-archive
  Tags: /tags/ || fa fa-tags
  Categories: /categories/ || fa fa-folder-open
  Link: /link/ || fa fa-link
  About: /about/ || fa fa-heart
  List||fa fa-list:
    - Music || /music/ || fa fa-music
    - Movie || /movies/ || fa fa-film
```
必须是 /xxx/，后面||分开，然后写图标名。

注意： 导航的文字可自行更改

例如：

```Markdown
menu:
  首页: / || fa fa-home
  时间轴: /archives/ || fa fa-archive
  标籤: /tags/ || fa fa-tags
  分类: /categories/ || fa fa-folder-open
  清单||fa fa-heartbeat:
    - 音乐 || /music/ || fa fa-music
    - 照片 || /Gallery/ || fa fa-picture-o
    - 电影 || /movies/ || fa fa-film
  友链: /link/ || fa fa-link
  关于: /about/ || fa fa-heart
```

## 代码
代码块中的所有功能只适用于Hexo默认的highlight渲染

如果使用第三方的渲染器，不一定会有效

### 代码高亮主题
默认主题

```Yaml
highlight_theme: darker
```

### 代码复製
主题支持代码复製功能

配置butterfly.yml

```Yaml
highlight_copy: true
```

### 代码框展开/关闭
在默认情况下，代码框自动展开，可设置是否所有代码框都关闭状态，点击>可展开代码
- true 全部代码框不展开，需点击>打开
- false 代码狂展开，有>点击按钮
- none 不显示>按钮

配置butterfly.yml

```Yaml
highlight_shrink: true #代码框不展开，需点击 '>' 打开
```


### 代码换行
在默认情况下，hexo-highlight在编译的时候不会实现代码自动换行。如果你不希望在代码块的区域里有横向滚动条的话，那么你可以考虑开启这个功能。

配置butterfly.yml

```Yaml
code_word_wrap: true
```



## 社交图标
Butterfly支持 font-awesome v5图标.

书写格式 图标名：url || 描述性文字

```Yaml
social:
  fa fa-github: https://github.com/ || Github
  fa fa-rss: /atom.xml || RSS链接
```



## 主页文章节选(自动节选和文章页description)
因为主题UI的关係，主页文章节选只支持自动节选和文章页description。

在butterfly里，有三种可供选择

- description 只显示description
- both 优先选择description，如果没有配置description，则显示自动节选的内容
- auto_excerpt 只显示自动节选
配置butterfly.yml

```Yaml
index_post_content:
  method: 3
  length: 500 # if you set method to 2 or 3, the length need to config
```

description在front-matter里添加



## 顶部图
顶部图有2种配置：具体url 和（留空，true和false，三个效果一样）

### page页
#### 当具体url时
主页的顶部图可以在Butterfly.yml设置index_img

archives页的顶部图可以在Butterfly.yml设置archive_img

其他page页的顶部图可以在各自的md页面设置front-matter中的top_img

>页面如果没有设置各自的top_img，则会显示default_top_img图片

#### 当顶部图留空，true和false
主页会显示纯颜色的顶部图

其他page的顶部图没有设置时，也会显示纯颜色的顶部图

### post页
post页的顶部图会优先显示各自front-matter中的top_img,如果没有设置，则会缩略图（即各自front-matter中的cover)，如果没有则会显示显示default_top_img图片

## 文章置顶
要为文章置顶，你需要安装插件(hexo-generator-index-pin-top 或者 hexo-generator-indexed)

如果使用hexo-generator-index-pin-top, 需要先卸载掉hexo-generator-index，然后在文章的front-matter区域里添加top: true属性来把这篇文章置顶

如果使用hexo-generator-indexed, 需要先卸载掉hexo-generator-index，然后在文章的front-matter区域里添加sticky: 1属性来把这篇文章置顶。数值越大，置顶的优先级越大

## 文章封面
文章的markdown文档上,在Front-matter添加cover,并填上要显示的图片地址。
如果不配置cover,可以设置显示默认的cover.

如果不想在首页显示cover,可以设置为false

配置butterfly.yml

```Yaml

cover:
  # 是否显示文章封面
  index_enable: true
  aside_enable: true
  archives_enable: true
  # 封面显示的位置
  # 三个值可配置 left , right , both
  position: both
  # 当没有设置cover时，默认的封面显示
  default_cover:
```

当配置多张图片时,会随机选择一张作为cover.此时写法应为

```Yaml
default_cover:
  - https://cdn.jsdelivr.net/gh/jerryc127/CDN@latest/cover/default_bg.png
  - https://cdn.jsdelivr.net/gh/jerryc127/CDN@latest/cover/default_bg2.png
  - https://cdn.jsdelivr.net/gh/jerryc127/CDN@latest/cover/default_bg3.png
```

## 文章页相关配置
### 文章meta显示
这个选项是用来显示文章的相关信息的。

配置butterfly.yml

```Yaml
post_meta:
  page:
    date_type: both # created or updated or both 主页文章日期是创建日或者更新日或都显示
    categories: true # true or false 主页是否显示分类
    tags: true # true or false 主页是否显示标籤
  post:
    date_type: both # created or updated or both 文章页日期是创建日或者更新日或都显示
    categories: true # true or false 文章页是否显示分类
    tags: true # true or false 文章页是否显示标籤
```

在文章顶部的资料

- date_type: 可设置文章日期显示创建日期(created)或者更新日期(updated)或者两种都显示(both)

- categories 是否显示分类

- tags是否显示标籤

### 文章版权
为你的博客文章展示文章版权和许可协议。

配置butterfly.yml

```Yaml
post_copyright:
  enable: false
  decode: false
  license: CC BY-NC-SA 4.0
  license_url: https://creativecommons.org/licenses/by-nc-sa/4.0/
```

### 文章打赏
在你每篇文章的结尾，可以添加打赏按钮。相关二维码可以自行配置。

对于没有提供二维码的，可配置一张软件的icon图片，然后在link上添加相应的打赏链接。用户点击图片就会跳转到链接去。

link可以不写，会默认为图片的链接。

配置butterfly.yml

```Yaml
reward:
  enable: true
  QR_code:
    - img: /image/wechat.jpg
      link:
      text: 微信
    - img: /image/alipay.jpg
      link:
      text: 支付宝
```

### 文章隐藏
2.3.0 开始主题不再默认提供文章隐藏功能

如需要文章隐藏功能，请装插件hexo-generator-indexed或者hexo-hide-posts

### TOC
在文章页，会有一个目录，用于显示TOC。

enable: 是否显示TOC
number: 是否显示章节数
auto_open: 可选择进入文章页面时，是否自动打开sidebar显示TOC


### 相关文章
相关文章推荐的原理是根据文章tags的比重来推荐

配置butterfly.yml

```Yaml
related_post:
  enable: true
  limit: 6 # 显示推荐文章数目
  date_type: created # or created or updated 文章日期显示创建日或者更新日
```

### 文章锚点
开启文章锚点后，当你在文章页进行滚动时，文章链接会根据标题ID进行替换
(注意: 每替换一次，会留下一个歷史记录。所以如果一篇文章有很多锚点anchor的话，网页的歷史记录会很多。)

## 头像
配置butterfly.yml

```Yaml
avatar:
  img: /img/avatar.png
  effect: true # 头像会一直转圈
```

## 图片描述
可开启图片Figcaption描述文字显示

配置butterfly.yml

```Yaml
photofigcaption: true
```

## Footer 设置
博客年份
since是一个来展示你站点起始时间的选项。它位于页面的最底部。

配置butterfly.yml

```Yaml
since: 2018
```

## 页脚自定义文本
footer_custom_text是一个给你用来在页脚自定义文本的选项。通常你可以在这里写声明文本等。支持 HTML。

配置butterfly.yml

```Yaml
footer_custom_text: Hi, welcome to my <a href="https://jerryc.me/">blog</a>!
```

## ICP
对于部分有备案的域名，可以在ICP配置显示。

配置butterfly.yml

```Yaml
ICP:
  enable: true
  url: http://www.beian.miit.gov.cn/state/outPortal/loginPortal.action
  text: 粤ICP备xxxx
  icon: /img/icp.png
```

## 右下角按钮

### 简繁转换

简体繁体互换

右下角会有简繁转换按钮。

配置butterfly.yml

```Yaml
translate:
  enable: true
  # 默认按钮显示文字(网站是简体，应设置为'default: 繁')
  default: 简
  #网站默认语言，1: 繁体中文, 2: 简体中文
  defaultEncoding: 1
  #延迟时间,若不在前, 要设定延迟翻译时间, 如100表示100ms,默认为0
  translateDelay: 0
  #当文字是简体时，按钮显示的文字
  msgToTraditionalChinese: "繁"
  #当文字是繁体时，按钮显示的文字
  msgToSimplifiedChinese: "简"
```

### 夜间模式
右下角会有夜间模式按钮

配置butterfly.yml

```Yaml
# dark mode
darkmode:
  enable: true
  # dark mode和 light mode切换按钮
  button: true
  autoChangeMode: false
```

V2.0.0 开始增加一个选项，可开启自动切换light mode 和 dark mode

- autoChangeMode: 1 跟随系统而变化，不支持的浏览器/系统将按照时间晚上6点到早上6点之间切换为 dark mode

- autoChangeMode: 2 只按照时间 晚上6点到早上6点之间切换为 dark mode,其余时间为light mode

- autoChangeMode: false 取消自动切换

### 閲读模式
閲读模式下会去掉除文章外的内容，避免干扰閲读。

只会出现在文章页面，右下角会有閲读模式按钮。

配置butterfly.yml

```Yaml
readmode: true
```

## 侧边栏设置
### 侧边排版
可自行决定哪个项目需要显示，可决定位置，也可以设置不显示侧边栏。

配置butterfly.yml

```Yaml
aside:
  enable: true
  mobile: true # 手机页面（ 显示宽度 < 768px ）是否显示aside内容
  position: right # left or right
  card_author:
    enable: true
    description:
  card_announcement:
    enable: true
    content: This is my Blog
  card_recent_post:
    enable: true
    limit: 5 # if set 0 will show all
  card_categories:
    enable: true
    limit: 8 # if set 0 will show all
    expand: none # none/true/false
  card_tags:
    enable: true
    limit: 40 # if set 0 will show all
    color: false
  card_archives:
    enable: true
    type: monthly # yearly or monthly
    format: MMMM YYYY # eg: YYYY年MM月
    order: -1 # Sort of order. 1, asc for ascending; -1, desc for descending
    limit: 8 # if set 0 will show all
  card_webinfo: true
```


### 访问人数 busuanzi (UV 和 PV)
访问 busuanzi 的官方网站查看更多的介绍。

配置butterfly.yml

```Yaml
busuanzi:
  site_uv: true
  site_pv: true
  page_pv: true
```

### 运行时间
网页已运行时间

配置butterfly.yml

```Yaml
runtimeshow:
  enable: true
  publish_date: 6/7/2018 00:00:00  
  ##网页开通时间
  #格式: 月/日/年 时间
  #也可以写成 年/月/日 时间
```

## 标签外挂（Tag Plugins）
标签外挂是Hexo独有的功能，并不是标准的Markdown格式。

以下的写法，只适用于Butterfly主题，用在其它主题上不会有效果，甚至可能会报错。使用前请留意

标签外挂虽然能为主题带来一些额外的功能和UI方面的强化，但是，标籤外挂也有明显的限制，使用时请留意。

# 主题配置二

## 评论

遵循 Valine的指示去配置你的 LeanCloud 应用。以及查看相应的配置説明。

然后配置butterfly.yml:

```Yaml
valine:
  enable: true # if you want use valine,please set this value is true
  appId:  # leancloud application app id
  appKey:  # leancloud application app key
  pageSize: 10 # comment list page size
  avatar: monsterid # gravatar style https://valine.js.org/#/avatar
  lang: en # i18n: zh-CN/zh-TW/en/ja
  placeholder: 记得留下你的暱称和邮箱....可以快速收到回復 # valine comment input placeholder(like: Please leave your footprints )
  guest_info: nick,mail,link #valine comment header info (nick/mail/link)
  recordIP: false # Record reviewer IP
  serverURLs: # This configuration is suitable for domestic custom domain name users, overseas version will be automatically detected (no need to manually fill in)
  bg: /image/comment_bg.png # valine background
  emojiCDN: # emoji CDN
  enableQQ: false # enable the Nickname box to automatically get QQ Nickname and QQ Avatar
  requiredFields: nick,mail # required fields (nick/mail)
  count: true # dispaly comment count in top_img
```
Valine于v1.4.5开始支持自定义表情，如果你需要自行配置，请在emojiCDN配置表情CDN。

同时在Hexo 工作目录下的source/_data/创建一个json文件valine.json,等同于Valine需要配置的emojiMaps，valine.json配置方式可参考如下


```Json
{ 
"tv_doge": "6ea59c827c414b4a2955fe79e0f6fd3dcd515e24.png",
"tv_亲亲": "a8111ad55953ef5e3be3327ef94eb4a39d535d06.png",
"tv_偷笑": "bb690d4107620f1c15cff29509db529a73aee261.png",
"tv_再见": "180129b8ea851044ce71caf55cc8ce44bd4a4fc8.png",
"tv_冷漠": "b9cbc755c2b3ee43be07ca13de84e5b699a3f101.png",
"tv_发怒": "34ba3cd204d5b05fec70ce08fa9fa0dd612409ff.png",
"tv_发财": "34db290afd2963723c6eb3c4560667db7253a21a.png",
"tv_可爱": "9e55fd9b500ac4b96613539f1ce2f9499e314ed9.png",
"tv_吐血": "09dd16a7aa59b77baa1155d47484409624470c77.png",
"tv_呆": "fe1179ebaa191569b0d31cecafe7a2cd1c951c9d.png",
"tv_呕吐": "9f996894a39e282ccf5e66856af49483f81870f3.png",
"tv_困": "241ee304e44c0af029adceb294399391e4737ef2.png",
"tv_坏笑": "1f0b87f731a671079842116e0991c91c2c88645a.png",
"tv_大佬": "093c1e2c490161aca397afc45573c877cdead616.png",
"tv_大哭": "23269aeb35f99daee28dda129676f6e9ea87934f.png",
"tv_委屈": "d04dba7b5465779e9755d2ab6f0a897b9b33bb77.png",
"tv_害羞": "a37683fb5642fa3ddfc7f4e5525fd13e42a2bdb1.png",
"tv_尴尬": "7cfa62dafc59798a3d3fb262d421eeeff166cfa4.png",
"tv_微笑": "70dc5c7b56f93eb61bddba11e28fb1d18fddcd4c.png",
"tv_思考": "90cf159733e558137ed20aa04d09964436f618a1.png",
"tv_惊吓": "0d15c7e2ee58e935adc6a7193ee042388adc22af.png"
}
```
## 分享

配置butterfly.yml

```Yaml
sharejs:
  enable: true
  sites: facebook,twitter,wechat,weibo,qq  #想要显示的内容
```

## 搜索系统

本地搜索
你需要安装 hexo-generator-search. 根据它的文档去做相应配置。注意格式只支持 xml。

配置butterfly.yml

```Yaml
local_search:
  enable: false
  labels:
    input_placeholder: Search for Posts
    hits_empty: "We didn't find any results for the search: ${query}" # if there are no result
```

## 美化/特效
### 自定义主题色
可以修改大部分UI颜色

配置butterfly.yml，比如：

颜色值必须被双引号包裹，就像"#000"而不是#000。否则将会在构建的时候报错！

```Yaml
theme_color:
  enable: true
  main: "#49B1F5"
  paginator: "#00c4b6"
  button_hover: "#FF7242"
  text_selection: "#00c4b6"
  link_color: "#99a9bf"
  meta_color: "#858585"
  hr_color: "#A4D8FA"
  code_foreground: "#F47466"
  code_background: "rgba(27, 31, 35, .05)"
  toc_color: "#00c4b6"
  blockquote_padding_color: "#49b1f5"
  blockquote_background_color: "#49b1f5"
```


### 网站背景
默认显示白色，可设置图片或者颜色

配置butterfly.yml

```Yaml
# 图片格式 background: url(http://xxxxxx.com/xxx.jpg)
# 颜色 background: '#49B202'
# 留空 显示白色
background:
```
留意: 如果你的网站根目录不是’/‘,使用本地图片时，需加上你的根目录。
例如：网站是 https://yoursite.com/blog,引用一张img/xx.png图片，则设置background为 `url(/blog/img/xx.png)


### footer 背景
footer 的背景会与top_img的一致, 当设置false时，将与主题色一致。

配置butterfly.yml

```Yaml
# footer是否显示图片背景(与top_img一致)
footer_bg: true
```
true

### 打字效果
打字效果activate-power-mode

配置butterfly.yml

```Yaml
# Typewriter Effect (打字效果)
# https://github.com/disjukr/activate-power-mode
activate_power_mode:
  enable: true
  colorful: true # open particle animation (冒光特效)
  shake: true #  open shake (抖动特效)
```

### 背景特效
静止綵带canvas_ribbon:
动态綵带canvas_ribbon_piao:
canvas-nest


### 鼠标点击效果
- 烟花fireworks:
- 爱心click_heart: true
- 文字ClickShowText:

### 页面美化
会改变ol、ul、h1-h5的样式

field配置生效的区域
- post 只在文章页生效
- site 在全站生效

配置butterfly.yml

```Yaml
# 美化页面显示
beautify:
  enable: true
  field: site # site/post
  title-prefix-icon: '\f0c1'
  title-prefix-icon-color: "#F47466"
title-prefix-icon填写的是fontawesome的icon的Unicode数。
```


### 网站副标题
可设置主页中显示的网站副标题或者喜欢的座右铭。

配置butterfly.yml

```Yaml
# 主页subtitle
subtitle:
  enable: true
  # 打字效果
  effect: true
  # 循环或者只打字一次
  loop: false
  # source调用第三方服务
  # source: false 关闭调用
  # source: 1  调用搏天api的随机语录（简体） https://api.btstu.cn/
  # source: 2  调用一言网的一句话（简体） https://hitokoto.cn/
  # source: 3  调用一句网（简体） http://yijuzhan.com/
  # source: 4  调用今日诗词（简体） https://www.jinrishici.com/
  # subtitle 会先显示 source , 再显示 sub 的内容
  source: false
  # 如果有英文逗号' , ',请使用转义字元 &#44;
  # 如果有英文双引号' " ',请使用转义字元 &quot;
  # 开头不允许转义字元，如需要，请把整个句子用双引号包住
  # 例如 ”&quotNever put off till tomorrow what you can do today&quot"
  # 如果关闭打字效果，subtitle只会显示sub的第一行文字
  sub:
    - 今日事&#44;今日毕
    - Never put off till tomorrow what you can do today
```

### 主页top_img显示大小
适用于 版本号 >= V1.2.0

默认的显示为全屏。site-info的区域会居中显示

```Yaml

# 主页设置
# 默认top_img全屏，site_info在中间
# 使用默认, 都无需填写（建议默认）
index_site_info_top: # 主页标题距离顶部距离  例如 300px/300em/300rem/10%
index_top_img_height:  #主页top_img高度 例如 300px/300em/300rem  不能使用百分比
```
注意：index_top_img_height的值不能使用百分比。
2个都不填的话，会使用默认值


### 页面加载动画preloader
当进入网页时，因为加载速度的问题，可能会导致top_img图片出现断层显示，或者网页加载不全而出现等待时间，开启preloader后，会显示加载动画，等页面加载完，加载动画会消失。

配置butterly.yml

```Yaml
# 加载动画 Loading Animation
preloader: true
```

## PWA
要为Butterfly配上 PWA 特性, 你需要如下几个步骤:

- 打开 hexo 工作目录

- npm install hexo-offline --save 或者 yarn add hexo-offline

- 修改_config.yml 在站点_config.yml中增加以下内容。

```Yaml
# offline config passed to sw-precache.
offline:
  maximumFileSizeToCacheInBytes: 10485760 # 缓存的最大文件大小，以字节为单位
  staticFileGlobs:
    - public/**/*.{js,html,css,png,jpg,gif,svg,webp,eot,ttf,woff,woff2}
  # 静态文件合集，如果你的站点使用了例如webp格式的文件，请将文件类型添加进去。
  stripPrefix: public
  verbose: true
  runtimeCaching:
    # CDNs - should be cacheFirst, since they should be used specific versions so should not change
    - urlPattern: /* # 如果你需要加载CDN资源，请配置该选项，如果没有，可以不配置。
      handler: cacheFirst
      options:
        origin: your_websie_url # 可替换成你的 url
```

更多内容请查看 hexo-offline的官方文档

在butterfly.yml中开启 pwa 选项。

```Yaml
pwa:
  enable: true
  manifest: /img/pwa/manifest.json
  theme_color: "#fff"
  apple_touch_icon: /img/pwa/apple-touch-icon.png
  favicon_32_32: /img/pwa/32.png
  favicon_16_16: /img/pwa/16.png
  mask_icon: /img/pwa/safari-pinned-tab.svg
  ```

在创建source/目录中创建manifest.json文件。

```Json
{
    "name": "string", //应用全称
    "short_name": "Junzhou", //应用简称
    "theme_color": "#49b1f5", //匹配浏览器的地址栏颜色
    "background_color": "#49b1f5",//加载应用时的背景色
    "display": "standalone",//首选显示模式 其他选项有：fullscreen,minimal-ui,browser
    "scope": "/",
    "start_url": "/",
    "icons": [ //该数组指定icons图标参数，用来时适配不同设备（需为png，至少包含一个192px*192px的图标）
        {
          "src": "images/pwaicons/36.png", //图标文件的目录，需在source/目录下自行创建。
          "sizes": "36x36",
          "type": "image/png"
        },
        {
            "src": "images/pwaicons/48.png",
          "sizes": "48x48",
          "type": "image/png"
        },
        {
          "src": "images/pwaicons/72.png",
          "sizes": "72x72",
          "type": "image/png"
        },
        {
          "src": "images/pwaicons/96.png",
          "sizes": "96x96",
          "type": "image/png"
        },
        {
          "src": "images/pwaicons/144.png",
          "sizes": "144x144",
          "type": "image/png"
        },
        {
          "src": "images/pwaicons/192.png",
          "sizes": "192x192",
          "type": "image/png"
        },
        {
            "src": "images/pwaicons/512.png",
            "sizes": "512x512",
            "type": "image/png"
          }
      ],
      "splash_pages": null //配置自定义启动动画。
  }
```
你也可以通过 Web App Manifest快速创建manifest.json。（Web App Manifest 要求至少包含一个 512*512 像素的图标）

可以通过Chrome插件Lighthouse检查 PWA 配置是否生效以及配置是否正确。

打开博客页面
启动Lighthouse插件 (Lighthouse插件要求至少包含一个 512*512 像素的图标)
关于 PWA（渐进式增强 Web 应用）的更多内容请参閲 Google Tools for Web Developers

# 进阶教程
## 建议
- 不要把个人需要的文件/图片放在主题source文件夹里，因为在升级主题的过程中，可能会把文件覆盖删除了。在Hexo根目录的source文件夹里，创建一个文件夹来放置个人文件/图片。文件夹不能命名为css、js和img引用文件直接为/文件夹名称/文件名
- 升级完主题，记得把新添加的配置复製到butterfly.yml去（如有）

## Gulp压缩
Gulp 是一款自动化构建的工具，拥有众多的插件。而我们只需要使用到几个插件来压缩Html/css/js。

### 安装Gulp

```Powershell
npm install --global gulp-cli
```

### 插件安装
#### 压缩HTML
可以使用gulp-htmlclean和gulp-htmlmin来压缩HTML

```Powershell
npm install gulp-htmlclean --save-dev
npm install --save gulp-htmlmin
```

#### 压缩CSS
可以使用gulp-clean-css来压缩CSS

```Powershell
npm install gulp-clean-css --save-dev
```

#### 压缩JS
由于Butterfly主题中的JS使用到了部分ES6语法，因此不能只使用 gulp-uglify 来压缩，还需要搭配其它的插件。两种搭配都可以有效的压缩JS代码，选一种适合自己的就行。

terser是 ES6+ 的 JavaScript 解析器

gulp-babel是一个JavaScript转换编译器，可以把ES6转换成ES5

gulp-uglify + terser

```Powershell
npm install --save-dev gulp-uglify
npm install terser
```

gulp-uglify + gulp-babel

```Powershell
npm install --save-dev gulp-uglify
npm install --save-dev gulp-babel @babel/core @babel/preset-env
```

#### 压缩图片
可以使用gulp-imagemin来压缩图片

```Powershell
npm install --save-dev gulp-imagemin
```
### 创建 gulpfile 文件
在Hexo的根目录，创建一个gulpfile.js文件
```Js
var gulp = require('gulp')
var cleanCSS = require('gulp-clean-css')
var htmlmin = require('gulp-htmlmin')
var htmlclean = require('gulp-htmlclean')
var imagemin = require('gulp-imagemin')
// tester (如果使用tester,把下面4行前面的//去掉)
// var uglifyjs = require('terser')
// var composer = require('gulp-uglify/composer')
// var pump = require('pump')
// var minify = composer(uglifyjs, console)

// babel (如果不是使用bebel,把下面两行註释掉)
var uglify = require('gulp-uglify')
var babel = require('gulp-babel')

// minify js - babel（ 如果不是使用bebel,把下面註释掉）
gulp.task('compress', () =>
  gulp.src(['./public/**/*.js', '!./public/**/*.min.js'])
    .pipe(babel({
      presets: ['@babel/preset-env']
    }))
    .pipe(uglify().on('error', function (e) {
      console.log(e)
    }))
    .pipe(gulp.dest('./public'))
)

// minify js - tester (如果使用tester,把下面前面的//去掉)
// gulp.task('compress', function (cb) {
//   var options = {}
//   pump([
//     gulp.src(['./public/**/*.js', '!./public/**/*.min.js']),
//     minify(options),
//     gulp.dest('./public')
//   ],
//   cb
//   )
// })

// css
gulp.task('minify-css', () => {
  return gulp.src('./public/**/*.css')
    .pipe(cleanCSS({
      compatibility: 'ie11'
    }))
    .pipe(gulp.dest('./public'))
})

// 压缩 public 目录内 html
gulp.task('minify-html', () => {
  return gulp.src('./public/**/*.html')
    .pipe(htmlclean())
    .pipe(htmlmin({
      removeComments: true, // 清除 HTML 註释
      collapseWhitespace: true, // 压缩 HTML
      collapseBooleanAttributes: true, // 省略布尔属性的值 <input checked="true"/> ==> <input />
      removeEmptyAttributes: true, // 删除所有空格作属性值 <input id="" /> ==> <input />
      removeScriptTypeAttributes: true, // 删除 <script> 的 type="text/javascript"
      removeStyleLinkTypeAttributes: true, // 删除 <style> 和 <link> 的 type="text/css"
      minifyJS: true, // 压缩页面 JS
      minifyCSS: true, // 压缩页面 CSS
      minifyURLs: true
    }))
    .pipe(gulp.dest('./public'))
})

// 压缩 public/uploads 目录内图片
gulp.task('minify-images', async () => {
  gulp.src('./public/img/**/*.*')
    .pipe(imagemin({
      optimizationLevel: 5, // 类型：Number  预设：3  取值範围：0-7（优化等级）
      progressive: true, // 类型：Boolean 预设：false 无失真压缩jpg图片
      interlaced: false, // 类型：Boolean 预设：false 隔行扫描gif进行渲染
      multipass: false // 类型：Boolean 预设：false 多次优化svg直到完全优化
    }))
    .pipe(gulp.dest('./public/img'))
})

// 执行 gulp 命令时执行的任务
gulp.task('default', gulp.parallel(
  'compress', 'minify-css', 'minify-html', 'minify-images'
))
```

注意： 如果有使用到Butterfly主题提供的mermaid标籤外挂，那需要把52行.pipe(htmlclean())註释掉，同时，把55行的collapseWhitespace: true,改为false

### 运行
在hexo g之后运行gulp就行。

```Powershell
gulp
```

