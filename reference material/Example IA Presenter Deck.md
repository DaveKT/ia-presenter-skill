# Example Deck Title
## Example Subtitle

---
### First Content Page (Heading 3)
	This is some example content. Notice that the content will show on the slide because I started this line with a tab.

This is some speaker text that will not show on the slide because it does not begin with a tab character. Note, headings always show and don't need a tab character.

---
### Second Content Page (Heading 3)

	This slide is going to demonstrate how to create an unordered list.

	- List Item One
	- List Item Two
	- List Item Three

A couple of notes about the content. First, the header will be at the top of the page. Second, the sentence will be in a left panel and the list will be in a right panel because there is a line without a tab separating the two sections. If the line without a tab were not there, the two sections would render one under the other.

1. Ordered List Item One
2. Ordered List Item Two
3. Ordered List Item Three

The list item above is an example of an ordered list. The list will not render on a slide because there is no tab in front of each line. If there were a tab, then this ordered list would render on the slide.

---
### Third Content Page (Header 3)

The page demonstrates how to add a link to the text and insert an image.

	To add a link to the text follow simple markdown rules.  [This is an example.](www.kagi.com) 

/assets/1_4runner-1500x.png
size: contain

The above line is rendering an image called 1_4runner-15000x.png on the slide. The contain modifier is ensuring the full image is rendered in the space provided.

---
### Fourth and Final Content Page (Header 3)
	As the documentation suggests, you can use standard markdown to format the text. This is **bold** and this is *italic*.

You can also insert a code block using backticks. You can optionally name the language being used after the first set of backticks.

```python
Import pandas as pd

print("Hello World!")
```
