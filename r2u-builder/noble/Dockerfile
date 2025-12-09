## Emacs, make this -*- mode: sh; -*-

FROM rocker/r2u:24.04

LABEL org.label-schema.license="GPL-2.0" \
      org.label-schema.vcs-url="https://github.com/eddelbuettel/r2u" \
      maintainer="Dirk Eddelbuettel <edd@debian.org>"

## This was not needed before but we need it now
ENV DEBIAN_FRONTEND=noninteractive

## Packages needed for r2u,
## and for docker which r2u checks for even though we do not use it here
## and for libapt-pkg-dev as we need to force a reinstallation of RcppAPT
RUN apt update -qq \
    && apt upgrade --yes \
    && apt install --yes --no-install-recommends \
           dh-r gpg-agent xvfb git \
           r-cran-remotes r-cran-data.table r-cran-crayon r-cran-httr \
           docker.io links

RUN installGithub.r eddelbuettel/r2u \
    && r -e 'r2u:::.createDefaultConfiguration()'

COPY debBuild.sh /usr/local/bin
COPY r2u.r /usr/local/bin/

CMD ["bash"]
