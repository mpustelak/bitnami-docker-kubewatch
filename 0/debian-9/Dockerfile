FROM bitnami/minideb:stretch
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages ca-certificates curl libc6 procps unzip wget
RUN wget -nc -P /tmp/bitnami/pkg/cache/ https://raw.githubusercontent.com/mpustelak/kubewatch/master/kubewatch.tar.gz && \
    tar -zxf /tmp/bitnami/pkg/cache/kubewatch.tar.gz -P --transform 's|files|/opt/bitnami|' --wildcards 'files' && \
    rm -rf /tmp/bitnami/pkg/cache/kubewatch.tar.gz

COPY rootfs /
RUN chown -R 1001:root /opt/bitnami/kubewatch/ && chmod g+rwX /opt/bitnami/kubewatch/
ENV BITNAMI_APP_NAME="kubewatch" \
    BITNAMI_IMAGE_VERSION="0.0.4-debian-9-r428" \
    KW_CONFIG="/opt/bitnami/kubewatch" \
    KW_FLOCK_URL="" \
    KW_HIPCHAT_ROOM="" \
    KW_HIPCHAT_TOKEN="" \
    KW_HIPCHAT_URL="" \
    KW_MATTERMOST_CHANNEL="" \
    KW_MATTERMOST_URL="" \
    KW_MATTERMOST_USERNAME="" \
    KW_SLACK_CHANNEL="" \
    KW_SLACK_TOKEN="" \
    KW_WEBHOOK_URL="" \
    PATH="/opt/bitnami/kubewatch/bin:$PATH"

WORKDIR /opt/bitnami/kubewatch
USER 1001
ENTRYPOINT [ "/entrypoint.sh" ]
