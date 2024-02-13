FROM almalinux
RUN yum install httpd -y
# when image creator running this onbuild would not run
# When someone else using this then it'll run
ONBUILD ADD simple.txt /tmp/
ONBUILD RUN echo "Hello"