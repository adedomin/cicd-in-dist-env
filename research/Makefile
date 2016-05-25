DOC=pandoc
DOCFLAGS=--filter pandoc-citeproc --csl=./style/ieee.csl
DOCNAME=cicd-dedominica
DOCTYPE=.pdf
DOCOBJ=./content/*.md
DOCHEAD=paper-head.md
DOCTAIL=paper-tail.md

all: doc
	
doc:
	$(DOC) $(DOCHEAD) $(DOCOBJ) $(DOCTAIL) -o $(DOCNAME)$(DOCTYPE) $(DOCFLAGS)

# you can do make DOCTYPE=.type instead
pdf:
	$(DOC) $(DOCHEAD) $(DOCOBJ) $(DOCTAIL) -o $(DOCNAME).pdf $(DOCFLAGS)

# for professor
docx:
	$(DOC) $(DOCHEAD) $(DOCOBJ) $(DOCTAIL) -o $(DOCNAME).docx $(DOCFLAGS)

clean:
	rm $(DOCNAME).*
