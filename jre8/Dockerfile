FROM centos:7

ENV PATH="/opt/local/sbin:/opt/local/bin:${PATH}" \
    JAVA_HOME="/opt/java"

RUN \
    set -x && \
    yum -y install \
        unzip \
    && \
    yum -y clean all && \
    rm -rf /var/cache/yum && \
    pushd /opt && \
    curl \
        --location \
        --silent \
        --show-error \
        --header "Cookie: oraclelicense=accept-securebackup-cookie" \
        http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/server-jre-8u144-linux-x64.tar.gz | tar xz && \
    mv jdk* java && \
    if [ ! -d "/opt/local/bin" ]; then mkdir -p "/opt/local/bin"; fi && \
    pushd local/bin && \
    for FILE in "${JAVA_HOME}/bin/"*; do ln -s "${FILE}" "$(basename ${FILE})"; done && \
    curl \
        --location \
        --silent \
        --show-error \
        --header "Cookie: oraclelicense=accept-securebackup-cookie" \
        --output /tmp/jce_policy-8.zip \
        http://download.oracle.com/otn-pub/java/jce/8/jce_policy-8.zip && \
    unzip -d /tmp /tmp/jce_policy-8.zip && \
    cp /tmp/UnlimitedJCEPolicyJDK8/*.jar "${JAVA_HOME}/jre/lib/security" && \
    rm -rf /tmp/{UnlimitedJCEPolicyJDK8,jce_policy-8.zip}
    