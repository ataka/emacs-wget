Emacs-wget README

This package contains an interface program for GNU wget on Emacs.

# Introduction

GNU Wget is a free software package for retrieving files using HTTP,
HTTPS and FTP, the most widely-used Internet protocols.  It is a
non-interactive command line tool.  More information, see wget web page:

* http://www.gnu.org/software/wget/

GNU Wget is originally written by Hrvoje Niksic.


Emacs-wget provides an interface of GNU wget for Emacs.  You can also
call it from web browser on Emacs, like Emacs/W3 or emacs-w3m.

The latest emacs-wget is available at:

* https://github.com/ataka/emacs-wget


# Requirements

GNU Emacs and GNU wget.

* GNU Emacs: http://www.gnu.org/software/emacs/
* GNU Wget:  http://www.gnu.org/software/wget/


# Installation

1.  make && make install

        $ tar xzvf emacs-wget-X.YY.tar.gz
        $ cd emacs-wget-X.YY
        $ make
        # make install

  1. If make fails, put all *.el files into your load-path directory.
2. Put following expressions into your .emacs file.

        (autoload 'wget "wget" "wget interface for Emacs." t)
        (autoload 'wget-web-page "wget" "wget interface to download whole web page." t)

3. Setting for Web browser on Emacs:
  1. With emacs-w3m, put the following code into your .emacs:

                (load "w3m-wget")

  2. With Emacs/W3, put the following code into your .emacs:

                (autoload 'w3-wget "w3-wget" "wget interface for Emacs/W3." t)

4. If wget version is 1.7 or less, put the following code into your .emacs:

        (setq wget-basic-options '("-v"))

5. When you write your `.wgetrc`:
  1. `quiet = on`

     Emacs-wget will fail to download.  Put the following into your .emacs:

                (setq wget-basic-options (cons "-equiet=off" wget-basic-options))

  2. `dir_prefix = PATH/TO/DOWNLOAD`

     Variable wget-download-directory will be ignored.  Put the
     following into your .emacs:

                (setq wget-basic-options (cons "-P." wget-basic-options))

  3. `timestamping = on`
     `mirror = on`  (`mirror=on` automatically sets `timestamping=on`)

     These options conflict with -nc option.  If your wget-default-options
     or wget-ftp-default-options have -nc option, get rid of it.

  4. `logfile = log`

     *wget* buffer will appear but show no information, because the
     output from wget is robbed by the 'log' file.  I don't have
     good idea, except not displaying surd *wget* buffer:

                (setq wget-process-buffer nil)

  5. If the system can not search wget command, tell emacs where to find
     it.

                (setq wget-command "C:/cygwin/bin/wget")


# Running with...

|(emacs-version)|wget -V|
|:--|:--|
|20.7 (Meadow 1.15)|1.8.2 (cygwin)|
|21.3.50 (CVS)|1.8.1, 1.8.2, 1.9.1|

If you find emacs-wget work with other environment above, please tell me
<masayuki.ataka@gmail.com>.


# Contact address

E-mail to <masayuki.ataka@gmail.com>.  Any information, bug-report,
request, comments, etc... are welcome.

If you send me a bug-report, please write your wget version, too.

I don't use emacs-wget with Emacs/W3, so please give me an information
about emacs-wget on Emacs/w3.


# Acknowledgments

This program shall never see the light without GNU wget, developer
Hrvoje Niksic, and other wget contributors.  Thanks to great program.

Great thanks to Takayuki Arakawa for his words, helps, and tests.
Without him, it would take long time to develop this package.

Juri Linkov <juri@jurta.org> greatly contributed to the development of
emacs-wget 0.5.0.  He send me lots of ideas, suggestions, and
bug-reports.  He also tested emacs-wget under development.

Yoichi NAKAYAMA <yoichi@eken.phys.nagoya-u.ac.jp> maintains FreeBSD
ports collection for emacs-wget.

Akira TAGOH <tagoh@debian.org> maintains debian package for emacs-wget.

## Thanks to:

* Mitsugu SAKAMOTO <mitsugu@argv.org>
  - Reported unsupported functions on Meadow-pre1.15
    (window-text-height, replace-regexp-in-string).

* TSURUDA Naoki <tsuru@yokohama.office.ne.jp>
  - Reported bug running on Meadow-1.15.
  - Reported arguments order problem when using with wget-1.8.2 (cygwin).

* KOSEKI Yoshinori <kose@yk.NetLaputa.ne.jp>
  - Suggestion for load timing of w3m-wget.el.

* SHINYA Akihiko <shinya@sonicteam.com>
  - Reported problem when setting .wgetrc
    (quiet, timestamping, mirror, dir_prefix, and logfile).

* NAKAYA Toshiharu <nakaya8@is.titech.ac.jp>
  - Reported critical problem that emacs-wget removes LANG environment
    variable from Emacs' system variable.
  - Reported unsupported function on Emacs-20 or less
    (read-directory-name).

* Wataru Tachibana <MLB33828@nifty.com>
  - Suggestion for changing permission after downloading by its
    filename extension.

* mace <mace@kirjakaapeli.lib.hel.fi>
  - Suggestion for asking download directory always when user option
    wget-download-directory is nil.


Local Variables:
fill-column: 72
End:
