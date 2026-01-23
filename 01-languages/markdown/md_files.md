# Basic Concepts

### Keep in mind

Whenever you want to go to a new line use double line break or preess enters two time to enter in a new line in the preview

## All types of heading
```markdown
# Heading1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6
```
Can add any styles, as markdown is just like html files so we can add styles too.

### For making characters bold
```markdown
text is **bold**
```
### For making characters italics
```markdown
Text is *italic*
```

### For both bold and italics
```markdown
text is ***bold_italic***
```

### Highlighting

usually these files will be uploaded in github, so in the github markdown the highlight and other features doesnt get rendered.

but we can do using html properties

```markdown
<mark>highlight</mark>
```
><mark>highlight</mark>

## Superscript and subscript doesnt work

but can make it work using html

```markdown
X<sup>2</sup>

H<sub>2</sub>0
```

 >H<sub>2</sub>0

>X<sup>2</sup>

## Creating emojis doesnt work

So we can copy the emoji and paste it in the markdown

Now if we want to show the code use backticks
 for whole or multiple lines use triple backticks ```

### Important note to keep in mind

If you want your syntax or the code you show to have proper indentation and highlighting so add the language you are using after the triple backticks.

other method is using the the word block and shifting it further away and it gets automatically rendered.

## To create links
```markdown
[Link]()
```
Inside the square parenthesis we put whatever we want inside.

In the parenthesis we put the site address in it.

```markdown
[Google](https://www.google.com)
```
>[Google](https://www.google.com/).

Or we can just paste the link in the file and it gets automatically rendered.

>https://www.google.com/

## Images

```markdown
![Google Logo](The link or location of the pic of google)
```

## To quote

```markdown
Use of angular brackets
> Hi
>> Hello
>>> How are you
```
>HI
>>hello
>>>How are you

## Horizontal line to rule out paragraphs

```markdown
This is a paragraph 

---

This is also a paragraph
```

Atleast 3 character must be there

>This is a paragraph
>
>---
>
>This is also a paragraph

## Draw Lists(points or bullet points)

```markdown
Ordered
1. Item 1
2. Item 2
3. Item 3

      
      or 

Unordered

* Item 1
* Item 2
* Item 3
```

Press TAB to nest lists.

## Github exclusive features.

```markdown

| Col1 | Col2   |
| ---- | ----   |
| This | is    |
|  an  | example | 
| table|   right? |
```
<mark>Notice how the bar alignment is different, but it does'nt matter of the alignment because it will render normally.</mark>


| Col1 | Col2   |
| ---- | ----   |
| This | is    |
|  an  | example | 
| table|   right? |

Now if you want to shift the contents of the table to left and right add semi column after the --- horizontal divider.

If the colon is right side, the contents get shifted to right and vice versa.

## Finally Checklists

```markdown
- [ ] Your checkbox

- [x] Unchecked checkbox
```
- [ ] Checked box

- [x] Unchecked box


----