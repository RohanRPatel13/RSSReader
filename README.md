# RSSReader

## Objectives
1. Familiarity with using XMLTrees to process XML
2. Familiarity with using while loops and static methods
3. Exposure to RSS technology

## The Problem
RSS (Really Simple Syndication) is an XML application for distributing web content that changes frequently. Many news-related sites, weblogs and other online publishers syndicate their content as an RSS Feed to whoever wants it.

For this project your task is to write a program that asks the user for the URL of an RSS 2.0 feed and for the name of an output file including the .html extension, reads the RSS feed into an XMLTree object and then uses the information in the XMLTree object to generate in the output file a nicely formatted HTML page with table of links to all the news items in the original feed.

### Input: RSS 2.0 XML Document

Note the following properties of RSS 2.0 XML documents:

- The children of the channel tag and of the item tag can occur in any order; do not assume they will appear in the order above. Furthermore there can be other children of other types not listed above.
- title, link, and description are required children of the channel tag, i.e., you should assume they are present. However, title and description may be blank, i.e., they may not have any text child.
- All the children of item tag are optional, i.e., do not assume they are present; but, either title or description must be present. However, the title and/or description tags, even if present, may be blank, i.e., they may not have any text child.
- If a source tag appears as a child of an item tag, it must have a url attribute.

Note that when your program creates an XMLTree object from a given RSS 2.0 feed, if it is successful, all you know is that the input is a valid XML document. It is up to your program to check that the label of the root of the XMLTree is an rss tag and that it has a version attribute with value "2.0". After that, your program can assume that the input is indeed a valid RSS 2.0 feed and the XMLTree has the structure described above; in other words, you do not need to check for the existence of the channel tag, or the title, link, and description tags inside that. Make sure you do not make any assumptions that are not specified in the structure described above and, in particular, make sure to check that the channel's title and description tags and each item's title and description tags have a child before trying to access it. However, the item's children link and pubDate, if present, are required to have a child with the needed information.

### Output: HTML Web Page
These are the minimum requirements for the generated web page. If you think you can produce better output or include more information, you should consult your instructor to make sure that any changes you want to implement are acceptable. This is what your output should include:

- the channel title as the page title (or "Empty Title" if the title tag has no children)
- a header with the page title inside a link to the channel link
- a paragraph with the channel description (or "No description" if the description tag has no children)
- a table with appropriate headers; each row should correspond to one news item with the following columns:
  - the publication date, if present, or "No date available"
  - the source, if present, which should be linked to the source url, or "No source available"
  - the title, if present and not empty, or the description, if not empty, or "No title available", which should be linked if a link for the news item is available
