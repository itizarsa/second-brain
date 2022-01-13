# mod.land

Source: Website
Status: Unprocessed
URL: https://mod.land/

Taking inspiration from the great [js.org](https://js.org/) project we at **[@denosaurs](https://github.com/denosaurs)** thought of giving something back to the deno community: a free and sleek URL where you can host a free website for your deno project.

## Table of Contents

- [For advanced users](https://mod.land/)
- [Thanks](https://mod.land/)

## How to get one?

Pretty simple.

### Step 1 - Create and statically host a website

Find a static site hosting service (we recommend [GitHub Pages](https://help.github.com/pages/)) and create your site. If you need some inspiration, this site is built and hosted with GitHub Pages and deployed with GitHub Actions.

### Step 2 - Choose your subdomain

Now you should determine your mod.land subdomain: either choose your username or the name of your repository, according to the existing GitHub Pages URL (for [http://foo.github.io/bar](https://foo.github.io/bar), either "foo.mod.land" or "bar.mod.land" would be possible).

### Step 3 - Add a CNAME to your repo

Add a file named "CNAME" to your root directory of your repository (or in the "gh-pages" branch, if you use that) with a single line matching the domain you have chosen (e.g. "foo.mod.land" without quotes). For more info about this step you can follow the [Custom URLs](https://docs.github.com/en/github/working-with-github-pages/configuring-a-custom-domain-for-your-github-pages-site) section at GitHub Pages Help.

```
+ foo.mod.land

```

### Step 4 - Claim your subdomain

To finish the procedure, make a pull request in our [GitHub repository](https://github.com/denosaurs/mod.land) that adds your subdomain to the list of existing mod.land domains. Your new URL should go live within 24 hours (keep an eye on your pull request in case of a naming conflict or a question from our side).

```
import { CNAMEs } from "./mod/types.ts";

export default <CNAMEs> {
  "@": {
    target: "denosaurs.github.io/mod.land",
  },
+ "foo": {
+   target: "foo.github.io/bar",
+ }
};

```

## For advanced users

Our subdomain are *CNAME* records which map one domain name to another. You can actually point your mod.land to many different services like [Vercel](https://vercel.com/) or [Netlify](https://netlify.com/).

## Important

As the owner of the repository, you keep complete control over your published content. That also means that all rights and duties that come along with publishing a GitHub Page (e.g. GDPR) remain in your responsibility.

## Thanks

... to [Cloudflare](https://www.cloudflare.com/) for their superb DNS service that makes this possible. Many thanks!