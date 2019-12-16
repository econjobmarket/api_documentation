# api_documentation

The documentation is organized in a manner that makes it useable on various websites.  The following rules should be followed:

1. Each directory contains files for a particular topic.  For example, the api directory has documents associated with transferring data from [backend.econjobmarket.org](https://backend.econjobmarket.org).  To create a new topic, make a new directory.
1. Each filename within a directory should consist of three parts, a title, an index and a filetype.  The title should  be the title you want to appear in link lists.  Spaces should be replaced with the `-` character so there are no spaces left in the string.  The title should be properly capitalized (as you would like it to appear in lists.  An example for a title is `Ad-Redisplay`.
1. An index is used to place the title in order in a link list.  So the article of `Ad-Redisplay` might be second on a list, so it would have index 2.  To build the filename, the first part of the string would then be `Ad-Redisplay.2`.
Finally, all files should be markdown files, so the filetype will always be `md`. Those rules give the full title of the file as `Ad-Redisplay.2.md`

These rules are used to ensure that when the documents are displayed on a satellite website, they look appropriate.  In the example above, when the file `Ad-Redisplay.2.md` is used in a list of links, the link title will be `Ad Redisplay`, and it will be second on the list (assuming there is a file with index 1.

Finally, you can build an index file to the documents in a directory by giving it an index 0.  Titles of such pages will be separated in link lists.  An index page should be a description with a list of links to the other files available under the topic. 
