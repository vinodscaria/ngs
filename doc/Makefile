all: ngsmet.1.md html man

ngsmet.1.md: ../c/vm.c ../c/bootstrap.ngs ../c/stdlib.ngs ../c/autoload/* ngsmet.header  make_methods_markdown.ngs
	(cat ngsmet.header ; ./make_methods_markdown.ngs) >$@

html: $(patsubst %.1.md,%.1.html,$(wildcard *.1.md))
man: $(patsubst %.1.md,%.1,$(wildcard *.1.md))

%.1.html: %.1.md pandoc.css
	pandoc -f markdown -t html -c pandoc.css -s $< -o $@
%.1: %.1.md
	pandoc -f markdown -t man -s $< -o $@

.PHONY: clean
clean:
	-rm *.1
	-rm *.1.html
	-rm ngsmet.1.md
