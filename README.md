"Spectral" theme for Pelican
===================================
This is an adaptation of the [html5up](html5up.net) template "Spectral" for the Python static site generator [Pelican](http://docs.getpelican.com/).

It it base on [Frank Valcarcel](http://frankvalcarcel.com) work on "Twenty", and other sources of inspiration.


## Template Breakdown

There are currently 12 templates:
```
├── archives.html 			// archive pages (right-sidebar)
├── article.html 				// article pages (no-sidebar)
├── banner.html 				// hero unit on index
├── base.html 				// all templates extend base, base contains head, body, and nav
├── category.html 			// category pages (right-sidebar)
├── style1.html 			// gallery section on index
├── style2.html 			// gallery section on index
├── style3.html 			// gallery section on index
├── cta.html 					// call to action near footer of index and archives
├── footer.html 				// copyright and social icons
├── index_page.html 				// one-to-one for index of original
├── most_recent.html 			// three column most recent articles template
├── page.html 				// all pages (no-sidebar)
└── pagination.html
```

## Previews
 - index.html (extends base.html)

![preview](preview.png "preview")

## Usage

This theme honors the following standard Pelican settings:

* Putting feeds in the `<head>` section:
        * `FEED_ALL_ATOM`
        * `FEED_ALL_RSS`
* Template settings:
        * `DISPLAY_PAGES_ON_MENU`
        * `DISPLAY_CATEGORIES_ON_MENU`
        * `MENUITEMS`
        * `LINKS` (Blogroll will be put in the sidebar instead of the head)
* Analytics & Comments
        * `GOOGLE_ANALYTICS` (classic tracking code)
        * `GOOGLE_ANALYTICS_UNIVERSAL` and `GOOGLE_ANALYTICS_UNIVERSAL_PROPERTY` (Universal tracking code)
        * `PIWIK_URL`, `PIWIK_SSL_URL` and `PIWIK_SITE_ID`

### Social links
You can add social links following at the bottom of the page, following the same convention that the pelican-bootstrap3 theme (https://github.com/getpelican/pelican-themes/tree/master/pelican-bootstrap3#sidebar-options)

### Facebook Open Graph

In order to make the Facebook like button and other social sharing options work better, the template contains Open Graph metatags like <meta property="og:type" content="article"/>. You can disable them by setting USE_OPEN_GRAPH to False. You can use OPEN_GRAPH_FB_APP_ID to provide a Facebook app id. You can also provide a default image that will be passed as an Open Graph tag by setting OPEN_GRAPH_IMAGE to a relative file path, which will be prefixed by your site's base url. Optionally, you can override this default image on a per article and per page basis, by setting the og_image variable in an article or page.


### Site Brand

You can provide a logo for your site using `SITELOGO`. For example: `SITELOGO =
'images/my_site_logo.png'`. You can then define the size of the logo using
`SITELOGO_SIZE`. The `width` of the `<img>` element will be set accordingly.

By default the `SITENAME` will be shown as well. It's also possible to hide the site name using the `HIDE_SITENAME` flag.


#### Caveats
**1. skel.js**<br>
html5up uses [skel.js](https://github.com/n33/skel) to handle responsiveness of their templates. For skel to work right css has to be available at the `{{ SITEURL }}/css/` path. I did not want to alter any of the files in the template (**not even the init.js**). So to fix this for development my [fab](http://www.fabfile.org/) script copies over the css and js from the static folder and places them into their corresponding locations in my output directory.
Here's my fab script I call `collectstatic`:

```python
def collectstatic():
  if os.path.isdir(DEPLOY_PATH):
    local('mkdir -p {deploy_path}/css/ {deploy_path}/js/ {deploy_path}/fonts/ {deploy_path}/images/'.format(**env))
    local('cp -rf {theme_path}/static/css/* {deploy_path}/css/'.format(**env))
    local('cp -rf {theme_path}/static/js/* {deploy_path}/js/'.format(**env))
    local('cp -rf {theme_path}/static/fonts/* {deploy_path}/fonts/'.format(**env))
    local('cp -rf {theme_path}/static/images/* {deploy_path}/images/'.format(**env))
```


**2. index page**<br>
Following [pelican's FAQ](http://docs.getpelican.com/en/3.6.3/faq.html#how-can-i-use-a-static-page-as-my-home-page), the index page must have a few extra parmeters

```
Template: index_page
URL:
save_as: index.html
Status: hidden
```

The `Image:` parameter can be used to define the background image


**4. articles categories**<br>
To generalize the use of this template, 2 article categories can be defined in the `pelicanconf.py` file.
```
STYLE3_CATEGORY = "blog"
STYLE3_TITLE = "Accumsan mus tortor nunc aliquet"
```
which correspond to the third gallery container in the template. The third containter list all the static pages.

```
├── blog						//standard articles
│   ├── article1.md
│   ├── article2.md
│   ├── article3.md
│   └── article4.md
├── pages
│   ├── about.md
│   └── portfolio.md
└── programming				//category
    └── article1.md
```

#### To Do
[ ] Portfolio Category<br>
[ ] Add `Featured` and `FeaturedImage` attribute to content and templates<br>


============================
#### Template Info
Twenty 1.0 by HTML5 UP<br>
html5up.net | @n33co<br>
Free for personal and commercial use under the CCA 3.0 license (html5up.net/license)


This is Twenty, a minimal, multi-page responsive site template for HTML5 UP.

As the name implies, this is my twentieth (!) design for HTML5 UP. Since the last
few have been single page affairs, I decided to go with something a bit more conventional
and threw in four extra page layouts. Beyond that, it's the usual drill: fully responsive,
built on HTML5/CSS3/skel, and CCA licensed like all my other stuff.

Special thanks to Michael Domaradzki (mdomaradzki.deviantart.com) for allowing me to
use his excellent photos in Twenty's demo*.

(* Not included with this download (replaced with generic placeholder images), as
I only have permission to use his work in my own on-site demos. Do NOT download
or use any of his work without prior explicit permission.)


AJ<br>
[n33.co](http://n33.co) [@n33co](http://twitter.com/n33co) [dribbble.com/n33](http://dribbble.com/n33)



#### Credits
Icons
 - Font Awesome (http://fortawesome.github.com/Font-Awesome/)

Other
 - jQuery (jquery.com)
 - html5shiv.js (@afarkas @jdalton @jon_neal @rem)
 - background-size polyfill (https://github.com/louisremi/background-size-polyfill)
 - Misc jQuery plugins (n33.co)
 - skel (n33.co)
