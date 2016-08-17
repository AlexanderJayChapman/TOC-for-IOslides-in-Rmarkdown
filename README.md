# TOC for IOslides in Rmarkdown

IOslides using Rmarkdown does not have the ability to add a table of content page in the YAML header. This document provides a workaround to automaticly add a TOC. By specifying section and subsection classes in the Rmd file the javascript file searches for the id's in the section classes and generates the table of content based on the name of the id's.

## Add TOC HTML

To add the table of content to the slides first create a new slide in Rmarkdown.

``` ## Table of content ```

Next add the following HTML to this page.

```{"HTML"}
<!-- Link to table of content javascript -->
<script src="TOC_generator.js"></script>

<!-- Link to table of content style -->
<link rel="stylesheet" type="text/css" href="toc-style.css">

<!-- add div element table of content for javascript to fill -->
<div id="toc"></div>
```

## Javascript

Now that the link to the javascript file has been added to the Rmarkdown slide we need to also add the file itself, by adding it to the working directory of your ``` .rmd ``` file.

You can download ``` TOC_generator.js ``` from the [TOC-for-IOslides-in-Rmarkdown](https://github.com/ShKlinkenberg/TOC-for-IOslides-in-Rmarkdown) GitHub page.

## CSS

Some basic styles have been added in the ``` TOC-style.css ``` file. Again available through the [TOC-for-IOslides-in-Rmarkdown](https://github.com/ShKlinkenberg/TOC-for-IOslides-in-Rmarkdown) GitHub page.

```{"CSS"}
li.section { color: black; }

li.subsection {font-size: .95em; 
               list-style-type:circle;
}
```

This file also needs to be added to the working directory.

## Add sections

To add a section that you want displayed in the table of content all you have te do is add a ``` .section ``` or ``` .subsection ``` class to the header of the slide.

This can be done by adding ``` {.section} ``` or ``` {.subsection} ``` after the heading.

```{"markdown"}
# Your heading one name {.section}

## Your heading two name {.subsection}
```

# Limitations

## Lowercase

The table of content can only be displayed in lowercase. This is due to the javascipt using the ellement id for retrieving the title text of the section. This variable only contains lowercase letters.

## No links

It would be nice if the table of content also had links to the referenced slides. Unfortunately linking to id text does not seem to work.

Linking to page id numbers does work. But the slide number is not available through the used method: 

```{"javascirt"}
document.querySelectorAll('.section, .subsection')
```

## Two levels

Only two levels are available to use in the table of content. This seems to be caused by the Rmarkdown header 3 not allowing to define a class.

```{"markdown"}
### Your heading three name {.subsubsection}
```

The above code does not seem to result in an HTML element containing the ``` .subsubsection ``` class.
