IMAGES_SRCS := $(shell ls *.tikz)
IMAGES_OBJS := $(IMAGES_SRCS:%.tikz=%.png)

CONVERT=convert
SED=sed
LATEXMK=pdflatex
MV=mv
.PHONY: all
all: $(IMAGES_OBJS)


%.pdf: %.tikz .tikz2pdf.tex
	@echo "   Compiling $< to $@"
	@$(SED) 's/\\input{%s}/\\input{$<}/' .tikz2pdf.tex > temp.tex
	@$(LATEXMK) -halt-on-error temp.tex
	@$(MV) temp.pdf $@



%.png: %.pdf
	@echo "   $@"
	@$(CONVERT) $< $@
