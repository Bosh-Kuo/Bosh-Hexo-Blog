---
title: 從零開始使用Hexo + Github Page搭建個人技術筆記網站(1) - 建立hexo部落格模板
date: 2022-01-20 16:58:52
tags:
- [Hexo]
category:
- [Hexo]
---

## 前置作業

在開始搭建hexo部落格前需要先安裝以下軟體，可以參考[官方文件](https://hexo.io/zh-tw/docs/)依照自己的作業系統安裝。

- Git
- Node.js
- VScode

<!-- more -->

<br/>

## **安裝Hexo**

### **下載 Hexo 套件包**


```bash
npm install hexo-cli -g
```

確認hexo-cli成功下載可以輸入`hexo -v` 查看 hexo-cli 版本，若有出現下方hexo-cli版本資訊就代表安裝成功囉，`注意，hexo-cli跟hexo是不一樣的東西`，如果熟悉react的朋友，我個人覺得`hexo-cli`跟`create-react-app`有點像，都是創建環境的工具，而`hexo`跟`react`才是框架本體。許多hexo主題套件會要求hexo的版本，並不是指這邊輸入`hexo -v`顯示的hexo-cli 版本，至於hexo版本怎麼看會在下方講到。

![](https://i.imgur.com/hpd7mip.png)

<br/>

### **創建hexo專案資料夾**

我選擇將hexo專案資料夾創建於我的桌面上

```bash
cd Desktop
```

```bash
hexo init Blog
```

<br/>

### **安裝專案需要的檔案**

```bash
cd Blog
```

```bash
npm install
```

完成後資料夾下應該會有下面這些檔案與資料夾：
![](https://i.imgur.com/O5gaNO3.png)

- _config.yml: 有關網站配置的檔案，可修改各種配置設定。例如：網站標題、網站的網址、使用主題名稱等等
- package.json: 紀錄專案的基本資訊如載入的套件、script等
- scaffolds: 當我們建立新文章時，Hexo 會根據 scaffolds 中的模板`.md`檔建立相對應的檔案，剛建立會有`draft.md, page.md, post.md`三種模板，分別對應草稿、頁面、文章。
- themes: 存放hexo網站主題，Hexo 會根據主題來解析 scouce 資料夾中的檔案並產生靜態頁面。預設主題為`landscape`
- source: 用來存放原始檔案的資料夾，例如 Markdown 檔、圖片、各種頁面（分頁、關於等）。資料夾以_開頭，如:`_posts, _imgs`但除了 `_posts` 資料夾以外以 `_` 開頭的檔案、資料夾或隱藏檔案會被忽略。
- source & public & .deploy_git: 執行`$ hexo generate`生成靜態網站文件時source資料夾中的Markdown 檔和 HTML 檔會被解析並根據主題渲染，並放到 public 資料夾，而其他檔案則會被拷貝過去。執行`$ hexo deploy`則會將 public 文件夾中的內容部署到 GitHub，並生成 `.deploy_git`資料夾，其內容與public幾乎完全同。

<br/>

## **看看部落格的雛形吧！**

當完成前述指令動作基本的hexo部落格就已經搭建好了，跟自己從零開始手刻一個部落格相比hexo真的是個快速又方便網站搭建神器！接下來使用hexo的一些基本指令來實現自己的部落格。

<br/>

### **新增文章**

```bash
$ hexo new [layout] <title>
```

建立一篇新的文章。如果沒有設定 `layout` 的話，則會使用 `_config.yml` 中的 `default_layout` 設定代替，`default_layout`為post。如果標題有包含空格，需使用引號括住，例如`" title"。`

![](https://i.imgur.com/LCPIWQT.png)
![](https://i.imgur.com/YgTqyW4.png)

<br/>

### **產生靜態網頁**

```bash
$ hexo generate
```

執行後，多了一個 public 目錄，點擊進去後，會發現裡面有一些內容，這是 Hexo解析`source`資料夾產生的靜態網頁資料，也就是決定部落格內容與外觀的一些文件，之後部署到github page做的事情其實就是把`public`資料夾內容搬到github上

<br/>

### **清除靜態檔案與快取**

```bash
$ hexo clean
```

清除快取檔案 (`db.json`) 和已產生的靜態檔案 (`public`)。建議在每次更新部落格內容執行hexo generate之前先執行

<br/>

### **本地伺服器**

```bash
$ hexo server
```

在本地端啟動 Hexo 伺服器，預設路徑為：`localhost:4000/`，可在自己電腦上預覽設定結果

![](https://i.imgur.com/SMPrFou.png)
![](https://i.imgur.com/2yz3f5h.png)

<br/>

## **參考資料**
- [【學習筆記】如何使用 Hexo + GitHub Pages 架設個人網誌](https://hackmd.io/@Heidi-Liu/note-hexo-github#%E5%89%8D%E7%BD%AE%E4%BD%9C%E6%A5%AD)
- [30 天利用 Hexo 打造技術部落格系列](https://ithelp.ithome.com.tw/users/20139218/ironman/3910)
- [Hexo文件-指令](https://hexo.io/zh-tw/docs/commands)