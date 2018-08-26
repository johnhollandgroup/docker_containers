FROM alpine as build

RUN apk update && apk --no-cache add bash py-pip && apk --no-cache add --virtual=build gcc libffi-dev musl-dev openssl-dev python-dev make curl openssl wget unzip
RUN curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get | bash
RUN wget --quiet https://releases.hashicorp.com/terraform/0.11.8/terraform_0.11.8_linux_amd64.zip \
  && unzip terraform_0.11.8_linux_amd64.zip \
  && mv terraform /usr/bin

FROM alpine as final

COPY --from=build /usr/bin/terraform /usr/bin/terraform
COPY --from=build /usr/local/bin/helm /usr/local/bin/helm
RUN apk update && apk add bash py-pip && apk add --virtual=build gcc libffi-dev musl-dev openssl-dev python-dev make && pip install azure-cli && \
  apk del --purge build 