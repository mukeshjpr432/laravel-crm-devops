FROM jenkins/jenkins:lts

USER root

RUN apt-get update && apt-get install -y \
    curl \
    wget \
    unzip \
    git \
    gnupg \
    lsb-release \
    apt-transport-https \
    ca-certificates

# Docker CLI
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /usr/share/keyrings/docker.gpg

RUN echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker.gpg] \
  https://download.docker.com/linux/debian bookworm stable" \
  > /etc/apt/sources.list.d/docker.list

RUN apt-get update && apt-get install -y docker-ce-cli

# Kubectl
RUN curl -LO "https://dl.k8s.io/release/v1.34.1/bin/linux/amd64/kubectl"

RUN install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

# Trivy
RUN wget -qO - https://get.trivy.dev/deb/public.key | gpg --dearmor | tee /usr/share/keyrings/trivy.gpg > /dev/null

RUN echo "deb [signed-by=/usr/share/keyrings/trivy.gpg] https://get.trivy.dev/deb generic main" \
    | tee /etc/apt/sources.list.d/trivy.list

RUN apt-get update && apt-get install -y trivy

# PHP + Extensions
RUN apt-get install -y \
    php \
    php-cli \
    php-mysql \
    php-xml \
    php-mbstring \
    php-curl \
    php-zip \
    php-gd \
    php-bcmath

# Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

USER jenkins
