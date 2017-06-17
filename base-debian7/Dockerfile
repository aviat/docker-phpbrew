FROM debian:7

ENV DEBIAN_FRONTEND noninteractive

# Add source repositories
RUN sed 's/^deb /deb-src /' /etc/apt/sources.list > /etc/apt/sources.list.d/deb-src.list

# These commands come from:
# https://github.com/phpbrew/phpbrew/wiki/Requirement

RUN apt-get update && apt-get build-dep -qy \
    -o APT::Install-Recommends=false        \
    -o APT::Install-Suggests=false          \
    php5

# libgd3 and libgd3-dev where removed from this list:

RUN apt-get update &&                \
    apt-get install -qy              \
    -o APT::Install-Recommends=false \
    -o APT::Install-Suggests=false   \
    php5                             \
    php5-dev                         \
    php-pear                         \
    autoconf                         \
    automake                         \
    curl                             \
    libcurl3-openssl-dev             \
    build-essential                  \
    libxslt1-dev                     \
    re2c                             \
    libxml2                          \
    libxml2-dev                      \
    php5-cli                         \
    bison                            \
    libbz2-dev                       \
    libreadline-dev                  \
    libfreetype6                     \
    libfreetype6-dev                 \
    libpng12-0                       \
    libpng12-dev                     \
    libjpeg-dev                      \
    libjpeg8-dev                     \
    libjpeg8                         \
    libxpm4                          \
    libltdl7                         \
    libltdl-dev                      \
    libssl-dev                       \
    openssl                          \
    gettext                          \
    libgettextpo-dev                 \
    libgettextpo0                    \
    libicu-dev                       \
    libmhash-dev                     \
    libmhash2                        \
    libmcrypt-dev                    \
    libmcrypt4

RUN apt-get update &&                \
    apt-get install -qy              \
    -o APT::Install-Recommends=false \
    -o APT::Install-Suggests=false   \
    curl                             \
    ca-certificates                  \
    vim

RUN curl -L -O https://github.com/phpbrew/phpbrew/raw/master/phpbrew > phpbrew
RUN chmod +x phpbrew && mv phpbrew /usr/local/bin/

RUN phpbrew init

RUN echo export PHPBREW_SET_PROMPT=1 >> /root/.bashrc && \
    echo source /root/.phpbrew/bashrc >> /root/.bashrc

# Move phpbrew to somewhere can be found by your $PATH
# sudo mv phpbrew /usr/local/bin/phpbrew


