# Hugo + Netlify

This repo demonstrates basic ways to incorporate Netlify functionality into a Hugo-built website.

## tools

 - [Hugo](http://gohugo.io/), to generate HTML
 - [Netlify](https://www.netlify.com/), Deployment and hosting platform


This example combines several features of each (you will find additional annotations in layout files):

### Output Headers

[Pipes](https://gohugo.io/hugo-pipes/) + [Scratch*](https://gohugo.io/functions/scratch/) + [Custom Output Formats](https://gohugo.io/templates/output-formats) + [Headers](https://www.netlify.com/docs/headers-and-basic-auth/)

Using Hugo Pipes to output our [CSS file](/layouts/partials/head.html), we will also set a (Scratch) variable to expose the file to outputs beside our HTML page.

Using Custom Output Formats, we will create a [_header](/layouts/index.headers) file, which Netlify uses to set headers for our site.


### Redirects

[Aliases](https://gohugo.io/content-management/urls/) + [Custom Output Formats](https://gohugo.io/templates/output-formats) + [Redirects](https://www.netlify.com/docs/redirects/)

Hugo allows you to set aliases for any page in your site, but this features generates HTML pages with redirects in the page. Here, we use the `.Alias` functionality, but disable the page creation in our [config](/config.toml#L5). 

See how the alias is set in front matter in [content/page-1.md](/content/page-1.md).

We will, instead, use Custom Output [Formats](/config.toml#L21) to output a [Redirects file](/layouts/index.redir) setting rewrite rules for your site. 


### CI configuration

[ENV](https://gohugo.io/commands/hugo_env/) + [Netlify.toml](https://www.netlify.com/docs/netlify-toml-reference/)

While you can set build commands through Netlify's control panel. The [netlify.toml](/netlify.toml) file is a handy and portable way to set variables for you all your branches and set up build commands. We'll use Hugo's ENV settings to distinguish between production (master) and other branches.

---

\* _n.b. `Scratch` may be superceded in a future version of Hugo by improvements to its existing variables functionality, in which case, it can be replaced by merely setting a variable._

