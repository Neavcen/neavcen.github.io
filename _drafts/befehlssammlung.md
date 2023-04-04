---
layout: post
title: Befehlssammlung
description:
image:
categories:
tags:
---

Neuen Entwurf erstellen
```bash
bundle exec jekyll draft "title"
```

Entwurf veröffentlichen (Entwurf -> Post)
```bash
bundle exec jekyll publish _drafts/my-new-draft.md
```

Post nicht mehr veröffentlichen (Post -> Draft)
```bash
bundle exec jekyll unpublish _posts/2014-01-24-my-new-draft.md
```

Website testen
```bash
jekyll serve
```

Website mit Entwürfen testen
```bash
jekyll serve --drafts
```