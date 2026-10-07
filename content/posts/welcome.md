---
title: "Welcome to my blog"
date: 2026-10-07
draft: false
tags: ["meta"]
categories: ["Blog"]
---

This is the first post — it is here so the site doesn't start empty. Delete it
(`content/posts/welcome.md`) once you've written your own.

## How to add a new post

From the browser: on GitHub, open `content/posts/`, choose **Add file → Create
new file**, name it `my-post.md`, paste the front matter below, write your post,
and commit. The site rebuilds and publishes automatically in about a minute.

```yaml
---
title: "My post title"
date: 2026-10-07
draft: true
tags: []
categories: []
---
```

Locally it's even faster:

```powershell
hugo new content posts/my-post.md
hugo server -D     # live preview at http://localhost:1313
```

Set `draft: false` (or remove the line) when a post is ready to go public, then
`git push`.

## Formatting

You get the usual Markdown — **bold**, _italic_, [links](https://gohugo.io),
lists, tables, and syntax-highlighted code:

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, world!")
}
```

The theme also supports per-post extras — `banner`/`thumbnail` images,
`photos` galleries, and `link` posts — see `themes/cactus/README.md`.
