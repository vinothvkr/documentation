---
title: "Content Styling"
description: "This article describes how to syle your documentation contributions to TrueNAS."
weight: 30
tags:
- corecontributing
- scalecontributing
- corecontentstyle
- scalecontentstyle
---

{{< toc >}}

This guide has many examples of how to style your documentation contributions.
TrueNAS documentation uses standardized Markdown, HTML, and Hugo syntax to transform text, add images, and link to other locations.
The guide is not exhaustive, but contains examples of the elements that are most commonly used when writing TrueNAS documentation.
To learn more about each markup language, see these resources:

* Markdown: https://daringfireball.net/projects/markdown
* CommonMark: https://spec.commonmark.org/
* HTML: https://www.w3schools.com/html/default.asp
* Hugo: https://gohugo.io/documentation/

## Markdown Examples

{{< tabs "MarkdownExamples" >}}
{{< tab "Headers" >}}

Use hashes (#) to designate a section of content:
```
# Level 1
## Level 2
### Level 3
```
On this website, the title of the article is designated as a level 1 heading.
The rest of the content should be organized with level 2 and greater headings.
This allows the article navigation sidebar to populate with links to the different sections of your article.

{{< /tab >}}
{{< tab "Inline Text Decoration" >}}

* Italics:		`*text*`
* Bold:			`**text**`
* Preformatted/Code: 	\`text\`

You can also use standard HTML tags to transform text:

* Marked/Highlighted:		`<mark>text</mark>`
* Insert/Underlined:		`<ins>text</ins>`
* Subscripted:			`<sub>text</sub>`
* Superscripted:		`<sup>TM</sup>`
* Deleted/Strikethrough:	`<del>text</del>`

{{< /tab >}}
{{< tab "Escape Characters" >}}

To escape a syntax character so that the character is displayed without transformation, use a backslash (`\`).
You can also use HTML escapes to add comments: `<!-- this text will not be displayed in the rendered article -->`

{{< /tab >}}
{{< tab "Linking" >}}

Linking to a site that is outside docs.truenas.com is done with square brackets and parentheses:

`[example link text](www.example.com)`

You can also link directly just by typing the URL with no additional markup: `www.example.com`
HTML linking syntax is also allowed: `<a href="www.example.com">Example Site</a>`

To link to another section of the **same** article, use an anchor (`#`) to refer to that section header.
The header title needs to be in lower case and spaces replaced with dashes (-): `[Escape Characters](#escape-characters)`

{{< /tab >}}
{{< tab "Lists" >}}

Lists can be ordered or unordered:

```
1. First
2. Second
3. Third

* Who
* What
* When
```

{{< /tab >}}
{{< tab "Code Blocks" >}}

A backtick (\`) starts or stops an inline code-block: Enter `ls` to list directory contents.
Using three \` backticks on a line starts or stops a multi-line block:

```
This is a multi-line code block.
foo
bar
baz
```

{{< /tab >}}
{{< tab "Block Quotes" >}}

Use the right carat (>) to designate a block quote:

```
> The entire paragraph is formatted as the quote.
>
> You can use a > for every line of the quote or at the beginning of each paragraph of text.
```

{{< /tab >}}
{{< /tabs >}}

## Hugo Style Elements

There are a number of style elements you can use that are built into the Hugo static site generator.
This site uses Hugo shortcode syntax for images, internal references, and admonition boxes.

The documentation website also uses the [Docsy](https://github.com/google/docsy) theme.
This theme has some additional styling elements that can be used to enhance your article.
See the [Docsy shortcodes guide](https://www.docsy.dev/docs/adding-content/shortcodes/) for a list of built-in reusable content snippets.

{{< tabs "HugoStyleElements" >}}
{{< tab "Linking to Other Articles on this Website" >}}

Internal references use the Hugo `ref` shortcode to look up a file by name:
```
[Creating a new ZFS Pool]({{\< ref "pools.md" >}})
(remove the escaping backslash \)
```

Linking to the index file of an article bundle requires using the generic linking syntax to point to the article location:
```
You can copy the [article template](/contributing/documentation/template/).
```


You can also use an anchor to link to a specific section within an article:
```
[Section Level 3]({{\< ref "example.md#section-level-3" >}})
(remove the escaping backslash \)
```

{{< /tab >}}
{{< tab "Images" >}}

To add an image to your article, you need to add the image file to your article bundle.
Then use the `figure` shortcode in your article to link to the image and define any additional parameters:

```
{{\< figure src="hardware-image" title="Example Image" />}}
(remove the escaping backslash \)
```

You can also use HTML to link to an image file that is relative to the site `/static/` directory:

```
<img src="/images/network-interfaces.png" width='700px'>
```

{{< /tab >}}
{{< tab "Admonition Boxes" >}}

A simple note box is created with the `hint` shortcode:

```
{{\< hint info >}}
This is a simple note box that has a gray background and blue border
{{\< /hint >}}
(remove the escaping backslash \)
```

Alert boxes can be given any title and use `info` and `warning` to define the color:
```
{{\< hint warning>}}
This is an alert that is titled Warning and uses a red coloration.
{{\< /hint >}}
(remove the escaping backslash \)
```

{{< /tab >}}
{{< tab "Graphical Fonts and Icons" >}}

You can call either the Font Awesome or Material Design graphical fonts in your text to be more precise about what buttons or icons to click in the TrueNAS web interface.
Below are examples of icons that are already being used on the Docs website, along with the exact code you would add to the Markdown file to call that icon.

To find icons that you can include with your text, please refer to the [Material Design](https://material.io/resources/icons/?style=baseline) or [Font Awesome](https://fontawesome.com/icons?d=gallery&s=solid&m=free) Icon Libraries. Note that only the *Free* and *Solid* Font Awesome icons are supported.

To improve accessibility assistance, please be sure to use the `aria-hidden` and `title` fields with your icon.
This allows users that require accessibility assistance like screen readers to be able to know what icon is being used.

{{< /tab >}}
{{< /tabs >}}

### Icon Examples

<i class="fa fa-ellipsis-v" aria-hidden="true" title="Options"></i> = `<i class="fa fa-ellipsis-v" aria-hidden="true" title="Options"></i>`

<i class="fa fa-cog" aria-hidden="true" title="Settings"></i> = `<i class="fa fa-cog" aria-hidden="true" title="Settings"></i>`

<span class="iconify" data-icon="fa:pencil"></span> = `<i class="fa fa-pencil" aria-hidden="true" title="Pencil"></i>`

<i class="fa fa-bell" aria-hidden="true" title="Alert"></i> = `<i class="fa fa-bell" aria-hidden="true" title="Alert"></i>`

<i class="fa fa-trash" aria-hidden="true" title="Delete"></i> = `<i class="fa fa-trash" aria-hidden="true" title="Delete"></i>`

<i class="fa fa-eye" aria-hidden="true" title="eye"></i> = `<i class="fa fa-eye" aria-hidden="true" title="eye"></i>`

<i class="fa fa-bars" aria-hidden="true" title="Menu"></i> = `<i class="fa fa-bars" aria-hidden="true" title="Menu"></i>`

<i class="material-icons" aria-hidden="true" title="System Update">system_update_alt</i> = `<i class="material-icons" aria-hidden="true" title="System Update">system_update_alt</i>`

### Key Strokes

When a specific key or key combination is to be used, use the `<kbd>` HTML code to highlight the keystrokes.  Here are a few examples:

<kbd>Ctrl + C</kbd> = `<kbd>Ctrl + C</kbd>`

<kbd>Delete</kbd> = `<kbd>Delete</kbd>`

<kbd>Command+c</kbd> = `<kbd>Command+c</kbd>`

<kbd>Shift+Insert</kbd> = `<kbd>Shift+Insert</kbd>`

{{< taglist tag="corecontributing" limit="10" >}}
