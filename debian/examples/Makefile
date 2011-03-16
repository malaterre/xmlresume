# -*- mode: makefile; coding: utf-8 -*-
# A sample Makefile for building your résumé using the
# xml-resume-library.  Requirements: xsltproc, fop, passivetex
# Copyright © 2002 Colin Walters <walters@debian.org>

# This should be the name of your résumé file, but without the .xml
# extension.
resume    ?= resume

# Parametric country and papersize values
country   ?= us
papersize ?= letter

# The styles you want to use.  These are for the United States; see
# the directory /usr/share/sgml/xml-resume-library/xsl/output/ for
# other styles.
FO_STYLE   = /usr/share/sgml/xml-resume-library/xsl/output/${country}-${papersize}.xsl
HTML_STYLE = /usr/share/sgml/xml-resume-library/xsl/output/${country}-html.xsl
TXT_STYLE  = /usr/share/sgml/xml-resume-library/xsl/output/${country}-text.xsl

.PHONY: all clean check
.SUFFIXES: .html .fo .pdf .xml .xsl .txt

all:	$(resume).html $(resume).txt $(resume).pdf

clean:
	-rm -f $(resume).html $(resume).pdf $(resume).fo $(resume).txt *~

$(resume).html: $(resume).xml
	xsltproc $(HTML_STYLE) $(resume).xml > $(resume).html

$(resume).txt: $(resume).xml
	xsltproc $(TXT_STYLE) $(resume).xml > $(resume).txt

$(resume).fo: $(resume).xml
	xsltproc $(FO_STYLE) $(resume).xml > $(resume).fo

$(resume).pdf: $(resume).fo
	fop -fo $(resume).fo -pdf $(resume).pdf
