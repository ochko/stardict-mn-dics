Mongolian Language dictionaries for Stardict
============================================

I have compiled some Mongolian dictionaries for Stardict from Babylon.

How to use stardict files
=========================

- Download this repository(https://github.com/ochko/stardict-mn-dics/zipball/master) and extract.
- Copy directories in en-mn into /usr/share/stardict/dic

How to make Stardict dictionary from Babylon dictionary
=======================================================

To convert babylon dictionary you need <tt>dictconv</tt> and <tt>stardict-tools</tt>. stardict-tools is collection of usefull commands for stardict format and other dictionary formats.

On debian based systems you can install with apt-get:
<tt>$ sudo apt-get install dictconv stardict-tools</tt>

Or you can build the tool from source http://code.google.com/p/stardictproject/

Let's assume you had a babylon dictionary file named dictionary.bgl

First convert <tt>bgl</tt> file to <tt>dic</tt> file:
<tt>$ dictconv -o dictionary.dic dictionary.bgl</tt>

Converted dictionary.dic file is simple tab separated text file. So you can open it in any text editor to see if it converted correctly. Most Mongolian dictionary files tend to be in some non-standard encodings. If that is the case you should use transcoder scripts accompanied in <tt>script</tt> directory of this repository. There is 2 transcoder scripts for 2 different encodings. Please use one of them and see if it fixes the file, otherwise try another one.
<tt>$ mon2unicode.sh dictionary.dic</tt>
or
<tt>$ mgl2unicode.sh dictionary.dic</tt>

Then there should be UTF-8 encoded new file <tt>dictionary.dic.utf8</tt>. You might want to add/edit dictonary entries in <tt>dictionary.dic.utf8</tt> if you're curious. Then create your stardict dictionary with <tt>tabfile</tt> command from stardict-tools.

<tt>$ /usr/lib/stardict-tools/tabfile dictionary.dic.utf8</tt>

It creates 3 files:

- dictionary.dict.dz
- dictionary.ifo
- dictionary.idx

You could edit <tt>dictionary.ifo</tt> file to change some meta info like name of dictionary etc.

To install new dictionay create new directory under <tt>/usr/share/stardict/dic</tt> and copy 3 files above into new direcrtory.

You are done!

Copyright &copy; 2009-2012 Ochirkhuyag.L
