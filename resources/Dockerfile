FROM rocker/tidyverse:4.5.3@sha256:913d87bd9b81480b97bd4fc18e619e71d12b0a034bc80bb841830ac10278fd1a

ENV DEBIAN_FRONTEND=noninteractive
ENV JAVA_HOME=/usr/lib/jvm/java-11-openjdk-current
ENV PATH=/usr/lib/jvm/java-11-openjdk-current/bin:${PATH}

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
    openjdk-11-jdk \
    wget \
    libpng-dev \
    libicu-dev \
    libpcre2-dev \
    libdeflate-dev \
    libzstd-dev \
    liblzma-dev \
    libbz2-dev \
    zlib1g-dev \
 && arch="$(dpkg --print-architecture)" \
 && ln -sfn "/usr/lib/jvm/java-11-openjdk-${arch}" "${JAVA_HOME}" \
 && printf 'JAVA_HOME=%s\n' "${JAVA_HOME}" >> /usr/local/lib/R/etc/Renviron.site \
 && R CMD javareconf \
 && rm -rf /var/lib/apt/lists/*

RUN install2.r --error --deps TRUE \
    rJava \
    tabulapdf \
    here
