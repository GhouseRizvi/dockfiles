FROM almalinux
ADD https://raw.githubusercontent.com/awslabs/git-secrets/master/CODE_OF_CONDUCT.md /tmp/
ADD dockerfiles-master.zip /tmp/
RUN cd /tmp/
RUN yum install zip unzip -yum
RUN unzip dockerfiles-master.zip