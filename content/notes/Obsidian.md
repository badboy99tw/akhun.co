---
title: Obsidian
---
{{< obsidian >}}

## 在 code block 使用 custom font

大部分 monospaced font 並不包含 CJK，造成全形的 CJK 文字和半形的英數字寬度不同，混搭沒辦法對齊。但我想用 code block 整理台語歌的簡譜（[[Markdown#Numbered Musical Notation]]），歌詞和符號如果沒辦法對齊會非常困擾。

目前找到 [Sarasa Gothic] 這個結合 [Iosevka] 和 [思源黑體] 的 [CJK] programming font，如果要在 Obsidian 用這個字型，需要執行幾個步驟。

首先在系統安裝 [Sarasa Gothic] 字型。[[macOS]] 比較簡單，用 [[homebrew]] 直接裝就可以了。

```shell
brew tap homebrew/cask-fonts
brew install font-sarasa-gothic
```

iOS 稍微麻煩，需要先安裝 [Fontcase] 這個 [開源][xFonts] 的字型安裝工具。接著到 [Sarasa Gothic Releases] 下載 [hinted] 版本的 ttf，例如 `sarasa-gothic-ttf-0.35.9.7z`。解壓縮後拿到 `sarasa-fixed-tc-regular.ttf`，丟到 Dropbox 或 iCloud，再透過 [Fontcase] 安裝。

安裝好字型後，接著在 Obsidian 的 Vault 資料夾新增 snippet，例如 `.obsidian/snippets/song.css`。

```css
@font-face {
    font-family: 'Sarasa Fixed TC';
    src:
        local('Sarasa Fixed TC')
}

body {
    --font-monospace: 'Sarasa Fixed TC';    
}
```

我是透過 Obsidian Sync 同步資料，所以記得 `Sync` 要開 `Themes and snippets`，`Appearance` 也要開對應的 `CSS snippets`，iOS 才吃得到同步過來的設定。

這邊直接 `body` 硬幹是因為手機版的 Obsidian 版本和桌機版差了三個月（筆記當下手機是 `1.0.5(v0.12.19)`，桌機是 `v0.13.23`），[[HTML]] 結構不太一樣，而且 Front Matter 的 `cssclass` 對 Obsidian 三種顯示模式（edit, preview, read）的支援程度也不同，所以先這樣。

### TODO

- 用 `cssclass` 修改特定筆記的字型就好

[Sarasa Gothic]: https://github.com/be5invis/Sarasa-Gothic
[Iosevka]: https://github.com/be5invis/Iosevka
[思源黑體]: https://zh.wikipedia.org/zh-tw/%E6%80%9D%E6%BA%90%E9%BB%91%E9%AB%94
[CJK]: https://en.wikipedia.org/wiki/CJK_characters
[Fontcase]: https://apps.apple.com/us/app/fontcase-manage-your-type/id1205074470
[xFonts]: https://github.com/manolosavi/xFonts
[Sarasa Gothic Releases]: https://github.com/be5invis/Sarasa-Gothic/releases
[hinted]: https://en.wikipedia.org/wiki/Font_hinting

{{< /obsidian >}}