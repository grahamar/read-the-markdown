# Giles Internals

### How does Giles work?

#### Parsing
Giles will crawl through your repository for any markdown files he can make sense of (*.md, *.markdown) and convert it
to HTML, using the [knockoff](https://github.com/tristanjuricek/knockoff) markdown parsing library for this.

#### Storing
Giles doesn't like storing more than 1 copy of any documentation file. So he hashes the generated HTML content using a
compound hash of SHA1 & MD5. Along with the compound hash, Giles uses the size of the file to tell if he's already got
an exact match of that file and therefore will not store it again but rather reference the stored copy. Giles also
compresses the stored HTML using the GZIP compression format.

#### Indexing
Giles indexes your documentation using [lucene](http://lucene.apache.org/) so you can search over every project he
knows of, or by project, or by project version.
