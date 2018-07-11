# New page added



## Comparison of page/wiki ideas.

Last updated 18 hours ago[ Edit on GitHub](https://github.com/cms-sw/cmssdt-wiki/blob/master/_snippets/untitled.md)

Research of available simple documentation solutions.

## Problem {#problem}

Currently the information is scattered around many places \( [twiki](https://twiki.cern.ch/twiki/bin/viewauth/CMS/SoftwareDevelopementToolsSubTask), [cms-sw.github.io](http://cms-sw.github.io/faq.html), various readme's in github repos\). Essential it is simpler just to ask someone how to do it then to look in docs.

We would like to solve it by simple to update, central and searchable website/ wiki's. We would also like it to be:

* Github focused for easy **hosting, controlled collaboration** and **developer focused**.
* Searchable.
* Easy to maintain.

## Solutions {#solutions}

### Gitbook legacy {#gitbook-legacy}

| **Pros** | **Cons** |
| --- | --- |
| Completely open sourceCan be self hosted and already used by CERN \( [configdocs.web.cern.ch](https://configdocs.web.cern.ch/configdocs/gbook/index.html) \) | No more free hosting at [legacy.gitbook.com](https://legacy.gitbook.com/) \(they are forcing to use new version\).Weak search. |

​

### New Gitbook \(this page\) {#new-gitbook-this-page}

| **Pros** | **Cons** |
| --- | --- |
| Nice interface for easy editing \(this page was edited online\) .Hosted for free \(with some limitations\).Included search.Sync with gitbook. | Only top 5 search results are shown.No possibility to self host.Looks bad on IE9 \( why we are still using it, again?\).Not stable \( got github sync error\) |

### Jekyll with a theme \([example page](https://cms-sw.github.io/cmssdt-wiki/)\) {#jekyll-with-a-theme-example-page}

| **Pros** | **Cons** |
| --- | --- |
| Static page hosted in Github.Ability to create dynamic content \(tables with results\) | Weak search unless configured [www.algolia.com](https://cmssdt.gitbook.io/wiki/_snippets/www.algolia.com) as search back-end \(need to ask for free license\)No possibility to self host.Takes time to configure.Text only. |

### Read the docs reStructuredText edition \([example page](https://mkdocs.readthedocs.io/en/stable/search.html?q=custom_theme)\) {#read-the-docs-restructuredtext-edition-example-page}

Readthedocs.com is preferred way to document a lot of opensource project. Underneath the hood it used [Sphinx](http://sphinx-doc.org/) to generate site. It is used to generate Python documentation.

| **Pros** | **Cons** |
| --- | --- |
| Most mature.Completely open source.Free page hosting.Integration with Github.Really nice search for free \( each matching word or phrase is colored\). | Text only.Will need conversion from .md to .rst files..rst has more powerful, but more complicated syntax to learn. |

### Read the docs markdown edition \([example page](https://cmssdt-wiki.readthedocs.io/en/read-the-docs/)\) {#read-the-docs-markdown-edition-example-page}

It is the same service, however, a different [backend](https://www.mkdocs.org/) is used to process .md files instead .rst. Same pros/cons except :

* We can write in markdown \( still need some restructuring though\);
* Search has no color marking \(still good though\).

