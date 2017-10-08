FROM n7lab/development-base

ENV JAVA_HOME=/opt/java

RUN \
    set -x && \
    pushd /opt && \
    curl \
        --location \
        --silent \
        --show-error \
        --header "Cookie: oraclelicense=accept-securebackup-cookie" \
        http://download.oracle.com/otn-pub/java/jdk/9+181/jdk-9_linux-x64_bin.tar.gz | tar xz && \
    mv jdk* java && \
    pushd local/bin && \
    for FILE in "${JAVA_HOME}/bin/"*; do ln -s "${FILE}" "$(basename ${FILE})"; done
    