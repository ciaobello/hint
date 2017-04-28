================================================================================
    hint            |   version 1.00    |   GPL v3 (see LICENSE)    | 2017-04-27
    Ilikelinux      |   https://twitter.com/Ilikelinux69
================================================================================

TOC:
    1.  What is this?
    2.  Install / Uninstall
    3.  How do I use it?
    4.  Who made it?


1.  What is this?

    'hint' is a cheat-sheet script for people who are too impatient to browse
    the manual page for a given program.  It's well-suited for those who might
    use a program only occasionally, and need only brief reminders on the
    'important bits'; the cliff-notes version of man pages, if you will.

    This particular version, written as a Bash script, is a reimplementation of
    a Python script originally written by Chris Lane.  The other version is the
    'main' version; this is the off-shoot.

    The main difference between 'hint' & 'cheat' should be that you should be able
    to browse it online on a github/jekyll page beside a blog (sinc with cronjob).


2.  Install / Uninstall

    To install this script, as root, run 'make install' from inside the top
    directory to which you've downloaded/extracted the program; it should be the
    same directory where you found this README file.

    To uninstall the program, as root and from that same directory (or whichever
    directory contains the Makefile), run 'make uninstall'.


3.  How do I use it?

    Using this script is straightforward enough, in the typical UNIX/Linux
    fashion:

    hint [OPTION] FILE[S]

    Options:
        -a or --add:        Add a text file to the hint directory
        -A:                 Add and compress (gzip) a text file
        -e or --edit:       Edit a hint, using editor in $EDITOR variable
        -k:                 Grep for keyword(s) in file names
        -g:                 Grep for keyword(s) inside file text
        -G:                 Same as above, but list full paths if found
        -l or --link:       Link a file instead of copying it to the hint dir
        -L:                 List all hints with full paths
        -h or --help:       List the help
        --version:          List version and author info
        -u or --update:     Update hint (safe way)
        -U:                 Overwrite all hints with downloaded versions


    Examples:

         hint ap:           List all files with 'ap' in the filename; if there
                            is only one result, it will be displayed
         hint -k:           List all available hints (in ~/.hint)
         hint -k tar:       Grep for all hints with 'tar' in the filename
         hint -k tar sh:    Grep for hints with 'tar' or 'sh' in filenames
         hint -a foo:       Add 'foo' to the hint directory
         hint -a foo bar:   Add both 'foo' and 'bar' to the hint dir
         hint -A *.txt:     Add and compress all .txt files in current dir
         hint -l foo.png    Create a link to foo.png in the cheat directory


    There are a few useful variables for people who use this script a lot:
    DEFAULT_CHEAT_DIR, CHEATPATH, CHEAT_TEXT_VIEWER, CHEAT_IMAGE_VIEWER and
    CHEAT_PDF_VIEWER.

    DEFAULT_CHEAT_DIR is the directory in which cheat sheets are stored by
    default.  This is set to $HOME/.cheat if left unspecified by the user.

    CHEATPATH is similar to the PATH variable, except it's used for cheat
    sheets.  If you're referencing cheat sheets from multiple directories,
    you'll want to make use of this environment variable.  If this variable is
    not set by the user, it's populated by DEFAULT_CHEAT_DIR.  If the user does
    set this variable, it's up to them to include every directory in which cheat
    sheets are kept, as DEFAULT_CHEAT_DIR is not automatically added to the
    CHEATPATH variable.

    CHEAT_TEXT_VIEWER is the program used to view the normal cheat sheets.  It's
    assumed to accept text from stdin ('cat' and 'less' are good options).
    'cat' is used by default.

    CHEAT_IMAGE_VIEWER is the program which is used to display image files, and
    CHEAT_PDF_VIEWER is the program which will display PDFs.  These variables
    are optional, but if you can't get the script to display images/PDFs, set
    them to the programs you want.


4.  Who made it?

    Adapted version (hint):  Ilikelinux alias luciano S.
                              https://twitter.com/Ilikelinux69

    Forked version:          James Hendrie
                              hendrie.james@gmail.com
                              https://github.com/jahendrie/cheat

    Main version:            Chris Lane
                              chris@chris-allen-lane.com
                              https://github.com/chrisallenlane
