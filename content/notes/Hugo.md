---
title: Hugo
---
{{< obsidian >}}

## Support Numbered Musical Notation

為了要讓整理好的簡譜也能正常顯示，需要把簡譜用支援 CJK 的 monospaced font 顯示，例如 [Sarasa Gothic]。但因為把整包 CJK 字型放到網站上實在太肥，想到既然 [Sarasa Gothic] 整合 [Iosevka] 和 [思源黑體]，那可不可以英數字用 [Iosevka]、CJK 靠 Google 提供的 webfont [Noto Sans Traditional Chinese] 來顯示呢？於是就來實驗看看。

[Iosevka] 可以從 [releases][Iosevka/releases] 抓 `ttf-iosevka-fixed-slab`，目前 `ttf-iosevka-fixed-slab-14.0.0.zip`，解開後拿會用到的 `iosevka-fixed-slab-regular.ttf` 就好，放到 static 裡面。[Noto Sans Traditional Chinese] 直接到網頁底下選 regular 拿 import 路徑。最後字型相關的設定如下：

```css
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+TC&display=swap')

@font-face
    font-family: 'Iosevka'
    size-adjust: 86% /* 土炮對齊 QQ */
    src: url('/fonts/iosevka-fixed-slab-regular.ttf')
```

那個 `size-adjust: 86%` 實在非常土炮，但我一時也不知道 [Sarasa Gothic] 做過什麼處理，就先這樣 QQ

設定細節可以看這個 [commit](https://github.com/badboy99tw/hugo-theme-sam/commit/bfb0c2e97346c3d9a66c5d4136332a470699ec19)；最後 render 起來的感覺可以參考 [[songs/雨夜花|雨夜花]]。

[Sarasa Gothic]: https://github.com/be5invis/Sarasa-Gothic
[Iosevka]: https://github.com/be5invis/Iosevka
[Iosevka/releases]: https://github.com/be5invis/Iosevka/releases
[思源黑體]: https://zh.wikipedia.org/zh-tw/%E6%80%9D%E6%BA%90%E9%BB%91%E9%AB%94
[Noto Sans Traditional Chinese]: https://fonts.google.com/noto/specimen/Noto+Sans+TC

### TODO

iOS 上試過 Safari、Firefox、Edge、Chrome 都吃不到 `size-adjust`，所以還是歪的。但正解應該是用 [[font#CJK 網路字型處理|WOFF]] 處理 [Sarasa Gothic]，有空來研究一下，不要再土炮啦！

## .Lastmod

如果想拿 git commit 的時間作為最後修改時間，可以在 `config.yaml` 裡設定 `enableGitInfo`：

```yaml
enableGitInfo: true
```

接著 page template 就能拿到 `.GitInfo` 或 `.Lastmod` 這些資訊了：

```html
{{ .GitInfo | jsonify }}
{{ .Lastmod.Format "Mon Jan 02, 2006" }}
```

但在 [[macOS]] 如果遇到 `.GitInfo` 是空值，可能是因為 [[macOS]] 是用 [[Unicode#NFD|NFD]] 格式儲存 unicode 檔名的關係，把 git 的 [[Git#core.quotePath|quotePath]] 關掉可以解決這個問題：

```shell
git config --global core.quotePath false
```

若還想在 [[Markdown]] 的 Front Matter 手動指定 `lastmod`，則需要 [從 config 設定 lastmod 的順位](https://gohugo.io/getting-started/configuration/#configure-dates)，例如：

```yaml
// config.yaml
frontmatter:
  lastmod:
    - lastmod
    - :git
    - date
    - publishDate
```

## References

- [Git Info Variables](https://gohugo.io/variables/git/)
- [Gitinfo fails on unicode filename](https://github.com/gohugoio/hugo/issues/3071)
- [Last Modified Date in Hugo](https://mertbakir.gitlab.io/hugo/last-modified-date-in-hugo/)

{{< /obsidian >}}
