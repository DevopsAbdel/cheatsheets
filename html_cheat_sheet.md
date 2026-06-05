# The Complete HTML Cheat Sheet
**v1.0 by Max Lockwood**

This HTML cheat sheet includes the most common HTML tags together with their attributes in an easy-to-read format, divided into the appropriate categories.

---

## Document Summary

HTML is the Web's universal markup language. HTML allows you to format text, add graphics, make links, input forms, frames, and tables, among other things, and save it all in a text file that any browser can read and display.

* `<!DOCTYPE html>`
    All HTML documents must start with a `<!DOCTYPE>` declaration. The declaration is not an HTML tag. It is an "information" to the browser about what document type to expect.
* `<html> ... </html>`
    The `<html>` HTML element represents the root (top-level element) of an HTML document, so it is also referred to as the root element. All other elements must be descendants of this element.
* `<head> ... </head>`
    This tag is used to specify meta data about the webpage. It includes the webpage's name, its dependencies (JS and CSS scripts), font usage etc.
* `<body> ... <body>`
    This tag contains everything a user sees on a webpage. It is a container for all of the webpage's contents. Headings, paragraphs, images, hyperlinks, tables, and lists are examples of visible contents.

### Example
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Document</title>
</head>
<body>
    <!-- Your content goes here -->
</body>
</html>
```

---

## Document Information

* `<base/>`
    Used to specify the base URL for your site, this tag makes linking to internal links on your site cleaner.
* `<meta/>`
    This is the meta data tag for the webpage. Can be useful for mentioning the page's author, keywords, original published date etc.
* `<title> ... </title>`
    As the name suggests, this tag contains the title/name of the webpage. You can see this in your browser's title bar for every webpage open in the browser. Search engines use this tag to extract the topic of the webpage, which is quite convenient when ranking relevant search results.
* `<link/>`
    This is used to link to scripts external to the webpage. Typically utilized for including stylesheets.
* `<style> ... </style>`
    The style tag can be used as an alternative to an external style sheet, or complement it. Includes the webpage's appearance information.
* `<script> ... </script>`
    Used to add code snippets, typically in JavaScript, to make webpage dynamic. It can also be used to just link to an external script.

### Example
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <base href="http://myfirstwebsite.com" target="_blank" />
    <title>My Website</title>
    <link rel="stylesheet" href="/css/styles.css">
    <script type="text/javascript">
        var dummy = 0;
    </script>
</head>
<body>
</body>
</html>
```

---

## Document Structure

* `<h1>`..`<h6> ... </h1>`..`</h6>`
    Six different variations of writing a heading. `<h1>` has the largest font size, while `<h6>` has the smallest.
* `<div> ... </div>`
    A webpage's content is usually divided into blocks, specified by the div tag.
* `<span> ... </span>`
    This tag injects inline elements, like an image, icon, emoticon without ruining the formatting / styling of the page.
* `<p> ... </p>`
    This element represents a paragraph.
* `<br/>`
    A line break for webpages. Is used when wanting to write a new line.
* `<hr/>`
    This element is most often displayed as a horizontal rule that is used to separate content (or define a change) in an HTML page.

### Example
```html
<div>
    <h1>Heading</h1>
    <p>First paragraph <span>icon</span> some more text</p>
    <hr/>
    <h2>Sub-heading</h2>
    <p>Another paragraph</p>
</div>
```

---

## Text Formatting

* `<strong> ... </strong>`
    Used to define text with strong importance. The content inside is typically displayed in bold.
* `<b> ... </b>`
    Make some text bold (without marking it as important).
* `<em> ... </em>`
    Used to define emphasized text. The content inside is typically displayed in italic.
* `<i> ... </i>`
    Also used to display text in italics, but does not emphasize it like the above tag.
* `<tt> ... </tt>`
    Formatting for typewriter-like text. No longer supported in HTML5.
* `<strike> ... </strike>`
    Used in HTML 4 to define strikethrough text. No longer supported in HTML5.
* `<cite> ... </cite>`
    Tag for citing author of a quote.
* `<del> ... </del>`
    Pre-formatted, 'monospace' text laid out with whitespace inside the element intact.
* `<ins> ... </ins>`
    Denotes text that has been inserted into the webpage.
* `<blockquote> ... </blockquote>`
    Quotes often go into this tag. Is used in tandem with the `<cite>` tag.
* `<q> ... </q>`
    Similar to the above tag, but for shorter quotes.
* `<abbr> ... </abbr>`
    Denotes abbreviations, along with the full forms.
* `<acronym> ... </acronym>`
    Tag for acronyms. No HTML5 support.
* `<address> ... </address>`
    Tag for specifying author's contact details.
* `<dfn> ... </dfn>`
    Tag dedicated for definitions.
* `<code> ... </code>`
    Used to display code snippets within a paragraph.
* `<sub> ... </sub>`
    Used for writing a subscript (smaller font just below the mid-point of normal font).
* `<sup> ... </sup>`
    Similar to the above tag, but for superscripting.
* `<small> ... </small>`
    Reduces text size. In HTML5, it often refers to redundant or invalid information.

---

## Links

* `<a href=""> ... </a>`
    Anchor tag. Primarily used for including hyperlinks.
* `<a href="mailto:"> ... </a>`
    Tag dedicated to sending emails.
* `<a href="tel://###-###"> ... </a>`
    Anchor tag for mentioning contact numbers. As the numbers are clickable, this can be particularly beneficial for mobile users.
* `<a name="name"> ... </a>`
    This tag can be used to quickly navigate to a different part of the webpage.
* `<a href="#name"> ... </a>`
    A variation of the above tag, this is only meant to navigate to a div section of the webpage.

### Link Attributes
* `download` - Specifies that the target will be downloaded when a user clicks on the hyperlink.
* `href` - Specifies the URL of the page the link goes to.
* `hdreflang` - Specifies the language of the linked document.
* `media` - Specifies what media/device the linked document is optimized for.
* `rel` - Specifies the relationship between the current document and the linked document.
* `target` - Specifies where to open the linked document.
* `type` - Specifies the media type of the linked document.

### Example
```html
<a href="https://www.google.com">Visit Google.com!</a>

<a href="mailto:abc@example.com">Send Email</a>
```

---

## Images

* `<img/>`
    A tag to display images in the webpage.
* `src="url"`
    The URL or path where the image is located on your drive or on the web.
* `alt="text"`
    The text written here is displayed when user hovers mouse over the image. Can be used to give additional details of the image.
* `height=""`
    Specifies image height in pixels or percentages.
* `width=""`
    Specifies image width in pixels or percentages.
* `align=""`
    The relative alignment of the image. Can change with changes to other elements in the webpage.
* `border=""`
    Specifies border thickness of the image. If not mentioned, defaults to 0.
* `<map> ... </map>`
    Denotes an interactive (clickable) image.
* `<map name=""> ... </map>`
    Name of the map associated between the image and the map.
* `<area/>`
    Specifies image map area.
* `<shape/>`
    Shape of the area.
* `<coords/>`
    Coordinates of the vital information of the shape. Example: vertices for rectangles, center/radius for circles.

### Example
```html
<img src="img_man.jpg" alt="Man walking in a park" width="500" height="600">
```

---

## Lists

* `<ol> ... </ol>`
    This tag defines an ordered list. An ordered list can be numerical or alphabetical.
* `<ul> ... </ul>`
    This tag defines an unordered (bulleted) list.
* `<li> ... </li>`
    This tag defines a list item. Is used inside ordered lists and unordered lists.
* `<dl> ... </dl>`
    This tag defines a description list. It is used in conjunction with `<dt>` (defines terms/names) and `<dd>` (describes each term/name).
* `<dt> ... </dt>`
    This tag defines a term/name in a description list.
* `<dd> ... </dd>`
    This tag is used to describe a term/name in a description list.

### Example
```html
<ol>
    <li>Coffee</li>
    <li>Tea</li>
    <li>Milk</li>
</ol>

<ul>
    <li>Bread</li>
    <li>Oranges</li>
    <li>Salad</li>
</ul>

<dl>
    <dt>Coffee</dt>
    <dd>Coffee is a drink prepared from roasted coffee beans.</dd>
    <dt>Tea</dt>
    <dd>Tea is an aromatic beverage prepared by pouring hot or boiling water over cured or fresh leaves.</dd>
</dl>
```

---

## Tables

* `<table> ... </table>`
    Marks a table in a webpage.
* `<caption> ... </caption>`
    Description of the table is placed inside this tag.
* `<thead> ... </thead>`
    Specifies information pertaining to specific columns of the table.
* `<tbody> ... </tbody>`
    The body of a table, where the data is held.
* `<tfoot> ... </tfoot>`
    Determines the footer of the table.
* `<th> ... </th>`
    The value of a heading of a table's column.
* `<tr> ... </tr>`
    Denotes a single row in a table.
* `<td> ... </td>`
    A single cell of a table. Contains the actual value/data.
* `<colgroup> ... </colgroup>`
    Used for grouping columns together.
* `<col> ... </col>`
    Denotes a column inside a table.

### Example
```html
<table>
    <colgroup>
        <col span="2">
        <col>
    </colgroup>
    <tr>
        <th>Name</th>
        <th>Education</th>
        <th>DOB</th>
    </tr>
    <tr>
        <td>Bob</td>
        <td>Computer Science</td>
        <td>12.05.1985</td>
    </tr>
    <tr>
        <td>Alice</td>
        <td>Medicine</td>
        <td>23.06.1975</td>
    </tr>
</table>
```

---

## Forms

* `<form> ... </form>`
    This tag is used to create an HTML form for user input.
* `action="url"`
    The URL listed here is where the form data will be submitted once user fills it.
* `method=""`
    It specifies which HTTP method (POST or GET) would be used to submit the form.
* `enctype=""`
    Only for POST method, this dictates the data encoding scheme to be used when form is submitted.
* `autocomplete`
    Determines if the form has auto-complete enabled.
* `novalidate`
    Determines whether the form should be validated before submission.
* `accept-charsets`
    Determines character encodings when form is submitted.
* `target`
    After submission, the form response is displayed wherever this refers to, usually has the following values: `_blank`, `_self`, `_parent`, `_top`.
* `<fieldset> ... </fieldset>`
    Identifies the group of all fields on the form.
* `<label> ... </label>`
    This is used to label a field in the form.
* `<legend> ... </legend>`
    This operates as a caption for the `<fieldset>` element.
* `<input/>`
    This tag is used to take input from the user. Input type is determined by a number of attributes.

### Example
```html
<form action="Script URL" method="GET|POST">
    form elements like input, textarea etc.
</form>
```

---

## Input Type Attributes

* `type=""`
    Determines which type of input (text, dates, password) is requested from the user.
* `name=""`
    Specifies the name of the input field.
* `value=""`
    Specifies the value contained currently in the input field.
* `size=""`
    Determines the input element width (number of characters).
* `maxlength=""`
    Specifies the most input field characters allowed.
* `required`
    Makes an input field compulsory to be filled by the user. The form cannot be submitted if a required field is left empty.
* `width=""`
    Determines the width of the input element, in pixel values.
* `height=""`
    Determines the height of the input element, in pixel values.
* `placeholder=""`
    Can be used to give hints to the user about the nature of the requested data.
* `pattern=""`
    Specifies a regular expression, which can be used to look for patterns in the user's text.
* `min=""`
    The minimum value allowed for an `<input>` element.
* `max=""`
    The maximum value allowed for an `<input>` element.
* `autofocus`
    Forces focus on the input element when webpage loads completely.
* `disabled`
    Disables the input element. User can no longer enter data.
* `<textarea> ... </textarea>`
    For longer strings of input. Can be used to get feedback, comments etc.

---

## Select & Option Attributes

* `<select> ... </select>`
    This tag specifies a list of options which the user can choose from.

### Select Attributes
* `name=""` - The name of a particular list of options.
* `size=""` - Total number of options given to the user.
* `multiple` - States whether the user can choose multiple options from the list.
* `required` - Specifies whether choosing an option/s is necessary for form submission.
* `autofocus` - Specifies that a drop-down list automatically comes into focus after a page loads.

* `<option> ... </option>`
    Tag for listing individual items in the list of options.

### Option Attributes
* `value=""` - The text visible to the user for any given option.
* `selected` - Determines which option is selected by default when the form loads.

* `<button> ... </button>`
    Tag for creating a button for form submission.

### Example
```html
<button type="submit">
    Submit form
</button>
```

---

## Objects and Iframes

* `<object> ... </object>`
    This tag is used to embed additional multimedia into a webpage. Can be audio, video, document (pdf) etc.
* `height=""` - Determines object height in pixel values.
* `width=""` - Determines object width in pixel values.
* `type=""` - The type/format of the object's contents.
* `<iframe> ... </iframe>`
    An inline block of content, this is used as a container for multimedia in a flexible manner. It floats inside a webpage, meaning it is placed relative to other webpage items.

---

## Iframe Attributes

* `name=""` - The name of the iFrame.
* `src=""` - The source URL/path of the multimedia object to be held inside the iFrame.
* `srcdoc=""` - Any HTML content to be displayed inside the iFrame.
* `height=""` - Determines the height of the iFrame.
* `width=""` - Determines the width of the iFrame.
* `<param/>` - For iFrame customization. This includes additional parameters to go along with the content.
* `<embed> ... </embed>` - This is used to embed external objects, like plugins (e.g. a flash video).

### Example
```html
<object width="1000" height="1000"></object>
<iframe src="some_other_webpage.html" width="500" height="500"></iframe>
<embed src="some_video.swf" width="500" height="500"></embed>
```

---

## Embed Attributes

* `height=""` - Determines the height of the embedded item.
* `width=""` - Determines the width of the embedded item.
* `type=""` - The type or format of the embedded content.
* `src=""` - The URL/path of the embedded item.

---

## HTML5 New Tags

* `<header> ... </header>`
    Specifies the webpage header. Could also be used for objects inside the webpage.
* `<footer> ... </footer>`
    Specifies the webpage footer. Could also be used for objects inside the webpage.
* `<main> ... </main>`
    Marks the main content of the webpage.
* `<article> ... </article>`
    Denotes an article.
* `<aside> ... </aside>`
    Denotes content displayed in a sidebar of the webpage.
* `<section> ... </section>`
    Specifies a particular section in the webpage.
* `<details> ... </details>`
    Used for additional information. User has the option to view or hide this.
* `<dialog> ... </dialog>`
    Used to build boxes or windows.
* `<summary> ... </summary>`
    Used as a heading for the above tag. Is always visible to the user.
* `<figcaption> ... </figcaption>`
    A description of the figure is placed inside these.
* `<mark> ... </mark>`
    Used to highlight a particular portion of the text.
* `<nav> ... </nav>`
    Navigation links for the user in a webpage.
* `<menuitem> ... </menuitem>`
    A particular item from a list or a menu.
* `<meter> ... </meter>`
    Measures data within a given range.
* `<progress> ... </progress>`
    Measures data within a given range.
* `<rp> ... </rp>`
    This tag is meant for showing text for browsers without ruby annotation support.
* `<rt> ... </rt>`
    Displays East Asian typography character details.
* `<ruby> ... </ruby>`
    Describes a Ruby annotation for East Asian typography.
* `<time> ... </time>`
    Tag for formatting date and time.
* `<wbr> ... </wbr>`
    A line-break within the content.

---

## HTML Character Objects

* `&#34;` or `&quot;` — Quotation Marks - "
* `&#38;` or `&amp;` — Ampersand - &
* `&#60;` or `&lt;` — Less than sign - <
* `&#64;` or `&Uuml;` — at sign - @ *(Note: image has typo/variation, standard is @)*
* `&#62;` or `&gt;` — Greater than sign - >
* `&#149;` or `&ouml;` — Small bullet - •
* `&#160;` or `&nbsp;` — Non-breaking space
* `&#153;` or `&ucirc;` — Trademark symbol - ™
* `&#169;` or `&copy;` — Copyright symbol - ©
