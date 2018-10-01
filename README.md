# Sample Git repository for managing .docx and .pdf files

Word files are tracked using Pandoc, as detailed [here][geradus] and [here][martinfenner]. Upon commit, Word files are converted to Markdown for text version tracking. To diff current changes with last commited version, convert manually.

```
pandoc -s file.docx -t markdown -o file.md
```

PDF files are tracked using Git LFS, as Pandoc does not accept PDF files as input.

## Setup
-   On Windows, this setup requires WSL, or capability to run `bash` scripts on a Windows machine. Update `./hooks/pre-commit` and `./hooks/post-commit` with the appropriate command to run Linux script (the default assumes WSL).
    - On Linux, simply update `./hooks/pre-commit` and `./hooks/post-commit` to directly run the scripts instead of calling `bash`.
-   Install [Git LFS][git-lfs] and [Pandoc][pandoc].
-   On a fresh clone, either:
    -   Change local Git hooks folder from `$GIT_DIR/hooks` to `./hooks`:  
        `git config core.hooksPath hooks`
    -   Copy contents of `./hooks` to `$GIT_DIR/hooks`
-   On an existing repository, append or copy (if not exists) the contents of `./hooks` to `$GIT_DIR/hooks`.

## Errata
-   Script to automate hook setup
-   Convert Linux shell script to a cross-platform one

[git-lfs]: https://git-lfs.github.com
[pandoc]: https://pandoc.org
[geradus]: https://github.com/vigente/gerardus/wiki/Integrate-git-diffs-with-word-docx-files
[martinfenner]: http://blog.martinfenner.org/2014/08/25/using-microsoft-word-with-git