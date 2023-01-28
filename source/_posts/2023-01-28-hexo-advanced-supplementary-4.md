---
title: Hexo 進階補充系列(4) - Butterfly 主題： 內文客製化配置
date: 2023-01-28 02:24:48
tags:
  - Hexo
  - Butterfly Theme
category:
  - Hexo
  - Advanced
cover: https://res.cloudinary.com/djtoo8orh/image/upload/v1674844446/Hexo%20Blog/2023-01-28-hexo-advanced-supplementary-4/DALL_E_2023-01-28_02.23.57_-_A_colorful_butterfly_stay_on_a_black_and_white_hexo_puzzle_odeqyu.png
description: 本文章紀錄如何客製化內文版型，包含了程式碼、文章版權、贊助、評論等客製化功能，並紀錄配置 butterfly  theme 的數學環境
---

## **Front-matter**

Front-matter 是 markdown 文件最上方以 --- 分隔的區域，用於指定個別檔案的變數。

### **Page Front-matter**

```
---
title	#【必需】頁面標題
date	#【必需】頁面創建日期
type	#【必需】標籤、分類和友情鏈接三個頁面需要配置
updated	#【可選】頁面更新日期
description	#【可選】頁面描述
keywords	#【可選】頁面關鍵字
comments	#【可選】顯示頁面評論模塊(默認 true)
top_img	#【可選】頁面頂部圖片
mathjax	#【可選】顯示mathjax(當設置mathjax的per_page: false時，才需要配置，默認 false)
katex	#【可選】顯示katex(當設置katex的per_page: false時，才需要配置，默認 false)
aside	#【可選】顯示側邊欄 (默認 true)
aplayer	#【可選】在需要的頁面加載aplayer的js和css,請參考文章下面的音樂 配置
highlight_shrink	#【可選】配置代碼框是否展開(true/false)(默認為設置中highlight_shrink的配置)
---
```

### **Post Front-matter**

```
---
title	#【必需】文章標題
date	#【必需】文章創建日期
updated	#【可選】文章更新日期
tags	#【可選】文章標籤
categories	#【可選】文章分類
keywords	#【可選】文章關鍵字
description	#【可選】文章描述
top_img	#【可選】文章頂部圖片
cover	#【可選】文章縮略圖(如果沒有設置top_img,文章頁頂部將顯示縮略圖，可設為false/圖片地址/留空)
comments	#【可選】顯示文章評論模塊(默認 true)
toc	#【可選】顯示文章TOC(默認為設置中toc的enable配置)
toc_number	#【可選】顯示toc_number(默認為設置中toc的number配置)
toc_style_simple	#【可選】顯示 toc 簡潔模式
copyright	#【可選】顯示文章版權模塊(默認為設置中post_copyright的enable配置)
copyright_author	#【可選】文章版權模塊的文章作者
copyright_author_href	#【可選】文章版權模塊的文章作者鏈接
copyright_url	#【可選】文章版權模塊的文章連結鏈接
copyright_info	#【可選】文章版權模塊的版權聲明文字
mathjax	#【可選】顯示mathjax(當設置mathjax的per_page: false時，才需要配置，默認 false)
katex	#【可選】顯示katex(當設置katex的per_page: false時，才需要配置，默認 false)
aplayer	#【可選】在需要的頁面加載aplayer的js和css,請參考文章下面的音樂 配置
highlight_shrink	#【可選】配置代碼框是否展開(true/false)(默認為設置中highlight_shrink的配置)
aside	#【可選】顯示側邊欄 (默認 true)
---
```

<br>

## **程式碼**

Butterfly 支持6種代碼高亮樣式：darker / pale night / light / ocean / mac / mac light / false

`highlight_height_limit` 配置程式碼高度限制，超出的部分會隱藏，並顯示展開按鈕，單位是 px，直接添加數字。

```yaml
# Code Blocks (代碼相關)
# --------------------------------------

highlight_theme: mac light #  darker / pale night / light / ocean / mac / mac light / false
highlight_copy: true # copy button
highlight_lang: true # show the code language
highlight_shrink: false # true: shrink the code blocks / false: expand the code blocks | none: expand code blocks and hide the button
highlight_height_limit: 300 # unit: px
code_word_wrap: false
```

<br>

## **圖片描述**

可開啟圖片Figcaption描述文字顯示

優先顯示圖片的 title 屬性，然後是 alt 屬性

```yaml
photofigcaption: true
```

<br>

## **文章頁相關配置**

### **文章相關信息**

```yaml
post_meta:
  page:
    date_type: both # created or updated or both 主頁文章日期是創建日或者更新日或都顯示
    date_format: relative # date/relative 顯示日期還是相對日期
    categories: true # true or false 主頁是否顯示分類
    tags: true # true or false 主頁是否顯示標籤
    label: true # true or false 顯示描述性文字
  post:
    date_type: both # created or updated or both 文章頁日期是創建日或者更新日或都顯示
    date_format: relative # date/relative 顯示日期還是相對日期
    categories: true # true or false 文章頁是否顯示分類
    tags: true # true or false 文章頁是否顯示標籤
    label: true # true or false 顯示描述性文字
```

### **文章版權**

```yaml
post_copyright:
  enable: true
  decode: false
  author_href:
  license: CC BY-NC-SA 4.0
  license_url: https://creativecommons.org/licenses/by-nc-sa/4.0/
```

如果有文章（例如：轉載文章）不需要顯示版權，可以在文章Front-matter單獨設置

```yaml
copyright: false
```

### **文章打賞贊助**

在每篇文章的結尾可以添加打賞按鈕，是說我比較喜歡贊助這個詞所以我把 `打賞` 改成 `贊助`。

可在 img 配置一張贊助平台的 icon 圖片，然後在 link 上添加相應的贊助平台連結或是 QR code 圖檔。

```yaml
# Sponsor/reward
reward:
  enable: false
  QR_code:
    - img: #QR code 或 icon 圖片
      link: #贊助平台 or QR code 的連結
      text: #說明文字
```

### **分頁按鈕**

```yaml
# post_pagination (分頁)
# value: 1 || 2 || false
# 1: The 'next post' will link to old post
# 2: The 'next post' will link to new post
# false: disable pagination
post_pagination: 2
```

<br>

## 標籤外掛（Tag Plugins）

<aside>
💡 標籤外掛是Hexo獨有的功能，並不是標準的Markdown格式。 而此處列出的標籤的語法只適用於 Butterfly 主題，用在其它主題上不會有效果。

</aside>

- mermaid

```yaml
# mermaid
# see https://github.com/mermaid-js/mermaid
mermaid:
  enable: true
  # built-in themes: default/forest/dark/neutral
  theme:
    light: default
    dark: dark
```

寫法：

```markdown
{% mermaid %}
內容
{% endmermaid %}
```

- [Node](https://butterfly.js.org/posts/4aa8abbe/#Note-Bootstrap-Callout)
- [tag-hide](https://butterfly.js.org/posts/4aa8abbe/#tag-hide)
- [Tabs](https://butterfly.js.org/posts/4aa8abbe/#Tabs)
- [Button](https://butterfly.js.org/posts/4aa8abbe/#Button)
- [label](https://butterfly.js.org/posts/4aa8abbe/#inlineImg)
- [timeline](https://butterfly.js.org/posts/4aa8abbe/#timeline)

<br>

## **評論**

 butterfly 官方文件提供了超過 10 種評論系統的選項，我選擇配置 Giscus。參考 [Giscus 文件](https://giscus.app/zh-CN)，根據下列步驟來部署

1. 到 repo 開啟 setting → features → 勾選 Discussions
2. 安裝 Gitscus 的 [Github App](https://github.com/apps/giscus) ，可以只勾選授權給 hexo blog 的 repo
3. 在 [Giscus 文件](https://giscus.app/zh-CN) 中輸入 github用戶名/倉庫名，設定頁面 ****↔️**** discussion 映射關係

設定好後在下方會顯示可以嵌入網站中的 JS script:

```markdown
<script src="https://giscus.app/client.js"
        data-repo="Bosh-Kuo/Bosh-Hexo-Blog"
        data-repo-id="your repo id"
        data-category="Announcements"
        data-category-id="your category id"
        data-mapping="title"
        data-strict="0"
        data-reactions-enabled="1"
        data-emit-metadata="0"
        data-input-position="bottom"
        data-theme="preferred_color_scheme" 
        data-lang="zh-TW"
        data-loading="lazy"
        crossorigin="anonymous"
        async>
</script>
```

對照著填入 `_config.yml`，只需要填入想要加入的設定，例如 data-mapping, 

```yaml
# Giscus
# https://giscus.app/
giscus:
  repo: Bosh-Kuo/Bosh-Hexo-Blog
  repo_id: # your repo id
  category_id: # your category id
  theme: 
    light: light
    dark: dark
  option:
    data-mapping: title
    data-strict: 1 #用 1 可以避免許多 title 長得太像使得 giscus 連結上錯誤的 discusion
```

接著條填寫評論區的通用設置

```yaml
comments:
  # Up to two comments system, the first will be shown as default
  # Choose: Disqus/Disqusjs/Livere/Gitalk/Valine/Waline/Utterances/Facebook Comments/Twikoo/Giscus/Remark42/Artalk
  use: Giscus
  text: true # Display the comment name next to the button
  # lazyload: The comment system will be load when comment element enters the browser's viewport.
  # If you set it to true, the comment count will be invalid
  lazyload: true
  count: false # Display comment count in post's top_img
  card_post_count: false # Display comment count in Home Page
```

<br>

## **字數統計**

安裝 hexo-wordcount 套件

```bash
npm install hexo-wordcount --save
```

配置 `_config.yml` 文件

```yaml
wordcount:
  enable: true
  post_wordcount: true
  min2read: true
  total_wordcount: true
```

<br>

## **Math 數學式環境配置**

butterfly theme 官方支持 `MathJax` 與 `KaTeX` 兩種數學工具，必須擇一使用，根據 butterfly theme 官方的敘述，MathJax 的功能多但加載速度較慢，而 KaTeX 則是功能較少，不過更快更輕量，且支援 katex 複製功能，使用者直接複製數學式可以得到數學式的 latex 表達式。因為這個部落格的數學式需求比較少，因此選擇使用較多人推薦的 `KaTeX`。

> toc 目錄不能正確顯示 KaTeX，不要在文章標題中使用數學式！！
> 

### **安裝 katex 工具**

原本使用 NexT theme 時官方建議使用 MathJax 數學工具，那時使用的 markdwon render 為 [hexo-renderer-pandoc](https://github.com/hexojs/hexo-renderer-pandoc) ， hexo 根目錄的 _config.yml 則為:

```yaml
# math
markdown:
  plugins:
    - markdown-it-footnote
    - markdown-it-sup
    - markdown-it-sub
    - markdown-it-abbr
    - markdown-it-emoji
    - hexo-math
```

- 首先須先卸載過去使用的 markdown render，若讀者原本使用其他 markdown render 也必須先將其卸載，這樣才能順利使用後續安裝的 markdown render。

```bash
npm uninstall hexo-renderer-pandoc
```

- 接著依照 butterfly 官方文件建議安裝 [hexo-renderer-markdown-it](https://github.com/hexojs/hexo-renderer-markdown-it) 與 @renbaoshuo/markdown-it-katex

```bash
npm install hexo-renderer-markdown-it --save 
npm install katex @renbaoshuo/markdown-it-katex --save
```

### 文件配置

修改 hexo 根目錄的 `_config.yml` 設定:

```yaml
# math
markdown:
    plugins:
      - plugin:
        name: '@renbaoshuo/markdown-it-katex'
        options:
          strict: false
```

修改 butterfly theme 下的 _config.yml 設定:

```yaml

# MathJax
mathjax:
  enable: false
  per_page: false

# KaTeX
katex:
  enable: true
  per_page: false
  hide_scrollbar: true
```

若文章中需要渲染數學式，需要在開頭的 front-matter 加上 `katex: true`。

<br>

## **參考資料**:

- [Butterfly 安裝文檔(一) 快速開始](https://butterfly.js.org/posts/21cfbf15/)
- [Butterfly 安裝文檔(二) 主題頁面](https://butterfly.js.org/posts/dc584b87/)
- [Butterfly 安裝文檔(三) 主題配置-1](https://butterfly.js.org/posts/4aa8abbe/)
- [Butterfly 安裝文檔(四) 主題配置-2](https://butterfly.js.org/posts/ceeb73f/)
- [giscus](https://github.com/giscus/giscus)