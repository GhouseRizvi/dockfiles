What is entrypoint ?
it is used to run the container
but here we cannot override the entrypoint but we can override the cmd

We cannot override entrypoint if you try to do so , it'll append to the provided instruction.

for best result use cmd and entrypoint in combination

