
### What is this?

[r2u][r2u] support repository with build infrastructure

### Details

This repository typically contains both the Docker container definitions, and
GitHub Actions, to govern builds for [r2u][r2u].  

### Background

Initially, [r2u][r2u] 'reused' and 're-packaged' existing [p3m][p3m]
(formerly RSPM or PPM) binaries but as the coverage expanded to both
[BioConductor][bioc] packages as well as arm64 packages where binaries were
not available we started to build more.  By 2025, not only was every package
in [r2u][r2u] built explicitly, it was generally also built here in the
'Actions' of this repository.

### Author

Dirk Eddelbuettel

[r2u]: https://eddelbuettel.github.io/r2u
[p3m]: https://p3m.dev
[bioc]: https://bioconductor.org
