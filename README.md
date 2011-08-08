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

**Note:** You need to run ``pdflatex`` with the ``--shell-escape`` parameter when compiling. Otherwise, the package is not able to execute the ``ai2pdf`` conversion tool from within LaTeX.

TODO
----
 * Enhance ``ai2pdf`` to recognize whether conversion is *necessary*: The script should check whether a PDF version of a given AI file already exists, and, if so, should only re-export if the file dates differ.
 * Make a Windows version of ``ai2pdf`` using VBA.
