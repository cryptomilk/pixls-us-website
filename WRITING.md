
Writing Content
===============

So you want to write some content for the site?  Awesome!

First, reach out to someone to make sure what you are wanting to write isn't already being worked on.  You can reach out to Pat (pat@patdavid.net) via email.  You can also check the [wiki topic on discuss][] to see what's possibly being worked on or in the queue (feel free to reply to that topic if you want feedback).  We also have our IRC channel, #pixls.us on irc.freenode.net ([webclient][]) if you want to drop in and ask someone (patdavid, DrSlony, andabata, LotR, houz, Mimir can all point you in the right direction - beware of houz though, he bites).

There are two main ways to write content for the site.  The easy way, and the hard way.  The easy way is for those folks who simply want to write a blog post or article and don't want to mess around with git or cloning the entire website.  The hard way is for those folks who want to help with the website in some way or make 100% sure that their content looks the way they want.

Unless you are going to hack at the website code, I suggest the easy way...



The Easy Way
------------
The easy way doesn't require you to do anything fancy.

Articles/posts for the site are written in [Markdown][].  These are just plain text files with some very lightweight markup to denote a few things (see the link for a basic Markdown introduction).

In order to view your Markdown rendered as it would appear on the website, we can use a browser + an appropriate extension<sup>*</sup>.

<sup>*</sup> You can also use any stand-alone text editor/previewer that you want.  There are many options available for all platforms, as well as some neat on-line versions like [dillinger.io][] and [stackedit.io][].

[dillinger.io]: http://dillinger.io/
[stackedit.io]: https://stackedit.io/


### Installing (Chrome)
To preview everything as it would appear on the website, the extension will need to allow custom css as well.

In [Chrome][] the [MarkView][] extension is known to work.  It not only shows the Markdown with custom styling, but it also auto-refreshes the view in the browser every time the parsed Markdown file is saved, which is nice.

1. Install [MarkView][].
    * Allow it to work on local files:
        In Chrome, go to: `chrome://extensions/` to see all of your extensions.  
        Find the MarkView extesion in the list and make sure the option to __"Allow access to file URLs"__ is _checked_:
        ![MarkView Extension Chrome List](https://github.com/pixlsus/website/raw/master/src/about/meta/chrome-extensions-markview.png)

2. Download the combined CSS file for pixls blogposts and save it somewhere easy to find:  
    https://raw.githubusercontent.com/patdavid/markview-css/master/pixls-blogpost.css

3. Add the CSS as an option in MarkView.
    * From the `chrome://extensions` MarkView entry, click **Options**.  
    Alternatively, from the MarkView icon on the Chrome toolbar, Right-Click and choose **Options**.
    * Under the section _"Custom Styling Instructions"_:  
    ![MarkView Custom Styling](src/about/meta/add-theme.png)
    * Find **"Add Theme CSS into Selection"** and click the _"Choose File"_ button.
    * Choose the `pixls-blogpost.css` file you downloaded in the previous step and click the _"Add Theme"_ button.

4. Select a "Document Theme".
    * In the section _"Selection"_, under **"Document Theme** the drop-down should have an entry for `pixls-blogpost` now.  Choose that theme:  
    ![MarkView Choose Theme](src/about/meta/choose-theme.png)



### Installing (Firefox)
After losing over an hour looking around, I don't see any really viable Firefox solution to live-previewing Markdown files while using custom CSS to match the pixls.us website.  The best option I could find right now appears to be [Markdown Viewer][],but it doesn't allow using custom styles or any auto-refreshing of the page on save.



The Hard Way
------------
Actually clone this repository and install the necessary packages to build it.  Check the [README.md](./README.md) file.  We will also be writing a CONTRIBUTING.md file soon for further details.

<hr>


Writing
-------
Besides using normal Markdown there are a couple of things to keep in mind for formatting while writing.


### Metadata (Frontmatter)
Every markdown file requires that there be frontmatter included.
If there will be any question on the characters being used, remember to escape them by enclosing the data in quotes.  In particular having things like colons (like CSS in `lede-style` for instance).

Until I get my crap together more, it's probably safer to copy the frontmatter from the last post of the type you're using (and modify as needed).

Required frontmatter include:

* `date`
* `title`
* `author`
* `layout`

#### `date`
The date metadata should be some form of [ISO 8601][].  It could technically be as sparse as a simple YYYY but more commonly:

`date: 2016-07-12T08:36:55-05:00`  

or

`date: 2016-07-12`

[ISO 8601]: https://en.wikipedia.org/wiki/ISO_8601


#### `title`
The article title.  Duh. :)

If there are any odd characters it would be safer to enclose the title in double quotes...

`title: "What're the best ways to help people? :)"`


#### `author`
The author name for the post.  This will appear at the bottom of the post.


#### `layout`
This specifies which type of template gets called for this post.  There are two main layout types we're using:

* `layout: article.hbt` for articles
* `layout: blog-posts.hbt` for blog posts

----

Other common frontmatter that is normally used (but _shouldn't_ break the site build if excluded) include:

* `sub-title`
* `lede-img`
* `lede-img-attribution`
* `lede-style`
* `author-img`
* `author-bio`

#### `sub-title`
The sub-title for the post.  Not needed, but have fun with it if you use it! :)

#### `lede-img`
The `lede-img` is the header image on posts.  Try to keep the image large in dimensions to accommodate bigger screen sizes (try to aim for a minimum of 1650px wide). Feel free to aggressively compress as neeeded.  I've been trying to target around no more than 300kb.


#### `lede-img-thumb`
The `lede-img-thumb` is the smaller thumbnail view of the `lede-img`.  It should be sized to around 1024px wide and also aggressively compressed to around 75kb-100kb at most.


#### `lede-attribution`
This should be html to attribute the source and license of the lede image.  For instance, the "Old Oak" lede image on the [Sharing Galore][sharing] uses the following metadata for attribution:
```html
lede-attribution: "<a href='https://discuss.pixls.us/t/old-oak-a-tutorial/1627'>Old Oak</a> by <a href='http://londonlight.org/zp/'>Morgan Hardwood</a> <a class='cc' href='https://creativecommons.org/licenses/by-sa/4.0/'>cba</a>"
```
[sharing]: https://pixls.us/blog/2016/06/sharing-galore/


#### `lede-style`
Just in case the lede image needs some slight modification to work well (centering and shifting) this will be injected into the page style (after the other styles). This should be normal CSS.

`lede-style: 'background-position: 0 0;'`


#### `author-img`
This is the headshot or avatar for the author.  

Normally this is 150px square.

While this is not a _required_ metadata, if it's not specified it will default to Pat David's ugly mug.

The image should be located at `src/images/authors/` but can be in the local directory.  The path should reflect its location.


#### `author-bio`
A short blurb about the author.  This can include links and other information and should be kept to a few sentences at most.

_Aside_: this should probably be moved to a yaml file or other template partial so that it can be called for authors by name (including the `author-img` probably).


#### Frontmatter example
For a blog post:
```
date: 
title: 
sub-title: 

lede-img:
lede-img-thumb:
lede-attribution:
lede-style:

author:
author-img:
author-bio:
collection: blogposts
layout:
```

Or an article:

```
date:
title:
sub-title:

lede-img:
lede-attribution:

author:
author-img:
author-bio:
type: "article"
collection: tutorial
layout: article.hbt
```


### Commands
When commands need to be referenced there is a special class available called `Cmd` to provide different styling:

```html
<span class='Cmd'>Colors → Desaturate...</span>
```


### Aside
Sometimes some text needs to be set _aside_ from the main writing.  There is an 'aside' class for this:

```html
<p class='aside'>This is some section of text that needs to be stylistically offset from the surrounding text.</p>
```


### Images
Images on posts and articles are normally inserted wrapped with a `<figure>` tag.  This is for both formatting and to make available the use of a `<figcaption>` tag to caption the image with semantic markup.  Markdown is smart enough to allow you to write straight HTML when needed and will pass it through to the output.

To include an image, with no caption:

```html
<figure>
    <img src='IMAGE.png' alt='Alt-Text'>
</figure>
```

To include an image _with_ a caption is straightforward:

```html
<figure>
    <img src='IMAGE.png' alt='Alt-text'>
    <figcaption>
        This is a caption for my image!
    </figcaption>
</figure>
```

You can also include a plain `<img>` tag if you want but this is not recommended.

#### Size/Width
By default, the image will be constrained to the max-width of the `<p>` elements.  This means that at the moment the width of images will be constrained to a max of **640px**.

Unless you add a class to the `<figure>` tag.  If you add `class='big-vid'` to the `<figure>` tag it will trigger a different style, allowing the image width to go up to **960px**:

```html
<figure class='big-vid'>
    <img src='IMAGE.png' alt='Alt-Text'>
</figure>
```

The reason for this is that videos share the same styling to make them large as well.


### Video
Embedded videos, like Youtube, can be inserted directly if they are wrapped in a `<div class='fluid-vid'>` tag.  This is to ensure that the iframe video is responsive with the rest of the site across various browser widths.

```html
<div class='fluid-vid'>
    <iframe width="640" height="360" src="https://www.youtube-nocookie.com/embed/cvA9KmLg7sY?rel=0" frameborder="0" allowfullscreen></iframe>
</div>
```

If you want to embed a _big_ version of the video, you can wrap it in two sets of `<div>`'s: one for `fluid-vid` and another for `big-vid`:

```html
<div class='big-vid'>
    <div class='fluid-vid'>
        <iframe width="640" height="360" src="https://www.youtube-nocookie.com/embed/cvA9KmLg7sY?rel=0" frameborder="0" allowfullscreen></iframe>
    </div>
</div>
```

This also works for other services that use `<iframe>` to embed things (like Google Maps or OpenStreetMap).



### Creative Commons Icons
We _are_ a community dedicated to Free Software photography after all - so it makes sense that we might want to release our images with permissive licensing as well!  We include the [Creative Commons][] icon fonts on the site (https://creativecommons.org/about/downloads/).

To use them, add the class `cc` to your element then use the appropriate text to show the desired icon. The below `<span>` will display the CC logo, By-Attribution, Share-Alike:

```html
<span class='cc'>
    cba
</span>
```
<strong>Icons Font</strong><br>
Logo and icons in an embeddable TTF.<br>
<small><strong>a</strong>: SA, <strong>b</strong>: BY, <strong>c</strong>: CC Circle, <strong>d</strong>: ND, <strong>n</strong>: NC,<br> <strong>m</strong>: Sampling, <strong>s</strong>: Share, <strong>r</strong>: Remix, <strong>C</strong>: CC Full Logo</small> <br><a href="http://mirrors.creativecommons.org/presskit/cc-icons.ttf">The ttf font file.</a>


[webclient]: http://webchat.freenode.net/?channels=%23pixls.us&uio=MTY9dHJ1ZSYyPXRydWUmOT10cnVl02
[wiki topic on discuss]: https://discuss.pixls.us/t/new-upcoming-pixls-us-posts-wiki/1393
[Markdown]: https://daringfireball.net/projects/markdown/basics
[Chrome]: https://www.google.com/chrome/browser/desktop/
[MarkView]: https://chrome.google.com/webstore/detail/markview/iaddkimmopgchbbnmfmdcophmlnghkim
[Markdown Viewer]: https://addons.mozilla.org/en-US/firefox/addon/markdown-viewer/
[Creative Commons]: http://creativecommons.org/
