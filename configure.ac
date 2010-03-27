AC_PREREQ(2.61)
AC_INIT(
  [ProLite],
  [0.0.1],
  [ralf@hemmecke.de])

# Sanity check
AC_CONFIG_SRCDIR([build-setup.sh])

# Certain configuration files are kept in the config subdirectory.
AC_CONFIG_AUX_DIR(config)
AC_CONFIG_MACRO_DIR(config)

# Init Automake (non-gnu standard)
AM_INIT_AUTOMAKE([-Wall -Werror foreign])


# We need notangle to get things going. That must be in the PATH.
AC_CHECK_PROGS([LATEX], [latex])

# Check for a latex package by trying to compile a short document.
AC_DEFUN([CHECK_LATEX_PACKAGE],
  [if ! (echo '\documentclass{article}\usepackage{$1}\begin{document}\end{document}' | $LATEX -interaction=nonstopmode); then
       AC_MSG_ERROR([Missing $1.sty LaTeX package.])
   fi])

# Test whether keyval latex package is installed.
# http://tug.ctan.org/tex-archive/macros/latex/required/graphics/
CHECK_LATEX_PACKAGE([keyval])

# Test whether listings latex package is installed.
# http://www.ctan.org/tex-archive/macros/latex/contrib/listings/
CHECK_LATEX_PACKAGE([listings])

# The Makefiles
AC_CONFIG_FILES([Makefile])

# Output everything
AC_OUTPUT
