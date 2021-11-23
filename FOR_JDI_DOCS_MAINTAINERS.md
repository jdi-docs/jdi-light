## What Is This Document?

This document is a byproduct of a major JDI Light documentation edit. The editor was mainly concerned with making it read more naturally for the international audience, but ultimately couldn't ignore the matter of making the style more uniform.

Here are some useful tips that should help to preserve this uniformity.

### Italic

_Italic_ text, marked by underscores, is generally used for:

- referring to a folder/directory ("...most documentation files are found in _source/includes/documentation_").
- making a note (_Note: don't use `<aside class="notice">` tags for notes, they don't go well with Markdown_).
- referring to a technical term, product name, etc. which is worth a visual accent ("_The Illuminati_ made me mention _Log4j_ in this example").
- just highlighting parts of a clause/text (though it probably must be used _sparingly_ in this case).

### Bold

**Bold** text, marked by double asterisks, is generally used for: 

- **list/table item highlighting** — if a list or a table includes items like method or option names that could use more visual accents, it might be nice to write them in bold and put their descriptions after an em dash (like I did here).
- highlighting **Very Important** parts of a clause/text (when you first meet **JDI UI Objects**, they'll likely need to inspire awe).

### Bold Italic

***Bold italic*** text, marked by triple asterisks, is generally used for: 

- marking file names (it might seem kind of counterintuitive, but the introductory sections of JDI Light docs are found in the ***index.html.md*** file).

### Inline Code

`Inline code`, marked by backticks, is generally used for:

- highlighting text fragments that represent parts of code: the background color change makes values like `smart.locators=//*[text()='%s']` more digestible. Inline code makes class names (`UIElement`), method names (`click()`, `sendKeys` etc.), or language keywords like `null` stand out even in a text loaded with other words words words and punctuation. Just don't mark them with triple backticks, single are enough.

### Bulleted Lists

At this point you'll likely get how to use bulleted lists, but there is a problem worth mentioning:

- Line breaks between list items might not behave as you expect, so you'll have to put `<br/>` after each item for them to render properly. <br/>
- Seriously, items can lose the bullets and try to hump each other, and that's the only hack that worked for me. Feel free to investigate the matter.

### Aligning Code Examples With Text

Code put into the code panel to the right of the main text body sometimes does not align with the text properly (you'd want parts of the text to be lower or higher than they are). The hack that was already in place used multiple `<br/>` tags to manipulate text position; I also went with that. Feel free to investigate the matter.

### TBD 

Document sections that are still under construction will contain unpleasant olive <font color="olive">TBD</font> text (put inside a `<font color="olive"></font>`). Remove the tags when you put an actual text there.
