![](images/name.png)
A hackable hugo theme for personal blog. Forked from [cactus](https://github.com/monkeyWzr/hugo-theme-cactus) created by [@monkeyWzr](https://github.com/monkeyWzr).

[Live demo on github pages](https://slashformotion.github.io/cogito).

Some works are still in progress. See the issues to see whats comming. 

## Why this theme ? 

I am not satisfied with original [cactus](https://github.com/monkeyWzr/hugo-theme-cactus) created by [@monkeyWzr](https://github.com/monkeyWzr). Check the original one out, it's may fit your requirements. This is not my case, I prefer to make my own fork.

***Be aware: with time, this theme will differ more and more from the original.***
## Install

1. Clone cogito to your hugo site's `themes` folder.
```
git clone https://github.com/slashformotion/cogito themes/cogito
```

2. Change your theme to cogito in your site config
```toml
# config.toml

theme = "cogito"
```

3. config your site. See [Config] or a [complete config sample](exampleSite/config.toml)
4. test your site

```
hugo server
```

5. publish your site in your prefered way. See hugo's doc: [Hosting & Deployment](https://gohugo.io/hosting-and-deployment/)

## Config

### Color themes

```toml
[params]

  colortheme = "white" # dark, light, white, or classic
```

### Custom CSS

```toml
[params]
  css = ["css/custom.css"]
```

You can add multiple custom stylesheets which will be loaded after the main theme css.
For example, the above line will load the CSS-file placed at `/static/css/custom.css`.

### Navigation

```toml
# Main menu which appears below site header.
[[menu.main]]
name = "Home"
url = "/"
weight = 1

[[menu.main]]
name = "All posts"
url = "/posts"
weight = 2

[[menu.main]]
name = "Tags"
url = "/tags"
weight = 3

[[menu.main]]
name = "About"
url = "/about"
weight = 4
```

### Homepage settings

* description: description will be displayed in the homepage. Markdown syntax is supported in the description string.
```toml
[params]

  description = "Hugo is a general-purpose website framework. Technically speaking, Hugo is a static site generator. Unlike systems that dynamically build a page with each visitor request, Hugo builds pages when you create or update your content. Since websites are viewed far more often than they are edited, Hugo is designed to provide an optimal viewing experience for your website’s end users and an ideal writing experience for website authors."
```

* set your main section (used as the link for the "writings" title on the homepage)

```toml
[params]
  mainSection = "posts"
```

* change the default main section title from Writings, to something else:

```toml
[params]
  mainSectionTitle = "Blog"
```

* Show only the 5 most recent posts (default)

```toml
[params]
  showAllPostsOnHomePage = false
  postsOnHomePage = 5
```
* show all posts

```toml
[params]
  showAllPostsOnHomePage = true
  postsOnHomePage = 5 # this option will be ignored
```

* show tagsoverview (default) or not
* 
```toml
[params]
  tagsOverview = true
```

* display the table of contents inline on blog posts, rather than as part of the navigation menu:

```toml
[params]
  tocInline = true
```

* show projects list (default) or not.

```toml
[params]
  showProjectsList = true
  projectsUrl = "https://github.com/monkeyWzr"
```

Projects section will not be shown if no data file is detected. See [Projects list](#projects-list) below.

### Projects list

Create your projects data file `data/projects.yaml|toml|json`. Hugo support yaml, toml and json formats.
for former hexo cactus users: please assign your json array to a `list` key.

for example, `data/projects.json`:
```json
{
   "list": [
      {
         "name":"Hexo",
         "url":"https://hexo.io/",
         "desc":"A fast, simple & powerful blog framework"
      },
      {
         "name":"Font Awesome",
         "url":"http://fontawesome.io/",
         "desc":"The iconic font and CSS toolkit"
      }
   ]
}
```

### Social media links

```toml
[[params.social]]
  name = "github"
  link = "https://github.com/monkeyWzr"

[[params.social]]
  name = "email"
  link = "monkeywzr@gmail.com" # no need for "mailto:" at the start

[[params.social]]
  name = "linkedin"
  link = "https://www.linkedin.com/in/monkeywzr/"
```

The `name` key expects the name of a [Font Awesome icon](https://fontawesome.com/icons?d=gallery&s=brands).

### Copyright

Assign your copy right to `.Site.Copyright`. Cactus will append current year to the head.

TODO: Customizable copyright year

```toml
copyright = "Zeran Wu" # cogito theme will use site title if copyright is not set
```

### Comments

Comments is disabled by default. Enable comments in your `.Site.Params`.
```toml
[params]
  [params.comments]
    enabled = true
    # engine = "disqus" # in progress
```

You can also enable/disable comments per post. in your posts' front matter, add:
```yaml
comments: true
```

The site config is ignored when `comments` option exists in front matter.

The default engine is disqus. **By now only disqus is supported in cogito.** I will add more options sooner or later. See [Comments Alternatives](https://gohugo.io/content-management/comments/#comments-alternatives)

Before using disqus, you need to register and get your [disqus shortname](https://help.disqus.com/en/articles/1717111-what-s-a-shortname). Assign your shortname in `.Site.disqusShortname`, or cogito will use `.Site.Title` by default.

```
disqusShortname = "wzr" # cogito will use site title if not set
```

### highlight

Use hugo's built-in [syntax highlighting](https://gohugo.io/getting-started/configuration-markup#highlight).

default config:

```toml
[markup]
  [markup.highlight]
    codeFences = true
    guessSyntax = false
    hl_Lines = ""
    lineNoStart = 1
    lineNos = false
    lineNumbersInTable = true
    noClasses = true
    style = "monokai"
    tabWidth = 4
```

### Analytics

Cactus uses hugo's built in analytics templates. Check [the official Hugo docs](https://gohugo.io/templates/internal#google-analytics) for details.

Set you tracking id in your site config.
```toml
googleAnalytics = "UA-XXXXXXXX-XX" # or G-XXXXXXXX if you are using Google Analytics v4 (gtag.js)
```

If you are using Google Analytics v3 (analytics.js), you can switch to asynchronous tracking by set `params.googleAnalyticsAsync` to `true`.
```toml
[params]
googleAnalyticsAsync = true # not required
```

### Related content

Cactus supports hugo's automatic related content. You can enable it in your site config:

```toml
[related]
  includeNewer = true
  threshold = 10
  toLower = true
  [[related.indices]]
    name = "keywords"
    weight = 80
  [[related.indices]]
    name = "title"
    weight = 80
  [[related.indices]]
    name = "tags"
    weight = 100
  [[related.indices]]
    name = "date"
    weight = 60
	pattern = "2006"
```

Please also check [Related Content](https://gohugo.io/content-management/related/) & [Better Relationships in Hugo with Hugo's Related Content](https://www.regisphilibert.com/blog/2018/04/hugo-optmized-relashionships-with-related-content/).

### RSS

The rss feed is not generated by default. you can enable it in your site config:

```toml
[params]
  rss = true
```

The rss link will be `https://example.com/index.xml` assuming your `baseURL` is set to `https://example.com/`

Please also check [Configure RSS](https://gohugo.io/templates/rss/#configure-rss)

### Mathjax

Cactus supports mathjax. Just add `mathjax` option in your site config:
```toml
[params]
  mathjax = true  # not required
```

You can also enable/disable mathjax per post. In your posts' front matter, add:
```yaml
mathjax: true # or false
```

The site config will be ignored when `mathjax` option exists in front matter.

### Archive 
Pagination on posts archive can be disabled to show all posts in chronological order

```toml
[params]
  showAllPostsArchive = true # or false (default)
```

## License

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

