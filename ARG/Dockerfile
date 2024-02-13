ARG Version
FROM almalinux:${Version:-8}
#above default value 8 is provided if user is not explicitly provided.
# and it is the only instruction before From
#once it is declared above FROM cannot be accessed after FROM.

ARG Greeting="Hello Good Morning"
RUN echo "$Greeting"
ENV Greet=${Greeting}
RUN echo "$Version"