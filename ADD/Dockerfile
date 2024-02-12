FROM almalinux
ADD https://raw.githubusercontent.com/awslabs/git-secrets/master/CODE_OF_CONDUCT.md /tmp/
ADD dockerfiles-master.zip /tmp/
WORKDIR /tmp/
RUN yum install zip unzip -y
RUN unzip dockerfiles-master.zip