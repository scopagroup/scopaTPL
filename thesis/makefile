filename=thesis

compile=latexmk 


all:
	@echo ${compile} 
	${compile} -halt-on-error -pdf ${filename}.tex 
	open -a Skim ${filename}.pdf
	@echo Done ....!


clean:
	rm -f *.aux *.log *.dvi *.blg *.bbl \
          *.fls *.fdb_latexmk *.out     \
          *.brf *.snm *.toc *.nav *.thm \
		  *.pdfsync *synctex.gz *.pdf
	@echo Cleaned ....! 


