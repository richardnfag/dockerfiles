FROM debian:stable-slim as builder

WORKDIR /usr/src/blog/

RUN apt -y update
RUN apt -y --no-install-recommends install \
        python3 python3-tk libpython3-dev python3-pip \
        r-base r-cran-littler r-base-dev \
        pandoc littler gcc-8-base

RUN R -e 'install.packages(c("blogdown", "reticulate"))'; \
    R -e 'blogdown::install_hugo()'
