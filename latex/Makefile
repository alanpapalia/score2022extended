CMD = pdflatex
BCMD = bibtex

all:
	$(CMD) root; $(BCMD)  root; $(CMD) root; $(CMD) root

simple:
	$(CMD) root

clean:
	rm -f *.aux *.fls *.fdb_* *.log root.pdf *.synctex.gz
	rm -f *.bbl *.bcf *.fmt *.blg *.xml *.out
	rm -rf auto
	clear

