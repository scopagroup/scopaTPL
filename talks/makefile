filename=talk

compile=latexmk 

all:
	@echo ${compile} 
	${compile} -halt-on-error -pdf ${filename}.tex 
	open -a Skim ${filename}.pdf

clean:
	rm -f *.aux *.log *.dvi *.blg *.bbl 	\
          *.fls *.fdb_latexmk *.out    		\
          *.brf *.snm *.toc *.nav *.synctex.gz 	\
		  *.pdfsync *.bcf *.pdf 
	@echo Cleaned ....! 


