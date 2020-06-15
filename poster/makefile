filename=poster
compile=pdflatex

all:
	${compile} ${filename}
	-bibtex ${filename}
	-bibtex ${filename}
	${compile} ${filename}
	${compile} ${filename}
	${compile} ${filename}
	open ${filename}.pdf
	@echo Done ....!


quick:
	${compile}  ${filename}
	open ${filename}.pdf
	@echo Done ....!

pdf:
	${compPdftex} ${filename}

abstract:
	${compPdftex} ${abstract}

bib:
	${compile} ${filename}
	bibtex ${filename}

log:
	emacs -nw ${filename}.log

clean:
	rm *.aux *.log *.dvi *.blg *.bbl *.out
	@echo Cleaned ....! 

%.pdf: %.tex
	${compile} $*
	${compile} $* 

