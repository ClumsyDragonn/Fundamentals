# Markdown Text Styling Guide

## Basic Text Styling

| Style | Syntax | Example |
|-------|--------|---------|
| Bold | `**text**` or `__text__` | **bold text** |
| Italic | `*text*` or `_text_` | *italic text* |
| Bold + Italic | `***text***` or `___text___` | ***bold italic*** |
| Strikethrough | `~~text~~` | ~~strikethrough~~ |
| Inline Code | `` `code` `` | `code` |

## Headings

```markdown
# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6
```

## Line Breaks

### Soft Line Break (within same paragraph):
Use two or more spaces at the end of a line:
```markdown
This is line 1  
This is line 2
```

### Hard Line Break (new paragraph):
Use a blank line between paragraphs:
```markdown
This is paragraph 1

This is paragraph 2
```

### HTML Line Break:
```markdown
This is line 1<br>
This is line 2
```

## Lists

### Unordered List:
```markdown
- Item 1
- Item 2
  - Nested item
```

### Ordered List:
```markdown
1. First item
2. Second item
3. Third item
```

## Links & Images

### Links:
```markdown
[Link text](https://example.com)
```

### Images:
```markdown
![Alt text](image.jpg)
```

## Code Blocks

### Single Line:
```markdown
`code here`
```

### Multiple Lines:

```javascript
function hello() {
  console.log("Hello World");
}
```


## Blockquotes

```markdown
> This is a quote
> It can span multiple lines
```

## Horizontal Lines

```markdown
---
***
___
```

## Escaping Special Characters

Use backslash `\` before special characters:
```markdown
\*
\#
\[
\]
```

## Combining Styles

```markdown
**Bold with *italic* inside**
***All bold and italic***
`**code with bold syntax**` (displays as code, not styled)
```

## IDE Style Code Formatting

IDE-style formatting displays code with syntax highlighting and proper formatting, just like in code editors (VS Code, IntelliJ, etc.).

### How to Write IDE Style Text:

Use triple backticks (`) followed by the language name:

```markdown
```language
code here
```
```

### Common Language Specifiers:

```markdown
```javascript
const greeting = "Hello, World!";
console.log(greeting);
```
```

```markdown
```python
def greet():
    print("Hello, World!")
greet()
```
```

```markdown
```html
<!DOCTYPE html>
<html>
  <body>
    <h1>Hello World</h1>
  </body>
</html>
```
```

```markdown
```css
body {
  background-color: #f0f0f0;
  font-family: Arial, sans-serif;
}
```
```

```markdown
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```
```

### Popular Language Codes:

| Language | Code |
|----------|------|
| JavaScript | `javascript` or `js` |
| Python | `python` or `py` |
| HTML | `html` |
| CSS | `css` |
| Java | `java` |
| C++ | `cpp` |
| SQL | `sql` |
| JSON | `json` |
| XML | `xml` |
| Bash/Shell | `bash` or `shell` |
| Markdown | `markdown` or `md` |
| Plain Text | `text` or leave blank |

### Example with Line Numbers (Using Markdown):

```markdown
```javascript
// Line 1
function add(a, b) {
  return a + b;
}
// Line 5
```
```

## Adjusting Font Size

### Method 1: Using HTML (Most Reliable)

```markdown
<span style="font-size:14px;">Small text</span>
<span style="font-size:20px;">Medium text</span>
<span style="font-size:28px;">Large text</span>
```

### Method 2: Using HTML Font Tag

```markdown
<font size="1">Size 1</font>
<font size="3">Size 3</font>
<font size="5">Size 5</font>
<font size="7">Size 7 (Largest)</font>
```
<font size="1">Size 1</font><br>
<font size="3">Size 3</font><br>
<font size="5">Size 5</font><br>
<font size="7">Size 7 (Largest)</font>

---
### Method 3: Using Headings (Predefined Sizes)

```markdown
# Heading 1 (Largest)
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6 (Smallest)
```
# Heading 1 (Largest)
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6 (Smallest)

---
### Method 4: Big and Small Tags

```markdown
<big>Bigger text</big>
<small>Smaller text</small>
```

<big>Bigger text</big><br>
<small>Smaller text</small>

---
### Method 5: Superscript & Subscript

```markdown
Normal text with <sup>superscript</sup>
Normal text with <sub>subscript</sub>
```

Normal text with <sup>superscript</sup><br>
Normal text with <sub>subscript</sub>

**Note:** HTML methods work in most Markdown renderers (GitHub, VS Code preview, etc.). The specific rendering may vary depending on your platform.
