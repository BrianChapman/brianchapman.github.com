---
layout: post
title: "Auto load Both Major and Minor Mode with Filetype"
description: ""
category: [tools]
tags: [emacs]
---
{% include JB/setup %}

I recently switched this blog from Wordpress to Jekyll. I really liked the idea of a pre-compiled web site that I can edit offline and upload with a simple git push (using GitHub's pages) command. My editor of choice for the site is Emacs. Emacs has major mode for editing markdown and I am already well versed in it, so it was a natural choice. 

One problem however, I wanted to open \*.md files and have both the the markdown-mode (marjor mode) and flyspell-mode (minor mode) activated. It turns out that this was as simple as adding this to your ~/.emacs file.

    (setq auto-mode-alist (cons '("\\.md$" . markdown-mode) auto-mode-alist))
    (add-hook 'markdown-mode-hook (lambda () (flyspell-mode 1)))

And while you are at it, you might want to add 

    (setq inhibit-startup-message t)

to inhibit the startup message.
