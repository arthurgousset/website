---
title: "⚙️ Math Typesetting"
date: 2022-01-17T8:00:00+01:00
draft: false
math: true
tags: ["typesetting"]
---

A summary of how I added simple mathjax support to Hugo.
After this, you can render maths easily by including it between code ticks `'$<maths>$'`

## Tools

From this [forum post](https://discourse.gohugo.io/t/mathjax-with-code-fences-2/27644/9), I found a great article by Yihui "[The Best Way to Support LaTeX Math in Markdown with MathJax](https://yihui.org/en/2018/07/latex-math-markdown/)". It includes the following JavaScript solution that can be loaded using the script below:

```js
// Not needed and only copied for future reference (in case the website is down)
(function() {
  var i, text, code, codes = document.getElementsByTagName('code');
  for (i = 0; i < codes.length;) {
    code = codes[i];
    if (code.parentNode.tagName !== 'PRE' && code.childElementCount === 0) {
      text = code.textContent;
      if (/^\$[^$]/.test(text) && /[^$]\$$/.test(text)) {
        text = text.replace(/^\$/, '\\(').replace(/\$$/, '\\)');
        code.textContent = text;
      }
      if (/^\\\((.|\s)+\\\)$/.test(text) || /^\\\[(.|\s)+\\\]$/.test(text) ||
          /^\$(.|\s)+\$$/.test(text) ||
          /^\\begin\{([^}]+)\}(.|\s)+\\end\{[^}]+\}$/.test(text)) {
        code.outerHTML = code.innerHTML;  // remove <code></code>
        continue;
      }
    }
    i++;
  }
})();
```

```js
// Script to be included in your Hugo website
<script src="//yihui.org/js/math-code.js" defer></script>
<!-- Just one possible MathJax CDN below. You may use others. -->
<script defer
  src="//mathjax.rstudio.com/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
```


## Changes to website

First, I created a new file in `layouts/partials/mathjax_support.html` and copied the script into it:

```js
// file: mathjax_support.html
<script src="//yihui.org/js/math-code.js" defer></script>
<!-- Just one possible MathJax CDN below. You may use others. -->
<script defer
  src="//mathjax.rstudio.com/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
```

Second, I created a new file in `layouts/partials/extend_head.html` and copied this code into it (from here: "[Render LaTeX math expressions in Hugo with MathJax 3](https://geoffruddock.com/math-typesetting-in-hugo/"). This lets you choose whether to render mathjax using `math: true` on individual pages. The extend_head.html file is called whenever the page is built an included between `<head></head>`.

```html
{{ if .Params.math }}
{{ partial "mathjax_support.html" . }}
{{ end }}
```

## Test typesetting

In markdown, I type this and see the output below

```md
Hi `$z = x + y$`.

`$$a^2 + b^2 = c^2$$`

`$$\begin{vmatrix}a & b\\
c & d
\end{vmatrix}=ad-bc$$`
```

Output below:

Hi `$z = x + y$`.

`$$a^2 + b^2 = c^2$$`

`$$\begin{vmatrix}a & b\\
c & d
\end{vmatrix}=ad-bc$$`

## Noob notes for math typesetting

### Simple algorithm typesetting

Quick hack for `algorithmic` package-like typesetting in `$\LaTeX$`:

```md
> Algorithm parameters: step size  `$\alpha \in (0 , 1] , \epsilon > 0$`   
Initialize  `$Q  ( s, a ), \  \forall s \in S^+ , a \in A ( s ),$` arbitrarily except that `$Q ( terminal , \cdot ) = 0$`    
>
> Loop for each episode:  
`$\quad$`Initialize `$S$`   
`$\quad$`Loop  for  each  step  of  episode:    
`$\qquad$`Choose  `$A$` from `$S$` using some policy derived from `$Q$` (eg `$\epsilon$`-greedy)   
`$\qquad$`Take action `$A$`, observe `$R, S'$`   
`$\qquad Q(S,A) \leftarrow Q(S,A) + \alpha[R+\gamma \max_a(S', a) - Q(S, A)]$`   
`$\qquad S \leftarrow S'$`    
`$\quad$` until `$S$` is terminal
```

Renders as:

> Algorithm parameters: step size  `$\alpha \in (0 , 1] , \epsilon > 0$`   
Initialize  `$Q  ( s, a ), \  \forall s \in S^+ , a \in A ( s ),$` arbitrarily except that `$Q ( terminal , \cdot ) = 0$`    
>
> Loop for each episode:  
`$\quad$`Initialize `$S$`   
`$\quad$`Loop  for  each  step  of  episode:    
`$\qquad$`Choose  `$A$` from `$S$` using some policy derived from `$Q$` (eg `$\epsilon$`-greedy)   
`$\qquad$`Take action `$A$`, observe `$R, S'$`   
`$\qquad Q(S,A) \leftarrow Q(S,A) + \alpha[R+\gamma \max_a(S', a) - Q(S, A)]$`   
`$\qquad S \leftarrow S'$`    
`$\quad$` until `$S$` is terminal