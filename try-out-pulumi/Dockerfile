#https://nodejs.org/en/download/package-manager/

#FROM mcr.microsoft.com/azure-cli
FROM amd64/ubuntu:20.04
#RUN add nodejs npm
#RUN apk add docker
ENV DEBIAN_FRONTEND=noninteractive 
RUN apt-get update && apt-get install -y nodejs npm 
RUN apt install -y apt-transport-https ca-certificates curl software-properties-common
RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
RUN add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
RUN apt-cache policy docker-ce
RUN apt install -y docker-ce

#RUN addgroup root docker
RUN curl -fsSL https://get.pulumi.com | sh
RUN curl -L -o go.tar.gz https://go.dev/dl/go1.18.linux-amd64.tar.gz
RUN rm -rf /usr/local/go && tar -C /usr/local -xzf go.tar.gz
RUN curl -sL https://aka.ms/InstallAzureCLIDeb | bash

ENV PATH="/usr/local/go/bin:${PATH}"
ENV PATH="/root/.pulumi/bin/:${PATH}"