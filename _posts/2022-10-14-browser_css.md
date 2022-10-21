---
title:  Editing the CSS of Websites with the Stylus Extension
categories: [Browser]
tags: [browser, css]
---

## Stylus

GitHub repo:
<a href="https://github.com/openstyles/stylus" target="_blank">https://github.com/openstyles/stylus</a>

---

## Invert All Colors

```css
:root {
  filter: invert(100%);
}
```

This is useful to get a quick dark mode if a site is too bright.

---

## GitHub Custom Fonts

```css
@-moz-document regexp("^https?://((education|gist|graphql|guides|raw|resources|status|developer|support|vscode-auth)\\.)?github\\.com/((?!generated_pages/preview).)*$"), regexp("^https?://www\.zuora\.com.*github\.com.*"), domain("githubusercontent.com"), domain("www.githubstatus.com"), domain("stylishthemes.github.io") {
  pre, code, tt, kbd:not(.badmono), samp, .blob-code, .file-data pre, .line-data,
  #gist-form .file .input textarea, .blob-code-inner {
    font-family: var(--ghd-font-family), Consolas, "Liberation Mono", Menlo, Courier, monospace !important;
    font-feature-settings: var(--ghd-font-feature-settings) !important;
    font-size: var(--ghd-font-size) !important;
  }
}
```

---

## Google Colab Font

```css
@-moz-document url-prefix("https://colab.research.google.com/") {
/*For the regular markdown text*/
.markdown {
    font-family:candara;
}

/*For the code blocks in markdown*/
.markdown :not(pre)>code {
    font-family:"YaHei Consolas Hybrid", consolas;
}

/*For the editor*/
.view-line, .line-numbers {
    font-family:"JetBrains Mono";
    font-weight: bold;
    font-size:14px;
    /*height:22px;*/
}
}
```
