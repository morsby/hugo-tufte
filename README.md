# Tufte Hugo Theme

Hugo-Tufte is a minimalist blog-like theme for the
[static site generator Hugo](https://gohugo.io) that
attempts to be a faithful implementation of the
[Tufte-css](https://github.com/edwardtufte/tufte-css) project.
It supports mathematical typesetting via [MathJax](https://www.mathjax.org).
By utilizing copious partial templates the theme is largely customizable.

## State of Project

This theme is largely unmaintained. If there is a particular fork
that should be considered the primary project please submit a PR
updating the README, thanks!

## Math

Mathjax renders LaTeX written inside of markdown files. LaTeX can be
written more or less as normal, but inline and display environments that
start with `\` must be escaped. Some examples:

- `This $\LaTeX$ will be rendered inline.`
- `This \\(\LaTeX\\) will be rendered inline.`
- `A simple displayed equation: $$f(x, y) := e^{x^2 - y^2}.$$`
- `A simple displayed equation: \\[f(x, y) := e^{x^2 - y^2}.\\]`

There currently seems to be some weirdness with other environments,
such as the `align` environment. These environments will render provided
they are wrapped in `<p>` tags and blank lines. The snippet below should
render correctly.

```
Let $G$ be a finite group with exponent $2$.  Then every element is
an involution, hence for any $x$, $y$ in $G$ we have:

<p>
\begin{align*}
  e &= (xy)^2  \\
  &=xyxy \implies \\
  y^{-1} &= xyx \implies \\
  y^{-1}x^{-1} &= xy,
\end{align*}
</p>

establishing that $G$ is abelian.
```

## Site Parameters

The site specific parameters that this theme recognizes are:

- `subtitle` string: This is displayed under the main title.
- `showPoweredBy` boolean: if true, display a shoutout to Hugo and this theme.
- `copyrightHolder` string: Inserts the value in the default copyright notice.
- `copyright` string: Custom copyright notice.

## Page Parameters

- `hideDate` boolean: if true, do not display a page date. When `meta` is set to
  true, `hideDate` takes greater precedence.
- `hideReadTime` boolean: if true, do not display the page's reading time
  estimate. When `meta` is set to true, `hideReadTime` takes greater precedence.
- `math` boolean: if true, try to render the page's LaTeX code using MatheJax.
- `meta` boolean: if true, display page metadata such as author, date, categories provided
  these page parameters exist and are not overridden. Content in the `/post` directory,
  (i.e., pages of type "post") ignore this parameter.
- `toc` boolean: if true, display the table of contents for the page.

## Shortcodes

This theme provides the following shortcodes in an attempt to completely
support all the features present in the
[Tufte-css](https://github.com/edwardtufte/tufte-css) project.

- `blockquote`

  - **Description**: Wrap text in a blockquote and insert optional
    `cite` or `footer` metadata.
  - **Usage**: Accepts the named parameters `cite` and `footer`.
  - **Example**:

  ```html
  {{% blockquote cite="www.shawnohare.com" footer="Shawn" %}} There is nothing
  more beautiful than an elegant mathematical proof. {{% /blockquote %}}`
  ```

- `epigraph`

  - **Description**: Create an epigraph with the wrapped text.
  - **Usage**: To include a footer with source attribution, pass in the
    optional named parameters `pre`, `cite`, `post`. These parameters
    make no styling assumptions, so spacing is important. A more compactly
    styled epigraph will be used if the `type` parameter is set to `compact`.
  - **Example**:

  ```
  {{% epigraph pre="Author Writer, " cite="Math is Fun" %}}
  This is an example of an epigraph with some math
  \\( \mathbb N \subseteq \mathbb R \\)
  to start the beginning of a section.
  {{% /epigraph %}}
  ```

- `marginnote`

  - **Description**: Wrap text to produce a numberless margin note.
  - Usage: `{{< marginnote >}}...{{< /marginnote >}}`
  - **Example**: `{{< marginnote >}}Some marginnote{{< /marginnote>}}`

- `sidenote`

  - **Description**: Wrap text to produce an automatically numbered sidenote.
  - **Usage**: identical to `marginnote`
    `{{< sidenote >}}...{{< /sidenote >}}`
  - **Example**: `{{< sidenote >}}Some sidenote{{< /sidenote >}}`

- `figure``

  - **Description**: Display a figure.
  - **Usage**: Accepts parameters:
    - type: "full" | "margin" | null
    - src: image source
    - title
    - caption
    - link
    - attr
    - attrlink
    - label: identifier
    - class: css class

  {{< figure type="full" src="http://placekitten.com/5000/1200" caption="A cat looking dabbily. Maybe at the camera, maybe not." width="5000" height="600" title="A cat." alt="A cat" >}}

## Templates

TODO

- [ ] Describe the role of each template file, as commenting within the files
      themselves seems to break the templates.
