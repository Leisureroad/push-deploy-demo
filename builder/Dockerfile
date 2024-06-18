FROM ubuntu:18.04
RUN apt-get update && \
    apt-get install -y wget gnupg2 unzip git jq \
                       apt-transport-https ca-certificates \
                       dnsutils curl gettext

ENV KUBECTL_VERSION=1.16.1
ENV GO_VERSION=1.14.2

# Install kubectl
RUN wget -q https://storage.googleapis.com/kubernetes-release/release/v${KUBECTL_VERSION}/bin/linux/amd64/kubectl && \
    chmod +x kubectl && \
    mv kubectl /usr/local/bin/

# Install gcloud
RUN echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | tee -a /etc/apt/sources.list.d/google-cloud-sdk.list && \
    wget -O- https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key --keyring /usr/share/keyrings/cloud.google.gpg add - && \
    apt-get update && \
    apt-get install -y google-cloud-sdk && \
    apt-get install -y google-cloud-sdk-gke-gcloud-auth-plugin
