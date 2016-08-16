# TOC for IOslides in Rstudio

IOslides using Rmarkdown does not have the ability to add a table of content page in the YAML header. This document provides a workaround to automaticly add a TOC. By specifying section and subsection classes in the Rmd file the javascript file searches for the id's in the section classes and generates the table of content based on the name of the id's.
