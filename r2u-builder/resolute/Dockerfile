## Emacs, make this -*- mode: sh; -*-

FROM rocker/r2u:26.04

LABEL org.label-schema.license="GPL-2.0" \
      org.label-schema.vcs-url="https://github.com/eddelbuettel/r2u" \
      maintainer="Dirk Eddelbuettel <edd@debian.org>"

## This was not needed before but we need it now
ENV DEBIAN_FRONTEND=noninteractive
## Allow Rust packages to be built
ENV CARGO_HOME="/opt/cargo"
ENV RUSTUP_HOME="/opt/rustup"
ENV PATH="/opt/cargo/bin:${PATH}"

## Packages needed for r2u,
## and for docker which r2u checks for even though we do not use it here
## and for libapt-pkg-dev as we need to force a reinstallation of RcppAPT
RUN apt update -qq \
    && apt upgrade --yes \
    && apt install --yes --no-install-recommends \
           dh-r gpg-agent xvfb git curl \
           r-cran-remotes r-cran-data.table r-cran-crayon r-cran-httr \
           docker.io links \
   && curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | bash -s -- -y

## Needed in transition
#RUN Rscript -e 'bspm::disable(); install.packages("data.table", type="source")'

RUN installGithub.r eddelbuettel/r2u \
    && r -e 'r2u:::.createDefaultConfiguration()'

COPY debBuild.sh /usr/local/bin
COPY r2u.r /usr/local/bin/

CMD ["bash"]
