# CV Archive

This directory stores maintainable CV sources and stable exported PDFs.

## Structure

```text
cv/
  README.md
  source/
    English_CV.md
    Chinese_CV.md
  academic/
    en/
      main.tex
      Yihan_Li_Academic_CV_EN.pdf
```

## Conventions

- Keep Markdown files in `cv/source/` as content drafts.
- Keep LaTeX sources close to the CV variant they build.
- Keep generated PDFs only when they are intended for review, sharing, or
  website download.
- Build the English academic CV with:

```sh
tectonic -o cv/academic/en cv/academic/en/main.tex
cp cv/academic/en/main.pdf cv/academic/en/Yihan_Li_Academic_CV_EN.pdf
cp cv/academic/en/main.pdf docs/assets/cv_en.pdf
```

`main.pdf` is treated as a local build output and ignored by Git. The stable
exported files are `Yihan_Li_Academic_CV_EN.pdf` and `docs/assets/cv_en.pdf`.
