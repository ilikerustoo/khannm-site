+++
date = "2018-14-03"
title = "Gator Grouper - checking for python docstrings"
math = "true"

+++


![Checklist](/images/gatorgrader.png)

## What is GatorGrader?

GatorGrouper is a tool that most students in the Computer Science department use to check their work is up to par to make sure their work is of the highest quality. This is an incredibly useful tool as it forces you to practice good coding habits and in turn leads to you no only improving your grade, but also improving as a programmer. As can be seen above, Gator Grouper works with GitHub and Gradle (and more) and contains a checklist of requirements that must be completed in order to pass which is also checked in TravisCI. For more details check out the `GatorGrader` [GitHub](https://github.com/GatorEducator/gatorgrader)

## The Initial State

As `GatorGrader` is still under development and is maintained by students of Allegheny College, the check for multi-line `python` comments did not exist and was not a priority although useful. `GatorGrader` would only check for single line `python` and `java` comments but only multi-line `java` comments since the use of `/* */` in `Java` made any comment multi-line even if the actual contents did not contain multiple lines and this made checking easy since `Java` contains this syntax to indicate a multi-line comment whereas `python` does not. However, in `python`, a `docsring` is seen as the closest equivalent to a multi-line comment. Therefore the task was to check for a content of multiple lines between a
pair of `""" """`

## The Problem and Solution

Initially our team was provided code by another colleague who take a quick look at the issue and the code worked by parsing through the `python` AST and utilized the `python` parser. This code seemed complex and did not work if the file that is put into the function has syntax errors and will throw an exception. Instead I proposed we use a regular expression which was how comments are already checked in `GatorGrader` and doing
this would follow a similar interesting implementation.

Although I proposed the use of regular expression, I had no experience with them and decided to learn about them to solve this issue. After learning some symbols and syntax, I struggled with finding and creating an appropriate regex. In my search for using `regex`, I found [Regex101](https://regex101.com/). It breaks down any regex and explains it fully symbol by symbol. My initial regex would simply detect `docstrings` rather than a multi-line `docstring`. I after much research I came up with `r'""".*?\n.*?"""'` which did indeed detect multi-line `docstrings` and used the `re.DOTALL` flag to search for new lines. For more explain of this regex, paste it into [Regex101](https://regex101.com/).

After completing the issue, I had come up with test cases using `parametrize` to follow suit in how
the other the test cases were done and to check for multiple types of content within the `docstring` that
may or may not be correct detected. However, I struggled with coming with up with more types of inputs for
`paramtrize` and asked my teammates to try and improve the input.

Solving this issue helps professors and students keep their code and documentation up to par as well as
help to pass checks like `pylint` which require the use of `docstrings` in certain parts of the code.




<!-- # h1 Heading
## h2 Heading
### h3 Heading
#### h4 Heading
##### h5 Heading
###### h6 Heading


---

**This is bold text**

__This is bold text__

*This is italic text*

_This is italic text_

~~Deleted text~~

This is text with inline math $\sum_{n=1}^{\infty} 2^{-n} = 1$ and with math blocks:

$$
\sum_{n=1}^{\infty} 2^{-n} = 1
$$

| Heading | Another heading |
| :----:  | :-------------: |
|  text   |      text       |
|  text   |      text       |
|  text   |      text       |

> Block quotes are
> written like so.
>
> They can span multiple paragraphs,
> if you like.

Some text, and some `code` and then a nice plain [link with title](https://github.com/davidhampgonsalves/davidhampgonsalves.com-hugo "title text!").

and then

+ Create a list by starting a line with `+`, `-`, or `*`
+ Sub-lists are made by indenting 2 spaces:
  - Marker character change forces new list start:
    * Ac tristique libero volutpat at
+ Very easy!

vs.

1. Lorem ipsum dolor sit amet
2. Consectetur adipiscing elit
3. Integer molestie lorem at massa

## Code

Inline `code`

``` js
var foo = function (bar) {
  return bar++;
};

console.log(foo(5));
``` -->
