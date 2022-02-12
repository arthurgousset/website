---
title: "🤷‍♂️ Hugo (noob notes)"
date: 2021-10-29T15:13:34+01:00
draft: false
tags: ["hugo", "noob notes"]
showtoc: false
---

### Create post

```bash
hugo new posts/<file.md>
```

### Clone Hugo website on new device

Install Hugo: `brew install hugo`.

Clone repo and submodules (e.g. themes):

```bash
git clone --recurse-submodules <repo>
```

Fetch and merge updates in submodule:

```bash
git submodule update --remote
```

_Source: [Git docs - 7.11 Git Tools - Submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules)_


Build and host locally `hugo server -D`

### Visualise Hugo in VS Code

1. In your terminal type `hugo server -D`
2. Copy the localhost address e.g. `http://localhost:1313/`
3. Open the command pallete (`Ctrl` + `Shift` + `P`)
4. Select "Simple Browser: Show"
5. Enter URL/web address (e.g. `http://localhost:1313/`)
6. Press `Enter`

Source: [Stack Overflow](https://stackoverflow.com/a/68539272)

### Exclude some files

In `config.yml`, to exclude specific files from the `content` and `data` directories when rendering your site, set `ignoreFiles` to one or more regular expressions to match against the absolute file path.

To ignore files ending with `.foo` or `.boo`:

```yaml
ignoreFiles:
- \.foo$
- \.boo$
```

To ignore a file using the absolute file path:

```yaml
ignoreFiles:
- ^/home/user/project/content/test\.md$
```


Source: [gohugo.io  - Ignore Content and Data Files when Rendering](https://gohugo.io/getting-started/configuration/#ignore-content-and-data-files-when-rendering)
