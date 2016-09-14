DOC=pandoc
DOCFLAGS=--filter pandoc-citeproc --csl=./style/ieee.csl --self-contained
DOCNAME=cicd-dedominica
DOCTYPE=pdf
DOCOBJ=./content/*.md
DOCHEAD=paper-head.md
DOCTAIL=paper-tail.md

all: doc
	
doc:
	$(DOC) $(DOCHEAD) $(DOCOBJ) $(DOCTAIL) -o $(DOCNAME).$(DOCTYPE) $(DOCFLAGS)

# changes figure to figure* so figures break two column layout
pdf:
	$(DOC) $(DOCHEAD) $(DOCOBJ) $(DOCTAIL) $(DOCFLAGS) --to latex \
		| sed 's/figure/figure\*/' | pdflatex --jobname=$(DOCNAME)
	rm *.aux *.log *.out

# for professor
docx:
	$(DOC) $(DOCHEAD) $(DOCOBJ) $(DOCTAIL) -o $(DOCNAME).docx $(DOCFLAGS)

json:
	@$(DOC) $(DOCHEAD) $(DOCOBJ) $(DOCTAIL) $(DOCFLAGS) --to json

clean:
	rm $(DOCNAME).*
