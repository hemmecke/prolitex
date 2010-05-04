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

prolitex0: prolitex.tex
	@awk '/^\\begin{chunk}{$@}/ {code=1;next};/^\\end{chunk}/ {code=0; next };code' $<
