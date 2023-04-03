N=3
ARCHIVE=xgerge01
PROJ=proj$(N)

.PHONY: all pdflatex over clean zip

all: pdflatex

$(PROJ).pdf: $(PROJ).ps
	ps2pdf $(PROJ).ps -sPAPERSIZE=a4

$(PROJ).ps: $(PROJ).dvi
	dvips -t a4 $(PROJ).dvi -sPAPERSIZE=a4

$(PROJ).dvi: $(PROJ).tex
	latex $(PROJ).tex -sPAPERSIZE=a4
	latex $(PROJ).tex -sPAPERSIZE=a4

pdflatex: $(PROJ).tex
	pdflatex $(PROJ).tex -sPAPERSIZE=a4
	pdflatex $(PROJ).tex -sPAPERSIZE=a4

over: all
	pdftk vzor.pdf multibackground $(PROJ).pdf output $(PROJ)-diff.pdf

clean: 
	rm -rf $(ARCHIVE).zip $(PROJ).pdf $(PROJ).aux $(PROJ).dvi $(PROJ).log $(PROJ).ps $(PROJ).fdb_latexmk $(PROJ).fls $(PROJ).out* $(PROJ).synctex.gz $(PROJ)-diff.pdf $(PROJ).te~ *-eps-converted-to.pdf

zip: clean
	zip -r $(ARCHIVE).zip $(PROJ).tex Makefile *.sty *.eps