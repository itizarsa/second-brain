# Markup from hell - HTMHell

Source: Website
Status: Unprocessed
URL: https://www.htmhell.dev/

![https://www.htmhell.dev/images/og/markup-from-hell.png?s=160621](https://www.htmhell.dev/images/og/markup-from-hell.png?s=160621)

---

A collection of bad practices in HTML, copied from real websites.

![Markup%20from%20hell%20-%20HTMHell%2080380694e9ae4a9abd828fec04940486/pentagramm.svg](Markup%20from%20hell%20-%20HTMHell%2080380694e9ae4a9abd828fec04940486/pentagramm.svg)

## #25 A link is a button is a link

[Andrea](https://twitter.com/andreavaghi)

[skip code sample](https://www.htmhell.dev/)

```
<a tabindex="0" type="button" href="/signup" role="link">
  <span class="focus" tabindex="-1"></span>
  <span>
    <span>
      <span>Sign up</span>
      <i class="icon icon-external-link" aria-hidden="true" role="img"></i>
    </span>
  </span>
</a>
```

→ [Details and tips on how to fix the diabolic code of #25.](https://www.htmhell.dev/25-a-link-is-a-button-is-a-link/)

1. `<input type="text" placeholder="First name">`
2. `<article> <div> <div class="sr-only">Image</div> <img src="/feature-teaser.png" alt="Feature teaser" /> </div></article><div> <span> <span>Exciting feature!</span> </span> <div> This text describes what the feature does! </div> <a href="/blog/feature"> <span>Read more</span> <svg viewBox="0 0 9 12" xmlns="http://www.w3.org/2000/svg"> <path d="M.84 10.59L5.42 6 .84 1.41 2.25 0l6 6-6 6z"></path> </svg> </a></div>`
3. `<button class="panel-heading" tabindex="0" href="#collapse0" aria-expanded="true"> <legend> Industries Served </legend></button>`