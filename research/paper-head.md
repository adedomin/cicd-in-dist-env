---
# Research into CICD principles and proposal of 
# alternatives based on methods used in the FOSS community.
# The build requires the following dependencies:
#    TeXLive
#    pandoc 
#    pandoc-citeproc

title: CICD - Working Title
#author: Anthony DeDominic
abstract: |
	*To be written.*
	*to see latest revision, please see:*
	
	*<https://github.com/adedomin/cicd-in-dist-env.git>*

papersize: letter
geometry: margin=2cm
fontfamily: mathpazo
fontsize: 10pt
header-includes:
- \hyphenpenalty 10000
- \usepackage{fancyhdr}
- \pagestyle{fancy}
- \fancyfoot[L]{CICD - DeDominic}
- \fancyfoot[C]{}
- \fancyfoot[R]{\thepage}
- \twocolumn
- \author{DeDominic, Anthony\\Eastern Connecticut State University\\Willimantic, USA\\dedominica@my.easternct.edu}

link-citations: Yes
# example citation
references:
- title: One-click science marketing
  volume: '11'
  URL: http://dx.doi.org/10.1038/nmat3283
  DOI: 10.1038/nmat3283
  issue: '4'
  container-title: Nature Materials
  publisher: Nature Publishing Group
  author:
  - family: Fenner
    given: Martin
    orcid: 0000-0003-1419-2405
  page: 261-263
  id: example
  type: article-journal
  issued:
    year: 2012
---

