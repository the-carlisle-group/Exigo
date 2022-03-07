# Exigo: Project Documentation For Dyalog APL

Exigo produces static websites from markdown files with built-in support for user guides, object model references,
item references, and blogs.

Exigo also produces HTML documents of an entire site with print CSS, suitable for creating books
with [Prince](https://www.princexml.com/).

## Folders
An Exigo project is a collection of one or more folders containing markdown files.
Each folder is of a certain type: Object Model, User Guide, or Item Reference. 
Additional types may be added from time to time. There
may be multiple folders of the same type. Each folder contains markdown files in its
root; there are no subfolders and thus only one level of heirarchy. 
The folder type determins how Exigo processes its markdown files, and the structure of the final site.
For example, the build process for an object model folder adds method and property links to each class topic.

1. **Object Model**:  This folder type contains markdown files for an object model - a markdown file for each object, method, and property.
 File names are of the following form: [Object]\_Class.md, [Object]\_Method\_[MethodName].md, [Object]\_Property\_[PropertyName].md   

2. **Item Reference:** This folder type contains a non-hierarchical collection of items, like a set of functions, or commands.
 Normally displayed alphabetically, items may be typed into mutually exclusive groups, and/or categorized into overlapping groups.
 The type and categories of an item are specfied inside its markdown file. 

3. **User Guide:** This folder type contains a hierarchical grouped and ordered collection of markdown files, like the chapters
 section of a book. The order and the heirarchy is specified by simple, plain text file inside the folder. 



## Links
In the markdown, the URL of internal links my be omitted:  

~~~
   The [ReadCSVFile]() method imports a CSV file.
~~~

or may be specified using only the tail end segement of the path:

~~~
   It is very easy to [read CSV files](ReadCSVFile)
~~~

If the tail end segment of the path is not unique within the site, the closest relative to the linking page is used.
This behavior may be overridden by specifing more of the path as neccessary:

~~~
   The [Delete](/Database/Methods/Delete) method of the Database object imports a CSV file.
~~~

## Building
~~~
#.Exigo.Admin.Build ''
~~~

We could have a view here too. Trivial really...

Assume source folder is /APLSource/DocSource

This builds the site and puts in in temp foider. The site can be checked out locally

## Publishing
To publish to Github Pages: 

~~~
#.Exigo.PublishGitHubPages ''
~~~

This builds the site and copies the html files to the root of the gh-pages branch, commits and pushes,
leaving you back on the branch where you were.
If there is no gh-pages branch, one is created as an orphan branch, with only the final html files, and no source markdown files.
