# Table of contents

<!-- TOC -->
* [Table of contents](#table-of-contents)
* [Manifesto](#manifesto)
  * [Consistency](#consistency)
  * [Language](#language)
<!-- TOC -->

# Manifesto

These code-styles is mainly derives from:

- [PEP 8](https://peps.python.org/pep-0008/)
- [PEP 257](https://peps.python.org/pep-0257/)
- [PEP 20](https://peps.python.org/pep-0020/)
- [Barry’s GNU Mailman style guide](https://barry.warsaw.us/software/STYLEGUIDE.txt)

If you have never heard of these or never actually read them - it is recommended to stop and go check it all out.
All the Python these Guidelines are based on these conventions and are designed mainly to illustrate:

- Why some of the Guidelines from documents above are used
- Which Guidelines from documents above are not used or interpreted differently
- What else is considered to be Guidelines

> While living in Russia, you may find the idea of 'ignoring any rules' or pretending to follow them the essential 
> part of daily life. In many cases this is the right thing to do. But if you do so, keep in mind that this is not 
> the case. Programming is build around conventions, which are the backbone for every successful team and product. 
> Each time you see a title
> 
>>                                        All secrets of Google's StyleGuide!
>
> or
> 
>>                                  How Django's developers organize their workflow
> 
> it's not about Google's StyleGuide being better and there is no secret in how Django's developer made this - it only
> about these teams sticking to their conventions and making it consistent. These teams developed a way, convenient 
> for the developers in that particular environment, but the fact that they keep holding on these standards made their
> products viable.

## Consistency

> As PEP 8 goes:
> > One of Guido’s key insights is that code is read much more often than it is written. The guidelines provided here 
> > are intended to improve the readability of code and make it consistent across the wide spectrum of Python code. 
> > As PEP 20 says, “Readability counts”. 
> >
> > A style guide is about consistency. Consistency with this style guide is important. Consistency within a project 
> > is more important. Consistency within one module or function is the most important.

Consistency is the most important part of writing and maintaining you code, and any others code. There should be no 
excuse to break these guidelines, unless there is a clear and explicit reason to do so. There is no 'more' or 'less'
important rules, conventions and guidelines in this Style Guide:

```python
comments_guidelines_importance  = 'Comments Style Guides' + ' are very important'
indents_guidelines_importance   = 'Indents Style Guides' + ' are very important'
classes_guidelines_importance   = 'Classes Style Guides' + ' are very important'

print(comments_guidelines_importance == indents_guidelines_importance == classes_guidelines_importance)  # > True
```

## Language

English is the language for any documentation, comments and object-names.

> Why should I write in English, when I am in Russia/Norway/India/Pakistan?

- English is a standard for programmers world-wide
- Almost any other documentation is in English, for some there is no translations/it is not full/it is outdated
- Object-names in Python are in English. If you can not understand them, documentation won't help either
- PEPs are in English. You need to read them, before reading these docs. There could be no updated translation for PEPs
- Writing and reading in English is a good practice to learn English
- No need to switch between languages makes work-flow more convenient

Any text, intended to be read by Users, should be made on a comfortable for Users language, depending on a specific
situation. By 'Users' I mean not a Developer, but the actual Users of your product, so all the documentation or 
interface elements for Users should be made on the language, that these Users prefer.