---
title: Hexo 補充系列 - 註冊個人網域域名(with Godaddy)與Github Page 設定
date: 2022-10-02 21:42:26
tags:
- [Hexo]
- [Hexo supplementary]
category:
- [Hexo]
---


## **自訂網域**

Github Pages 原本就會提供一個預設的網域: `<使用者名>.github.io` ，以這個的部落格為例，我的 repo 名稱為 **Bosh-Kuo-Blog**，因此 Github Pages 提供預設的網址為 `bosh-kuo.github.io/Bosh-Hexo-Blog/` 。若想要把網址換成自己喜歡的名字，可以 “買” 一個屬於自己的網址，再將原網站綁到買來的網址上。

<br>

<!-- more -->

### **購買域名**

買網域的管道有很多，我看到大多數的教學文章都是從 [godaddy](https://tw.godaddy.com/?checkAvail=1&itc=mya_dom_srch&pl_id=1&key=mya_domain_search) 這個網站買的，因此我第一次買個人網域就選擇使用它了。 godaddy 的網頁介面做的滿不錯的，至少算是新手友善，至於價格由於我是第一次買網域所以我也不太清楚自己買貴還是買便宜，總之我花了約莫 NT$ 380 購買了 `boshkuo.com` 這個網域一年的使用權，直得注意的一點是 godaddy 預設開啟自動續約服務，我個人這次買網域的目的比較偏實驗性質，因此有手動關閉自動續約，反正過期了還是可以繼續用原本 Github Pages 提供的預設網域 XD。

<br>

### **設定 Godaddy DNS server**

當有人在瀏覽器輸入 `boshkuo.com` 這個網址，godaddy 的 DNS server 的就會解析  `boshkuo.com` 這個網址對應的 IP 回傳給使用者，因爲我們的 Blog 是放在 Github 的網址上，所以我們需要設定讓 godaddy 的 DNS server 知道要把請求轉到 Github 網址去。

我們在 godaddy 的 DNS 管理頁面新增 4 組 Github 的網址 IP，類型為 `A`，名稱為 `@` ，內容值如下依序新增四組，

- 185.199.108.153
- 185.199.109.153
- 185.199.110.153
- 185.199.111.153

新增完後把原本 godaddy 預設的類型 A 紀錄刪除。

![](https://i.imgur.com/UUgt9a0.png)

<br>

## **Github Pages 設定**

接著 repo 的 Custom domain 設定中填寫購買的域名，在 Github Repository deploy branch 會新增一個叫做 `CNAME` 的檔案，裡面有一行剛剛設定好的 Custom domain name，CNAME 的功能在於讓 Github 知道 `boshkuo.com` 始於哪個 User 的哪個 repo，因此 `CNAME` 會放在要 deploy 的 branch 下。設定好並且 Github action 也完成 deploy 後點擊網址會發現網站沒有 CSS 或是 404 not found，這是因為目前的網頁靜態內容還是使用過去的網址，只需要調整 Hexo 設定檔並且重新生成一次文章並且部署應該就沒問題了。

![](https://i.imgur.com/f3G2gAD.png)

<br>

## **Hexo 設定**

我們需要更改 `_config.yml` 檔中的 `url` 部分，因為他會影響到靜態網頁文件所有跟 url 有關聯的地方。

```yaml
url: http://boshkuo.com/  # 網站的網址:無個人網域(https://Bosh-Kuo.github.io/Bosh-Hexo-Blog/)
root: /  # 網站根目錄:無個人網域(/Bosh-Hexo-Blog/)
```

我有嘗試過 url 用 `http://boshkuo.com/Bosh-Hexo-Blog/`，root 用 `/Bosh-Hexo-Blog/` ，但卻不 work，個人推測是依照目前的設定， `boshkuo.com` 就代替 `https://Bosh-Kuo.github.io/Bosh-Hexo-Blog/` 這段網址，因此 `http://boshkuo.com/Bosh-Hexo-Blog/` 則會導到 `http://boshkuo.com/Bosh-Hexo-Blog/Bosh-Hexo-Blog` 去，至於要怎麼讓網站放在域名的下一層目前還沒有找到解法，就先這樣吧～

![](https://i.imgur.com/EZYBVLj.png)

接下來重新 deploy 一次應該就 ok 了 ～

<br>

## **參考資料**

- [架設部落格第一次就上手 Hexo + Github + 自訂網域](https://chanchandev.com/note/Hexo/hexo-introduction/2335841689/)
- [如何使用 Hexo + Github Page 自訂網域名稱 + Cloudflare SSL 免費憑證](https://wualnz.com/%E5%A6%82%E4%BD%95%E4%BD%BF%E7%94%A8-Hexo-Github-Page-%E7%94%A8-Cloudflare-%E7%B6%81%E5%AE%9A%E5%80%8B%E4%BA%BA%E7%B6%B2%E5%9D%80/)
- [【基礎教學】利用 Hexo 與 GitPage 建置個人 Blog](https://medium.com/@a3216lucy/%E5%9F%BA%E7%A4%8E%E6%95%99%E5%AD%B8-%E5%88%A9%E7%94%A8-hexo-%E8%88%87-gitpage-%E5%BB%BA%E7%BD%AE%E5%80%8B%E4%BA%BA-blog-79f34cbc1d86)