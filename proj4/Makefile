N=4
ARCHIVE=xgerge01
PROJ=proj$(N)

.PHONY: all pdflatex clean zip

all: pdflatex

$(PROJ).pdf: $(PROJ).ps
	ps2pdf $(PROJ).ps

$(PROJ).ps: $(PROJ).dvi
	dvips -t a4 $(PROJ).dvi

$(PROJ).dvi: $(PROJ).tex
	latex $(PROJ).tex
	bibtex $(PROJ)
	latex $(PROJ).tex
	latex $(PROJ).tex

pdflatex: $(PROJ).tex
	pdflatex $(PROJ).tex
	bibtex $(PROJ)
	pdflatex $(PROJ).tex
	pdflatex $(PROJ).tex

clean: 
	rm -rf $(ARCHIVE).zip $(PROJ).pdf $(PROJ).aux $(PROJ).dvi $(PROJ).log $(PROJ).ps $(PROJ).fdb_latexmk $(PROJ).fls $(PROJ).out* $(PROJ).synctex.gz $(PROJ).te~ $(PROJ).bbl $(PROJ).blg *-eps-converted-to.pdf

zip: clean
	zip -r $(ARCHIVE).zip $(PROJ).tex $(PROJ).bib Makefile czechiso.bst