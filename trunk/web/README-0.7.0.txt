Camomile 0.7.0:

This is a beta release of Camomile library package.  Camomile is a
comprehensive Unicode library for ocaml.  Camomile provides Unicode
character type, UTF-8, UTF-16, UTF-32 strings, conversion to/from
about 200 encodings, collation and locale-sensitive case mappings, and
more.

Copyright 2001, 2002, 2003, 2004, 2005, 2006 Yamagata Yoriyuki

This library is free software; you can redistribute it and/or modify
it under the terms of the GNU Lesser General Public License as
published by the Free Software Foundation; either version 2 of the
License, or (at your option) any later version.

This library is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
Lesser General Public License for more details.

The GNU Lesser General Public Licence (LGPL) is contained in the file COPYING.

The following files are authored by different persons.  For their
licenses, see the relevant notice of each file or directory.

configure.in Makefile.in : Jean-Christophe FILLIATRE
	Licensed by LGPL

locales : International Business Machines : 
	derived from the ICU package.  see locales/licence.html
mappings : Free Software Foundation : 
	derived from glibc.  Licensed by LGPL
	(CP932 has a different origin.  See the premable of the file CP932)
unidata : Unicode Inc. : see unidata/README

1. Installation

The library is designed to work all platform supported by ocaml,
but currently the build procedure requires GNU tools. (GNU Make, grep,
and sh command for run the configure.)

In the top of the source directory, do the following.
	$ ./configure
	$ make
Become root and do the following.
	# make install

The installation directories depend on whether you have findlib, which
is automatically detected.  If you do not have findlib, Library files
(camomile.cma, camomile.cmxa and other auxiliary files) and
interface files (camomileLibrary.cmi) are installed to ocaml standard
library directory.  If you have findlib, these files are governed by
findlib and installed as a package named "camomile".  For either
cases, data files are put under /usr/local/share/camomile by default.
If you give the configure option as
	$ ./configure --datadir=XXXX 
data files are placed under XXXX/camomile.  Also, programs
"camomilecharmap.(byte or opt)" and "camomilelocaledef.(byte or opt)"
are installed to {bindir} (a directory specified by configure).
Running commands with --help option display their usage.

You can uninstall the library by
	# make uninstall

If you have ocamldoc,
	$ make dochtml
creates dochtml directory in the source directory, and HTML
documentation.  Similarly,
	$ make doclatex
	$ make doctexi
	$ make man
creates LaTeX, Texi, man documentation respectively.

2. Using libraries

2.1 Packing

All module are packed to CamomileLibrary module, i.e. have names as
CamomileLibrary.<module name>.

2.2 Configuration

You can specify the location of data files used by camomile.  This
functionality is useful, for example, if you plan to use compiled
binary with Camomile on machines with different directory structures.

"make install" automatically installs all data files into the default
locations, which are specified by CamomileDefaultConfig module.  If
you just wanted to use default configuration, you can use
Main.Camomile module.  Main.Camomile module has *almost* same
interface to Camomile 0.6.X

To configure individual module, you have to pass a module containing
configuration values to Make or Configuration functor.  Or, you can
use Main module which defines Main.Make functor.  Main.Make functor
returns a module which contains all modules which are properly
configured.  ConfigInt.Type module type specifies what values should
be defined.

2.3 Individual modules.

See *.mli files.

2.4 Migration from 0.6.X

Replace all references to Camomile with
CamomileLibrary.Main.Camomile.  CamomileLibrary.Main.Camomile
have the *almost* same interface with the previous Camomile.

3. Author

You can contact the author by yori@sourceforge.net

4. Acknowledgement

Peter Jolly provided CP932 conversion table.  Kawakami Shigenobu
contributed findlib support.  Alain Frisch, Peter Jolly, Kawakami
Shigenobu provided several bug fixes.

