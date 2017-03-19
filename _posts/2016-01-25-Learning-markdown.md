---
layout: post
title:  "Learning markdown"
date:   2016-01-25 12:15:12 -0500
categories: markup-language
---
## markdorwn

markdown is a lightweight markup language, it was designed so that it can be converted to HTML and many other formats.

You can see the [markdown documentation][md-doc] to learn how to write.

------

### Headers

      # H1
      ## H2
      ### H3
      #### H4
      ##### H5
      ###### H6

      Alternatively, for H1 and H2, an underline-ish style:

      Alt-H1
      ======

      Alt-H2
      ------


# H1
## H2
### H3
#### H4
##### H5
###### H6

Alternatively, for H1 and H2, an underline-ish style:

Alt-H1
======

Alt-H2
------

------

### Text

    You can modify text and play with italic with *asterisk* or _underscores_.

    you can modify text and play with bold **asterisk** or __underscores__.

    you can play with both of them writing with **asterisks and _underscores_**.

    You can strikethrough words using two tildes. ~~Scratch this.~~

You can modify text and play with italic with *asterisk* or _underscores_.

you can modify text and play with bold **asterisk** or __underscores__.

you can play with both of them writing with **asterisks and _underscores_**.

You can strikethrough words using two tildes. ~~Scratch this.~~

------

### Programing language

You can use syntax highlighting for any programing language, for example:

{% highlight text %}
  ```javascript
  function fancyAlert(arg) {
    if(arg) {
      $.facebox({div:'#foo'})
    }
  }
  ```
{% endhighlight %}

You will have this:
 
  {% highlight javascript %}
  function fancyAlert(arg) {
    if(arg) {
      $.facebox({div:'#foo'})
    }
  }
  {% endhighlight %}

------

### List

    1. First element
    2. Second element
      * Unordered sub-list first element. 
      * Unordered sub-list second element.
    1. Actual numbers don't matter, just that it's a number
        1. Ordered sub-list first element.
        1. Ordered sub-list second element.
    4. And another item.

    You can write a paragraph indent at the same level of your unordered-ordered list.

    You can write a separate line writing 2 spaces at the end of a line  
    like this.

    * Unordered list can use asterisks
    - Or minuses
    + Or pluses

1. First element
2. Second element
  * Unordered sub-list first element. 
  * Unordered sub-list second element.
1. Actual numbers don't matter, just that it's a number
    1. Ordered sub-list first element.
    1. Ordered sub-list second element.
4. And another item.

You can write a paragraph indent at the same level of your unordered-ordered list.

You can write a separate line writing 2 spaces at the end of a line  
like this.

* Unordered list can use asterisks
- Or minuses
+ Or pluses

------

### Links

    You can write links using this: [Press me, i am a link][press-link].

    You can paste an image using this: ![i am an image][image-no-link-url]

    You can paste an image with a referenced link using this: [![i am an image with link][image-url]][image-link]

You can write links using this: [Press me, i am a link][press-link].

You can paste an image using this: ![i am an image][image-no-link-url]

You can paste an image with a referenced link using this: [![i am an image with link][image-url]][image-link]

------

### Referenced links

    [press-link]: https://www.google.com
    [image-no-link-url]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Image without link"
    [image-url]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Image with link"
    [image-link]: http://daringfireball.net/projects/markdown/

------

### Tables

You can create tables.

    | *Lanuages*      | `framework`     | **side**   |
    | ------------- | ------------- | ------:|
    | ruby          | Ruby on Rails | server |
    | javascript    | Angularjs     | client |
    | php           | Laravel       | server |
    | python        | Django        | server |

The result is this:

![tables](/assets/files/tables.png)

------

### Blockquotes

    > Blockquotes are very helpful.
    > This line is part of the same quote.

    New line

    > Another **line**.

> Blockquotes are very helpful.
> This line is part of the same quote.

New line

> Another **line**.

------

### Conclusion

In this page, I can't show all the benefits of markdown because jekyll doesn't support some syntaxes like tables (i had to use an image to show the result) or headers.  
Check the doc for more information.  

# Thanks for read !

------

[md-doc]: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
[press-link]: https://www.google.com
[image-no-link-url]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Image without link"
[image-url]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Image with link"
[image-link]: http://daringfireball.net/projects/markdown/


