hBook 0.1.0

hBook is a simple book markup format, loosely based off of the DocBook format, providing properties and values for semantic HTML or XHTML. hBook is an early attempt at a simple and open microformat standard suitable for embedding book markup in HTML, XHTML, Atom, RSS, and arbitrary XML.

Author
D.a. Thompson (http://dathompson.blogspot.com)

Acknowledgments

Copyright and patents statements apply.

Elements:
dedication, set, book, part, partintro, colophon, appendix, article, chapter, preface, section

Example
Here is a simple book marked up with hBook:

<div class="preface">
  This is the preface.
</div>

<div class="part" id="pt-1-name">
	This is part one.
  <div class="chapter" id="ch-2-name">
    This is the first chapter.
    <div class="section" id="sec-1-name">
      This is the first section.
      <div class="section" id="sub-sec-name">
        This is the first sub-section.
      </div>
    </div>
  </div>
</div>

Errata and Updates
Known errors and issues in this specification are corrected in resolved and closed issues. Please check there before reporting issues.

Introduction
The iCalendar standard (RFC2445), has been broadly interoperably implemented (e.g. Apple's "iCal" application built into MacOSX).

In addition, bloggers often discuss events on their blogs -- upcoming events, writeups of past events, etc. With just a tad bit of structure, bloggers can discuss events in their blog(s) in such a way that spiders and other aggregators can retrieve such events, automatically convert them to iCalendar, and use them in any iCalendar application or service.

This specification introduces the hCalendar format, which is a 1:1 representation of the aforementioned iCalendar standard, in semantic HTML. Bloggers can both embed hCalendar events directly in their web pages, and style them with CSS to make them appear as desired. In addition, hCalendar enables applications to retrieve information about such events directly from web pages without having to reference a separate file.

The key words "must", "must not", "required", "shall", "shall not", "should", "should not", "recommended", "may", and "optional" in this document are to be interpreted as described in RFC 2119.

XHTML is built on XML, and thus XHTML based formats can be used not only for convenient display presentation, but also for general purpose data exchange. In many ways, XHTML based formats exemplify the best of both HTML and XML worlds. However, when building XHTML based formats, it helps to have a guiding set of principles.

Use the most accurately precise semantic XHTML building block for each object etc.

Otherwise use a generic structural element (e.g. <span> or <div>), or the appropriate contextual element (e.g. an <li> inside a <ul> or <ol>).

Use class names based on names from the original schema, unless the semantic XHTML building block precisely represents that part of the original schema. If names in the source schema are case-insensitive, then use an all lowercase equivalent. Components names implicit in prose (rather than explicit in the defined schema) should also use lowercase equivalents for ease of use. Spaces in component names become dash '-' characters.

Finally, if the format of the data according to the original schema is too long and/or not human-friendly, use <abbr> instead of a generic structural element, and place the literal data into the 'title' attribute (where abbr expansions go), and the more brief and human readable equivalent into the element itself. Further informative explanation of this use of <abbr>: Human vs. ISO8601 dates problem solved
	
For practical implementations, it should be noted that Internet Explorer's support for styling <abbr> elements is poor, and may require wrapper elements.

Root Class Name
The root class name for hBook is "book". An element with a class name of "book" is itself called an hBook.

The root class name for articles is "article". An element with a class name of "article" is itself called an hBook article.

For authoring convenience, both "book" and "article" are treated as root class names for parsing purposes. If a document contains elements with class name "article" but not "book", the entire document has an implied "book" context.

article should be considered required for each article listing.

Properties and Sub-properties
The properties of an hBook are represented by elements inside the hBook. Elements with class names of the listed properties represent the values of those properties. Some properties have sub-properties, and those are represented by elements inside the elements for properties.

Property List
hBook properties

bookinfo
	copyright
		year
		holder
	isbn
	issn
	pages
	pubdate
	description
	publisher
		name
		address
	version
	release-date
	title
	subtitle
	lccn
	authorgroup
		author
			firstname
			lastname
		contributor
			type
			firstname
			lastname
	keywords

part
	chapter
		section

frontcover
halftitlepage: contains the title of the book
titlepage: contains the title of the book, name of author(s) and publisher
imprint: left page with copyright, publisher, library printing information
dedication: right page with short dedication
foreword: written by someone other than the author(s)
toc: table of contents
preface: preface, including acknowledgements
chapter: each chapter is given its own DIV element
references: contains list of references
appendix: each appendix is given its own 
bibliography
glossary
index
colophon: describes how the book was produced
backcover
footnote