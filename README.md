latex-ai2pdf
============

ai2pdf is a tool to automatically convert Adobe Illustrator figures to PDF during the LaTeX build process. No more manual conversions in Illustrator after you edited files.

Requirements
------------

You need Mac OS, Adobe Illustrator, and TeXlive (or another TeX distribution).

Installation
------------

 1. Put ``ai2pdf`` (without extension) somewhere into your ``$PATH``, e.g., ``/usr/local/bin``
 2. Put ``ai2pdf.sty`` in it's own directory your local texmf tree, e.g., ``/usr/local/texlive/texmf-local/tex/latex/ai2pdf/``
 3. Run ``texhash`` to update your TeX package cache.

At this point you can run ``pdflatex --shell-escape ai2pdf.tex`` to see whether everything works. The output should look like in ``ai2pdf.pdf``.

Usage
-----

Look at ``ai2pdf.tex`` for a minimal example. ``ai2pdf`` redefines the ``\includegraphics`` command. Whenever you include a file that exists with a ``.ai`` extension, Adobe Illustrator is called and the file is exported to PDF. You don't need any extra commands in your tex source. Just use ``\includegraphics`` as usual.

``ai2pdf`` uses the file modification date to decide whether the PDF for an AI
file needs to be created/updated. Only if the PDF file does not exist or the
modification date of the AI is newer than the PDF's, Illustrator is called to
update the PDF file.

**Note:** You need to run ``pdflatex`` with the ``--shell-escape`` parameter when compiling. Otherwise, the package is not able to execute the ``ai2pdf`` conversion tool from within LaTeX.

Using in Teams
--------------

If you intend to use ``ai2pdf`` in teams where not everyone uses a Mac and
Illustrator, or where not everyone can be expected to have ``ai2pdf``
installed, check ``Tools/ai2pdfwrapper.sty``.

The idea is to copy ai2pdfwrapper.sty to the directory where your main latex
file resides. You can then include the wrapper instead of ``ai2pdf``. The
wrapper will check whetehr ``ai2pdf`` is available and, if not, output a
warning message. Compilation continutes though, only the PDF files might be
out of date.

TODO
----
 * Make a Windows version of ``ai2pdf`` using VBA.
