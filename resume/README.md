# Typeset resume

`Tyler_Darisme_Resume.pdf` is the resume that [afig.dev/resume](https://afig.dev/resume) shows and
offers for download. The site serves it at `afig.dev/resume.pdf`, fetched from this folder on
`main`. Changes go live within about five minutes of merging, with no site deploy needed.

`../README.md` is the source of truth for content. This PDF is built from
`Tyler_Darisme_Resume.tex`, and the two files are kept in sync by hand.

## Updating after a README change

1. Diff `../README.md` against the `.tex` and carry every content change over. Only change the
   wording the README changed.
2. Build it with [Tectonic](https://tectonic-typesetting.github.io/). The file uses `fontspec`, so
   it needs XeLaTeX or LuaLaTeX; plain `pdflatex` will fail. On Overleaf, set the compiler to
   XeLaTeX.

   ```
   tectonic -X compile Tyler_Darisme_Resume.tex
   ```

3. Check the output before committing:
   - **The PDF must be exactly one page.** If new content overflows, tighten the wording of the
     longest bullets first. Don't shrink fonts or margins below the current values.
   - Render the page and look at it. Check for one- or two-word orphan lines and overfull boxes
     (text running into the right margin; Tectonic prints these as warnings).
   - Extract the text (for example with `pdftotext` or PyMuPDF). It should read top to bottom in
     order, with no split or merged words. Hyphenation and `fi`/`fl` ligatures are turned off on
     purpose so that ATS parsers see whole words; keep them off.
4. Commit the `.tex` and the `.pdf` together.

## Conventions the README doesn't carry

- No emoji. Star counts are plain text ("243 GitHub stars").
- Header links show their real addresses (`github.com/a-Fig`), so they still work when printed.
- Each entry header is a single line: organization | role on the left, location | dates on the
  right.
