---
title: "🤷‍♂️ Hugo (noob notes)"
date: 2021-10-29T15:13:34+01:00
draft: false
tags: ["hugo", "noob notes"]
showtoc: false
---

### Clone Hugo website on new device

Install Hugo: `brew install hugo`.

Clone repo and submodules (e.g. themes):

```bash
git clone --recurse-submodules <repo>
```

Source: [How to "git clone" including submodules?](https://stackoverflow.com/questions/3796927/how-to-git-clone-including-submodules)

Build and host locally `hugo server -D`

### Visualise Hugo in VS Code

1. In your terminal type `hugo server -D`
2. Copy the localhost address e.g. `http://localhost:1313/`
3. Open the command pallete (`Ctrl` + `Shift` + `P`)
4. Select "Simple Browser: Show"
5. Enter URL/web address (e.g. `http://localhost:1313/`)
6. Press `Enter`

Source: [Stack Overflow](https://stackoverflow.com/a/68539272)