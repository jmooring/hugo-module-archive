# Hugo Module &ndash; Archive

This Hugo module creates year, month, and day archive pages for one section of a site. The module includes shortcodes and partials to render an archive widget or outline.

Requires Hugo v0.146.7 or later.

## Configuration

To add this module to your project, initialize your project as a Hugo module:

```sh
hugo mod init foo
```

In the above, `foo` is typically something like `github.com/user/project`.

Then add this to your site configuration:

```toml
[[module.imports]]
path = 'github.com/jmooring/hugo-module-archive'

[params.modules.archive]
section = '/posts/'   # The section for which to build archive pages.
prefix = '/archive/'  # The URL prefix for archive pages.
paginate = true       # Whether to paginate archive pages.
navigation = false    # Whether to display previous and next buttons on archive pages.

[params.modules.archive.formats]
year = "2006"
month = "January 2006"
day = "2 January 2006"
```

In the date formats above you may also use [localization tokens] such as `:date_long` and `:date_medium`.

[localization tokens]: https://gohugo.io/functions/time/format/#localization

To override archive page titles, create an i18n file:

```text
archive_title_year = 'Yearly archive for'
archive_title_month = 'Monthly archive for'
archive_title_day = 'Daily archive for'
```

## Usage

Run these commands to build your site:

```text
mkdir -p assets/data
hugo list published > assets/data/published-content.csv
hugo
```

### Shortcodes

To insert an archive widget in your content:

```text
{{< archive/widget >}}
```

To insert an archive outline in your content:

```textv
{{< archive/outline >}}
```

### Partials

To include an archive widget within a template:

```text
{{ partial "archive/widget.html" }}
```

To include an archive outline within a template:

```text
{{ partial "archive/outline.html" }}
```

## Try it

```text
git clone --single-branch -b hugo-github-issue-448 https://github.com/jmooring/hugo-testing hugo-github-issue-448
cd hugo-github-issue-448
mkdir -p assets/data
hugo list published > assets/data/published-content.csv
hugo server
```
