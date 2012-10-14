#Mongolian Language dictionaries for Stardict

If you have a need to use Mongolian dictionaries there one great open source software called [Stardict](http://code.google.com/p/stardict-3/). It has many [free dictionaries](http://abloz.com/huzheng/stardict-dic/) but lacks Mongolian dictionaries. Here is my attempt make it.

#How to use
-----------
To use pre-compiled stardict dictionaries:

- Download this repository(https://github.com/ochko/stardict-mn-dics/zipball/master) and extract.
- Copy directories in **en-mn** into **/usr/share/stardict/dic**

#How make your own dictionary from scratch
------------------------------------------

##Requirements
You will need **stardict-tools**. It is collection of usefull commands for stardict format and other dictionary formats. On debian based systems you can install with apt-get:

<tt>$ sudo apt-get install stardict-tools</tt>

##Create your terms
Make a tab separated file containing one term per line. For example:
<pre>
aeroplane	n. нисдэг онгоц.
afresh	adv. цоо шинээр, дахин.
afternoon	n. үдээс хойш.
</pre>
This file has 3 lines, each starts with a term and then <tt>TAB</tt> character, and then definition.

##Compile dictionary
<tt>$ /usr/lib/stardict-tools/tabfile dictionary.txt</tt>

It'll create 3 files:
- dictionary.dict.dz
- dictionary.ifo
- dictionary.idx

You should edit **dictionary.ifo** file to set name of the dictionary. But don't touch lines *wordcount, idxfilesize, sametypesequence*. These are important informations for startdict to understand structure of your dictionary.
To install new dictionay create new directory under **/usr/share/stardict/dic** and copy 3 files above into new direcrtory.

#How to convert from babylon dictionaries
-----------------------------------------

##Requirements
You'll need **dictconv** and **stardict-tools**. On debian based systems you can install with apt-get:
<tt>$ sudo apt-get install dictconv stardict-tools</tt>

Or you can build the tool from [source](http://code.google.com/p/stardictproject/).

##Convert babylon to dic format
Let's assume you had a babylon dictionary file named **dictionary.bgl**

To convert *bgl* file to *dic* file run:
<tt>$ dictconv -o dictionary.dic dictionary.bgl</tt>

Converted *dictionary.dic* file is simple tab separated text file. So you can open it in any text editor to see if it converted correctly. 

##Fix encodings
Most old Mongolian dictionary files tend to be in some non-standard encodings. If that is the case, you should use transcoder scripts accompanied in **script** directory of this repository. There is 2 transcoder scripts for 2 different encodings for now. Please use one of them and see if it fixes the file by open it in text editor, otherwise try another one.
<tt>$ mon2unicode.sh dictionary.dic</tt>
or
<tt>$ mgl2unicode.sh dictionary.dic</tt>

Then there should be UTF-8 encoded new file <tt>dictionary.dic.utf8</tt>. 

<tt>$ /usr/lib/stardict-tools/tabfile dictionary.dic.utf8</tt>

You could edit <tt>dictionary.ifo</tt> file to change some meta info like name of dictionary etc.

#Thanks!

[melug](https://github.com/melug) for mappings for mon2unicode.sh.

#Copyright and License
----------------------

Axlsx &copy; 2009-2012 by [Ochirkhuyag.L](mailto:ochkoo@gmail.com). It is licensed under the MIT license.
