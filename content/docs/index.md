---
Title: Docs
Description: Documentation that came with Pico.
# hidden: true
---

## Welcome to Pico

Congratulations, you have successfully installed [Pico][] %version%.
%meta.description% <!-- replaced by the above Description header -->

## Creating Content

Pico is a flat file CMS. This means there is no administration backend or
database to deal with. You simply create <b>.md</b> files in the content folder
and those files become your pages. For example, this file is called <b>index.md</b>
and is shown as the main landing page.

When you install Pico, it comes with some sample contents that will display
until you add your own content. Simply add some .md files to your content
folder in Pico's root directory. No configuration is required, Pico will
automatically use the content folder as soon as you create your own
<b>index.md.</b> Just check out [Pico's sample contents][samplecontents] for an
example!

If you create a folder within the content directory (e.g. content/sub) and
put an index.md inside it, you can access that folder at the URL
%base_url%?sub. If you want another page within the sub folder, simply create
a text file with the corresponding name and you will be able to access it
(e.g. content/sub/page.md is accessible from the URL %base_url%?sub/page).
Below we've shown some examples of locations and their corresponding URLs:

<table style="width: 100%; max-width: 40em;">
    <thead>
        <tr>
            <th style="width: 50%;">Physical Location</th>
            <th style="width: 50%;">URL</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>content/index.md</td>
            <td><a href="%base_url%">/</a></td>
        </tr>
        <tr>
            <td>content/sub.md</td>
            <td><del>?sub</del> (not accessible, see below)</td>
        </tr>
        <tr>
            <td>content/sub/page.md</td>
            <td><a href="%base_url%?docs/sub/page">?sub/page</a></td>
        </tr>
    </tbody>
</table>

If a file cannot be found, the file <b>content/404.md</b> will be shown. You can add
<b>404.md</b> files to any directory. So, for example, if you wanted to use a special
error page for your blog, you could simply create content/blog/404.md.

Pico strictly separates contents of your website (the Markdown files in your
content directory) and how these contents should be displayed (the Twig
templates in your themes directory). However, not every file in your content
directory might actually be a distinct page. For example, some themes (including
Pico's default theme) use some special "hidden" file to manage meta data (like
<b>_meta.md</b> in Pico's sample contents). Some other themes use a <b>\_footer.md</b> to
represent the contents of the website's footer. The common point is the `_`: all
files and directories prefixed by a <b>\_</b> in your <b>content</b> directory are hidden.
These pages can't be accessed from a web browser, Pico will show a 404 error
page instead.

As a common practice, we recommend you to separate your contents and assets
(like images, downloads, etc.). We even deny access to your <b>content</b> directory
by default. If you want to use some assets (e.g. a image) in one of your content
files, use Pico's <b>assets</b> folder. You can then access them in your Markdown
using the <code>&#37;assets_url&#37;</code> placeholder, for example:
<code>!\[Image Title\](&#37;assets_url&#37;/image.png)</code>

### Text File Markup

Text files are marked up using [Markdown][] and [Markdown Extra][markdownextra].
They can also contain regular HTML.

At the top of text files you can place a block comment and specify certain meta
attributes of the page using [YAML][] (the "YAML header"). For example:

    ---
    Title: Welcome
    Description: This description will go in the meta description tag
    Author: Joe Bloggs
    Date: 2001-04-25
    Robots: noindex,nofollow
    Template: index
    ---

These values will be contained in the <b>{{ meta }}</b> variable in themes (see
below). Meta headers sometimes have a special meaning: For instance, Pico not
only passes through the <b>Date</b> meta header, but rather evaluates it to really
"understand" when this page was created. This comes into play when you want to
sort your pages not just alphabetically, but by date. Another example is the
<b>Template</b> meta header: It controls what Twig template Pico uses to display
this page (e.g. if you add <b>Template: blog</b>, Pico uses <b>blog.twig</b>).

In an attempt to separate contents and styling, we recommend you to not use
inline CSS in your Markdown files. You should rather add appropriate CSS
classes to your theme. For example, you might want to add some CSS classes to
your theme to rule how much of the available space a image should use (e.g.
<b>img.small { width: 80%; }</b>). You can then use these CSS classes in your
Markdown files, for example:
<code>!\[Image Title\](&#37;assets_url&#37;/image.png) {.small}</code>

There are also certain variables that you can use in your text files:

-   <code>&#37;site_title&#37;</code> - The title of your Pico site
-   <code>&#37;base_url&#37;</code> - The URL to your Pico site; internal links
    can be specified using <code>&#37;base_url&#37;?sub/page</code>
-   <code>&#37;theme_url&#37;</code> - The URL to the currently used theme
-   <code>&#37;assets_url&#37;</code> - The URL to Pico's `assets` directory
-   <code>&#37;themes_url&#37;</code> - The URL to Pico's `themes` directory;
    don't confuse this with <code>&#37;theme_url&#37;</code>
-   <code>&#37;plugins_url&#37;</code> - The URL to Pico's `plugins` directory
-   <code>&#37;version&#37;</code> - Pico's current version string (e.g. `2.0.0`)
-   <code>&#37;meta.\*&#37;</code> - Access any meta variable of the current
    page, e.g. <code>&#37;meta.author&#37;</code> is replaced with <b>Joe Bloggs</b>
-   <code>&#37;config.\*&#37;</code> - Access any scalar config variable,
    e.g. <code>&#37;config.theme&#37;</code> is replaced with <b>default</b>

### Blogging

Pico is not blogging software - but makes it very easy for you to use it as a
blog. You can find many plugins out there implementing typical blogging
features like authentication, tagging, pagination and social plugins. See the
below Plugins section for details.

If you want to use Pico as a blogging software, you probably want to do
something like the following:

1. Put all your blog articles in a separate <b>blog</b> folder in your <b>content</b>
   directory. All these articles should have a <b>Date</b> meta header.
2. Create a <b>blog.md</b> or <b>blog/index.md</b> in your <b>content</b> directory. Add
   <b>Template: blog-index</b> to the YAML header of this page. It will later show a
   list of all your blog articles (see step 3).
3. Create the new Twig template <b>blog-index.twig</b> (the file name must match the
   <b>Template</b> meta header from Step 2) in your theme directory. This template
   probably isn't very different from your default <b>index.twig</b> (i.e. copy
   <b>index.twig</b>), it will create a list of all your blog articles. Add the
   following Twig snippet to <b>blog-index.twig</b> near <b>{{ content }}</b>:
    ```
     {% for page in pages("blog")|sort_by("time")|reverse if not page.hidden %}
         <div class="post">
             <h3><a href="{{ page.url }}">{{ page.title }}</a></h3>
             <p class="date">{{ page.date_formatted }}</p>
             <p class="excerpt">{{ page.description }}</p>
         </div>
     {% endfor %}
    ```

## Customization

Pico is highly customizable in two different ways: On the one hand you can
change Pico's appearance by using themes, on the other hand you can add new
functionality by using plugins. Doing the former includes changing Pico's HTML,
CSS and JavaScript, the latter mostly consists of PHP programming.

This is all Greek to you? Don't worry, you don't have to spend time on these
techie talk - it's very easy to use one of the great themes or plugins others
developed and released to the public. Please refer to the next sections for
details.

### Themes

You can create themes for your Pico installation in the <b>themes</b> folder. Pico
uses [Twig][] for template rendering. You can select your theme by setting the
<b>theme</b> option in <b>config/config.yml</b> to the name of your theme folder.

[Pico's default theme][picotheme] isn't really intended to be used for a
productive website, it's rather a starting point for creating your own theme.
If the default theme isn't sufficient for you, and you don't want to create
your own theme, you can use one of the great themes third-party developers and
designers created in the past. As with plugins, you can find themes in
[our Wiki][wikithemes] and on [our website][officialthemes].

All themes must include an <b>index.twig</b> file to define the HTML structure of
the theme, and a <b>pico-theme.yml</b> to set the necessary config parameters. Just
refer to Pico's default theme as an example. You can use different templates
for different content files by specifying the <b>Template</b> meta header. Simply
add e.g. <b>Template: blog</b> to the YAML header of a content file and Pico will
use the <b>blog.twig</b> template in your theme folder to display the page.

Below are the Twig variables that are available to use in themes. Please note
that URLs (e.g. <b>{{ base_url }}</b>) never include a trailing slash.

-   <b>{{ site_title }}</b> - Shortcut to the site title (see `config/config.yml`)
-   <b>{{ config }}</b> - Contains the values you set in `config/config.yml`
    (e.g. `{{ config.theme }}` becomes `default`)
-   <b>{{ base_url }}</b> - The URL to your Pico site; use Twig's `link` filter to
    specify internal links (e.g. `{{ "sub/page"|link }}`),
    this guarantees that your link works whether URL rewriting
    is enabled or not
-   <b>{{ theme_url }}</b> - The URL to the currently active theme
-   <b>{{ assets_url }}</b> - The URL to Pico's `assets` directory
-   <b>{{ themes_url }}</b> - The URL to Pico's `themes` directory; don't confuse this
    with `{{ theme_url }}`
-   <b>{{ plugins_url }}</b> - The URL to Pico's `plugins` directory
-   <b>{{ version }}</b> - Pico's current version string (e.g. `%version%`)
-   <b>{{ meta }}</b> - Contains the meta values of the current page
    -   <b>{{ meta.title }}</b> - The <b>Title</b> YAML header
    -   <b>{{ meta.description }}</b> - The <b>Description</b> YAML header
    -   <b>{{ meta.author }}</b> - The <b>Author</b> YAML header
    -   <b>{{ meta.date }}</b> - The <b>Date</b> YAML header
    -   <b>{{ meta.date_formatted }}</b> - The formatted date of the page as specified
        by the date_format parameter in your
        config/config.yml
    -   <b>{{ meta.time }}</b> - The [Unix timestamp][unixtimestamp] derived from the
        Date YAML header
    -   <b>{{ meta.robots }}</b> - The <b>Robots</b> YAML header
    -   ...
-   <b>{{ content }}</b> - The content of the current page after it has been processed
    through Markdown
-   <b>{{ previous_page }}<b> - The data of the previous page, relative to
    current_page`
-   <b>{{ current_page }}</b> - The data of the current page; refer to the "Pages"
    section below for details
-   <b>{{ next_page }}</b> - The data of the next page, relative to `current_page`

To call assets from your theme, use <b>{{ theme_url }}</b>. For instance, to include
the CSS file <b>themes/my_theme/example.css</b>, add
<b><link rel="stylesheet" href="{{ theme_url }}/example.css" type="text/css" /></b>
to your `index.twig`. This works for arbitrary files in your theme's folder,
including images and JavaScript files.

Please note that Twig escapes HTML in all strings before outputting them. So
for example, if you add <b>headline: My <strong>favorite</strong> color</b> to the
YAML header of a page and output it using <b>{{ meta.headline }}</b>, you'll end up
seeing <b>My <strong>favorite</strong> color</b> - yes, including the markup! To
actually get it parsed, you must use <b>{{ meta.headline|raw }}</b> (resulting in
the expected <code>My **favorite** color</code>). Notable exceptions to this
are Pico's <b>content</b> variable (e.g. <b>{{ content }}</b>), Pico's <b>content</b> filter
(e.g. <b>{{ "sub/page"|content }}</b>), and Pico's <b>markdown</b> filter, they all are
marked as HTML safe.

#### Dealing with pages

There are several ways to access Pico's pages list. You can access the current
page's data using the <b>current_page</b> variable, or use the <b>prev_page</b> and/or
<b>next_page</b> variables to access the respective previous/next page in Pico's
pages list. But more importantly there's the <b>pages()</b> function. No matter how
you access a page, it will always consist of the following data:

-   <b>{{ id }}</b> - The relative path to the content file (unique ID)
-   <b>{{ url }}</b> - The URL to the page
-   <b>{{ title }}</b> - The title of the page (`Title` YAML header)
-   <b>{{ description }}</b> - The description of the page (<b>Description</b> YAML header)
-   <b>{{ author }}</b> - The author of the page (`Author` YAML header)
-   <b>{{ date }}</b> - The date of the page (`Date` YAML header)
-   <b>{{ date_formatted }}</b> - The formatted date of the page as specified by the
    `date_format` parameter in your `config/config.yml`
-   <b>{{ time }}</b> - The [Unix timestamp][unixtimestamp] derived from the page's
    date
-   <b>{{ raw_content }}</b> - The raw, not yet parsed contents of the page; use the
    filter to get the parsed contents of a page by passing
    its unique ID (e.g. `{{ "sub/page"|content }}`)
-   <b>{{ meta }}</b> - The meta values of the page (see global `{{ meta }}` above)
-   <b>{{ prev_page }}</b> - The data of the respective previous page
-   <b>{{ next_page }}</b> - The data of the respective next page
-   <b>{{ tree_node }}</b> - The page's node in Pico's page tree; check out Pico's
    [page tree documentation][featurespagetree] for details

Pico's <b>pages()</b> function is the best way to access all of your site's pages.
It uses Pico's page tree to easily traverse a subset of Pico's pages list. It
allows you to filter pages and to build recursive menus (like dropdowns). By
default, <b>pages()</b> returns a list of all main pages (e.g. <b>content/page.md</b> and
<b>content/sub/index.md </b>, but not `content/sub/page.md` or `content/index.md`).
If you want to return all pages below a specific folder (e.g. `content/blog/`),
pass the folder name as first parameter to the function (e.g. `pages("blog")`).
Naturally you can also pass variables to the function. For example, to return a
list of all child pages of the current page, use `pages(current_page.id)`.
Check out the following code snippet:

    <section class="articles">
        {% for page in pages(current_page.id) if not page.hidden %}
            <article>
                <h2><a href="{{ page.url }}">{{ page.title }}</a></h2>
                {{ page.id|content }}
            </article>
        {% endfor %}
    </section>

The <b>pages()</b> function is very powerful and also allows you to return not just
a page's child pages by passing the <b>depth</b> and <b>depthOffset</b> params. For
example, if you pass <b>pages(depthOffset=-1)</b>, the list will also include Pico's
main index page (i.e. <b>content/index.md</b>). This one is commonly used to create
a theme's main navigation. If you want to learn more, head over to Pico's
complete [pages() function documentation][featurespagesfunction].

If you want to access the data of a particular page, use Pico's <b>pages</b>
variable. Just take <b>content/\_meta.md</b> in Pico's sample contents for an
example: <b>content/\_meta.md<b> contains some meta data you might want to use in
your theme. If you want to output the page's <b>tagline</b> meta value, use
<b>{{ pages["_meta"].meta.logo }}<b>. Don't ever try to use Pico's `pages` variable
as an replacement for Pico's `pages()` function. Its usage looks very similar,
it will kinda work and you might even see it being used in old themes, but be
warned: It slows down Pico. Always use Pico's `pages()` function when iterating
Pico's page list (e.g. `{% for page in pages() %}…{% endfor %}`).

#### Twig filters and functions

Additional to [Twig][]'s extensive list of filters, functions and tags, Pico
also provides some useful additional filters and functions to make theming
even easier.

-   Pass the unique ID of a page to the <b>link</b> filter to return the page's URL
    (e.g. <b>{{ "sub/page"|link }}</b> gets <b>%base_url%?sub/page</b>).
-   You can replace URL placeholders (like <code>&#37;base_url&#37;</code>) in
    arbitrary strings using the <b>url</b> filter. This is helpful together with meta
    variables, e.g. if you add <code>image: &#37;assets_url&#37;/stock.jpg</code>
    to the YAML header of a page, <b>{{ meta.image|url }}</b> will return
    <b>%assets_url%/stock.jpg</b>.
-   To get the parsed contents of a page, pass its unique ID to the <b>content</b>
    filter (e.g. <b>{{ "sub/page"|content }}</b>).
-   You can parse any Markdown string using the <b>markdown</b> filter. For example,
    you might use Markdown in the <b>description</b> meta variable and later parse it
    in your theme using <b>{{ meta.description|markdown }}</b>. You can also pass meta
    data as parameter to replace <code>&#37;meta.\*&#37;</code> placeholders
    (e.g. <b>{{ "Written by *%meta.author%*"|markdown(meta) }}</b> yields "Written by
    _John Doe_"). However, please note that all contents will be wrapped inside
    HTML paragraph elements (i.e. <b>< p>…< /p></b>). If you want to parse just a single
    line of Markdown markup, pass the <b>singleLine</b> param to the <b>markdown</b> filter
    (e.g. <b>{{ "This really is a *single* line"|markdown(singleLine=true) }}</b>).
-   Arrays can be sorted by one of its keys using the <b>sort_by</b> filter
    (e.g. <b>{% for page in pages|sort_by([ 'meta', 'nav' ]) %}...{% endfor %}</b>
    iterates through all pages, ordered by the <b>nav</b> meta header; please note the
    <b>[ 'meta', 'nav' ]</b> part of the example, it instructs Pico to sort by
    <b>page.meta.nav</b>). Items which couldn't be sorted are moved to the bottom of
    the array; you can specify <b>bottom</b> (move items to bottom; default), <b>top</b>
    (move items to top), <b>keep</b> (keep original order) or <b>remove</b> (remove items)
    as second parameter to change this behavior.
-   You can return all values of a given array key using the <b>map</b> filter
    (e.g. <b>{{ pages|map("title") }}</b> returns all page titles).
-   Use the <b>url_param</b> and <b>form_param</b> Twig functions to access HTTP GET (i.e.
    a URL's query string like <b>?some-variable=my-value</b>) and HTTP POST (i.e. data
    of a submitted form) parameters. This allows you to implement things like
    pagination, tags and categories, dynamic pages, and even more - with pure
    Twig! Simply head over to our [introductory page for accessing HTTP
    parameters][featureshttpparams] for details.

### Plugins

#### Plugins for users

Officially tested plugins can be found at http://picocms.org/plugins/, but
there are many awesome third-party plugins out there! A good start point for
discovery is [our Wiki][wikiplugins].

Pico makes it very easy for you to add new features to your website using
plugins. Just like Pico, you can install plugins either using [Composer][]
(e.g. <b>composer require phrozenbyte/pico-file-prefixes</b>), or manually by
uploading the plugin's file (just for small plugins consisting of a single file,
e.g. </b>PicoFilePrefixes.php</b>) or directory (e.g. <b>PicoFilePrefixes</b>) to your
<b>plugins</b> directory. We always recommend you to use Composer whenever possible,
because it makes updating both Pico and your plugins way easier. Anyway,
depending on the plugin you want to install, you may have to go through some
more steps (e.g. specifying config variables) to make the plugin work. Thus you
should always check out the plugin's docs or `README.md` file to learn the
necessary steps.

Plugins which were written to work with Pico 1.0 and later can be enabled and
disabled through your <b>config/config.yml</b>. If you want to e.g. disable the
<b>PicoDeprecated</b> plugin, add the following line to your `config/config.yml`:
`PicoDeprecated.enabled: false`. To force the plugin to be enabled, replace
`false` by `true`.

## Config

Configuring Pico really is stupidly simple: Just create a <b>config/config.yml</b>
to override the default Pico settings (and add your own custom settings). Take
a look at the <b>config/config.yml</b> for a brief overview of the
available settings and their defaults.

But we didn't stop there. Rather than having just a single config file, you can
use a arbitrary number of config files. Simply create a <b>.yml</b> file in Pico's
<b>config</b> dir and you're good to go. This allows you to add some structure to
your config, like a separate config file for your theme (`config/my_theme.yml`).

Please note that Pico loads config files in a special way you should be aware
of. First of all it loads the main config file <b>config/config.yml</b>, and then
any other <b>\*.yml</b> file in Pico's <b>config</b> dir in alphabetical order. The file
order is crucial: Config values which have been set already, cannot be
overwritten by a succeeding file. For example, if you set <b>site_title: Pico</b> in
<b>config/a.yml</b> and <b>site_title: My awesome site!</b> in <b>config/b.yml<b>, your site
title will be "Pico".

## Documentation

For more help have a look at the Pico documentation at http://picocms.org/docs.

[pico]: http://picocms.org/
[picotheme]: https://github.com/picocms/pico-theme
[samplecontents]: https://github.com/picocms/Pico/tree/master/content-sample
[markdown]: http://daringfireball.net/projects/markdown/syntax
[markdownextra]: https://michelf.ca/projects/php-markdown/extra/
[yaml]: https://en.wikipedia.org/wiki/YAML
[twig]: http://twig.sensiolabs.org/documentation
[unixtimestamp]: https://en.wikipedia.org/wiki/Unix_timestamp
[composer]: https://getcomposer.org/
[featureshttpparams]: http://picocms.org/in-depth/features/http-params/
[featurespagetree]: http://picocms.org/in-depth/features/page-tree/
[featurespagesfunction]: http://picocms.org/in-depth/features/pages-function/
[wikithemes]: https://github.com/picocms/Pico/wiki/Pico-Themes
[wikiplugins]: https://github.com/picocms/Pico/wiki/Pico-Plugins
[officialthemes]: http://picocms.org/themes/
[pluginupgrade]: http://picocms.org/development/#upgrade
[modrewrite]: https://httpd.apache.org/docs/current/mod/mod_rewrite.html
[allowoverride]: https://httpd.apache.org/docs/current/mod/core.html#allowoverride
[nginxconfig]: http://picocms.org/in-depth/nginx/
