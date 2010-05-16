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
# This is the main Makefile of the unprose literate programming
# project.
###################################################################
bin_SCRIPTS = prolitex

prolitex: prolitex.awk
	cp $< $@
	chmod +x $@

# prolitex.awk.tex is simple. The whole program is just linearly
# distributed over the chunk environment, so we just extract the
# contents of these environments. (That's the simplest tangle.)
prolitex.awk: prolitex.awk.tex
	awk '/^\\begin{chunk}/{c=1;next};/^\\end{chunk}/{c=0;next};c' $< > $@
