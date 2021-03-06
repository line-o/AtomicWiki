AtomicWiki
==========

AtomicWiki is a wiki engine, tightly integrated with the eXist-db native XML database (http://exist-db.org).

Features
--------

* **Hierarchical collections**: articles are organized into collections. Each collection may contain one or more articles and an arbitrary number of sub-collections.
* **Blog support**: a collection can be displayed as a weblog feed.
* **Rich wiki markup** with syntax highlighting: our wiki editor allows for fast authoring with a number of useful extensions, e.g. to display a block of source code. The wiki editor supports on-the-fly syntax highlighting of the wiki markup.
* **XML storage**: article metadata is saved using the Atom Syndication Format, which allows for easy exchange with other systems or news readers. The article content is stored separately as an HTML file, so authors can choose to directly edit the HTML using editing tools outside the wiki (e.g. oXygen).
* **XQuery scripting**: embed XQuery code directly into a document and have it executed. Directly query data stored in the database from within an article. Furthermore, all wiki macros are written in XQuery and you can add your own any time.
* **eXist-db Integration**: AtomicWiki ships as a self-contained package which can be deployed into any eXist-db using eXist's application repository. It runs alongside other apps within the same db and ignores any documents which are not part of the wiki.

Current State
-------------
This version of AtomicWiki is a complete rewrite of the older code base. It is usable, but not yet feature-complete. The following features are planned to be implemented next:

+ **Access control**: Right now users can view/edit any resource if they have access rights on the database resource. The editing forms do not provide any means to restrict access. We plan to implement a dedicated security model for the wiki based on ACLs. 
+ **User management**: While users can be added/edited using eXist-db standard tools, there are no forms for this within the wiki.
+ **Commenting**: commenting and annotations will be a major feature of AtomicWiki. We plan to go beyond simple comments attached to an article, allowing users to annotate virtually everything: an article, a piece of text within a page, a relation between two resources, ... 
+ **Resource upload**: Likewise, images or other resources can be uploaded using eXist-db tooling, but not from within the wiki.
+ **Editor improvements**: auto-complete for links, more keyboard shortcuts ...
+ **HTML WYSWIG editor**: since all content is stored as XML/HTML, we could also support editing content with a WYSWIG editor instead of wiki markup. The goal is to allow any type of editor to be plugged in.

Download
--------

You can [https://github.com/exist-db/AtomicWiki/downloads](download) a zip containing a ready-to-install application 
package plus additional libraries required by eXist. Unzip the downloaded archive and proceed with installing jars.


## Compilation

* Requirements: Java 8, Apache Maven 3.3+, Git.

If you want to create an EXPath Package for the app, you can run:

```bash
$ mvn package
```

There will be a `.xar` file in the `target/` sub-folder.


Uploading the package
---------------------
The .xar file is an installable package containing the code and initial data for AtomicWiki. You can install this into any eXist 
instance using the application repository manager. In a web browser, open the 
admin web page of your eXist instance and select "Package Repository". Switch to the "Upload" tab and select the .xar
file for upload, then click "Upload Package". After installation has finished, your new version of AtomicWiki (now stored
inside the database) should be accessible at:

     http://localhost:8080/exist/apps/wiki/

