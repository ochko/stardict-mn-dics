Mongolian Language dictionaries for Stardict
============================================

I have compiled some Mongolian dictionaries for Stardict from Babylon.

Required tools
==============

Use dictconv to convert Babylon dictionary to dic format. Stardict-tools is collection of usefull commands for stardict format and other dictionary formats.

On debian based systems you can install:
# sudo apt-get install dictconv stardict-tools

Or you can build the tool from source http://code.google.com/p/stardictproject/

How to make dictionaries
========================

# dictconv -o name-of.dic name-of.bgl
# mon2unicode.sh name-of.dic
# /usr/lib/stardict-tools/tabfile name-of.dic.utf8


Copyright &copy; 2009-2012 Ochirkhuyag.L
