###################################################################
#
# ProLiteX
# Copyright (C) 2010,  Ralf Hemmecke <ralf@hemmecke.de>
#
###################################################################
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
###################################################################
# This is the main Makefile of the prolitex literate programming
# project.
###################################################################
bin_SCRIPTS = prolitex

###################################################################
# prolitex.sty should live somewhere in the the path given by
# TEXINPUTS. This directory can be configured via
# ./configure --datadir=...
# datadir is usually set to ${prefix}/share so
# pkgdatadir will be ${datadir}/prolitex
###################################################################
dist_pkgdata_DATA = prolitex.sty prolitex.awk

###################################################################
# We put the original sources into the distribution.
###################################################################
EXTRA_DIST = prolitex.ins prolitex.dtx prolitex.awk.tex prolitex.bib

prolitex: prolitex.awk
	echo '@AWK@ -f $< -- "$$@"' > $@
	chmod +x $@

# prolitex.awk.tex is simple. The whole program is just linearly
# distributed over the chunk environment, so we just extract the
# contents of these environments. (That's the simplest tangle.)
prolitex.awk: prolitex.awk.tex
	awk '/^\\begin{chunk}/{c=1;next};/^\\end{chunk}/{c=0;next};c' $< > $@

prolitex.sty: prolitex.ins prolitex.dtx
	echo '\def\PATH{${abs_srcdir}/}' | cat - $< | $(LATEX)


###################################################################
# Documentation
###################################################################
dvi-local: prolitex.dvi prolitex.awk.dvi
ps-local:  prolitex.ps  prolitex.awk.ps
pdf-local: prolitex.pdf prolitex.awk.pdf

%.dvi: %.dtx
	$(LATEX) $<

%.ps: %.dvi
	$(DVIPS) $<

%.pdf: %.dtx
	$(PDFLATEX) $<

%.dvi: %.tex prolitex.sty
	$(LATEX) $<
	$(BIBTEX) $(<:%.tex=%.aux)
	$(LATEX) $<
	$(LATEX) $<

%.pdf: %.tex prolitex.sty
	$(PDFLATEX) $<
	$(BIBTEX) $(<:%.tex=%.aux)
	$(PDFLATEX) $<
	$(PDFLATEX) $<

EXTS=4ct 4tc aux bbl blg css dvi html idv lg log out pdf ps sty tmp toc xref
CLEANFILES=$(EXTS:%=prolitex.%) $(EXTS:%=prolitex.awk.%) \
  prolitex prolitex.awk texput.log article.log article.aux