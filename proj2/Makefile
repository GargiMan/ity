N=2
ARCHIVE=xgerge01-fit
PROJ=proj$(N)

.PHONY: all pdflatex over clean zip

all: pdflatex

$(PROJ).pdf: $(PROJ).ps
	ps2pdf $(PROJ).ps

$(PROJ).ps: $(PROJ).dvi
	dvips -t a4 $(PROJ).dvi 

$(PROJ).dvi: $(PROJ).tex
	latex $(PROJ).tex
	latex $(PROJ).tex

pdflatex: $(PROJ).tex
	pdflatex $(PROJ).tex
	pdflatex $(PROJ).tex

over: all
	pdftk vzor.pdf multibackground $(PROJ).pdf output $(PROJ)-diff.pdf

clean: 
	rm -rf $(ARCHIVE).zip $(PROJ).pdf $(PROJ).aux $(PROJ).dvi $(PROJ).log $(PROJ).ps $(PROJ).fdb_latexmk $(PROJ).fls $(PROJ).out* $(PROJ).synctex.gz $(PROJ)-diff.pdf $(PROJ).te~

zip: clean
	zip -r $(ARCHIVE).zip $(PROJ).tex Makefile