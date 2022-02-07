---
title: Git
---

{{< obsidian >}}

## config

### core.quotePath

解決 unicode 檔名在 macOS 亂碼的問題。舉例來說，在某個 git repo，如果有個 unicode 檔名的檔案：

```shell
touch 測試.md
```

把 `quotePath` 設成 `true`（預設），會看到亂碼：

```shell
> git config --global core.quotePath true
> git status

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	"\346\270\254\350\251\246.md"
```

把 `quotePath` 設成 `false`，就能正常顯示：

```shell
> git config --global core.quotePath false
> git status

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	測試.md
```

{{< /obsidian >}}
