# Cheat sheet: writing a page inside /docs

What is this: A few rules about headings, internal linking, images and more that we kept in mind. It's _how we did_ it.

For who: Anyone documenting in the KERI Suite and WOT-terms repo specifically.

What problem does it solve: Everything that is important to do the right way, but you keep forgetting how to do it. Here's the cheat sheet to remind you and assist you.

What's the result: The KERI Suite uses Docusaurus to generate enhanced technical documentation. Complying with the rules in this cheat sheet means optimal readability, less broken links, well-styled images, etc.

> [!NOTE]
> Use an editor that fixes markdown links when changing file names or moving files. We recommend _[Visual Studio Code](https://code.visualstudio.com)_.
>
> Change default setting in Visual Studio Code:
>
> -   Go to preferences
> -   Type in search field: “markdown link update”
> -   Set to “prompt” or “always”
>
> ([This video](https://www.youtube.com/watch?v=3hcN0yfOAzQ) explains.

Use empty lines between every block:

Right:
```
# Main title

## Subtitle

A paragraph text

Another paragraph text
```
Wrong:
```
# Main title
## Subtitle
A paragraph text
Another paragraph text
```
Start a page with a `#` followed by a space.

(If you start with a `##` then Docusaurus will ad a `#` based on the file name. Not desirable.)

Example:

`# Main title`

This will result in a `<h1>` in the final html after the Markdown is parsed.

Add structure to your document by adding `<h2>`, in Markdown a `##` followed by a space.

Example:
```
# Main title

Lorem ipsum dolor sit amet, consectetur adipiscing elit.

## Subtitle 1

Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium

## Subtitle 2

Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit.
```
> [!NOTE]
> -   Unlike a CMS like Wordpress, Docusaurus is file based. Renaming a file means that a link to this file no longer works if the file name is not also changed inside the link.
>
> -   After renaming a file or directory you will have to restart the localserver to take effect. Also it is recommended to use an incognito browser to avoid caching issues. (And even then it looks like sometimes it may take while before links start to work.)

Internal linking is not easy in most content management systems. In Docusaurus it's difficult to keep all links working after renaming files. Here you will find best practise.

General rules:

-   use relative links
-   use the `.md` extension at the end
-   use the **file**name, not what you see in the browser address bar (numbers at the beginning of a file are used for ordering and removed in the url. You should use the file name with numbers in it)

Let's take this file system:
```
├── concepts
│   ├── concepts.md
│   └── keri-dev-env.md
├── education
│   ├── intro.md
```
To create a link inside education/intro.md TO concepts/concepts.md write the following:
```
[Link to concepts](https://weboftrust.github.io/keridoc/docs/how-we-did/keridoc/concepts/concepts.md)
```
If you do it this way, you can make Visual Studio Code [work for you](#strongly-recommended) and update the links if you move or rename files.

There are more ways to create links, read about it on [https://docusaurus.io/docs/markdown-features/links](https://docusaurus.io/docs/markdown-features/links), but this is how we do it here.

To create a link to an anchor in the same page:
```
[anchor link inside the same page](#foo)
```
```
[Link to concepts](https://weboftrust.github.io/keridoc/docs/how-we-did/keridoc/concepts/concepts.md#foo)
```
```
[link text](https://www.example.com)
```
-   Use html syntax (not markdown)
-   however, use `className` and not the normal `class`
-   and use `require` for local images
-   do not add html attributes like `width` or `height` and do not use `style='…'`
-   always use an `alt` attribute. If the image is decorative leave it empty (`alt=""`), else write something as if you explain the image to someone on the phone

You can copy these examples and use it (there is a copy button available at the right):
```
<img className="inline-small-start" src={require('/static/img/foo.png').default} alt="Foo" />
```
```
<a href="https://www.example.com"><img className="inline-small-start" src={require('/static/img/foo.png').default} alt="Foo" /></a>
```
```
<img className="inline-small-start" src='https://www.example.dom/img/foo.png' alt="Foo" />
```
```
<a href="https://www.example.com"><img className="inline-small-start" src='https://www.example.dom/img/foo.png' alt="Foo" /></a>
```
You can insert images using Markdown but you cannot style these images using classes (CSS). So that is not very usable. That is why we use html syntax.

Images are styled via CSS.

The following classes are available for styling (there is a copy button available at the right):
```
inline-thumb-start
```
```
inline-thumb-end
```
```
inline-small-start
```
```
inline-small-end
```
```
inline-medium-start
```
```
inline-medium-end
```
Start means “to the left” (in left-to-right languages).

When no class is added the image will be 100% width.

TBW

More info: [https://docusaurus.io/docs/markdown-features/assets#images](https://docusaurus.io/docs/markdown-features/assets#images)

Use

-   [kebab-case](https://en.wikipedia.org/wiki/Naming_convention_\(programming\)#Delimiter-separated_words)
-   all lower case (except… in the glossary, where you will find files like `ACDC.md` etc. These abbreviations need to be uppercase)

This is how it is done in a default Docusaurus install.

Examples:

Directory: `tutorial-basics`

File: `create-a-page.md`

Combined: `tutorial-basics/create-a-page.md`

No conventions (yet), except two:

-   remove spaces and replace with dash, underscore or nothing.
-   put all media files in `/static` (and not in an image dir somewhere in `/doc`).

The sidebar menu is autogenerated and sorted alphanumerically.
```
├── concepts
│   ├── concepts.md
│   └── keri-dev-env.md
├── education
│   ├── intro.md
```
The directories “concepts” and “education” are called “categories” in Docusaurus. To give them a custom order, do as follows:
```
├── 02_concepts
│   ├── concepts.md
│   └── keri-dev-env.md
├── 01_education
│   ├── intro.md
```
As a bonus effect, the Visual Studio File Explorer will rearrange the directories, so will other systems like MacOS Finder etc. It is simple, effective (and intuitive for most people).

The `01_` and `02_` are removed and not visible in the browser. Renumbering will change paths in internal links but Visual Studio Code will fix these paths for you if you [have configured it to do so](#strongly-recommended).

Thank you for going all the way down the cheat sheet. Have a great time writing!