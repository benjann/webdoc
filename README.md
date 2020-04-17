# webdoc
Stata module to create a HTML or Markdown document including Stata output

`webdoc` provides tools to create a HTML or Markdown document from within Stata
in a weaving fashion. This is especially useful if you want to produce a HTML
or Markdown document that contains Stata output.

To install the `webdoc` package from the SSC Archive, type

    . ssc install webdoc, replace

in Stata. Stata version 10.1 or newer is required.

---

Installation from GitHub:

    . net install webdoc, replace from(https://raw.githubusercontent.com/benjann/webdoc/master/)

---

Main changes:

    11nov2019 (version 1.2.8)
    - -webdoc do- produced some output in the results window that was not
      supposed to be produce; this is fixed
    - -hardcode- is now also supported for GIF and JPEG

    26oct2019 (version 1.2.6)
    - the -nokeep- graph option had no effect if the graph format was SVG; this is
      fixed
    - in Stata 16, SVGs embedded in the HTML file did not always display correctly
      because -webdoc append- (which is used to copy the SVG to the HTML file) 
      was breaking very long lines (> 32,768 characters) due to an internal limit 
      of Mata's -fget()- function; this is fixed
    - -webdoc graph- now passes options -weight()- and -height()- through to 
      -graph export- in all cases; in earlier versions, -weight()- and -height()-
      were only taken into account for PNG and TIFF
    - the default width of 500 pixels is now also applied to GIF and JPEG, not only
      to PNG and TIFF (this is currently only relevant for Sata 16 on Mac)

    14apr2018 (version 1.2.5)
    - options width() and height() in -webdoc graph- were ignored if as() contained 
      more than one element; this is fixed
    - the help file now has suffix .sthlp instead of .hlp

    21dec2017 (version 1.2.4)
    - sthlp() option of -webdoc stlog- now has a -noid- suboption to ignore the 
      log-id when constructing internal links
    - -webdoc toc- now looks for -id="..."- in HTML headings; if found, the 
      specified id will be used instead of making up an own id

    13nov2017 (version 1.2.3)
    - the 30jan2017 update introduced an error due to which comments in Stata output 
      were not always tagged correctly; this is fixed

    12apr2017 (version 1.2.2)
    - option header(include()) returned error (due to a typo in file handle); this
      is fixed

    02feb2017 (version 1.2.1)
    - when pre-processing the do-file and processing the log files, lines starting
      with "*" in a multiline-command could be misinterpreted; this is fixed

    17jan2017 (version 1.2.0)
    - -webdoc close- caused error if -logall- was active; this is fixed
    - option -linesize()- of -webdoc stlog- did not always behave as expected;
      this is fixed

    28nov2016 (version 1.1.8)
    - -webdoc stlog quietly- added
    - -webdoc do- now allows arguments
    - -logall- did not capture Stata commands at the beginning of a do-file if
      the do-file was included by a nested -webdoc do- command; this is fixed
    - some internal changes related to the -cmdlog- and -dosave- options

    04nov2016 (version 1.1.7)
    - -webdoc substitute- added
    - -webdoc stlog oom- and -webdoc stlog cnp- no longer have any effect if used 
      outside an stlog section or if webdoc is not initialized
    - fixed a bug with in -webdoc local-

    31oct2016 (version 1.1.6)
    - -webdoc local- can now also be used within an stlog section
    - -webdoc graph- commands within an stlog section were not executed if nodo
      was on; this is fixed
    - WebDoc_stloc was not backed up in nested calls to -webdoc do-; this is fixed
    - the functions for parsing command lines have been rewritten; they are now more
      transparent and faster
    - stripping of webdoc commands in -webdoc strip- or when processing a log file
      has been improved
    - globals set by -webdoc stlog- are now kept until the next -webdoc stlog- 
      command

    21oct2016 (version 1.1.4)
    - webdoc did not work in Stata 9 because because it uses the tokenget() function
      that was introduced in Stata 10; version control has now been promoted to 10.1
    - -webdoc stlog- now has a linesize() option
    - new options mark() and tag() have been added to -webdoc stlog-
    - new option -certify- has been added to -webdoc stlog-
    - there is a new -webdoc local- command
    - current r()-returns are now preserved by -webdoc stlog- and -webdoc stlog close- 
    - dosave option: a message with a link to the file is now displayed
    - fixed a bug in -webdoc stlog, dosave: command-
    - the -link- option of -webdoc graph- now has an optional argument to select the
      target file
    - the -hardcode- option of -webdoc graph- now supports SVG
    - -webdoc append- now has a drop() option
    - now using http instead of https to copy CSS and Javascript files in Stata 12 
      or earlier (only relevant if option -selfcontained- is specified)
    - header option -charset()- now defaults to "iso-8859-1" (Windows, Unix) or 
      "mac" (MacOSX) if webdoc is used in Stata 13 or earlier
    - file open errors could occur on Windows (probably due to virus scanners) 
      when replacing files using unlink() followed by fopen(); webdoc now uses 
      multiple tries to open the file

    10sep2016 (version 1.1.2)
    - the -link- option of -webdoc graph- now has an optional argument to select
      the target file
    - the -hardcode- option of -webdoc graph- now supports SVG
    - -webdoc append- now has a drop() option

    01sep2016 (version 1.1.1):
    - -webdoc init, header()- now also works if no docname is specified
    - CSS/scripts: bootstrap/bootswatch updated to version 3.3.7; jquery now loaded 
      from code.jquery.com, not ajax.googleapis.com; links to CCS files and scripts
      now include Subresource Integrity (SRI) hash
    - -webdoc append- now has a substitute() option
    - compound double quotes in -webdoc stlog, sthlp()- caused error; this is fixed
    - -webdoc stlog, sthlp- now uses a more robust link substitution procedure
    - when determining the amount if indentation, ltrim now treats tabs as blanks
      and ignores lines that only contain white space
    - figure id was empty if -webdoc graph name- was used without any stlog 
      information being available; this is fixed

    06aug2016 (version 1.1.0):
    - webdoc released on SSC
