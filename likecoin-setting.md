+++
author = "Hugo Authors"
title = "在Hugo的anatole模板增加Likecoin拍手功能"
date = "2022-11-12"
description = "在原本的模板上在側邊欄新增了「分類」和「標籤」區塊，並在內文中新增了「utteranc留言板」和「Likecoin拍手功能」，這篇和大家介紹新增「Likecoin拍手功能」於內文中"
tags = ["Blog"]
categories = ["Other"]
series = ["github-blog"]
aliases = ["likecoin-setting"]
+++

> 原本的版型很美，但是缺少了一些互動的功能讓人有點空虛，因此新增了相當於按讚的「likecoin拍手功能」，這篇和大家介紹如何設置「likecoin拍手功能」。
>

## Likecoin拍手功能

最一開始會接觸到「Likecoin讚賞幣」是在找地方寫文章時，遇到一個[Matters](https://matters.news/)這個很文青的部落格，也順便研究了一下Likecoin，他的理念是：每一個掌聲都可以變為對創作者實際的支持。因此他也算是虛擬貨幣的一種，既然是貨幣就一定會有匯率，實際上他的匯率還算不錯，因此好好耕耘自己的寫作能力以及部落格，也可以化為一筆小小的收入，詳細的介紹請看官方說明[讚賞公民](https://docs.like.co/v/zh/user-guide/civic-liker)。
在幫別人點讚的時候還可以給作者實際上的支持，這樣不是很棒嗎？

## Likecoin讚賞幣設置

在設置的時候參考了網路上的資料，基本步驟如下：
1. 先申請[Liker ID](https://docs.like.co/v/zh/user-guide/liker-id)
2. 決定放置的位置，我是想放在留言板上面，以我使用的anatole主題為例，我的路徑是`/exampleSite/themes/anatole/layouts/_default/single.html`，在留言板的前面貼上以下語法
```html
<!-- LikeCoin -->
<div>
	<h3>
		<!-- 這邊放上想要說的話 -->
	</h3>
	{{ partial "likecoin.html" . }}
</div>
```
3. 新增上面所指定的`/exampleSite/themes/anatole/layouts/partials/likecoin.html`檔案，並於檔案內寫上以下語法
```html
<iframe class="LikeCoin" height="235"
	src="https://button.like.co/in/embed/{{ .Site.Params.likerID }}/button?referrer={{ .Permalink }}"
	width="100%" frameborder=0>
</iframe>
```
4. 在`config/_default/config.toml`內設置在第一步驟申請的Liker ID，語法如下
```toml
[params]
likerID = "LikerID" ##請依照您的Liker ID進行修改
```
5. 執行hugo server運行網站，並看實際上是否滿意放置的位置

## 小結

以Likecoin來代替按讚，除了可以滿足虛榮心之外，也可換成實際的金錢，這點真的非常吸引我，因為我目前的文筆還不是很好，但是又需要有一些額外的助力讓我更有動力寫文章，所以這種一步一步慢慢累積的感覺也許很適合我，在這邊推薦給大家，請試試看！

------

#### 參考資料：

* 如何在 Hugo 開發環境的文章中加入 LikeCoin button https://docs.like.co/v/zh/user-guide/creator/self-host/hugo
