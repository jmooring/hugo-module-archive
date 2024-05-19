# Hugo Module &ndash; Archive

> [!CAUTION]
> Do not use. This is work in progress.

This Hugo module creates year, month, and day archive pages for one section of a site. The module includes shortcodes and partials to render an archive widget or outline.

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

[permalinks.page]
posts = '/:year/:month/:day/:slug'

[params.modules.archive]
section = 'posts'   # The section for which to build archive pages.
prefix = 'archive'  # The URL prefix for each archive page.

[params.modules.archive.formats]
year = "2006"
month = "January 2006"
day = "2 January 2006"
```

In the above, change "posts" to another section name as needed.

To override the list titles, create the following keys in your i18n files:

- `archive_title_year`
- `archive_title_month`
- `archive_title_day`

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
