# Build the report

Overleaf: choose New Project → Upload Project, upload the complete package ZIP, select `report/main.tex` as the main document, and use pdfLaTeX. Include the outer repository folder in the path if retained by Overleaf.

For a smaller Overleaf project, upload only `main.tex` and the complete `figures/` directory from this folder.

Local TeX Live or MiKTeX: open a terminal in this folder and run `pdflatex -interaction=nonstopmode -halt-on-error main.tex` twice. The second pass resolves the contents and bookmarks.

Standard LaTeX packages and Latin Modern fonts are sufficient. No custom fonts, `.bib`, `.cls`, `.sty`, or simulation software are needed to compile the document. Compilation does not execute TRNSYS or PVsyst.
