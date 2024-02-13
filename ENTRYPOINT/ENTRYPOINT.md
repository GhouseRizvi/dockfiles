What is entrypoint ?
it is used to run the container
but here we cannot override the entrypoint but we can override the cmd

We cannot override entrypoint if you try to do so , it'll append to the provided instruction.

for best result use cmd and entrypoint in combination

if we use CMD and entrypoint in combination, cmd will act as a argument provider
like 
CMD ["google.com"]
ENTRYPOINT["ping","-c5"]
here whenever run this container cmd will act as argument provider
and we can override also here since cmd is a argument provider.

CMD is the default argument to the entrypoint.
like ENTRYPOINT ["nginx","-g","daemon off;"]