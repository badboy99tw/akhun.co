---
title: hugo
---
{{< obsidian >}}

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

但在 [[macOS]] 如果遇到 `.GitInfo` 是空值，可能是因為 [[macOS]] 是用 [[unicode#NFD|NFD]] 格式儲存 unicode 檔名的關係，把 git 的 [[git#core.quotePath|quotePath]] 關掉可以解決這個問題：

```shell
git config --global core.quotePath false
```

## References

- [Git Info Variables](https://gohugo.io/variables/git/)
- [Gitinfo fails on unicode filename](https://github.com/gohugoio/hugo/issues/3071)

{{< /obsidian >}}
