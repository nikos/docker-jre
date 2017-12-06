FROM centos:7

ENV PATH="/opt/local/sbin:/opt/local/bin:${PATH}" \
    JAVA_HOME="/opt/java"

RUN \
    set -x && \
    pushd /opt && \
    curl \
        --location \
        --silent \
        --show-error \
        --header "Cookie: oraclelicense=accept-securebackup-cookie" \
        http://download.oracle.com/otn-pub/java/jdk/9.0.1+11/jre-9.0.1_linux-x64_bin.tar.gz | tar xz && \
    mv jre* java && \
    if [ ! -d "/opt/local/bin" ]; then mkdir -p "/opt/local/bin"; fi && \
    pushd local/bin && \
    for FILE in "${JAVA_HOME}/bin/"*; do ln -s "${FILE}" "$(basename ${FILE})"; done
