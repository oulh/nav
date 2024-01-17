# Hugo版 WebStack 主题

**预览**DEMO：[oulh.github.io/nav](https://oulh.github.io/nav)
![](https://raw.githubusercontent.com/oulh/hugo-webstack/master/static/images/smartmockups_lqc03197.jpg)
本项目是基于**纯静态**的网址导航网站[webstack.cc](https://github.com/WebStackPage/WebStackPage.github.io) 制作的[Hugo](https://gohugo.io/)主题，在[iplaycode/webstack-hugo](https://github.com/iplaycode/webstack-hugo/tree/5e85297db430079c468dd33e78a945556973c73a/)的基础上完善和增加功能：

1. 增加：api自动获取网站logo图片
2. 增加：支持添加多个导航(子)页面
3. 增加：本地搜索，支持拼音匹配（支持首字母）
4. 增加：卡片显示列数变化
   - 手机端显示双列
   - 平板、PC、2/4k大屏自适应
   - 分类菜单收回或展开时，显示列数+1或-1
5. 内容增加
   - 友情链接区域
   - 页面顶部天气
   - 暗色和亮色模式切换
   - 不蒜子访问量统计(页脚)
   - 在线编辑按钮(适用于 github + 自动化部署；可隐藏)
6. 修改个别样式，增加一些可自定义配置项
7. 分类标题前的图标库升级到 [FontAwesome-v6-free](https://origin.fontawesome.com/search)

## 使用方式

### 本地构建

方式1：把主题文件夹hugo-webstack复制到themes目录，即`/themes/hugo-webstack`，将exampleSite目录下的文件复制到hugo站点根目录（覆盖原有文件），然后自行修改和构建。

方式2：以git子模块方式安装

在站点根目录下 ：

```sh
git init
git submodule add https://github.com/oulh/hugo-webstack.git themes/hugo-webstack
```

### 自动构建

方式3：**最方便**

可以 导入 或 Fork 这个初始模板： [github.com/oulh/nav](https://github.com/oulh/nav)，直接在线编辑+自动构建，无需本地环境。

自动构建平台可以选择 Github Pages、Cloudflare、Vercel、Netlify等。

## 文件说明

以下是可自定义的与网站内容相关的文件：

- 网站配置：/hugo.toml

- 主页面配置：/data/webstack.yml

- 子页面配置：/content/xxx.md

- “关于”页面：/content/about.md

- 图标等静态文件：/static/images


## 使用说明

### 网站配置项 [hugo.toml](https://github.com/oulh/hugo-webstack/blob/master/exampleSite/hugo.toml)

```toml
baseURL = "http://example.org/"
languageCode = "zh-CN"
title = "一二导航"
theme = "hugo-webstack"

#true:允许大写字母url路径，false:将url路径转换成小写
disablePathToLower = true

#页脚：作者名字
copyright = "oulh"

#网站信息，不显示，仅供搜索引擎参考
[params]
  keywords = "网页导航,webstack,hugo"
  description = "Webstack Hugo版主题"

#是否开启搜索栏，true开启，false关闭
[params.search]
  enable = true

#设置默认模式，true暗色模式，false亮色模式
[params.darkmode]
  enable = false

#主页菜单栏显示在线编辑按钮（编辑github文件，适用于自动化部署的情况）
[params.edit]
  # true显示按钮，false不显示
  enable = true
  # 站点对应的github仓库链接
  url = "https://github.com/oulh/nav/blob/main/data/webstack.yml"
  
#桌面端右上角github按钮
[params.github]
  enable = true
  url = "https://github.com/oulh/nav"
  
  [permalinks]  
  404 = "/404.html"
  
#是否对本地搜索功能开启拼音匹配，true开启，false禁止。
#拼音库体积337k，支持首字母匹配
[params.pinyin]
  enable = true
```

### 导航分类和网址配置 [webstack.yml](https://github.com/oulh/hugo-webstack/blob/master/exampleSite/data/webstack.yml)

可以复制下面的配置，以便于修改编辑自己的内容。title和url是必要属性，logo、description、qrcode可留空或删除。

```yaml
---
- taxonomy: 常用工具
  icon: fa-star
  links: 
    - title: 网络剪贴板
      url: https://netcut.cn/
      logo: images/logos/xxx.png
      qrcode: https://api.qrserver.com/v1/create-qr-code/?size=150x150&data=https://netcut.cn/
      description: 在线跨屏剪切文字
    - title: 草料二维码
      qrcode: images/qrcodes/cli.png
      url: https://cli.im/url
      description: 在线二维码生成工具
    - title: 在线文件传输
      url: https://musetransfer.com/

- taxonomy: 云服务平台
  icon: fa-cloud
  links: 
    - title: Github
      url: https://github.com/
  
- taxonomy: 网络资源
  icon: fa-download
  list: 
    - term: 软件
      links:
        - title: 果核剥壳
          url: https://www.ghxi.com/
          description: 互联网的净土。PC软件，手机软件，正版软件，破解软件
    - term: 游戏
      links:
        - title: 老男人游戏网
          url: https://www.oldmantvg.net/
          description: 仓储式主机资源站 精校 完整 极致 静待您的垂青
          
- taxonomy: 影视影音
  icon: fa-video-camera
  list: 
    - term: 影视
      links:
        - title: 阿里小站
          url: https://pan666.cn
          description: 阿里云盘资源共享站。人人为我，我为人人的共享资源社区
    - term: 字幕
      links:
        - title: 字幕库
          url: https://zmk.pw/
        - title: SubHD
          url: https://subhd.tv/
    - term: 音乐
      links:
        - title: 果核音乐搜搜
          url: https://music.ghxi.com/
        - title: 音乐磁场
          url: https://www.hifini.com/

- taxonomy: 友情链接
  icon: fa-link
  friend:
    - title: 子页面一
      url: sub1
      description: 本站子页面一，对应content目录的sub1.md，可重命名、删除、复制。
    - title: 一为导航
      url: https://nav.iowen.cn/
      description: onenav主题演示站
    - title: 趣导航
      url: https://qssily.com/
      
---
```

#### icon: 分类图标

分类标题前面的图标参考：[FontAwesome-v6-free](https://origin.fontawesome.com/search) ，如果访问不了就试试这个：[FontAwesome中文网图标库v5](https://fontawesome.com.cn/v5)

```yaml
<i class="fa-solid fa-star"></i>
icon: fa-star

<i class="fa-regular fa-star"></i>
icon：fa-regular fa-star
```

#### logo: 导航网址的图标

1. 使用api自动获取，**留空或去掉**"logo" 配置项即自动在线加载logo图标。api提供者：**[一为API](https://api.iowen.cn/)**, thanks!

2. 使用本地静态文件，存放路径：`/static/images/logos/`；

   配置写法：

   - 主页面：`logo: images/logos/xxx.png`
   - 子页面：`logo: ../images/logos/xxx.png`

   如果图片不存在，则自动使用默认的logo图片：favicon.png（在images目录下，可替换）

#### qrcode：二维码

可以加二维码，webstack.yml中的配置如下

```yaml
    - title: 二维码演示
      qrcode: images/qrcodes/cli.png
      logo: 
      url: https://cli.im/url
      description: 二维码演示，手机扫一扫，也可以点击
```

### 添加自定义导航(子)页面

在`content/` 目录下新建markdown文件，配置格式参考示例`sub1.md`。

md文件名就是访问链接的子路径，如 [oulh.github.io/nav/sub1](https://oulh.github.io/nav/sub1)

示例配置：[sub1.md](https://github.com/oulh/hugo-webstack/blob/master/exampleSite/content/sub1.md)

```yaml
---
type: nav #固定值nav(生成导航页)
title: 子页面一 #留空则使用网站标题
search: #搜索栏
  enable: true #true显示，false不显示
edit: #在线编辑
  enable: true #true显示，false:不显示
  url: https://github.com/oulh/nav/blob/main/content/sub1.md

data: #以下为导航链接内容
#下面内容的格式与/data/webstack.tml 一样
---
```

